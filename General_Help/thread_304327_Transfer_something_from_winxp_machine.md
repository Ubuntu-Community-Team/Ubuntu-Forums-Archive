---
title: "Transfer something from winxp machine"
date: 2006-11-21
forum: General Help
---

### Post by DougieFresh4U on 2006-11-21
I would like to put some thing on a floppy from my machine that runs WinXP and then put it on this Linux only machine. Am having problems with XP machine saying can not format disk then saying disk is write protected. How can I accomplish this task I am trying to do?

---

### Post by taurus on 2006-11-21
Just mount your XP from Ubuntu and transfer files over.  Fast and easy (cut out the middle step, flopy disk)...

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by echo $USER on 2006-11-21
What is the current file system of the disk?

---

### Post by Demon012 on 2006-11-21
From what you have said it appears that you have a non dual booted ubuntu machine and a seperate windows xp machine in which case you cannot mount the windows partition directly so back to the floppy.

Put the floppy disk in your windows xp machine and (as long as it has no data that you need on it) format it by going into my computer (or holding the windows button and pressing E to bring up explorer) and then right click on the floppy drive and select format. Use full format to make sure it gets the job done.

After the format has completed just copy over the files to the floppy disk and then put the floppy in your Ubuntu machine and Ubuntu should mount the now freshly formatted fat32 floppy disk with your data on. 

Ubuntu support read/write with fat32 so if you need to ever transfer files to your WinXP machine just put them on that floppy and both the XP machine and Ubuntu will be happy.

Hope this helps,

Demon012

---

### Post by DougieFresh4U on 2006-11-21
I believe the disk is just blank. Forgive my stupidity on this as I have never done this sort of thing before. I put disk in windows machine and a little window pops up saying disk not formatted would I like to format, after a minute or say I get the previous mentioned errors

---

### Post by taurus on 2006-11-21
Look at your floppy disk and make sure the tag in the upper left is not pushed up!!!

---

### Post by echo $USER on 2006-11-21
Could be defected, try another disk.

---

### Post by DougieFresh4U on 2006-11-21
taurus, I'm talking 2 differant machines

---

### Post by marianom on 2006-11-21
I suggest you install pscp in the windows machine ([http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)) and then just transfer the files to whatever directory you want from the command line in xp:

pscp myfile.txt your_user@your_ip:/home/your_user

---

### Post by taurus on 2006-11-21
> **DougieFresh4U said:**
> taurus, I'm talking 2 differant machines
I know.  You have XP on one machine and Ubuntu on another, and you need to transfer some files from XP to Ubuntu!  Look at the floppy disk to make sure it's not write protected or try another one.  I suppose you don't have a thumbdrive, USB, that you can use instead of a floppy disk!

---

### Post by DougieFresh4U on 2006-11-21
taurus, I have 3 different floppy's and all keep telling me write protected. No, I don't have those things you mentioned. I guess it's a lost cause for now. thanks

---

### Post by taurus on 2006-11-21
Any change you have some CD-RWs!!!

---

### Post by DougieFresh4U on 2006-11-21
got some of those but when i right click on the file I want, it does not give me that option. i hit the send to and only floppy or mail,IM & documents. Can you enlighten me as to how to get it to CD-RW ?

---

### Post by taurus on 2006-11-21
You have those files in your XP and you want to transfer them to your Ubuntu machine!  Just open your burning app and tell it to burn data.  Then, navigate to where those files are either drag them to your burning window or add them!

---

### Post by DougieFresh4U on 2006-11-21
To be honest with you, I don't even know if there is a burning thingy on this window machine. how would I know? I guess this sounds quit stupid of me

---

### Post by taurus on 2006-11-21
If you don't have a burning app for your XP, you can download one free and use it to burn all the stuff, files & ISO images...

