---
title: "Are any alsa drivers required to boot?"
date: 2007-12-13
forum: General Help
---

### Post by Roasted on 2007-12-13
I can't get sound working, so I went to a how-to guide that suggested I remove all alsa drivers and utilities. I removed the utils and drivers in synaptic. Immediately my system shut off. I can't boot into Ubuntu now. I get nothing but a black screen after I select it from the boot loader...

What can I do??!!?

---

### Post by Roasted on 2007-12-13
I was talking to my cousin more about this. He simply said this is why he prefers Fedora over Ubuntu, because I guess Ubuntu allowed me to uninstall something that was required by the system to function.

I get zero response from my laptop when I boot it up. I can get into Vista okay, but once I select Ubuntu I get a black screen. I've had it sitting here for the last 10 minutes with no error, no beeps, no messages or anything.

Seriously, this is beyond ridiculous. I uninstalled a sound driver and sound utility and my system crashed instantly. 

Giving this thread 15 minutes before I throw Fedora on. Any clues to what I can do to save it?

---

### Post by Rocket2DMn on 2007-12-13
If you have a LiveCD, you can boot into that.  Once there you should be able to reinstall the ALSA packages.  I'm not sure how to have it install to your hard drive partition of Ubuntu, but there is surely a way.  I'll look into it and post back, you should also search around for how to do that.

Could you reboot into recovery mode at all?

---

### Post by Roasted on 2007-12-13
Recovery mode brings me to an MS-DOS looking screen that eventually says root@jason:~#

What do I do now?

---

### Post by Rocket2DMn on 2007-12-13
That means you are at a terminal rather than a GUI interface.  You can reinstall the ALSA packages from here.
```
apt-get install alsa-base alsa-utils
```

---

### Post by Roasted on 2007-12-13
Is alsa-base required to run the gui? I removed alsa-utils and I believe alsa-base became highlighted in red.

Being I'm half asleep I hit apply thinking it was just giving me a minor warning. Then my computer shut off. That woke me up... I just don't understand why it'd let me do that without any error. Just a highlighted mark.

---

### Post by Rocket2DMn on 2007-12-13
I wouldn't imagine that it's required for the GUI or for Ubuntu in general, but you didn't even get to the loading sequence did you?  That isn't a GUI problem, that makes it seem that something more fundamental is broken.  When the GUI fails, it typically fails right when you get to the login screen.
I suggest reinstalling the ALSA stuff, and if that doesn't work, try booting into an older kernel (if you have on available) which can be seen at the GRUB menu.

---

### Post by Roasted on 2007-12-13
I got this output:

after it prompted me to hit Y at the y/n prompt...

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main alsa-utils 1.0.14-1ubuntu4 Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/alsa-utils/alsa-utils_1.0.14-1ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/alsa-utils/alsa-utils_1.0.14-1ubuntu4_i386.deb) Could not resolve 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

For the record, I DID run sudo apt-get update.

---

### Post by Rocket2DMn on 2007-12-13
Sounds like you're probably just not online.  Put in your LIveCD to use as a repository.  Once the CD is is, run the command
```
apt-cdrom add
```
This means apt-get will look to the cd as well.  Run the install command I gave you above and it should find the ALSA stuff on the cd.

---

### Post by Roasted on 2007-12-13
Still did the same thing. Unable to fetch some archives. 

It was mounted originally because when I ran the command it said unmounting. So I ran it again and it said mounting. So I hit the other apt-get alsa command and it gave me the same output.

---

### Post by Rocket2DMn on 2007-12-13
If you can boot from an older kernel, do that.  Otherwise boot from your original one that is broken.  Give the system enough time that it would normally take to boot up, then try and get to a tty by hitting CTRL+ALT+F1
If you successfully get to a command line interface it means it really was just your GUI that's broken.  Here you should have internet connection (assuming the computer is normally connected to the internet).
Login with your username and run the following command from there:
```
sudo apt-get install alsa-base alsa-utils --fix-missing --fix-broken
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```
With any luck, that should get you the GUI back.

---

### Post by Roasted on 2007-12-13
No luck. I'm sick of this. 

I see you're a Gutsy user and a Fedora user. Why do you use both? Is there one you prefer? I'm about to bounce on over to the other side after this ridiculous fiasco... Thoughts?

---

### Post by Rocket2DMn on 2007-12-13
I use Fedora Core 5 to run a gameserver from my apartment.  Personally, I think Ubuntu is way easier to use and probably has better support.  Fedora always seems "dark" and not very inviting to me, but they do have their own fanbase who would probably disagree with me.  I rarely have to access the server computer anymore, it's pretty much autonomous, but I am thinking about putting Debian on it.
If you want to give Fedora a try, go for it, nobody is here to tell you what OS you should use.  You may find that you like it, or you may come crawling back, who knows :)
Good luck!

