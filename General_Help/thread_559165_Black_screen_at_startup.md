---
title: "Black screen at startup"
date: 2007-09-24
forum: General Help
---

### Post by speadskater on 2007-09-24
I have an Alienware (something), my computer specs are:
AMD 6000+
nvidia 8800gts
2 gigs of ram

I just got the computer about 4 weeks ago and i decided to dual boot Vista and Ubuntu.  I insert the ubuntu 7.04 64 bit addition (requested from the site weeks before) into the drive and restart the computer.  i click the install and run button... and my screen goes black for about five minutes before starting up (even the light on the power button turned orange).  I was able to install it on the hard drive.  After that i restarted my computer and the screen went black for about 10 minutes until it finally ejected the cd and shut off.

Now when i tried to reboot without the cd, the black screen doesn't go away.  (i know there's a driver issue with the 8800, but i'm not sure how to install it or if that's even the problem.)

Along with the problem starting up ubuntu, vista also had a weird start up and seems to want to load something on the desktop that can't be loaded (can't click any of the buttons on it, have to go through start menu)

I've ran ubuntu on my laptop for a while now and love it (still a newb though), but with this new desktop there seems to be problem after problem after problem (mostly vista related)

---

### Post by quixotic-cynic on 2007-09-25
Some possibilities:

* disk is corrupt (boot the cd and select the 'check' option)
* new laptop hardware incompatibile
* your new HDD is going to die 

I wouldn't panic but I can't really see a way that a default install of ubuntu could modify your NTFS file system so if Vista actually boots but is screwed up then your HDD may be the problem.

There may be other possibilities that people with more beans can point out...

Have you tried booting with another linux boot disk - such as Damn Small Linux? (50meg download)

---

### Post by speadskater on 2007-09-25
I haven't tried anything other than ubuntu.

The vista part is fine... that was just a program my bro installed messing the startup.

The disk is fine.

Could it be a first time startup thing? and if so should i just let it run all day with the black screen and hope that it eventually loads a driver and starts up?

I also have the 32 bit addition of ubuntu, should i try that?

---

### Post by quixotic-cynic on 2007-09-26
To troubleshoot the startup thing you are going to need someone with more xp points than me - (so if anyone else wants to post)...

> PC (Intel x86) desktop CD
    For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows, as well as newer Apple Macintosh systems based on Intel processors. Choose this if you are at all unsure.

64-bit PC (AMD64) desktop CD
    Choose this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon). If you have a non-64-bit processor made by AMD, or if you need full support for 32-bit code, use the Intel x86 images instead. 

You could try the 32bit one - you can't get worse than a blank screen right? If you do use the 32 bit one it should work fine (it just wont be using the full potential of the cpu).

The other thing you could do is use the Ubuntu Alternate install disk (still installs Ubuntu just gives you better options during install and works faster) for your CPU architecture and install just a command line system (one of the options on the menu) and then see if that boots (it is initially much simpler and thus more likely to boot). If that worked you could then use "sudo aptitude install xorg gdm gnome" to get the graphical environment... 

I've been thinking about the hardware possibility and decided that if the Live CD boots Ubuntu fine (normal install disc) then I definitely think you can get an install working on your system - it is just a matter of how (usually is, right)?

I hope this post gets you a little closer.

---

### Post by speadskater on 2007-09-28
Ok, so i got the Linux to work with the 32 bit cd.  now the problem is that when i installed and enabled the graphics card driver... the GUI died.  Is there a problem with the nvidia 8800 driver?  I'm guessing since its so new, that its hard to come up with a working Linux driver, but i'm not sure.

I really want high screen resolution and desktop effects, but if the driver doesn't work, than i can't use it.

