---
title: "I've messed up the graphical interface! X server disabled..."
date: 2007-05-20
forum: General Help
---

### Post by Irishpolyglot on 2007-05-20
Hi everyone!!! I am very silly - I found some site about improving the graphics (which I didn't really need to do) and entered in some code to upgrade/change it, and now I can't access the desktop! When I boot up I see> Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem? and when I select OK it just gives standard system info with > (==) Using config file "etc/x11/xorg.conf at the end, followed by a message > The X server is now disabled. Restart GDM when it is configured correctly
I've learned my lesson not to enter any old random code into the command prompt now!!!](*,)
Any advice on what I should do? Unfortunately I can't access the code I entered in - not sure how to get into Firefox's history from the outside (I'm back on windows at the mo'... :oops:). If it's really complicated I might just re-install Ubuntu, but I suppose it's a good experience so I know not to be so enthusiastic to enter any old code!!
Thankssss

---

### Post by de_pol on 2007-05-20
```
dpkg-reconfigure xserver-xorg
```

---

### Post by Borzo on 2007-05-20
It would help if we knew what exactly did you do? Have you altered xorg.conf?

---

### Post by Irishpolyglot on 2007-05-20
Still not working... I tried that dpkg. It just said conflicting actions and gave me a list of options to add. Not too useful.
But I realised that if I press up and down I can see previous entried to the command line, so here is what I wrote:
> sudo apt-get
sudo apt-get install wpasupplicant
sudo gedit /etc/network/interfaces
lspci | grep -i network
lspc: -vv
sudo -s
lspci | grep -i network
sudo apt-get update
sudo apt-get install xorg-drive-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo modprobe -r bcmwls
sudo rmmod ndiswrapper
Not sure where the relevant code entered ends, but that should show what I did!! Can anyone help??? Thanks!

---

### Post by Borzo on 2007-05-20
Here's what you did:

installed wpasupplicant ( for the wireless network )
edited /etc/network/interfaces
listed your PCI bus
installed xorg-driver-fglrx ( an ATI driver for xorg )
done some setting for ATI
probed modules
unloaded ndiswrapper module

since you have a problem with your xorg display , then this must have something to do with the driver or the setup.

I don't have an ATI card so i don't really know what exactly could be the problem, my guess is that you have a problem in xorg.conf ( the configuration file for X Windows )

1- Do you actually have an ATI graphics card installed?
2- have you changed the string ati to fglrx in /etc/X11/xorg.conf ?
3- Have you looked in xorg's logs for some clues? ( more /var/log/Xorg.0.log ) ?
4- Have you made a backup of /etc/X11/xorg.conf before doing this work ( always a good thing to do )
5- have you read the documentation or any posts on setting xorg.conf for the ATI driver?
6- have you tried, in console to remove the driver? ( apt-get remove xorg-driver-fglrx )

---

### Post by Irishpolyglot on 2007-05-20
1- Do you actually have an ATI graphics card installed?

  No. I have nVidea GeForce Go 7900 GS. Feel free to tell me how stupid what I just did was :-P I literally just copied what I saw on the website without question. NO MORE!!!

2- Have you made a backup of /etc/X11/xorg.conf before doing this work ( always a good thing to do )
  No :( As I said, this was an extremely silly thing of me to do.... I'll definitely back up before doing something like this ever again.

3- have you read the documentation on setting xorg.conf for the ATI driver?
  No... same aswer as above... I didn't need to do this, I don't know why I did lol...

3- have you tried, in console to remove the driver? ( apt-get remove xorg-driver-fglrx )
  No - haven't tried anything.

4- Have you looked in xorg's logs for some clues? ( more /var/log/Xorg.0.log ) ?
 No, how do I access that? What should I enter exactly (not sure how to read files from the command line, I'm still a n00b..) Cheers!

I just saw your edited version of the questions... I didn't change any strings or removed drivers. If I remove the new driver will it default to old?

---

### Post by Borzo on 2007-05-20
Well, Don't worry about doing silly things, we all do that at some stage ;)
The good news is that this is not fatal, just remove the driver you have installed and let us know if it helped.
when you boot into console, login as root and do :

apt-get remove xorg-driver-fglrx
reboot

---

### Post by Death_Sargent on 2007-05-20
you may have to reconfigure your xorg s that command fails to do so

thankfully ati-config makes a backup for you

try either of the two commands if just uninstalling does not work

```
cp /etc/X11/xorg.conf.fglrx-0 /etc/X11/xorg.conf
```

or 

```
cp /etc/X11/xorg.conf.original-0
```

---

### Post by Irishpolyglot on 2007-05-20
ok, so I tried apt-get remove xorg-driver-fglrx and it said > E: Could not open lock file /var/lib/dpkg/lock - open (13 permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
So then I entered
cp /etc/X11/xorg.conf.fglrx-0 /etc/X11/xorg.conf
and got back > cp: cannot create regular file '/etc/X11/xorg.conf' : Permission denied
The same with cp /etc/X11/xorg.conf.original-0 /etc/X11/xorg.conf
Hmm.. seems odd. Any other thoughts??

---

### Post by Cene on 2007-05-20
Try **sudo** before any command, so sudo apt-get remove xorg-driver-fglrx and sudo cp /etc/X11/xorg.conf.fglrx-0 /etc/X11/xorg.conf

---

### Post by Irishpolyglot on 2007-05-20
Alright, so I used all the same commands with *sudo* before them and they worked within themselves (no error or permission messages and the apt-get remove xorg-driver-fglrx showed the deletion of the file). The copy commands seemed to work too.. but each time I entered a command, I rebooted after and nothing has changed - still getting the same error messages and going back into the command line...
So, what shall I do? Thanksss

---

### Post by ericallen on 2007-05-20
have you tried
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Martje_001 on 2007-05-20
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
If I may ask, what does "-phigh" do?

---

### Post by ericallen on 2007-05-20
> **Martje_001 said:**
> ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
If I may ask, what does "-phigh" do?

I'm not sure, but it says in the xorg.conf
>  If you have edited this file but would like it to be automatically updated
 again, run the following command:
   sudo dpkg-reconfigure -phigh xserver-xorg
so it could work

---

### Post by hessiess on 2007-05-20
sudo dpkg-reconfigure xserver-xorg

and change the driver back to your old one

---

### Post by Irishpolyglot on 2007-05-20
ok, I'm in the menu, but I'm not quite sure what my old driver is... I tried a couple at random and it didn't help. I've got a 256MB Nvidia GeForce Go 7900 GS PCI Express x15 graphics card. I'm assuming the video card = graphics card here...probably wrong. How can I find out which one I have? As I said, I've a DELL Inspiron 9400 - can I boot into Windows again and see there?
Thanks!

---

### Post by leibowitz on 2007-05-20
Try 'nv' or 'nvidia' for the driver.

---

### Post by Irishpolyglot on 2007-05-20
Yes it was nv!!! Problem solved :) Thanks a million for your help everyone!!
=D>=D>=D>=D>=D>=D>=D>

---

### Post by hessiess on 2007-05-20
that driver works for most things but wont get the most out of your card. download the .run for your card from nvidia's website

---

