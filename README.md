# Calculator

---------

**계산기 구현**

>숫자를 누르면 라벨에 뜨워주고 연산자를 누르고 숫자를 누르면 새로운 숫자가 라벨에 나오고 equl버튼을 누르면 결과값을 도출한다. 


1+2 = 누르면 3이 나온다. 

구현 부분을 살펴보자

1. 버튼 동그랗게 radius 부여하기. outletCollection을 이용하여 한 번에 적용해 주었다. 

>```swift
>@IBOutlet var allButtons: [UIButton]!
>override func viewDidLoad() {
>        super.viewDidLoad()
>        // Do any additional setup after loading the view.
>        setLayout()
>        
>    }
>func setLayout(){
>        allButtons.forEach({
>            $0.layer.cornerRadius = $0.layer.frame.size.height  * 0.44
>        })
>    }
>```
>
><img width="350" alt="image-20200511230031404" src="https://user-images.githubusercontent.com/49120090/81570213-3dab9f80-93db-11ea-957b-40c7f26b88f0.png">
>
>아울렛은 좌측 동그라미 버튼을 끌어 적용시켜줄 버튼에 연결해주었다. 

2. 숫자를 눌렀을 때 label에 보여주기

>```swift
>@IBAction func buttonTapped(_ sender: UIButton) {
>        let button = sender.titleLabel?.text
>        
>        if tapped {
>            resultLabel.text = resultLabel.text!+button!
>        }else{
>            resultLabel.text = button!
>            tapped = true
>        }
>        
>    }
>```
>
>마찬가지로 func 옆의 버튼을 이용하여 숫자 버튼만 적용해주어 숫자 버튼을 누른 경우만 띄워주도록 해주었다. 

3. plus button을 눌렀을 때의 action

>```swift
>@IBAction func plusButton(_ sender: UIButton) {
>        if isPlus == false {
>            num! = (Int(resultLabel.text!)!)
>            tapped = false
>            isPlus = true
>        }
>        
>    }
>```
>
>플러스 버튼이 눌리면 그 때 라벨에 있는 text를 읽어와 정수형으로 변환하여 num에 저장한다. 

4. equal button을 눌렀을 때의 action

>```swift
>@IBAction func equalButton(_ sender: UIButton) {
>        if isPlus{
>            num2! = (Int(resultLabel.text!)!)
>            
>            print(num2!)
>            sum = num2! + num!
>        }
>  isPlus = true
>  resultLabel?.text = String(sum!)
>```
>
>equal 버튼이 눌리면 결과값을 반환해주어야하는데 equal button이 눌렸을 때 라벨에서 text를 읽어와 정수형을 변환을 한 후 num2에 저장을 한다 . 그리고 처음 입력한 숫자가 저장되어있는 num과 num2의 연산을 하고 String 으로 변환하여 반환한다. 
>
>다른 사칙연산 또한 마찬가지로 구현하였다. 




