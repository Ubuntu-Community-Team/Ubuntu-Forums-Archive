---
title: "PLEASE help (file/folder permissions)"
date: 2005-05-14
forum: General Help
---

### Post by xbilly on 2005-05-14
Okay. I am fairly new to linux. I am using Hoary 5.04 and I would like to know exactly HOW do I change permissions for folders? It says that "I am not the owner" therefore I "can't change permissions". I need to be able to do this so I can update my firefox and such. Please help, I am completly lost!

---

### Post by Mike Buksas on 2005-05-14
[QUOTE=xbilly]Okay. I am fairly new to linux. I am using Hoary 5.04 and I would like to know exactly HOW do I change permissions for folders? It says that "I am not the owner" therefore I "can't change permissions". I need to be able to do this so I can update my firefox and such. Please help, I am completly lost![/QUOTE]
 Are you using nautilus (the built-in graphical file viewer) or the command line?

From the command line, the command you want is chmod. Basic useage is 
  chmod <mode> file/directory, where mode is a combination of letters which specify world, group, or user permmissions. The man page is a big help.

If you're working on directories for which you don't have the permission to change, run them as root by putting sudo in front, or switching to the user who owns the directories with su <username>

Holler if you need more info.

---

### Post by nad on 2005-05-14
[http://www.ubuntulinux.org/wiki/UserDocumentation](http://www.ubuntulinux.org/wiki/UserDocumentation)

---

### Post by Mike Buksas on 2005-05-14
[QUOTE=Mike Buksas]Are you using nautilus (the built-in graphical file viewer) or the command line?

From the command line, the command you want is chmod. Basic useage is 
  chmod <mode> file/directory, where mode is a combination of letters which specify world, group, or user permmissions. The man page is a big help.

If you're working on directories for which you don't have the permission to change, run them as root by putting sudo in front, or switching to the user who owns the directories with su <username>

Holler if you need more info.[/QUOTE]
 On second thought, though, you may not want to do this. If you're having an update problem with firefox, the problem is probably not the directory permissions. Are you updating with synaptic or apt-get? Synaptic will ask for the root password and run as root, bypasing the whole directory permissons problems. You can stick sudo in front of apt-get. If this is doesn't work, I'd treat this as a problem with your firefox installation and ask a more specific question about that.

Sorry for the confusion.

---

### Post by xbilly on 2005-05-14
I wanted to install some extentions for firefox. But I am unable to until I update to the new version. So I "downloaded" it... from there I can reinstall it to a new folder on my desktop. However, I would much rather just install it to the original mozilla-firefox folder in the /etc folder. When extracting the files, I get the message saying I do not have permission to do this. SO I right click on the /etc folder so that I can change the permissions by NOPE! NO DICE! I am not "the owner" apperently and I am unable to do so. I am sooo utterly confused. I have never used linux in my life.

---

### Post by rjhale3629 on 2005-05-14
[QUOTE=xbilly]Okay. I am fairly new to linux. I am using Hoary 5.04 and I would like to know exactly HOW do I change permissions for folders? It says that "I am not the owner" therefore I "can't change permissions". I need to be able to do this so I can update my firefox and such. Please help, I am completly lost![/QUOTE]


Lets start of easy - If you're trying to update firefox (I assume you are trying to upgrade), use synaptic  (System -> Administration -> Synaptic Package Manager). Since you are new - stick to what ubuntu provides for now. Read up on package management - you don't want to fork up your install of ubuntu------yet.........

If you want to change permisions - two things - First open nautilus - Go to File -> Create Folder. Make a new folder called test. Right click on the folder. Click on properties and then permissions - this is the easiest way to change permissions for now. Click on other folders and check out the permissions. Second - open a console (Applications -> System tools -> teminal. type *man chmod* - Read. The command line is the best way to go about changing permissions - because no matter what Windowing environment you are in, you always have the command line.

Good luck

Randy

---

### Post by rjhale3629 on 2005-05-14
[QUOTE=xbilly]I wanted to install some extentions for firefox. But I am unable to until I update to the new version. So I "downloaded" it... from there I can reinstall it to a new folder on my desktop. However, I would much rather just install it to the original mozilla-firefox folder in the /etc folder. When extracting the files, I get the message saying I do not have permission to do this. SO I right click on the /etc folder so that I can change the permissions by NOPE! NO DICE! I am not "the owner" apperently and I am unable to do so. I am sooo utterly confused. I have never used linux in my life.[/QUOTE]


Dang - posts pile up quick 

Don't unpack it to /etc - you don't have permision for that. What extension are you trying to install?   I'll try it and then we'll see what is happening.

---

### Post by xbilly on 2005-05-14
Wow. I could never fathom something being so difficult to update. I have firefox 1.0.2/ I want 1.0.4. That is all. NOW. How do I go about DOING this.

---

### Post by rjhale3629 on 2005-05-14
It's not that difficult upgrading - it just looks really difficult. 

Go to System - Administration - Ubuntu Update manager. If you check for updates (assuming you haven't upgraded) you should see an update to firefox 1.0.2. Run the update manager and get everything up to date. Crap - I just went back and re-read your post - you have 1.0.2. You've probably already done this

Now for the annoying part - I call this annoying cause it is for the new folk. Ubuntu should provide an update to 1.0.4 shortly - It just hasn't been done yet. The developers are probably (I say that because I'm not one) are working through the issues of getting it tested and deployed. So it will be done soon - just not yet. Keep watching....

My best advice would be hold off for right now - It is possible to install 1.0.4 - but it's best to not be on the cutting edge of a release and like I said - you don't want to fork up your install yet - give them some time and it will be there.

---

### Post by Mike Buksas on 2005-05-15
[QUOTE=rjhale3629]It's not that difficult upgrading - it just looks really difficult. 

Go to System - Administration - Ubuntu Update manager. If you check for updates (assuming you haven't upgraded) you should see an update to firefox 1.0.2. Run the update manager and get everything up to date. Crap - I just went back and re-read your post - you have 1.0.2. You've probably already done this

Now for the annoying part - I call this annoying cause it is for the new folk. Ubuntu should provide an update to 1.0.4 shortly - It just hasn't been done yet. The developers are probably (I say that because I'm not one) are working through the issues of getting it tested and deployed. So it will be done soon - just not yet. Keep watching....

My best advice would be hold off for right now - It is possible to install 1.0.4 - but it's best to not be on the cutting edge of a release and like I said - you don't want to fork up your install yet - give them some time and it will be there.[/QUOTE]
 The posts are coming in pretty fast here. I'll second what Randy said about waiting for 1.0.4 to be pacakged and available before you change the contents of /etc on your own. The file permissions of Linux probably seem like a nuisance right now, but they are an important part of Linux security. For example they are part of the reason that it is much harder for malicious code to take root and spread on Linux systems. They also make it harder to accidentally damage your system by changing something that you shouldn't. 

There's no reason that you cannot install 1.0.4 into your *own* file space, however. I don't recall how the install process of firefox works, but if it gives you an option about where to install, select your home directory. Then you can run your new version, install the plug in, and use that until 1.0.4 is available through apt.

---

### Post by rjhale3629 on 2005-05-15
Greetings - Sorry I had to cut out last night:

Check this out:
[http://www.ubuntuforums.org/showthread.php?t=34099&highlight=1.0.4](http://www.ubuntuforums.org/showthread.php?t=34099&highlight=1.0.4)

It's being worked on now. 

Here's a short article on unix file permissions: 
[http://www.onlamp.com/pub/a/bsd/2000/09/06/FreeBSD_Basics.html](http://www.onlamp.com/pub/a/bsd/2000/09/06/FreeBSD_Basics.html)

---

