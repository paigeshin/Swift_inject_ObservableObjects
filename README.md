# Swift_inject_ObservableObjects


```swift

protocol ViewModelProtocol: ObservableObject {
    var name: String { get }
    var nickname: String { get }
}

class ViewModel: ViewModelProtocol {
    var name: String = "" {
        willSet { self.objectWillChange.send() }
    }
    var nickname: String = "" {
        willSet { self.objectWillChange.send() }
    }
}

struct MyView<T: ObservableObject>: View where T: ViewModelProtocol {
    
    @StateObject var vm: T
 
    
    var body: some View {
        VStack {
            Text(vm.name)
        }
        
    }
    
}


```
