---
title: "Logitech G602 extra buttons"
date: 2016-09-08
forum: General Help
---

### Post by Jacob-Gates on 2016-09-08
Hey everyone, I am completely aware that there are many tutorials on how to set up buttons and I have read many of them. I can't get more than the 7 buttons to work (left click, right click, wheel button, scroll up, scroll down, and the extra 2 that are currently set to forward and back). Three of the other buttons only output "1 2 3" respectively when I press them. Two others change the sensitivity of the mouse. And the last one doesn't even get recognized in Ubuntu at all, even when using 'xev' to monitor the button presses.

What I have tried: I created a .conf file in the usr/share/X11/xorg.conf.d with 
```
Section "InputClass"    Identifier "Mouse Remap"
    MatchProduct "Logitech G602"
    MatchDevicePath "/dev/input/event*"
    Option "ButtonMapping" "1 2 3 4 5 6 7 8 9 11 12 13"
EndSection
```

I have also tried using xinput to quickly test some other options like (where "11" is my mouse receiver's xinput list id)
```
xiput set-button-map 11 1 2 3 4 5 6 7 8 9 10 11 12 13
```

Have any of you solved this? Am I just stupid and missing something?

---

### Post by #&amp;thj^% on 2016-09-09
For those with or looking to buy a Logitech G602, the answer is unfortunately Windows for a fix sad I had figured beforehand that it was some kind of assignment issue as I didnt see it possible for 2 different devices to be assigned the same keysym, but thats apparently due to my lack of understanding how such codes are assigned.

I installed the Logitech software on a buddys windows computer and changed the (top 3) buttons to Shift, Alt, and Super- this allows me to use shift/alt/super + left/middle/right click for use within my wm (Mate). This is a permanent change until you change it again, so at least you only need windows once.
And I heard there was a software made for Linux that also would allow some control of the mouse buttons...but the truth be told I have no experience with this as of yet.
It is hosted at Github: [https://pwr.github.io/Solaar/](https://pwr.github.io/Solaar/)
And there was also A PPA here: [https://launchpad.net/~daniel.pavel/+archive/ubuntu/solaar](https://launchpad.net/~daniel.pavel/+archive/ubuntu/solaar)
But that has not had any love for 162 weeks so I would advise to look at the Github link.
Anyway Good luck...and let us know here how it works out.
Kind Regards

---

### Post by Jacob-Gates on 2016-09-11
Sorry I didn't reply earlier, I never got a notification that I had a reply. That's really sad that there isn't much of an answer. I really like to set some of the buttons to more than just a key stroke. I do have dual boot with windows 10 but right now Windows can't figure out I have a logitech mouse plugged up, problems all around with this mouse. I guess I'll try that Solaar program. 

Are there any mice that has many extra buttons that work well with ubuntu? It seems like there is a huge lack of support in linux for extra mouse buttons. I wish someone would look into that. Maybe I should improve my knowledge of this stuff and attempt to myself.

Thanks for your suggestions. You have at least helped me realize I'm fighting a losing battle.

---

