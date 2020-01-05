# Bed-Time-Fan

##  Bed Time Fan With Sound. 

Added Some screens here.

![](https://github.com/pawankv89/Bed-Time-Fan/blob/master/images/screen_1.png)
![](https://github.com/pawankv89/Bed-Time-Fan/blob/master/images/screen_2.png)
![](https://github.com/pawankv89/Bed-Time-Fan/blob/master/images/screen_3.png)
![](https://github.com/pawankv89/Bed-Time-Fan/blob/master/images/screen_4.png)

## Usage

#### Controller

``` swift 

import UIKit
import AVFoundation

class ViewController: UIViewController {
    
    @IBOutlet weak var stackView: UIStackView!
    
    @IBOutlet weak var fanImageView: UIImageView!
    
     @IBOutlet weak var button_1: UIButton!
     @IBOutlet weak var button_2: UIButton!
     @IBOutlet weak var button_3: UIButton!
     @IBOutlet weak var button_4: UIButton!
     @IBOutlet weak var button_5: UIButton!
     @IBOutlet weak var button_6: UIButton!
    
    var timeInterval: Double = 0.01
    var animationRotation: Double = 10
    var animation: CGFloat = 0
    var timer = Timer()
    var timerSlow = Timer()
    
    var button_1_isOn: Bool = false
    var button_2_isOn: Bool = false
    var button_3_isOn: Bool = false
    var button_4_isOn: Bool = false
    var button_5_isOn: Bool = false
    var button_6_isOn: Bool = false
    
    let radiansToDegrees: (CGFloat) -> CGFloat = {
              return $0 * (180.0 / CGFloat.pi)
          }
         
    let degreesToRadians: (CGFloat) -> CGFloat = {
              return $0 / 180.0 * CGFloat.pi
          }
    
    
    var fanRunningSoundEffect: AVAudioPlayer?
    var fanOnSoundEffect: AVAudioPlayer?
    var fanOffSoundEffect: AVAudioPlayer?
    var buttonPrassedType: Double = 0
    
    override func didRotate(from fromInterfaceOrientation: UIInterfaceOrientation) {
        var text=""
        switch UIDevice.current.orientation {
        case .portrait:
            text="Portrait"
            self.stackView.axis = .vertical
        case .portraitUpsideDown:
            text="PortraitUpsideDown"
            self.stackView.axis = .vertical
        case .landscapeLeft:
            text="LandscapeLeft"
            self.stackView.axis = .horizontal
        case .landscapeRight:
            text="LandscapeRight"
            self.stackView.axis = .horizontal
        default:
            text="Another"
        }
        NSLog("You have moved: \(text)")
    }
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
    }
    
    override func viewWillAppear(_ animated: Bool) {
        super.viewWillAppear(animated)
        
        if #available(iOS 12.0, *) {
            if self.traitCollection.userInterfaceStyle == .dark {
                // User Interface is Dark
                
                fanImageView.image = fanImageView.image?.withRenderingMode(.alwaysTemplate)
                fanImageView.tintColor = UIColor.white
                
            } else {
                // User Interface is Light
                
                fanImageView.image = fanImageView.image?.withRenderingMode(.alwaysTemplate)
                fanImageView.tintColor = UIColor.white
            }
        } else {
            // Fallback on earlier versions
            fanImageView.image = fanImageView.image?.withRenderingMode(.alwaysTemplate)
            fanImageView.tintColor = UIColor.white
        }
        
    }
    
    @objc func timerStop() {
        
        var fanAnimation: CGFloat = 0
        
        if timerSlow != nil {
            timerSlow.invalidate()
        }
        
        playOffFanSound()
        
        timerSlow = Timer.scheduledTimer(withTimeInterval: 1/20, repeats: true, block: {_ in
        
            self.timer.invalidate()
            //Play Fan Sound Stop
            self.fanRunningSoundEffect?.stop()
            
            let transform = CGAffineTransform(rotationAngle: self.degreesToRadians(fanAnimation));
            
            if fanAnimation >= 360 {
                fanAnimation = 0
                self.timerSlow.invalidate()
                //Play Fan Sound Stop
                self.fanOffSoundEffect?.stop()
            }
                
            self.fanImageView.transform = transform
                
            fanAnimation = fanAnimation + CGFloat(10)
        })
    }
    
    @objc func timerReset1() {
        
        //Fast Speed
        animationRotation = 10
        timeInterval = 1/20
        
        timer.invalidate()
        
        // start the timer
        timer = Timer.scheduledTimer(timeInterval: timeInterval, target: self, selector: #selector(timerUpdate), userInfo: nil, repeats: true)
        
        //Play Fan Sound Stop
        fanRunningSoundEffect?.stop()
        //Play Fan Sound
        playFanSound()
        
    }
    
    @objc func timerReset2() {
           
        //Fast Speed
        animationRotation = 11
        timeInterval = 1/25
        
        timer.invalidate()
           
           // start the timer
           timer = Timer.scheduledTimer(timeInterval: timeInterval, target: self, selector: #selector(timerUpdate), userInfo: nil, repeats: true)
           
        //Play Fan Sound Stop
        fanRunningSoundEffect?.stop()
        //Play Fan Sound
        playFanSound()
        
       }
    
    @objc func timerReset3() {
           
        //Fast Speed
        animationRotation = 12
        timeInterval = 1/30
        
        timer.invalidate()
           
           // start the timer
           timer = Timer.scheduledTimer(timeInterval: timeInterval, target: self, selector: #selector(timerUpdate), userInfo: nil, repeats: true)
           
        //Play Fan Sound Stop
        fanRunningSoundEffect?.stop()
        //Play Fan Sound
        playFanSound()
    
       }
    
    @objc func timerReset4() {
        
        //Fast Speed
        animationRotation = 13
        timeInterval = 1/35
        
        timer.invalidate()
           
           // start the timer
           timer = Timer.scheduledTimer(timeInterval: timeInterval, target: self, selector: #selector(timerUpdate), userInfo: nil, repeats: true)
          
        //Play Fan Sound Stop
        fanRunningSoundEffect?.stop()
        //Play Fan Sound
        playFanSound()
        
       }
    @objc func timerReset5() {
           
        //Fast Speed
        animationRotation = 14
        timeInterval = 1/40
        
        timer.invalidate()
           
           // start the timer
           timer = Timer.scheduledTimer(timeInterval: timeInterval, target: self, selector: #selector(timerUpdate), userInfo: nil, repeats: true)
           
        //Play Fan Sound Stop
        fanRunningSoundEffect?.stop()
        //Play Fan Sound
        playFanSound()
        
       }
    @objc func timerReset6() {
        
       //Fast Speed
       animationRotation = 15
       timeInterval = 1/45
        
       timer.invalidate()
           
           // start the timer
           timer = Timer.scheduledTimer(timeInterval: timeInterval, target: self, selector: #selector(timerUpdate), userInfo: nil, repeats: true)
           
        //Play Fan Sound Stop
        fanRunningSoundEffect?.stop()
        //Play Fan Sound
        playFanSound()
        
       }

    // called every time interval from the timer
    @objc func timerUpdate() {
        
        if animation >= 360 {
            //animation = 90
            animation = 10

        }
        
        let transform = CGAffineTransform(rotationAngle: self.degreesToRadians(self.animation));
            
        self.fanImageView.transform = transform
            
        self.animation = self.animation + CGFloat(animationRotation)
            
        print("animation " + String(describing: self.animation))
      
    }

    func buttonPrassed(sender: UIButton) -> () {
        
        let switch_on: String = "switch_on_1"
        let switch_off: String = "switch_off_1"
        
        if buttonPrassedType == 1 {
            
            button_1.setBackgroundImage(UIImage(named: switch_on), for: .normal)
            button_2.setBackgroundImage(UIImage(named: switch_off), for: .normal)
            button_3.setBackgroundImage(UIImage(named: switch_off), for: .normal)
            button_4.setBackgroundImage(UIImage(named: switch_off), for: .normal)
            button_5.setBackgroundImage(UIImage(named: switch_off), for: .normal)
            button_6.setBackgroundImage(UIImage(named: switch_off), for: .normal)
            
            let buttonImage: String = (button_1_isOn == true) ? switch_on : switch_off
            button_1.setBackgroundImage(UIImage(named: buttonImage), for: .normal)
            
            button_2_isOn = false
            button_3_isOn = false
            button_4_isOn = false
            button_5_isOn = false
            button_6_isOn = false
            
        } else if buttonPrassedType == 2 {
            
            button_1.setBackgroundImage(UIImage(named: switch_on), for: .normal)
            button_2.setBackgroundImage(UIImage(named: switch_on), for: .normal)
            button_3.setBackgroundImage(UIImage(named: switch_off), for: .normal)
            button_4.setBackgroundImage(UIImage(named: switch_off), for: .normal)
            button_5.setBackgroundImage(UIImage(named: switch_off), for: .normal)
            button_6.setBackgroundImage(UIImage(named: switch_off), for: .normal)
            
            let buttonImage: String = (button_2_isOn == true) ? switch_on : switch_off
            button_2.setBackgroundImage(UIImage(named: buttonImage), for: .normal)
            
            button_1_isOn = true
            button_3_isOn = false
            button_4_isOn = false
            button_5_isOn = false
            button_6_isOn = false
            
        } else if buttonPrassedType == 3 {
            
            button_1.setBackgroundImage(UIImage(named: switch_on), for: .normal)
            button_2.setBackgroundImage(UIImage(named: switch_on), for: .normal)
            button_3.setBackgroundImage(UIImage(named: switch_on), for: .normal)
            button_4.setBackgroundImage(UIImage(named: switch_off), for: .normal)
            button_5.setBackgroundImage(UIImage(named: switch_off), for: .normal)
            button_6.setBackgroundImage(UIImage(named: switch_off), for: .normal)
            
            let buttonImage: String = (button_3_isOn == true) ? switch_on : switch_off
            button_3.setBackgroundImage(UIImage(named: buttonImage), for: .normal)
            
            button_1_isOn = true
            button_2_isOn = true
            button_4_isOn = false
            button_5_isOn = false
            button_6_isOn = false
                   
        } else if buttonPrassedType == 4 {
            
            button_1.setBackgroundImage(UIImage(named: switch_on), for: .normal)
            button_2.setBackgroundImage(UIImage(named: switch_on), for: .normal)
            button_3.setBackgroundImage(UIImage(named: switch_on), for: .normal)
            button_4.setBackgroundImage(UIImage(named: switch_on), for: .normal)
            button_5.setBackgroundImage(UIImage(named: switch_off), for: .normal)
            button_6.setBackgroundImage(UIImage(named: switch_off), for: .normal)
            
            let buttonImage: String = (button_4_isOn == true) ? switch_on : switch_off
            button_4.setBackgroundImage(UIImage(named: buttonImage), for: .normal)
            
            button_1_isOn = true
            button_2_isOn = true
            button_3_isOn = true
            button_5_isOn = false
            button_6_isOn = false
                
        } else if buttonPrassedType == 5 {
            
            button_1.setBackgroundImage(UIImage(named: switch_on), for: .normal)
            button_2.setBackgroundImage(UIImage(named: switch_on), for: .normal)
            button_3.setBackgroundImage(UIImage(named: switch_on), for: .normal)
            button_4.setBackgroundImage(UIImage(named: switch_on), for: .normal)
            button_5.setBackgroundImage(UIImage(named: switch_on), for: .normal)
            button_6.setBackgroundImage(UIImage(named: switch_off), for: .normal)
            
            let buttonImage: String = (button_5_isOn == true) ? switch_on : switch_off
            button_5.setBackgroundImage(UIImage(named: buttonImage), for: .normal)
            
            button_1_isOn = true
            button_2_isOn = true
            button_3_isOn = true
            button_4_isOn = true
            button_6_isOn = false
        
        } else if buttonPrassedType == 6 {
            
            button_1.setBackgroundImage(UIImage(named: switch_on), for: .normal)
            button_2.setBackgroundImage(UIImage(named: switch_on), for: .normal)
            button_3.setBackgroundImage(UIImage(named: switch_on), for: .normal)
            button_4.setBackgroundImage(UIImage(named: switch_on), for: .normal)
            button_5.setBackgroundImage(UIImage(named: switch_on), for: .normal)
            button_6.setBackgroundImage(UIImage(named: switch_on), for: .normal)
            
            let buttonImage: String = (button_6_isOn == true) ? switch_on : switch_off
            button_6.setBackgroundImage(UIImage(named: buttonImage), for: .normal)
            
            button_1_isOn = true
            button_2_isOn = true
            button_3_isOn = true
            button_4_isOn = true
            button_5_isOn = true
        }
        
        let path = Bundle.main.path(forResource: "fan_button_sound.mp3", ofType:nil)!
        let url = URL(fileURLWithPath: path)

        do {
            fanOnSoundEffect = try AVAudioPlayer(contentsOf: url)
            fanOnSoundEffect?.play()
                        
        } catch {
            // couldn't load file :(
        }
    }
    
    func playFanSound() -> () {
        
        let path = Bundle.main.path(forResource: "fan_on_sound.mp3", ofType:nil)!
               let url = URL(fileURLWithPath: path)

               do {
                   fanRunningSoundEffect = try AVAudioPlayer(contentsOf: url)
                   fanRunningSoundEffect?.play()
                   fanRunningSoundEffect?.numberOfLoops = -1 //For Play Conntinous without audio time out if Audio Time 1 min then continous play more time
               } catch {
                   // couldn't load file :(
               }
        
    }

    func playOffFanSound() -> () {
        
        let path = Bundle.main.path(forResource: "fan_off_sound.mp3", ofType:nil)!
               let url = URL(fileURLWithPath: path)

               do {
                   fanOffSoundEffect = try AVAudioPlayer(contentsOf: url)
                   fanOffSoundEffect?.play()
               } catch {
                   // couldn't load file :(
               }
        
    }
    
    @IBAction func button1(_ sender: UIButton) {
        
        buttonPrassedType = 1
        
        button_1_isOn = !button_1_isOn
        
        //Update Button Type
        buttonPrassed(sender: sender)
        
        (button_1_isOn == true) ? timerReset1() : timerStop()
        
    }
    @IBAction func button2(_ sender: UIButton) {
        
        buttonPrassedType = 2
        
        button_2_isOn = !button_2_isOn
        
        //Update Button Type
        buttonPrassed(sender: sender)
        
       (button_2_isOn == true) ? timerReset2() : timerReset1()
    
    }
    
    @IBAction func button3(_ sender: UIButton) {
        
        buttonPrassedType = 3
        
        button_3_isOn = !button_3_isOn
        
        //Update Button Type
        buttonPrassed(sender: sender)

       (button_3_isOn == true) ? timerReset3() : timerReset2()
        
    }
    @IBAction func button4(_ sender: UIButton) {
        
        buttonPrassedType = 4
        
        button_4_isOn = !button_4_isOn
        
        //Update Button Type
        buttonPrassed(sender: sender)

        (button_4_isOn == true) ? timerReset4() : timerReset3()
    }
    @IBAction func button5(_ sender: UIButton) {
        
        buttonPrassedType = 5
        
        button_5_isOn = !button_5_isOn
        
        //Update Button Type
        buttonPrassed(sender: sender)
        
       (button_5_isOn == true) ? timerReset5() : timerReset4()
    }
    @IBAction func button6(_ sender: UIButton) {
        
        buttonPrassedType = 6
        
        button_6_isOn = !button_6_isOn
        
        //Update Button Type
        buttonPrassed(sender: sender)
        
       (button_6_isOn == true) ? timerReset6() : timerReset5()
    }
}



``` 

## License

This code is distributed under the terms and conditions of the [MIT license](LICENSE).

## Change-log

A brief summary of each this release can be found in the [CHANGELOG](CHANGELOG.mdown). 


