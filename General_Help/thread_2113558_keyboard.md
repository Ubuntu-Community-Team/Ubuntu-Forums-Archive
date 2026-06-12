---
title: "keyboard"
date: 2013-02-07
forum: General Help
---

### Post by albaniaguard on 2013-02-07
hi.
my keyboard dont work vary good,some butons work and some not work and some doing diferen work.
can you help me

---

### Post by Stonecold1995 on 2013-02-08
You have to elaborate more.  Do you mean if you press keys, a different letter will appear?  Or do you mean some keys are stuck/broken?  If it's a hardware problem, you probably won't find much help here, because there's not much you can do from a software perspective when it comes to a broken keyboard.

---

### Post by srekcahrai on 2013-02-08
Maybe you chose wrong keyboard layout.

Goto System Settings > Keyboard Layout > Layouts

---

### Post by fantab on 2013-02-08
> **albaniaguard said:**
> hi.
my keyboard dont work vary good,some butons work and some not work and some doing diferen work.
can you help me

You have to elaborate more as suggested in post #2... or we cant help. We can only guess what your real issue...

If you are referring to special keys like Media keys, then yes some of the keys don't work in Linux... because most of the keyboard manufacturers make drivers and other compatibility for Windows only...  

However we can assign same functionality to other keys... But first please elaborate on the issue you have...

---

### Post by albaniaguard on 2013-02-08
my keyboard is not broken,and i have 1 year ho i use ubuntu and work good,but now some butons dont work.
q,t,n,j,u-dont work and b- when i use doing small the windou of broswer..

---

### Post by fantab on 2013-02-08
Try using another Keyboard, if you can, and see if it works... also try and use your present keyboard on another machine and see if the issue persists...

Then check the keyboard layout in System Settings -> keyboard -> layout settings and see what keyboard layout you have... and report back.

---

### Post by albaniaguard on 2013-02-08
but i have laptop and i cant change the keyboard  :(

---

### Post by HermanAB on 2013-02-08
X handles the keyboard and mouse. Sometimes it goes haywire.  You may be able to fix a key by defining it the way it should be with xmodmap. Otherwise you need to re-install your system. This happened to me twice in 20 years, so it is not totally unheard of.

---

### Post by albaniaguard on 2013-02-08
i waiting for the new version of linux.i can doing format now,if i doing i lost vary much dokuments.

---

### Post by fantab on 2013-02-08
You should have mentioned in your very first post that you have a laptop. 

I you can then try this from the Terminal:

```
$ sudo dpkg-reconfigure keyboard-configuration
```If that doesn't help then the safest and simplest thing will be to reinstall Ubuntu... 

You must however, BACK UP all your Data first... if you have a separate /home then you can manually install Ubuntu by selecting "Something Else" when you are asked to choose disk formatting method during Ubuntu install... then just format the '/' partition and opt to use the same /home that you are using now without formatting it...

Good luck...

---

### Post by albaniaguard on 2013-02-08
Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-24-generic

 this say in terminal,what i nead doing now?

i have the laptop in one disc and i cant doin this.

---