---

### Post by Roasted on 2007-12-13
Only reason I'm thinking about trying it out is due to what my cousin said. He doesn't like apt-get because he said it seems to confuse itself sometimes, as if it's not that solid. When I asked him about what the problem was I just encountered, he asked me if I thought he was still lying.

This is just ridiculous. What am I to do now? Reinstall? For what? Why? I uninstalled a sound driver package that a how-to guide told me to do. I don't understand the problem here.

---

### Post by Rocket2DMn on 2007-12-13
It's possible that something else happened and yout alsa uninstall just seems to be the source of the problem.  apt-get is an old and well established package manager.  Fedora uses yum which i don't particularly like.  Where did you get this guide anyway?  I would like to see it.

---

### Post by Roasted on 2007-12-13
I got it on linuxquestions.org. Somebody had a laptop ALMOST identical to mine. I say almost because it was an A215, but it wasn't a S7422. However, it's the same base model, his just had different features. He told me what he did, which is as follows...

I bought a Toshiba Satellite A215-S7437 and the sound and wireless were not working and the screen resolution was only up to 800x600.

I first installed the 64-bit version of Ubuntu 7.10 Gutsy Gibbon and shrunk Windoze Vista, the 32-bit version, down to 50 Gb and I gave the other 150 Gb over to Ubuntu Linux, the 64-bit version.

Well, installing the ATI driver and rebooting then brought the screen resolution up to 1280x800 as it is under Windoze Vista, the 32-bit version, which I hate.