[http://www.cdburnerxp.se/download.php](http://www.cdburnerxp.se/download.php)

---

### Post by DougieFresh4U on 2006-11-21
Thank you. I will log into forum on that machine and click your link . Thanks again.

---

### Post by taurus on 2006-11-21
> **DougieFresh4U said:**
> Thank you. I will log into forum on that machine and click your link . Thanks again.
No problem and I hope you have a CD/DVD burner already on your XP, right!

---

### Post by DougieFresh4U on 2006-11-21
No I don't. I've just logged in using windows machine-so slow , ok I' gonna try that link you sent

---

### Post by taurus on 2006-11-21
Is there a CD/DVD burner on any of your machine?  You need a burner before you can burn your files to a CD or a DVD.

---

### Post by DougieFresh4U on 2006-11-21
I downloaded burner from the link you gave taurus but when I open it I get message, There are no compatible CDR drives reported. Some older CDR drives are not currently supported. I don't understand what that really means.

---

### Post by taurus on 2006-11-21
The first question is do you have a burner in the machine that you have XP running right now?

---

### Post by DougieFresh4U on 2006-11-21
no I don't but I thought thats what I just downloaded from CDBurnerXP Pro.

---

### Post by taurus on 2006-11-21
You need to have a CD/DVD burner that connects to your machine first before you can use it.  The one you just downloaded is only a software to burn stuff to that physical device...  And since you don't have a burner on your machine, that app is useless now.  Do you have any machine that has a burner connected to it?

Also, how do you connect those two machines, XP & Ubuntu, to the internet?  Do they both connect through a router?

---

### Post by DougieFresh4U on 2006-11-21
you so right,  useless, I use a router I believe. (SpeedStream) and I hook both through that-Ethernet oh why can't this be Sal's problem and not mine

---

### Post by taurus on 2006-11-21
Hey, if you connect both XP and Ubuntu to a router, why not install samba on your Ubuntu and use it to mount your XP on it.  Then, you can copy stuff from XP over to your Ubuntu.  No need to burn or use any media to transfer files between them!

---

### Post by DougieFresh4U on 2006-11-21
Sounds good to me. I shall work on that immediatly. :-k  Thank you for all your help. :)

---

### Post by DougieFresh4U on 2006-11-21
I need help w/Samba, like where is it and what do I do? Don't know about this one

---

### Post by taurus on 2006-11-21
> **DougieFresh4U said:**
> I need help w/Samba, like where is it and what do I do? Don't know about this one
Okay, have a look at this link then.

[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

---

### Post by DougieFresh4U on 2006-11-21
ok i got this far and let the troubles begin:  sudo smbpasswd -L -e your_username
Failed to find entry for user your_username.
Failed to modify password entry for user your_username

---

### Post by taurus on 2006-11-21
You need to put in your actual username there for your_username!

---

### Post by DougieFresh4U on 2006-11-21
duh!

---

### Post by DougieFresh4U on 2006-11-21
how do I find the address of my linux box? sorry for asking so many stupid questions

---

### Post by taurus on 2006-11-21
Maybe this command helps?

```
ifconfig
```

---

### Post by DougieFresh4U on 2006-11-21
I think I broke windows. i got the address. now I re-booted windows like it saidand when it comes back from shurt down it's stuck saying : ISOLINUX 3.11 Debian-2006-03-16 blah blah blah and then it say : Loading.... and blinking cursor

---

### Post by DougieFresh4U on 2006-11-21
got it, now what do I put for drive under Map Network Drive?

---

### Post by Demon012 on 2006-11-22
Just going back to the floppy disk option trust me there is a write protect switch on the actual floppy disk itself here is a image that will show you where to look.

[http://doit.ort.org/course/storage/images/342.gif](http://doit.ort.org/course/storage/images/342.gif)

Basically if you can see 2 holes on the disk at the front it is write protected and you need to turn the floppy over and slide the plastic tab down to block the one hole to allow you to write the files.

---

### Post by Demon012 on 2006-11-22
> **DougieFresh4U said:**
> got it, now what do I put for drive under Map Network Drive?

In windows xp you normally put something along these lines:

> \\192.168.0.100\ShareName

Obviously the IP you put there needs to be the IP of the share on your Ubuntu machine and the sharename has to be the name of the share you have setup.

---

### Post by DougieFresh4U on 2006-11-22
Thank you Demon012. yes I saw the 2 holes an I slid the thingy down but then got told 'Windows could not complete format'. I have pretty much given up on this whole mess. The Samba thing is almost complete but I got hung up on the last part w/the windows set up. And I do not know if I have static IP address or the other one they mentioned (dhlcsl)  or some thing like that. ](*,)

---

