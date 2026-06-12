---
title: "E: subprocess usr/bin/dpkg received a segmentation fault"
date: 2008-04-03
forum: General Help
---

### Post by clanky on 2008-04-03
When trying to install the latest updates I got this message, everything seemed to download OK, but when ubuntu tried to install the updates it came back with this message.

There are a couple of other threads on this and the only solution which seems to have worked is to replace the RAM, and even this only seems to have worked for 1 person, can anyone give me some idea of what might be wrong and any other ideas of how to fix it, failing that will buy some new RAM tomorrow.

---

### Post by erginemr on 2008-04-03
To rule out the possibility of RAM failure, please reboot your system and select memcheck (or memtest) from the Grub menu.

---

### Post by prshah on 2008-04-03
> **clanky said:**
> 
There are a couple of other threads on this and the only solution which seems to have worked is to replace the RAM, and even this only seems to have worked for 1 person, can anyone give me some idea of what might be wrong and any other ideas of how to fix it, failing that will buy some new RAM tomorrow.

If you think the problem is RAM, run the "memtest" option from your system grub boot screen or the ubuntu live cd. Anything that shows up in RED during the test is bad. An exhaustive test will run for hours; but mostly if there is any real problem in the memory it will be found within 10~15 mins, after which you can interrupt it.

You can try clearing your (secondary memory) swap partition. Use the "swapoff -a" command to turn off swap usage, then use the "mkswap -c /dev/hdx9" command where "/dev/hdx9" is to be replaced with your actual swap partition. NOTE: These commands have great potential for harming your computer. Use with extreme care. Post here if you'd like more details on these commands.

---

### Post by erginemr on 2008-04-03
Following this success story:
[http://www.linuxquestions.org/questions/debian-26/dpkg-returned-an-error-code-1-segmentation-fault-249353/](http://www.linuxquestions.org/questions/debian-26/dpkg-returned-an-error-code-1-segmentation-fault-249353/)

You can also have a problem in one of the installed packages, so don't despair. Dpkg receives the "segmentation fault" flag but it probably receives the error signal from another misfit package. So, please try to track down the whole process and post the error message you receive in detail.

---

### Post by sekinto on 2008-04-03
nevermind

---

### Post by clanky on 2008-04-03
OK, thanks for the info, have run the memtest and it all seems OK.

I have followed the thread in the linuxquestions link and I am completely lost, what do I have to run to get the error message that you mentioned?

Thanks.

---

### Post by philinux on 2008-04-03
Run this in a terminal.

sudo dpkg-reconfigure -a

It takes awhile to run.

---

### Post by clanky on 2008-04-03
> **philinux said:**
> Run this in a terminal.

sudo dpkg-reconfigure -a

It takes awhile to run.

I almost replied to say that I had tried that before and it didn't seem to do anything, but then I realised that it was phrased slightly differently, it is running now and i will post results when finished.

Thanks.

---

### Post by erginemr on 2008-04-03
> When trying to install the latest updates I got this message, everything seemed to download OK, but when ubuntu tried to install the updates it came back with this message.

If the above command works, you are good to go. 

But if it doesn't, you can reproduce the error message from the terminal with this set of commands:
```
sudo apt-get update
sudo apt-get upgrade
```
which will try to update your system and fail with a series of error messages.

---

### Post by clanky on 2008-04-03
OK, I ran sudo dpkg-reconfigure-a

It took an age, but it all seemed to go through OK

I have saved the terminal output in a text file so that I could post it here.

I got a message saying that I should restart my computer, and when I did so, logged in with my password, and the computer seemed to crash just at the point where it should have displayed the desktop, any idea what i have done?

It will boot in recovery mode, but when I exit recovery mode exactly the same thing happens, I get the login screen and then system crashes.

---

### Post by clanky on 2008-04-03
Maybe I should clarify a little, when I say that the system crashes, what actually happens is that it returns to the login screen, tried to login again and the same result.

---

### Post by erginemr on 2008-04-03
I believe the command to apply should have been:
```
sudo dpkg --configure -a
```
which will reconfigure your Debian package management system, in lieu of 
```
sudo dpkg-reconfigure -a
```
which will reconfigure EVERYTHING.

Out of curiosity, I had tried the latter command once, but I was terrified at the notion of the sheer amount of things it set out to configure, so I cancelled immediately.

Anyway, let's try to bring your screen back. Try this command from the terminal:
```
ls -l /etc/X11/xorg.conf*
```
This command will list the config file "xorg.conf", which is responsible for your Gnome screen congifuration and resides in "/etc/X11" folder, along with its backups taken automatically.

What you should do is to check the date of xorg.conf, the original one and find the back up with the most recent date. Don't use the *.failsafe files though, they are for something else.

So, lets say the file with the most recent date is "/etc/X11/xorg.conf_backup_200803272103". Then you need to issue this set of commands:
```
cd /etc/X11/xorg.conf
sudo cp xorg.conf xorg.conf.mybackup
sudo cp xorg.conf_backup_200803272103 xorg.conf
```
Here, the first line changes to the /etc/X11/ directory. Second one takes a back up of your current xorg.conf file And the third overwrites the current one with the penultimate copy. You can use Tab to auto-complete your commands and Tab twice to give you a list of your available options.

Try to restart your graphical server with the command:
```
startx
```

---

### Post by erginemr on 2008-04-03
Yo&#305;u should really try the the above, no matter how intimidating it may seem. But if the replacement doesn't work for whatever reason, you may also issue the command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
which will try to configure your X server (desktop) automatically. You should back up your current xorg.conf file first though, as this command may revert to another driver and I may ask you to post the contents of the broken xorg.conf file later. So, first;
```
cd /etc/X11/xorg.conf
sudo cp xorg.conf xorg.conf.mybackup
```
and then;
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by clanky on 2008-04-04
I have logged in using failsafe gnome, tried all of the above and still no success when i try to login using either gnome or xclientscript.

I am going back to sea shortly and I am going to be without an internet connection for 3 months, should I just bite the bullet and re-install ubuntu while I still have time to set it all up again.

---

### Post by erginemr on 2008-04-04
OK then. 

What is your graphics card brand and model? 

If you are willing to strive a bit more:

Do you have access to your computer at the moment? Are you dual-booting it with Windows? If so, can you please use either one of the following Windows programs:
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)
[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

to view your Linux drive from within Ubuntu and post the contents of the malfunctioning **/etc/X11/xorg.conf** file here?

Nevermind if you say you will reinstall Ubuntu anyway.

---

### Post by clanky on 2008-04-04
erginemr, thanks very much for all your help, I would have tried to work through this (just for the learning curve) if I wasn't going back to sea so soon, right now I just really need a working system, so I have re-installed.

I have got my screen back and am just downloading updates at the moment, so not sure whether they will work or not, we will see.  I will let you know how it goes.

Thanks again for all your help.

---

### Post by erginemr on 2008-04-04
You are most welcome **clanky**. All that matters is that you have a working system, this way or the other...

By the way, looking at your avatar, you seem to have a penchant for rafting / surfing. I would love to try rafting one day, if I can gather enough courage. 8-[

So, take care and have fun at sea! 8-)

---

### Post by clanky on 2008-04-04
All working and able to update / download without any problems.  Thanks to everyone for all the help, I would have loved to have worked through the problem and solved it rather than just doing a re-install, but like I said I am off to sea on Sunday / Monday so I really just had to bite the bullet and re-install.

As for my avatar, I am just starting to get into kayaking in a pretty big way, **erginemr** if you fancy having a try at rafting, go for it, rivers are awesome, no matter how you get down them.

---