Next, I fixed the wireless problem by going to this website [[http://www.datanorth.net/~cuervo/rtl8187b/]](http://www.datanorth.net/~cuervo/rtl8187b/]) and following their instructions and downloading their PATCHED driver and installing it. The wireless now works. However, whenever I boot up Ubuntu, I have to open a root terminal and change to the directory of the wireless driver and manually crank up the wireless lan connection and it works fine. The wireless drivers did not compile or work with hardy heron kernel 2.6.24; only with 2.6.22-14-smp gutsy gibbon kernel. Don't know why.

Next, the sound problem. Apparently, the alsa drivers did not properly edit or modify the /etc/modules.conf files and other files? Anway, _**I fixed it by first using Synaptic to remove all the alsa drivers and utilities and tools, also, just in case, and then going to this website and following their instructions:**_

[http://www.alsa-project.org/main/ind...dule-hda-intel](http://www.alsa-project.org/main/ind...dule-hda-intel)

It seems that you have to properly manually edit the /etc/modules.conf file and possibly other files. Then I installed the realtek audio drivers.

Here is a copy of my EDITED /etc/modules.conf file:

# ALSA portion
alias snd-card-0 snd-hda-intel
alias snd-card-1 snd-cmipci
options snd-cmipci id=&#8221;first&#8221; mpu_port=0×330

# OSS/Free portion
#alias sound-slot-0 snd-card-0
#alias sound-slot-1 snd-card-1
# OSS/Free portion - card #1
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

# OSS/Free portion - card #2 (cmipci)
alias sound-slot-1 snd-card-1
alias sound-service-1-0 snd-mixer-oss
alias sound-service-1-3 snd-pcm-oss
alias sound-service-1-12 snd-pcm-oss

Here is a copy of my ORIGINAL /etc/modules.conf file:

# ALSA portion
alias snd-card-0 snd-hda-intel
alias snd-card-1 snd-cmipci

# OSS/Free portion
alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1

Also, here is a copy of my ORIGINAL /etc/modutils/alsa file which I have NOT yet edited. I will try editing it after I see how everything works:

# ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-hda-intel
# module options should go here

# OSS/Free portion
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0

# card #1
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

Also, here is a copy of my &#8220;/etc/modprobe.d/sound&#8221; file which I edited, according to some instructions on this website [[http://www.datanorth.net/~cuervo/blo...e-a215-s7407/]](http://www.datanorth.net/~cuervo/blo...e-a215-s7407/]) which I followed:

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=toshiba

My original &#8220;/etc/modprobe.d/sound&#8221; file is:

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel

I had to add the line &#8220;options snd-hda-intel model=toshiba&#8221; to the /etc/modprobe.d/sound file in a text editor such as gedit.

I rebooted and the sound works. You figure it out.



I uninstalled the bold/underlined above. I went to synaptic, typed in alsa, and on the right side it told me whether that particular package was a driver or utility. I found both and marked for removal. However, when I selected the one package, it prompted me saying another one will be removed too. I have no idea which one. I made the mistake of just clicking apply. However, I'm just confused over why it didn't prompt me that it was a serious issue. It seemed like it was an alert like "Yo, that's cool, but keep in mind if you uninstall that package, this one over here will uninstall too." K, no big deal. Fine. I hit apply and BAM. Black screen.


Now, what can I do to fix this? Is there a way to fix it? Or should I just reinstall? If I have my root/home on different directories and I reinstall, will things like my theme and my compiz fusion settings still remain if I don't format my home partition? Or is that information saved on root, where it would obviously be formatted?

---

### Post by Rocket2DMn on 2007-12-13
OK, for starters I'm not a very big fan of following guides that people post all over the web.  I prefer to take guides from solid sources.  Just because something worked for somebody doesn't mean it's going to work for you - esp since you dont have the exacty same hardware.
I suggest going back and undoing all the changes you made to files (you will have to do it from the command prompt or boot from a livecd and mount the filesystem).  "nano" is a nice simple command line text editor that you can use.
I hope you keep backups of most of your stuff, but all of your data is still on your hard drive.  If you reinstall everything will be wiped from those partitions, so you would have to backup everything first.
Since you have windows, you can access your ubuntu partition using the driver from [http://fs-driver.org/](http://fs-driver.org/)
From what I understand, it works in vista.  Be aware that it is not guaranteed to work with the ext3 filesystem, but if youre just backing stuff up it should be fine (see [http://fs-driver.org/faq.html#acc_ext3](http://fs-driver.org/faq.html#acc_ext3) ).
Using that you can backup anything you need from your linux partition either to a folder on your windows drive if you have space, to an external drive, or even to dvd.

It is almost always possible to fix problems, but we just don't have enough information on what went wrong to provide an accurate solution for what you did (if the above suggestion doesnt work).  A reinstall would probably be the easiest way at this point.

---

### Post by Roasted on 2007-12-13
I don't have anything worthwhile on the laptop due to the sound not working. I got this laptop 3 flippin weeks ago and I've spent hours a day trying to get the sound working. It's at the point where I'm about done using Linux on it and I'll just let my desktop as my Linux machine. I vowed to not put anything on the laptop till I got wireless and sound working. Wireless works. Sound doesn't.

I know about nano. But what good does that do me? I uninstalled two packages when this issue happened. Logically I would think reinstalling them would help... which I thought I did earlier... and it didn't work. :(

---

### Post by Rocket2DMn on 2007-12-13
Yeah, but you modified some other files as well - I would revert to the original setup in those as well.  Otherwise just wipe it and start fresh since you got nothing to lose with it.

---

### Post by Roasted on 2007-12-13
But while I'm at it I'm trying to FIX the problem. Reinstalling is just a last resort for me. How can I fix the issues? What would I be changing?

---

### Post by Rocket2DMn on 2007-12-13
So we've come full circle.
First you need to install all packages you removed, I'm assuming it's only alsa-utils and alsa-base and alsa-tools - but don't quote me on that, you're the one who actually did it and saw what it said.  How you go about this is up to you, were you ever able to get to a tty when booting to your normal kernel?  If so, download them with 
```
sudo apt-get install alsa-base alsa-utils alsa-tools
```  
If not, you are stuck at the recovery terminal with no internet.  You can load the packages onto a usb drive, mount it, and install with dpkg.
[http://packages.ubuntu.com/gutsy/sound/alsa-base](http://packages.ubuntu.com/gutsy/sound/alsa-base)
[http://packages.ubuntu.com/gutsy/sound/alsa-utils](http://packages.ubuntu.com/gutsy/sound/alsa-utils)
[http://packages.ubuntu.com/gutsy/sound/alsa-tools](http://packages.ubuntu.com/gutsy/sound/alsa-tools)
running this on the deb files:
```
dpkg -i filename.deb
```


Second you need to undo the stuff you did before that, like changing the modules file and whatnot.

Then you have to restart gnome
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

If ALL else fails and you can be connected to the internet at a tty (or be able to use your livecd as a repository like we covered earlier), you can reinstall the GUI stuff with
```
sudo apt-get install ubuntu-desktop --reinstall
```

---

### Post by Roasted on 2007-12-13
If you're ever in the Philly area of Pennsylvania, I'll treat ya to a drink.

That did the trick. I don't know if it was the beginning part or not, but I just ran everything + the last command where you reinstall ubuntu desktop. Everything is working now! Thanks bro!

Now to get my sound working... ahhhhhhhhh!!

---

