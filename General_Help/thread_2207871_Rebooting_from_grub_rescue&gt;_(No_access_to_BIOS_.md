---
title: "Rebooting from grub rescue&gt; (No access to BIOS or booting options)"
date: 2014-02-25
forum: General Help
---

### Post by andrew94 on 2014-02-25
Hi guys, I have kind of delicate problem. I did very dumb thing.  I'm using MSI U100 Wind Notebook. **I have Windows XP Home Edition installed on my laptop but I also wanted to install Ubuntu after long time of not using it.** What Happened: I booted ubuntu to my laptop from USB, and started installation. Since it wasn't for the first time **I let it install and I started doing some work. But meanwhile my laptop's battery totally drained out, the installation was interupted (in the wrongest time) and Linux propably wasn't actually installed. I tried to boot again but I'm only able to get to the grub rescue> screen.** I know I can use boot repair, booting another system, etc. But** _I can't even get to the BIOS or boot devices list (normally F11 key.)_** Only thing I can currently get to is grub rescue>. So my questions are: 
[B]
Can I boot already installed windows from grub rescue> ?[/B]  ***EDIT: *No you can't !**[B]
Can I boot USB stick from grub rescue> ? *EDIT*: No you can't !

[/B]Please, help me. I appreciate any ideas ! :)
[SIZE=5]
EDIT:

**[SOLUTION] **[/SIZE]**[SIZE=4]Rebooting from grub rescue> (No access to BIOS or booting options)[/SIZE]**[SIZE=5]
[SIZE=3]
Alright, so... The solution of this problem wasn't too difficult to find but it definitely took me some time so I hope someone will use these information. 
[/SIZE][SIZE=3]
[SIZE=4]1. Boot Ubuntu (you can boot other Linux based system but I [/SIZE][/SIZE][/SIZE][SIZE=4]recommend Ubuntu for this) on any other computer. 
2. Start installation - set your install folder as your USB stick (I recommend at least 4GB) - **! **Installation will took lot of time - you have to be patient **!**
3. Once the installation is done turn off this computer. 
4. Plug USB stick in the computer with corrupted booting. 
5. Continue by any other  grub rescue recovering  tutorial with one difference: your Ubuntu system file now will be your USB stick. 
6. Boot from USB stick, once you are in Ubuntu, repair your computer booting system (you can find plenty of tutorials how to do that).
7. Be happy :)[/SIZE]

[SIZE=4]If anyone would have any problem, contact me and I will try to help you. 

*Special thanks to*: 'jeanjd63' [/SIZE]



[RIGHT]*ImagineSavior, 2014*[/RIGHT]

---

### Post by jeanjd63 on 2014-02-25
Hello
What return :
**ls**
and
**set**

---

### Post by andrew94 on 2014-02-25
Hello. returns:

ls
(hd0) (hd0,msdos6) (hd0,msdos5) (hd0,msdos2) (hd0,msdos1) (fd0) 
set
prefix=(hd0,msdos5)/boot/grub
root=hd0,msdos5

---

### Post by jeanjd63 on 2014-02-25
You can try :
**insmod  linux**
**linux /vmlinuz root=/dev/sda5  ro**[COLOR=#000000][FONT=Arial] [/FONT][/COLOR]
**initrd /initrd.img**
**boot**

---

### Post by andrew94 on 2014-02-25
insmod linux
error: file not found

I don't think these commands will work because linux wasn't actually installed. The installation was stopped because of drained battery. But thanks.

---

### Post by jeanjd63 on 2014-02-25
I think you have to boot from your LiveUSB and reinstall ubuntu. In bios options you can do this.

---

### Post by andrew94 on 2014-02-25
I can't do that. I already mentioned that because of interupted installation of Ubuntu there is no way to get in booting options or BIOS. Normally while booting laptop is says something like: Press F11 to open menu. But now there is nothing like that, just MSI logo and there is no way (at least I think so) I can enter BIOS or boot options. That's why I'm asking for direct boot from grub rescue.

---

### Post by jeanjd63 on 2014-02-25
You can try to remove the batterie and try to turn power on. Of course the computer will  not boot, but it's possible after this you can have the boot menu.

---

