---
title: "Video card driver breaks ubuntu..."
date: 2008-02-09
forum: General Help
---

### Post by zac199 on 2008-02-09
Ok so... Im usiing a ATI radeon X1300 video card... and im also using ubuntu 7.10 on a diffrent internal harddrive from my windows...

Ok so heres my problem... When I install ubuntu it works PERFECTLY... I <3 it lol... But when I log on I get the "restricted drivers" pop-up thing... So I click it, activate my video card driver, (its the ATI radeon video driver). Then it says to restart, so I do... now heres my problem...

When I restart it goes to the splash screen, all nice and clean, but when the bar fills, the screen goes black... and just sits there... and from what I see I get 0 hard drive activity... So ya... Every time this happens I have to reinstall ubuntu...

Please help... As soon as this works I should be able to use Wine to play wow... xD then Ill never use vista xD!

---

### Post by Rocket2DMn on 2008-02-09
Hey, this problem is actually fairly common, so I wrote a little tutorial to reconfigure X.  It works for most people - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
You will want to select the "fglrx" driver when prompted if it is available rather than "ati", since fglrx is the restricted driver you install.  Once you get back into the GUI, if something still isn't right, here is the documentation on installing the restricted driver for ATI cards: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-44352176e719033e226dffcab95c6e2647bdb882](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-44352176e719033e226dffcab95c6e2647bdb882)
Good luck!

---

### Post by zac199 on 2008-02-10
Ya still didnt fix it... It still wont boot when I turn on my driver...

---

### Post by Rocket2DMn on 2008-02-10
OK get to a TTY when your blank screen with CTRL+ALT+F1 and run
```
sudo dpkg-reconfigure xserver-xorg -phigh
```  That will autoconfigure and hopefully get you back into the GUI.  
Then you can try to reinstall the fglrx drivers - [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
Try the directions for Ubuntu 7.10, otherwise you may need to follow the directions for Edge (manually install)

---

### Post by zac199 on 2008-02-11
OK i got it to work... reformated it one more time... and found a program called ENVY... which installed the drivers for me... :D thnx for you're help

---

