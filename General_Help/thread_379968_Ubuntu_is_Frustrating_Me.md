---
title: "Ubuntu is Frustrating Me"
date: 2007-03-09
forum: General Help
---

### Post by phaedo5 on 2007-03-09
Ubuntu is killing me so far.  It installs great (Edgy Eft).  Boots up, looks nice.  

First problem, extremely slow scrolling speed on browsers and pretty much anything.  So I look for fixes, and I don't really find anything specific.  

So I decide to update the NVIDIA driver I have because I am pretty sure Linux is recognizing it as a generic.  I download the package and I can't figure out how to boot into a command line.  

I figure out that I need to change the run level.  I just need to edit the inittab file.  But there isn't one.  Not on my version.  So I can't figure out anything as far as booting without a window system starting up.  

Then I find something on Upstart 0.3.5.  But I can't figure out how to install it.  Seems like I should have to boot to a command line to install that too.  

I'm really getting nowhere.  I am wondering about Suse and Mandriva at this point.  I know this is a pathetic vague noob post.  But I am more or less just venting.  Any help or suggestion wouldn't hurt though if anyone is feeling charitable.  

It makes me wish I had a Linux expert for a roommate instead of a drunken idiot.

Thanks.

---

### Post by desheikh on 2007-03-09
Hi,

Did you start experiencing the slow browsing after installing the nvidia drivers or before?

Im quite sure you dont need to be changing runlevels while installing the nvidia driver.

Ali

---

### Post by Famicommie on 2007-03-09
You shouldn't have to boot into a lower runlevel to install the nVidia drivers. All you should need to do is run commands from a terminal, which can be accessed in a number of ways.

1. Applications -> Accessories -> Terminal
or
2. Pressing alt+F2 and typing in 'gnome-terminal' (no quotations)

However, there's an even easier way.

Install EasyUbuntu from
[http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)

Under the 'System' tab, it will have an automatic nVidia driver package install :)

---

### Post by ~LoKe on 2007-03-09
If Ubuntu is giving you trouble, I can say that Mandriva and Suse will give you trouble as well.  These problems are considerably common, but are easy to overcome.  The great thing about these forums is the userbase.  With so many people here, it's easy to find an answer most of the time.

Example:
Title: "Installing the nVidia Drivers"
Body: "Hi, I'm trying to install the nVidia drivers but I'm not sure how to get to the terminal.  Any advice on how to do this?"

You'll probably get a reply like the following:
"Have you downloaded the driver?  If not, download it to your home directory (/home/username/, or ~/ for short) and then press **Ctrl+Alt+F1**.  You'll be at a black screen with text.  You'll probably have to login (username/password).  After that, you'll be able to issue commands.  To install the driver, type the following:
```
sudo sh *.run
```
An installer will come up, follow the onscreen instructions (simple instructions, yes/no answers).

If you have any problems doing this, just post here and let us know."

It's that simple most of the time.

---

### Post by phaedo5 on 2007-03-09
Ok, I guess I thought you needed to change the run level to boot into a command line because of the error I get when trying to install the NVIDIA driver.  

It says:
You appear to be running an X server; please exit X before installing...

And you can't just run init 3 at the terminal as I used to.  So I don't know where to go from there.  

I will check out EasyUbuntu, but I would still like to learn.  

Granted, I never got the drivers installed under Mandriva either, but I didn't have any super slow scrolling problems.  I really want to learn the ins and outs of Ubuntu since it is so popular.  But the scrolling problem is a big one.  It's like trying to driving a car with a broken windshield.  

And to that one question, no I haven't installed the drivers yet.  I can't.  

Btw, when I look in the xorg.conf file, my "Device" section says it is generic.  That's why I assumed I needed the new driver.  I thought perhaps it would fix the slow scrolling.

---

### Post by confused57 on 2007-03-09
> **phaedo5 said:**
> Ok, I guess I thought you needed to change the run level to boot into a command line because of the error I get when trying to install the NVIDIA driver.  

It says:
You appear to be running an X server; please exit X before installing...

And you can't just run init 3 at the terminal as I used to.  So I don't know where to go from there.  

I will check out EasyUbuntu, but I would still like to learn.  

Granted, I never got the drivers installed under Mandriva either, but I didn't have any super slow scrolling problems.  I really want to learn the ins and outs of Ubuntu since it is so popular.  But the scrolling problem is a big one.  It's like trying to driving a car with a broken windshield.  

And to that one question, no I haven't installed the drivers yet.  I can't.  

Btw, when I look in the xorg.conf file, my "Device" section says it is generic.  That's why I assumed I needed the new driver.  I thought perhaps it would fix the slow scrolling.

Until you can get your "nvidia" drivers installed, why don't you try changing the driver to "nv"...nv works pretty well for my nvidia card...you may have to reboot, or press ctrl+alt+backspace to restart gdm to get it working.

---

### Post by M$LOL on 2007-03-09
With Ubuntu, or any other form of linux, you will have to do some user setup to get it working. Things will go wrong, and you will need to have patience and be willing to put in the effort. Once you do get it working though, it will make Windows look like a sloth next to a cheetah.

---

### Post by phaedo5 on 2007-03-10
Ok, so after all of that, changing the driver to "nv" did the trick.  No more slow scrolling.  No more generic video card driver.  

Only I don't totally understand what changing it to nv did.  Can anyone tell me that?

---

### Post by der_joachim on 2007-03-10
The "nv" driver is an open source driver for nvidia cards. As long as you are not using any 3D applications, you're good. The closed source official nvidia drivers (called "nvidia") have 3D acceleration and they are quite decent.

If you want to enable the closed source Nvidia drivers, read [this wiki page]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"). You will not install the newest version, but for the moment, you'll be set.

---

### Post by slack42 on 2007-05-30
If you want to get into a command line without x running you can type shutdown now into a terminal and it will put you into single user mode. When I tried to install the nvidia driver I got the same message about x still running so what I did was I got to a command prompt by going ctrl+alt+f1 and then shutdown gdm (gnome) by typing /etc/init.d/gdm stop and then I was able to run the installer. I know you have the problem solved but I just thought I would let you know how I was able to get into a command prompt.

---

### Post by zero244 on 2007-05-30
Install Automatix2......and then install the Nvidia drivers from there......its like two clicks and your done.
Do a search for Automatix2.....its a deb file so its an easy install.
These drivers should work fine and will give you 3D support.....though I must admit I cant get Beryl working with them. But otherwise they work fine.
You can install ntfs support and several other features with just a couple of clicks.

---

