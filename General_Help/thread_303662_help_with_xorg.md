---
title: "help with xorg"
date: 2006-11-20
forum: General Help
---

### Post by stop_that on 2006-11-20
hello there
well i had problems with booting ect and i done 
> sudo dpkg-reconfigure xserver-xorg

and i ran through it clicking and it finally loaded, however i have a very low refresh rate and moving down Internet pages in sluggish (not Internet connection!)

pls couls someone rum me through reconfiguring xorg properly or a quick solution like a  default xorg document ?
im running ati radeon x600

---

### Post by PrinceArithon on 2006-11-20
Did you do it in the shell or did you do it through the terminal??

Here is what I suggest

sudo /etc/init.d/gdm stop

sudo dpkg-reconfigure xserver-xorg

After you finished configuring it again

sudo /etc/init.d/gdm restart


If for some reason you can't get out of the shell or it doesn't do anything for you type in this

sudo init 6

sudo init 6 will restart your system

---

### Post by stop_that on 2006-11-20
i seem to have got it working by redoing xorg however when i attempt to play on ET (enemy territory) the graphics are slow and textures are missing ?

---

### Post by CatKiller on 2006-11-20
Have you installed the appropriate driver for your graphics card?

---

### Post by stop_that on 2006-11-21
I Installed the Ati driver at xorg set-up screen.
I never experienced this problem before i tried installing the ati drivers instead of the default ubuntu drivers :(

---

### Post by CatKiller on 2006-11-21
> **stop_that said:**
> I Installed the Ati driver at xorg set-up screen.
I never experienced this problem before i tried installing the ati drivers instead of the default ubuntu drivers :(

Do you mean **ati** or **fglrx**? One is the open-source one, and one is the closed-source one.

---

### Post by Rajiv_Nair on 2006-11-21
if u hv ur fglrx drivers installed for ur ATI card, runnin 
sudo aticonfig --initial --force 
will replace ur xorg.conf with da default xorg.conf for fglrx

---

### Post by stop_that on 2006-11-23
still nothing can you tell me some way off restoring default driver that was being used and worked.without reinstalling.if there is any such way

---

### Post by telovoyagarcar on 2006-11-23
Today i had the same problem and i followed these instructions and now i got the ATI driver right and smooth:

First open and edit the xorg.conf file:

sudo gedit /etc/X11/xorg.conf

and add these lines at the end of the file:

[B]Section "Extensions"
        Option  "Composite" "Disable"
EndSection[/B]


Then install the driver:

Make sure the restricted repository is enabled in /etc/apt/sources.list or this guide will not work!

You can check this by looking in the sources.list file where these 2 lines need to be without the "#" at the begining:

[B]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted[/B]

Then use these commands... just copy and paste like i did:

sudo apt-get update

sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed

sudo apt-get install xorg-driver-fglrx

sudo depmod -a

sudo aticonfig --initial

sudo aticonfig --overlay-type=Xv


And finally Reboot your system:

sudo shutdown -r now

That worked for my x800xl

You need to have the machine connected to internet or you won't get the packages..

Good luck.. i hope this helps

---

### Post by CatKiller on 2006-11-23
> **stop_that said:**
> still nothing can you tell me some way off restoring default driver that was being used and worked.without reinstalling.if there is any such way

Since you've not said what you've done at any point, I can only point you at these pages:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

```
sudo dpkg-reconfigure xserver-xorg
```

is what you'd use to configure your graphics drivers again without reinstalling. It was almost certainly the **ati** graphics driver that you were using after you first installed.

---

