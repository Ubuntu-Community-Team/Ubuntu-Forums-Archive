---
title: "Headphone jack issues"
date: 2008-02-14
forum: General Help
---

### Post by jasonpeinko on 2008-02-14
When i plug anything into my headphone jack sound still comes out my speakers on my laptop (dv6000). I can hear sound through the headphone jack though too, how can i disable the speakers? there is no way to turn the speakers down in the volume control panel without effecting the headphones.

---

### Post by rahulsharma on 2008-02-14
hey if you are using usb headphones then you need to edit the asoundconf file see thiis link for help
[http://ubuntuforums.org/showthread.php?t=509598](http://ubuntuforums.org/showthread.php?t=509598)
if you are using normal headphones then try this what i use 

right click on the volume icon and check on the mute box to mute it after that left click on the volume icon it will show you to increase or decrease the volume (it should be at zero as you have muted) then click on + sign there till it reaches to maximum(though you can set it to the desired volume you want) and you may note that it will still show a cross sign on the volume icon which symbolizes that laptop speakers are off and you will get sound in headphones only. 
hope this is clear and would be helpful atleast it worked for me ....if it doesn't work then i guess you need some expert :guitar:

---

### Post by jasonpeinko on 2008-02-20
does not work, my friend had a similar laptop model and he said that his were doing the same thing on windows and he had to send it in and it turned out it was a hardware error

---

### Post by monkeymind90 on 2008-02-21
I've been getting the same problem and its definitely not a hardware issue. Check out this link [https://wiki.ubuntu.com/HP_Pavillion_dv6000_%28dv6604nr%29?highlight=%28dv6000%29](https://wiki.ubuntu.com/HP_Pavillion_dv6000_%28dv6604nr%29?highlight=%28dv6000%29) 
I don't know if it works because I can't open alsa-base from terminal for some reason, but I have seen this fix in a few places with positive results. Tell me if you can succesfully open alsa-base in terminal.

---

