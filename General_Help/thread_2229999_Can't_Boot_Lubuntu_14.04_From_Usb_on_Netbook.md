---
title: "Can't Boot Lubuntu 14.04 From Usb on Netbook"
date: 2014-06-16
forum: General Help
---

### Post by john246 on 2014-06-16
Hello. I have an old netbook in my house and it is having problems with Windows 7 and is frustratingly slow. I don't mean slow as in internet speed, but rather with viewing folders, opening up small applications, etc. I suspect there is something wrong with the hard drive as it is nearly 5 years old and is usually the first thing to go on a computer. I had the similar situation with my desktop. In an effort to see if it was simply a hard drive issue, I wanted to create a bootable OS in order to test it out. I burnt Lubuntu 14.04 32bit onto a Usb drive and it worked fine on my desktop. However, when I try to do it on the netbook, I get a black screen with a blinking underscore. Does anyone have any suggestions on what the problem may be? I appreciate any/all replies. Thank you.

---

### Post by mörgæs on 2014-06-16
Hi, welcome to the fora.

I guess that you have Nvidia graphics and that the **nomodeset** boot option will do the trick.

---

### Post by john246 on 2014-06-16
Hi [[COLOR=#000000]**mörgæs**[/COLOR]]("http://ubuntuforums.org/member.php?u=939075"), it probably does have an Nvidia graphics card. How would I go about finding the option to use the **nomodeset** feature? Thanks for the reply!

---

### Post by john246 on 2014-06-16
By the way, I simply want to run it from the USB drive. Thanks.

---

### Post by mörgæs on 2014-06-17
By pushing F6 from the boot menu:
[http://i.stack.imgur.com/FfEwE.png](http://i.stack.imgur.com/FfEwE.png)

---

### Post by john246 on 2014-06-17
Thanks for telling me that, but when I insert the USB, it straight up goes to a black screen with the blinking underscore. It doesn't even give me a selection to chose from the boot menu in the linux OS.

---

### Post by mörgæs on 2014-06-17
If you repeatedly press left Shift during boot do you get to a menu?

---

### Post by john246 on 2014-06-19
Sorry for the late reply. I do not get anything when pressing shift. I am probably going to burn a different linux OS onto the USB and test it out. Do you recommend any others? I just thought Lubuntu would have been nice as it is lightweight and has all the Ubuntu capabilities.

---

### Post by mörgæs on 2014-06-20
Yes. Lubuntu is a good option. You should be able to see the F6 menu there.

---

