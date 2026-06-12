---
title: "Can't make Palm Detect really work"
date: 2022-01-27
forum: General Help
---

### Post by Ralph L on 2022-01-27
I have an Aspire E5-575G laptop running Xubuntu 18.04. xinput -list says it uses an "ELAN0501:00 04F3:3019 Touchpad" (really a Clickpad). I am a thumb clicker, and a palm dragger--particularly with the heal of my right hand. I like to use the vertical scroll bar along the right side of the touchpad so I have it enabled. My major palm drag problem is when I begin typing and move my right hand fingers to the "jkl" keys. I usually drag over the vertical scroll bar and send the cursor to "who knows where". Recently I looked at laptops in Costco. Of course, they all ran Windows. I was pleasantly surprised how well they handled palm detect with vertical scrolling enabled. I tried several times on several different laptiops to "cause problems" with the heal of my hand passing over the vertical scroll bar. The Windows system correctly detected my palm (didn't detect it as a finger) every time and the cursor didn't fly all over the place. In fact it never moved. So I know it is possible to have a large clickpad that behaves correctly. Does anyone know how to get clickpads on linux working as well as they do on Windows--especially with regard to Palm Detect)????
I can't make the synaptics PalmDetect feature really work. I have listed all the synaptics settings by entering "synclient" into Terminal. Since I am not a finger tapper I have "tap to click" turned off, as well as all one, two, and 3 finger taps and scrolls.  I have PalmDetect=1, PalmMinWidth=4, PalmMinZ=50--trying to make only the smallest possible area be detected as a finger.. However, I can change PalmMinWidth and PalmMinZ to almost anything and it seems to make no difference. Even with PalmMinWidth and PalmMinZ set to 1, slight palm touches are still detected as a finger. I also have RightEdge=3185 very close to the physical right edge of the touchpad to try to make the width of the vertical scrollbar as narrow as possible. The RightEdge feature works, but setting the scroll bar very narrow doesn't seem to keep the system from detecting the heal of my hand as a finger touch.
Oh, I also have "syndaemon -i 1.5 -d -R" in my "Sessions and Startup". That's to disable the touchpad during typing and hold it disabled for 0.8 seconds. I got this setting from [https://askubuntu.com/questions/192566/how-do-i-verify-that-syndaemon-is-disabling-the-touchpad-while-i-type](https://askubuntu.com/questions/192566/how-do-i-verify-that-syndaemon-is-disabling-the-touchpad-while-i-type) . 
I've googled a lot and not found anything that worked. Also, I understand that wayland in newer systems no longer use synaptics. Does anybody know if that works better???

Any help in making my clickpad better behaved would be much appreciated........

---