(i can use linux with the command line... do you know any commands that i can use so i won't have to reinstall linux completely)

---

### Post by quixotic-cynic on 2007-09-29
You can type ```
sudo nano /etc/X11/xorg.conf
``` to access the config for the graphics stuff. (You may need to go here to change resolution and desktop effects too so remember it). When you have your graphics back you can use gedit instead of nano. The currently used driver is this part:

```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

```

Yours will have something different than "ati" obviously. As an emergency fix you can set your driver to "vesa" and that will let you use the gnome environment to go about fixing your stuff.

Which driver did you install - and how?  IIRC, by default the open source driver is already installed for the nvidia cards. The closed source one you can install is the one from nvidia so it shouldn't screw up. If you can remember the name of the driver package then you can use ```
sudo aptitude remove packagename
``` to remove the package. To reinstall it you can use ```
sudo aptitude reinstall packagename
``` but I would be sceptical of just this last line, by itself, fixing your setup.

A final thing that is useful to know is that if you delete /etc/X11/xorg.conf using```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
sudo rm /etc/X11/xorg.conf
``` it will autodetect and create a replacement when you try to start X (which can help, perhaps in conjunction with uninstalling the problematic driver). Note: ctrl + alt + backspace will close all apps and restart X.

You can also reconfigure X (the thing that serves you your graphics) using ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` The actual program you run here is dpkg-reconfigure, the -phigh part is a parameter, and the package you are reconfiguring (the X one) is the 'xserver-xorg' part of the line... sudo temporarily gives your user the rights to edit root-owned stuff (you may well know this).

---

### Post by speadskater on 2007-09-29
> **quixotic-cynic said:**
> You can type ```
sudo nano /etc/X11/xorg.conf
``` to access the config for the graphics stuff. (You may need to go here to change resolution and desktop effects too so remember it). When you have your graphics back you can use gedit instead of nano. The currently used driver is this part:

```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

```

Yours will have something different than "ati" obviously. As an emergency fix you can set your driver to "vesa" and that will let you use the gnome environment to go about fixing your stuff.

Which driver did you install - and how?  IIRC, by default the open source driver is already installed for the nvidia cards. The closed source one you can install is the one from nvidia so it shouldn't screw up. If you can remember the name of the driver package then you can use ```
sudo aptitude remove packagename
``` to remove the package. To reinstall it you can use ```
sudo aptitude reinstall packagename
``` but I would be sceptical of just this last line, by itself, fixing your setup.

A final thing that is useful to know is that if you delete /etc/X11/xorg.conf using```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
sudo rm /etc/X11/xorg.conf
``` it will autodetect and create a replacement when you try to start X (which can help, perhaps in conjunction with uninstalling the problematic driver). Note: ctrl + alt + backspace will close all apps and restart X.

You can also reconfigure X (the thing that serves you your graphics) using ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` The actual program you run here is dpkg-reconfigure, the -phigh part is a parameter, and the package you are reconfiguring (the X one) is the 'xserver-xorg' part of the line... sudo temporarily gives your user the rights to edit root-owned stuff (you may well know this).

Haha, i have no idea what i'm doing with this.

I'm not sure which driver i used.  i just pressed enable restricted drivers, it downloaded and installed one file, and told me to restart.  Apparently that's not the best choice?

I tried the ```
sudo nano /etc/X11/xorg.conf
``` but i wasn't quite sure what to do after, it just gave me a blank screen to type things in and had a couple of commands at the bottom.

After that i tried the reconfigure, but it didn't do anything.

It does give me a report when it realizes that the x-serve doesn't work, do you want me to copy that down and post it up here?

---

### Post by quixotic-cynic on 2007-09-30
> **speadskater said:**
> I'm not sure which driver i used.  i just pressed enable restricted drivers, it downloaded and installed one file, and told me to restart.  Apparently that's not the best choice?

There is no problem with that choice - if you want to play games or use other advanced graphical apps that is what you need.

Type ```
sudo aptitude search nvidia
``` and have a look at the packages listed. I think that the driver you installed would be nvidia-glx (it it is it will have an 'i' next to it to signify that it is installed. (So now, based on the prev post you should be able to remove it if you want)...

> **speadskater said:**
> I tried the ```
sudo nano /etc/X11/xorg.conf
``` but i wasn't quite sure what to do after, it just gave me a blank screen to type things in and had a couple of commands at the bottom.

Ok, that really should -not- be happening ;)

Did you maintain the same case or just type /etc/x11/ ? The case does matter. If you typed it correctly and the file is empty then you have something else to worry about.

You can check to see if the file is there manually by typing
```
cd /etc/X11/
ls
```
(cd changes directory and ls lists files)

Digression: You can type *man command* to read a manual on each command, eg *man ls*. Page up and down allow you to change the pages and q will quit the manual. Typing *cd --help* etc is also very useful.

> **speadskater said:**
> After that i tried the reconfigure, but it didn't do anything. 

Fair enough, I just installed ubuntu on an nvidia based machine today - I would say the best fix for now is to make sure that *Driver "nv"* is what is written in your xorg.conf - so the next stage is to try using nano again to sucessfully view the file, and not just open up a blank one.

> **speadskater said:**
> It does give me a report when it realizes that the x-serve doesn't work, do you want me to copy that down and post it up here?

It would probably be a good idea but it will take someone with more knowledge than me to work out the problem.

Finally, even if you have "no idea what you are doing with this" you can still get better by trying stuff like this. I have only been using ubuntu for about a month and a bit and I am much better than I was but I still get the 'no idea' thing now and again... ^_^

---

### Post by speadskater on 2007-09-30
hmm, what you told me to do did get my gui to work agian, it just needed a restart.  The resolution is low and the correct drive isn't installed yet, but i'll just update the system and download the linux driver directly from the nvidia site.

I'll edit this post once i enable the driver


EDIT:

... hmm managed to update it, but when i enabled the driver guess what happened?

i lost the gui again... and now its just the terminal isn't even there... yeah, i'm just going to format the partition and try again.

---

### Post by FSHero on 2007-10-07
I don't know if this has anything to do with anything...


... but I thought that the nvidia-glx driver in the Ubuntu 7.04 repository was 96.31 at present (2007-10-07).

I thought that one needs a 100 series driver to get Geforce 8 cards working. I recently did an install of 32 bit Kubuntu Feisty Fawn on my PC, and it has a GeForce 8. However, when I go to restricted-manager, no drivers are offered to be installed.

Out of interest, if what I said was correct, when will a 100 series driver be packaged for *buntu?

---

### Post by quixotic-cynic on 2007-10-07
Good post - I found what you where talking about:

> As of Ubuntu 7.04 (Feisty Fawn) the recommended way to install the binary drivers is to use System &#8594; Administration &#8594; Restricted Devices Manager. This will try and automatically choose the correct version out of:

    * nvidia-glx-legacy (corresponds to the 71xx driver)
    * nvidia-glx (which corresponds to the 96xx driver)
    * nvidia-glx-new (which at the time of writing corresponded to the 97xx driver)

If your card does not appear in this list of cards known by Ubuntu 7.04 NVIDIA binary drivers (e.g. the 8600GT) then there is no Ubuntu 7.04 supported binary driver. For unsupported workarounds try the links in See Also.

The list [here]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/appendix-a.html") (or [http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)) shows that the 8800 GTS is supported by the latest driver.

So, I would check the list to see if your GPU is on it - if it isn't then you unfortunately have to wait for nvidia to get a move on (are linux users second-class customers to them possibly?).

If it is on the list but not in the repos then you can either wait for the ubuntu packager ppl to upgrade it or get the dirver yourself from [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html).

---

### Post by fumduck on 2007-10-07
so does it restart once the screen goes black??
it might be a nosplash problem..... ?? before you reformat the partion..
 boot from live cd.. at prompt for loading ubuntu.. hit f4 and choose screen size.. and then hit run /install ubuntu    
Once you get into ubuntu  go to applications-->Accessorries--> terminal  type in  sudo gedit /boot/grub/menu.lst

you should find your ubuntu  somewhere in there like this:


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 64 (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0a1993ea-8499-45c5-aa9f-eb23da153ec4 ro quiet [COLOR="Red"]no splash[/COLOR] 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot



notice the no splash add that in and take out any 'vga='
 and see if that works.. that was my issue in 64  
but If you try to just get ubuntu running without restricted drivers.. then figure out what you can do, I am sure there are ways to install latest drivers
but you might want to make sure ubuntu works.. then break it.. because then you know it was something you did.. 
peace

---

### Post by speadskater on 2007-10-07
> **quixotic-cynic said:**
> Good post - I found what you where talking about:



The list [here]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/appendix-a.html") (or [http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)) shows that the 8800 GTS is supported by the latest driver.

So, I would check the list to see if your GPU is on it - if it isn't then you unfortunately have to wait for nvidia to get a move on (are linux users second-class customers to them possibly?).

If it is on the list but not in the repos then you can either wait for the ubuntu packager ppl to upgrade it or get the dirver yourself from [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html).

From what i see in the list it does work, but i remember that when i bought this computer the graphics card i got was "superclocked"  maybe that is it messing up.  I'll try to contact then within the next day or so.  School is slowing this process down

---

