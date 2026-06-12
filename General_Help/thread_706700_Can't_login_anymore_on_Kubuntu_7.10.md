---
title: "Can't login anymore on Kubuntu 7.10"
date: 2008-02-24
forum: General Help
---

### Post by negge on 2008-02-24
This is what just happened:

I added a new user 'cause I tried to configure a new FTP account. I did this by going to System settings and then User management. Everything went fine. Then after a while when I opened up a new shell window I got maybe 20 lines saying something like "bash: [: invalid argument" and when I tried to edit /etc/vsftpd.conf I get an error saying "Segmentation failed (core dumped)". I thought a quick reboot might solve the problem.

Now when I boot up Kubuntu I get to the login screen, and when I enter my password the screen goes black and then the login screen comes up again. I tried logging in with the new user I created but still the same. I thought the new user ****** everything up so I rebooted in failsafe mode and deleted the user. Still I couldn't login.

What the hell should I do? I searched google but all I got was noobs that forgot their passwords and such things... When I get to the login screen and choose to login through the a shell instead I get the same bash invalid argument ******** but atleast I can login.

I hope somebody here can help me out.

**Update**: I rebooted to my Windows XP partition and used some program to access the Linux partition. In the file .xsession-errors which is in my home directory I found the following:

> /etc/X11/Xsession: line 92:  6020 Segmentation fault      (core dumped) chmod 600 "$ERRFILE"

Don't know if that's to any help but still.

---

### Post by sumguy231 on 2008-02-24
I'm not sure if this would actually help, but you could completely reinstall and reconfigure X like so:
```
sudo apt-get --purge --reinstall install xserver-xorg
```
Just answer all the questions about your hardware when the configuration comes up.

Edit: Oh yeah, and since you can't log in you'll probably have to do it from a text terminal. Get to one by pressing Ctrl+Alt+F7. And when you're done reinstalling, run this command:
```
sudo /etc/init.d/kdm restart
```

---

### Post by negge on 2008-02-25
I'll try that when I get home from work today.

**Edit:** I'll post the weird "bash invalid argument" errors that I get aswell.

---

### Post by negge on 2008-02-25
> **sumguy231 said:**
> I'm not sure if this would actually help, but you could completely reinstall and reconfigure X like so:
```
sudo apt-get --purge --reinstall install xserver-xorg
```
Just answer all the questions about your hardware when the configuration comes up.

Edit: Oh yeah, and since you can't log in you'll probably have to do it from a text terminal. Get to one by pressing Ctrl+Alt+F7. And when you're done reinstalling, run this command:
```
sudo /etc/init.d/kdm restart
```

I tried to do what you just said but I was unable to connect to the Internet. Then I tried booting with the live CD and mounted my Linux partition but I figured if I did the above command then it wouldn't reinstall the xserver that was on the partition. I also did a fsck on the partition but there were no errors.

Is there any way to get a copy of the long list of text that shows up when you boot in recovery mode? It says "Segmentation failed" everywhere...

If no one has posted something in the next couple of hours I'll just do a clean install and make a backup right after I've installed the most essential apps and hope this **** doesn't happen again.

It sucks that Ubuntu has no option to restore a broken installation like XP does (or am I missing something?)

---

### Post by sumguy231 on 2008-02-25
I'm not sure if you've reinstalled yet, but...
I think you might be able to find the errors you're looking for in /var/log/boot or /var/log/messages.

By the way, the closest thing on Ubuntu to repairing a broken install (at the moment) is to put your /home folder on a different hard drive partition and then reinstall over the rest of the system leaving that partition intact.

---

### Post by negge on 2008-02-26
I'll post those logs here when I get back home again, I got some great little app for Windows that allows me to browse and save files from Ubuntu's ext3 partition. I haven't reinstalled yet, I'm gonna do it tonight I think. 

I'll backup the /home folder too, never thought of that before so. Not much valuable inside there, the biggest hustle after a reinstall is installing and configuring all your programs...

---

### Post by negge on 2008-02-26
I decided to skip all the hard work and just do a clean install, it seemed like the easiest way, afterall I'm quite new to Linux. Thanks for all your help though, now I know where to come in the future when I've got something else on my mind.

---

### Post by sumguy231 on 2008-02-26
By the way, the majority of your program configs are kept in hidden directories in your home folder (they all start with a .) so if you get those backed up it can be like nothing ever happened.

---

### Post by dimethroxy on 2008-02-26
exact same problem here...

this happened after today update! 

this is the THRID TIME an update broke my kubuntu...

are they even testing those damn updates?! i'm tired of that ****.

---

### Post by Horsman on 2008-02-26
This just happened here on my friends computer with the most recent update as well, anyway to revert?

---

### Post by sumguy231 on 2008-02-27
What packages were in it? I haven't had any update problems lately but I have updates to kaffeine waiting to be installed right now.

---

