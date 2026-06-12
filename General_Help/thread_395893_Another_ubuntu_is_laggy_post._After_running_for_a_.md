---
title: "Another ubuntu is laggy post. After running for a while only"
date: 2007-03-28
forum: General Help
---

### Post by kc0eks on 2007-03-28
Hello all,

Thanks to anyone who helps me with this one :)

Upon first booting up ubuntu runs great, everything scrolls smoothly, video works smooth...all in all everything is nice.

I have noticed that after about a day or so of running the following: firefox starts scrolling jumpy, video plays choppy...windows wont move smooth..etc etc. Basically the system runs like crap all around. 

Being new to linux I have no idea how to troubleshoot this...

I have the fglrx drivers for ati installed, and they appear to be running ok. I think... ;) 

Allrighty..lets the help begin! :)
Thanks all!

---

### Post by s_h_a_d_o_w_s on 2007-03-28
I have same problem after suhtting system off for a week

---

### Post by LCC on 2007-03-28
I had the same problem (ATI) but after installing the driver it works fine, which version of Ubuntu are you running?
 if 6.10 try this script for ATI (it comes with XGL/BERYL as well)

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI#Automatic_installation](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI#Automatic_installation)

follow the instruction on the link above.

If you don`t want beryl now (if you do don`t make it default) use this how to

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Disable_Composite_Extension](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Disable_Composite_Extension)

[COLOR="Navy"] Disable Composite Extension

In Ubuntu Edgy the Composite extension is enabled by default, however, fglrx does not yet support Composite with DRI. In order to disable Composite you have to edit the xorg.conf file:

sudo gedit /etc/X11/xorg.conf

and add these lines at the end of the file:
File: /etc/X11/xorg.conf

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

    * Note: Xubuntu does not have gedit. The default text editor in Xubuntu is called mousepad.
    * Note: Kubuntu does not have gedit. The default text editor in Kubuntu is called kate.
    * Another option is to use nano (or vim). 

[edit] Installation
[edit] Method 1: Install the 8.28.8 Driver the Ubuntu Way

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx[/COLOR]

hope it helps.

---

### Post by Swankyman on 2007-03-29
Hi

when it starts to run slow check what processes are running.

I had the same problem and after running ps -A in the terminal I got hundreds of compiz running even though I didn't have it running (if you see what I mean!!)

[https://launchpad.net/bugs/97359](https://launchpad.net/bugs/97359)

Rich

---

### Post by tthkbw on 2007-03-29
Almost certainly this is a driver issue.  I wish I could help specifically, but I'm not sure how I fixed this problem on my install (although I have apparently fixed it).  

I had no wild processes, the only difference I could see was than when scrolling was fast and I was scrolling, X took only about 30% of the cpu, but when it was slow, the same application scrolling took 99% of the cpu.  Now I never see the 99%.

See my description and comments in this post:

[http://ubuntuforums.org/showthread.php?t=392662](http://ubuntuforums.org/showthread.php?t=392662)

---

### Post by ceeg on 2007-03-29
Remove whatever you did to install fglrx:
```

sudo apt-get remove --purge xorg-driver-fglrx

```

Clean up apt:
```

sudo apt-get clean

```

Reinstall fglrx drivers:
```

sudo apt-get install xorg-driver-fglrx

```

Set up the driver:
```

sudo dpkg-reconfigure xserver-xorg

```

Agree to automatic detection and when asked, choose fglrx.

Reboot:
```

sudo reboot

```

See if that fixed it.

See if direct rendering is enabled
```

glxinfo | grep direct

```

If yes it should be responding a lot better. If your applications are still starting slow in Gnome, add your hostname to the localhost segment of your /etc/hosts file.

Open the hosts file
```

sudo nano /etc/hosts

```

It should look like this:
```

127.0.0.1     localhost     hostname
127.0.1.1     hostname

```

Report back :)

---

### Post by kc0eks on 2007-03-30
thank you all for your ideas...certainly gives me something to work with!
I shall report back soon.... :)

---

### Post by kc0eks on 2007-04-02
ok still having problems...
I have reinstalled my drivers, seems like all that went well. Xorg shows fglrx...
if I reboot scrolling is fine, for a while...seems like the amount of time everything works varies quite a bit. Scrolling anything with images is terrible, although even scrolling text in gedit is jumpy. 

This is reallllly annoying. ;)

thanks again for everyone who helps !

---

