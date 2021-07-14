# JavaScript Function Study 

### Function
- 함수는 input과 output 이 중요하다.
- 프로그램을 설명하는 기본적인 building block 이다.
- 서브 프로그램이라고도 불리며 여러번 재사용이 가능하다.
- 대체적으로 한가지의 task 어떠한 값을 계산하는데 사용된다.
--------------
##### 1. JavaScript에서의 Function declaration
- function name(param1, param2) { body... return; }
 - function 키워드를 사용하고, 이름을 정의하고, 파라미터들을 나열하고, 함수안에 비즈니스 로직을 작성한 후 리턴해 준다.
- 하나의 함수는 한가지 동작만 하도록 만들어야 한다.
- 함수의 이름을 작성할 땐 무언가를 동작하는것이기 때문에 command, verb 형태로 지정해야 한다.
- javascript에서 function은 object이다.
``` javascript
function printHello() {
    console.log('hello');
}
printHello();
``` 
``` javascript
function log(message) {
    console.log(message);
}
log('hello@');
``` 

사용하는 사람이 숫자를 전달할 수도 있는데, 다른함수에서 타입이 중요한 경우 javascript는 난해 할 수있다.
타입스크립트 playground에 타입스크립트로 작성하면 자바스크립트로 작성한것을 볼 수 있다.
``` typescript
function log2(message: string): number {
    console.log(message);
    return 0;
}
```
타입스크립트로 타입을 작성하여 함수를 정의할 수 있다.

-------------
##### 2. Parameters
- Premitive parameters: passed by value 메모리에 value가 그대로 저장됨
- object parameter: passed by reference 메모리에 reference가 저장됨
 - 오브젝트는 레퍼런스로 전달되기 때문에 함수안에서 오브젝트의 값을 변경하게 되면 그변경된 사항이 그대로 메모리에 적용된다.
``` javascript
function changeName(obj) {
    obj.name = 'coder';
}
const dongho = {name: 'dongho'};
changeName(dongho);
console.log(dongho);
```
---------

##### 3. Default Parameters (added in ES6)
``` javascript
function showMessage(message,from = 'dongho') {
    console. log('${message} by ${from}');
}
showMessage('Hi!');
``` 
from 부분에 넣어준 값이 없어 unknown이라고 표현된다.
es5에는 없었지만 현재는 파라미터 옆에 원하는 default 값을 지정할 수 있다.

-----
##### 4. Rest parameters  (added in ES6)
- ...을 작성하게 되면 배열형태로 전달되게 된다. 
``` javascript
function printAll(...args) {
    for(let i =0; i <args.length; i++)
    {
        console.log(args[i]);
    }
    // 다른 형태의 for loop
    for(const arg of args) {
        console.log(arg);
    }
    // for each 사용
    args.forEach((arg) => console.log(arg));
}
```
printAll('learn','javascript','cool');
인자를 세개 전달 했다. args는 즉 3개가 담긴 배열이다.
배열 args의 갯수만큼 출력한다. 

------

##### 5. Local Scope
``` javascript
let globalMessage = 'gloval'; // global variable
function printMessage() {
    let message = 'hello'; // local variable
    console.log(message);
    console.log(globalMessage);
}
printMessage();
``` 
- 밖에서는 안이 보이지 않고, 안에서만 밖을 볼 수 있다.
  - 안에서는 외부에서 선언된 변수를 사용할 수 있지만, 외부에선 함수내에서 선언된 변수를 사용할 수 없다.
-----------

##### 6. Return a Value
``` javascript
function sum(a,b) {
    return a+b;
}
const result = sum(1,2); 
console.log('sum: ${sum(1,2)}');
```
return 타입이 없는 함수들은 default로 
return undefined가 들어가 있는거고 이게 생략이 가능한 것이다. 

##### 7. Early return, early exit
- 현업에서 종종 이렇게 지적이 들어올 수 있다. 
``` javascript
//bad 
function upgradeUser(uesr) {
    if(uesr.point > 10) {
        // wrong upgrade logic
    }
}
```
