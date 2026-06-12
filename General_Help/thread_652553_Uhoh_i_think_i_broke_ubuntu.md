---
title: "Uhoh i think i broke ubuntu"
date: 2007-12-28
forum: General Help
---

### Post by arpalermo on 2007-12-28
Im  new to ubuntu... 

The problem is my sound just died and wont work, and whenever i come across a page with flash in it firefox becomes unresponsive and eventually so does the rest of ubuntu.

Ok, I tried to install java today but had no idea what i was doing, downloaded a bunch of stuff, clicked on a lot of things, and got a lot of boxes asking for my password. It never really worked - i tried some site with a java animation and it wouldnt work right.

I forgot about it and evrything was working ok... i installed amorak and got it to play some music... then i went to some youtube video and everything started becoming unresponsive. The youtube video was playing but not correctly, with the sound skipping and everything out of sync, and amorak just stopped playing.

 The computer became completely unresponsive so i shut it off. Then i started it back up... it wouldnt load... started it up again and there is no sound anywheres... restarted a dozen times and still no sound. Im using a sound card but it was working perfectly before this happened, i never had to install any drivers or anything. Also pages with java would just say "install missing plugi completelyns" and stuff but now they make firefox crash.

What is this? How can i make things how they were before? Could someone guide me through this... i have no idea how to do anything at all... :(

Also, this is completely unrelated, but someone told me that Mac OS is linux based! Is this true? Does that mean its just another distro like ubuntu or fedora and such? And how can this be? I thought the guy that invented linux made it so that linux has to stay free...

---

### Post by marshall.robert on 2007-12-28
as for your sound problem im not sure i can help you, but if you install a package called 'Ubuntu Restriced Extras' that sorts you out with stuff like java and flash, also mp3 codecs and stuff like that.

and mac is unix based, not linux.

-rob

---

### Post by empthollow on 2007-12-28
OS X is based on a bsd kernel which yes is unix.  linux was originally a hack of the unix kernel.  OSX has a base system that is pretty much the same as unix but where is differs is  the graphical environment.  Apple wrote their own graphical and periferal handling system to run on the unix base system (they of course customized the kernel and underlying system). that system is called cocoa and replaces X11, they then wrote the infamous aqua desktop which replaces gnome or any of the other desktop environments.  Hope that helps you understand how they can use open source and still have a proprietary os. 


As for your problems with the sound, i'm not sure where your problem is.  i usually install the sun java package from the repositories and that serves my java needs.  i have had some sound issues with different programs open and both using alsa or oss sound and one of them just hangs on the the device so the other can't output anything.  maybe one of the java apps you installed is holding the device hostage so to speak.  you could go to system -> preferences -> sounds to try and do some troubleshooting on sounds devices.

---

### Post by Victormd on 2007-12-29
Try this thread:

[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

There you'll find a script to install flash/java/mplayer. Keep in mind that this thread is for AMD64 version of Ubuntu 7.10

---

