---
title: "Lubuntu : no graphic interface"
date: 2013-03-06
forum: General Help
---

### Post by Antoine33 on 2013-03-06
Hello,

I've installed Lubuntu 32 bits on my netbook Asus eeepc X101CH.
The installation was sucessfull, however when I start nothing is displayed except command line asking my login and my password.
When I enter it, it works but It is still the command-line.
Thanks to CTRL+ALT+F1 I shift to the shell and enter the command-line : startx
I get that: 

> [COLOR=#000000][FONT=Arial]
X : cannot stat /tmp/.X11-Unix (no such file or directory, abording.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]xinit: giving up[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]xinit : unable to connect to X server : connection refused[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]xinit : server error[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]xauth: error in locking authority file /root/.Xauthority[/FONT][/COLOR]

Can you help me.
Best regards,
Antoine

---

### Post by Rex Bouwense on 2013-03-06
1. How do you know that the installation was successful?
2.  I also own an ASUS EeePC and to get out of CLI, you press CTR+ALT+F7.  Does that get you back to the grafic interface?

---

### Post by Antoine33 on 2013-03-06
Hello,
Thank you for your answer

1. I would say, I guess It was successful because I didn't get any bad message.
2. CTRL+ALT+F7 : it lists few line with Starting .... [ok] and stops at stoppink System V runlevel compatibility [OK]

---

### Post by Rex Bouwense on 2013-03-06
If you have never been able to boot your system then I do not understand how you can say in was a successful install.  Or have you had a successful boot?

---

### Post by Antoine33 on 2013-03-06
I didn't have any successful boot...
I tried once more ctrl+alt+f7 and I get
stopping save kernel messages [OK]

---

### Post by Rex Bouwense on 2013-03-06
1.  Did you try Lubuntu on your computer before you installed it?  Problems would have surfaced.
2.  Did you check the hash (MD5Sum) on your download?  did they match?
3.  Did you burn the image at the slowest possible speed?  Sometimes you get a bad burn at the higher speeds.

edit:  What version are you trying to install?  Is it a normal install (not WUBI, minimal install, etc)?

---

### Post by Antoine33 on 2013-03-07
> **Rex Bouwense said:**
> 1.  Did you try Lubuntu on your computer before you installed it?  Problems would have surfaced.
2.  Did you check the hash (MD5Sum) on your download?  did they match?
3.  Did you burn the image at the slowest possible speed?  Sometimes you get a bad burn at the higher speeds.

edit:  What version are you trying to install?  Is it a normal install (not WUBI, minimal install, etc)?

1. No I did not.
2. No, I don't know what it is.
3. Yes
4. I install the 12.10 version Standard PC 32-bits version from here : [https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

---

### Post by Cheesemill on 2013-03-07
You need to check the MD5SUM of the iso file that you downloaded before burning it to disk to check that you don't have a corrupt download.
It does mention this on the download page that you linked to.

Instructions can be found here...
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by black veils on 2013-03-07
boot the install media if it is a live version which shows a desktop. just see if it loads the desktop and functions. its the first menu entry and will load by default, after about 10 seconds or something.

---

### Post by Antoine33 on 2013-03-07
> **Cheesemill said:**
> You need to check the MD5SUM of the iso file that you downloaded before burning it to disk to check that you don't have a corrupt download.
It does mention this on the download page that you linked to.

Instructions can be found here...
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The MD5SUM is OK but when I check the files of the LIVE USB, it says that 1 file is corrupted. 

> **black veils said:**
> boot the install media if it is a live version which shows a desktop. just see if it loads the desktop and functions. its the first menu entry and will load by default, after about 10 seconds or something.

when I launch the LIVE version I just get the command-line...

Therefore I tried to get a new version here : [http://lubuntu.net/](http://lubuntu.net/)
I've downloaded the first link and It keeps the same... command-line still...

---

### Post by Cheesemill on 2013-03-07
> **Antoine33 said:**
> The MD5SUM is OK but when I check the files of the LIVE USB, it says that 1 file is corrupted.

In that case the bootable USB creation wasn't successful.

How are you creating your bootable USB stick?

---

### Post by Antoine33 on 2013-03-07
> **Cheesemill said:**
> In that case the bootable USB creation wasn't successful.

How are you creating your bootable USB stick?

I am using the software Lili USB Creator.

---

### Post by Rex Bouwense on 2013-03-07
Back again.  The best and easier (in my humble opinion) way to create a bootable flash drive is to use UNetbootin.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

That should fix you right up.

---

### Post by Cheesemill on 2013-03-07
+1 for Unetbootin.

I've always had more luck creating bootable USB sticks with Unetbootin than any other method (except good old dd for iso's that support it).

---

### Post by Rex Bouwense on 2013-03-07
> I've always had more luck creating bootable USB sticks with Unetbootin than any other method
I have been using it for a while.  Only one failure (Debian) and I am sure that was my fault.  Never had a problem with any Ubuntu or Lubuntu ISO.  It is so easy.

---

### Post by Antoine33 on 2013-03-08
It seems It comes from the computer. The USB Live has no error and the MD5SUM is the same.
Nevertheless I keep the command-line and If I enter startx I get : fatal server error : no screens founds

---

### Post by black veils on 2013-03-08
for now, if you have the patience, it might be worth trying [[COLOR=#0000cd]bodhi linux[/COLOR]]("http://www.bodhilinux.com/") or [[COLOR=#0000cd]peppermint os[/COLOR]]("http://peppermintos.com/"), maybe they have some driver support which is not included with your current system.

by try, i mean boot the live system from usb stick, not install.

---

### Post by Antoine33 on 2013-03-08
> **black veils said:**
> for now, if you have the patience, it might be worth trying [[COLOR=#0000cd]bodhi linux[/COLOR]]("http://www.bodhilinux.com/") or [[COLOR=#0000cd]peppermint os[/COLOR]]("http://peppermintos.com/"), maybe they have some driver support which is not included with your current system.

by try, i mean boot the live system from usb stick, not install.

All right, I am going to do that. So It is not possible to use Lubuntu on these computer, even an elder version?

---

### Post by black veils on 2013-03-08
> **Antoine33 said:**
> All right, I am going to do that. So It is not possible to use Lubuntu on these computer, even an elder version?


i don't know, which is why i suggested those. they are based on ubuntu.

---

### Post by Antoine33 on 2013-03-08
> **black veils said:**
> i don't know, which is why i suggested those. they are based on ubuntu.

I've installed Perppermint and It works well. I don't know if it is better than Bodhi Linux but anyways, I am glad that I finally get Ubuntu on my computer!
Thanks a lot for your help. I am greatful for this help and I am sorry for my english.

---

### Post by black veils on 2013-03-08
ha thats good!  mark the thread as solved by going to **thread tools** >> **mark as solved**

---

