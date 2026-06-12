---
title: "[SOLVED] gedit Firefox OpenOffice crashing in 6.06"
date: 2008-02-07
forum: General Help
---

### Post by cjax1 on 2008-02-07
Hello.

I know this problem has been posted before but I haven't found an answer. I've been using this 6.06 install for quite a while now but this just started happening sometime in the last few days, maybe three or four. I can't think of anything I've done as far as changes or installing anything recently except change theme settings and font settings on the desktop but I've since set them back the way I had them for a long time and I still have the same problem.

When trying to save something in gedit it crashes if I try to change the save location. If I just let it save to Documents it saves fine.

In Firefox when I save a web page if I try to change the name of the web page before I save it it crashes right away.

And I just learned by searching that users with this same problem were reporting that Openoffice was doing the same thing. So I tried it and sure enough it's crashing too when trying to save a document. I had to kill those windows and as usual the document recovery feature is worthless.

I have a backup of the entire system back on Jan 21-08 that should be good and I may just restore to that date, I know everything was working then, but I was just wondering if anyone knows the answer to this problem.

Many thanks

---

### Post by apetresc on 2008-02-07
Run gedit from a terminal and make it crash -- it should leave behind some sort of diagnostic message in the terminal, post it here.

Also, is there any particular reason why you're still on 6.06? 7.10 is pretty rockin', you know :)

---

### Post by kerry_s on 2008-02-07
hmm, sounds like permission issues.

---

### Post by cjax1 on 2008-02-07
Thanks for the quick reply.

I did that and there was no message in terminal. It just went back the prompt.

I haven't checked to see if this has affected any other apps. I do remember a system update recently but I can't remember what it was or even if thats when this problem started. I think this started 2-4 days ago.

I think I'm going to get in the habit of doing a complete system backup each time before I install any updates even if I have to wait. The only updates that have affected me so far was the last two kernel updates. Each of the last two kernel updates screwed up the grub menu.lst. The first time the entry for Windows was gone. Last time it was an entry for another distro I have installed was gone and there was an entry for each and every old kernel in Ubuntu and all the recovery entries. Long list. I keep a backup of menu.lst now to make redoing it easier.

I'm going to search around a little more but can't keep my eyes open much longer. :)

I did try 7.10 once but it seemed to make it so hard to create desktop web shortcuts and a couple other things, I forget now. If I remember correctly I didn't figure out how to set up some panels on the desktop. I like to have one that slides out from the side, and I usually have a couple on the top and so on. It seamed like they made it hard for me to customize it the way I always set it up. I have the bottom panel looking like a Mac's. It was something like that anyhow. Or maybe it was trying to put shortcuts on the panels too. I know, minor stuff. I know I have to upgrade sometime. I'm sort of waiting for the next LTS version. Then I will move on. 6.06 has treated me very well.

Who knows, maybe it's time to move up to 7.10 anyway. :)

---

### Post by cjax1 on 2008-02-07
Permission issues would cause just typing a different name into the save box in firefox? Sometimes I save two or more emails in Yahoo email, pictures and text, as a web page so I can view the same page on my laptop when I don't have an internet connection. It's info I need. But every one of the pages saves as Showletter.html so I rename them before I save them so I can put all the files in one folder and put them on my flashdrive. I can delete the name in the save box but the instant I type the first letter to rename Firefox crashes. If I just let it save as Showletter.html they save fine. that's whats so strange to me.

If it is permission issues do you know what it might be? I can understand if where I was saving to was read only, and I know this isn't the case, but that wouldn't cause a crash as far as I know. It just wouldn't save. I'd get an error message. Unless there's some other part of permissions I don't know.

Sorry but I need some rest. I'll check back later. Thanks.

---

### Post by cjax1 on 2008-02-07
This morning I tried saving something in Bluefish and GIMP and they both crashed. So now it's affecting Firefox, gedit, OpenOffice, GIMP, and I wouldn't doubt if there's more but I haven't tried. I tried opening all four in terminal and making them crash and the only one that gave me any message was GIMP.

chris@ubuntu-desktop:~$ gimp

(script-fu:5873): LibGimpBase-WARNING **: script-fu: wire_read(): error
Segmentation fault
chris@ubuntu-desktop:~$

So now I'm curious what a segmentation fault is. It's off to work for me. I'll look this up later.

Many thanks.

---

### Post by apetresc on 2008-02-07
> **cjax1 said:**
> This morning I tried saving something in Bluefish and GIMP and they both crashed. So now it's affecting Firefox, gedit, OpenOffice, GIMP, and I wouldn't doubt if there's more but I haven't tried. I tried opening all four in terminal and making them crash and the only one that gave me any message was GIMP.

chris@ubuntu-desktop:~$ gimp

(script-fu:5873): LibGimpBase-WARNING **: script-fu: wire_read(): error
Segmentation fault
chris@ubuntu-desktop:~$

So now I'm curious what a segmentation fault is. It's off to work for me. I'll look this up later.

Many thanks.

A segmentation fault is a type of error where a process tries to access memory that it has not allocated. This can happen for a very large variety of reasons, and is a very serious error.

The fact that such a thing is happening to so many unrelated applications leads me to believe that the problem, in fact, is due to a faulty library. You may, at some point, have been upgrading something like gtk or libc or libstdc++ and had (either through a hardware fault, a bug, accidental cancellation) some sort of corruption going on. Now certain C/C++ functions are causing segfaults. This is the only explanation I can think of for the sudden onset of segfaults in a variety of unrelated programs.

This bug is probably harder to fix than its worth. Is it within the realm of possibility to do a backup and reinstall? Unless your problem is hardware related (try running a memtest86!), this will solve it and it is unlikely that it will return.

---

### Post by y-lee on 2008-02-07
Be warned a hardware error could possibly cause this. try using a live cd either ubuntus or knoppix and if it still happens something is wrong with your machine physically. If not your hardware I would most likely reinstall that error might be very hard to track down. :(

---

### Post by cjax1 on 2008-02-07
Hi,

As suggested y-lee I boot up the 6.06 live CD and tested Firefox and gedit and they did not crash. I was praying it wasn't hardware related.

What you mentioned Adrian did get me thinking. I did try unsuccessfully to install the latest Skype by adding "deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free" to my /etc/apt/sources.list file but apparently the latest version doesn't work on 6.06 because certain dependencies are out of date or something. I did have Skype working a long time ago but that was in another 6.06 install. I'm not sure if I did something or if it was unrelated but after that failed attempt the other day I did get an automatic update for something. Now that I think about it that update may have been related to gtk or libc or libstdc++. I'm not even sure if it was related to me trying to install Skype or not. I bet it was though. I'm going to pay more attention to these updates.

So I'm going to restore to my system backup on the 21st. It's a complete system backup not just my home directory so I won't have to reinstall anything. Thank god for backups. If I still get these problems I guess I'll have to assume it's a hardware problem but I don't think so. And I'm going to pay close attention and document any updates I get and test again.

Thanks for all your help. If I don't post back here tonight then all is well.

Thanks again. :)

---

### Post by y-lee on 2008-02-07
I> As suggested y-lee I boot up the 6.06 live CD and tested Firefox and gedit and they did not crash. I was praying it wasn't hardware related.

that is great news.  I was worried too. Hope the back up goes ok and good luck :)

---

### Post by cjax1 on 2008-02-07
I know I said if I don't post back here tonight then all is well but all is well. I just wanted to say the restore went fine and everything is back to normal. I got one update so far that was libapr0 but everything is still working. I can save in all the programs. It was probably something I did.

Thanks everyone.

---

### Post by y-lee on 2008-02-07
I think it was where you mixed debian stuff in with ubuntu in your source list.

> I did try unsuccessfully to install the latest Skype by adding "deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free" to my /etc/apt/sources.list file

Ubuntu is based on debian but there are differences. I would never be brave enough to try that one. :lolflag: 

I could be wrong but anyway go ahead and mark this as solved when you are sure everything is doing ok. Good luck.

---

### Post by cjax1 on 2008-02-08
OK, I'll mark it as solved. I was wondering if I should mark it as solved since I didn't actually solve the problem, just did a restore to get rid of the problem but I'll mark it as solved.

As far as adding that line to sources.list, I remember I did that some time ago and it worked great. I got Skype installed. But when I did it recently evidently the latest version of Skype requires dependencies that are newer versions than what I had. But from now on, after I upgrade to the latest Ubuntu, I'll just download the .deb package for Skype and install it myself if I want Skype, unless it's in one of the repositories. I'm still not sure what happened. I didn't try to upgrade any dependencies or libraries myself. It may not even be related to Skype. Who knows. I'm just glad for backups in this case.

Thanks again for your help.

---

### Post by cjax1 on 2008-03-06
Well it's been three weeks and everything has been working fine. But this same damn problem has come back just this morning. I have to restore again. Damn it!! I downloaded Linuxmint and I think I'll be installing that instead. I've been trying to hold out until 8.04LTS to upgrade Ubuntu but I can't wait for that now. Does anyone have a clue what's causing this? I haven't installed anything extra. I have a notice this morning there are some updates but I haven't even opened it and don't plan to.

---

### Post by cjax1 on 2008-03-07
This time the problem went away on its own. I'm thinking maybe it's a memory problem. Looks like I'll be running a memory test tonight. I guess if I have any more problems I'll start a new thread.

Can't wait for 8.04LTS :)

---

### Post by cjax1 on 2008-05-13
Hello. I wanted to report that I believe I found the culprit to my troubles. I simply reseated the memory modules, and even switched them around. It's been at least 6 weeks now since I did this. This Dell E310 came with two modules for a total of 512Mb RAM. Well, after using another installed distro on another partition for a short time (Sorry, I just did not have time to mess with it at that time) then trying Ubuntu I started getting the errors again, even after the latest updates at that time. But after re-seating the memory the errors in Ubuntu never returned. Not once. What I don't understand is, if it was the memory why the problem never showed up using the other distro. Maybe it's the way Ubuntu and the other one uses memory but it does seem like the memory was at fault. Just dirty contacts or whatever.

So my humble recommendation is if anyone else is having this segmentation error try re-seating the memory. It's not the first time re-seating something has fixed a problem.

I'm now using 8.04 and loving it. Go Ubuntu! Love you.

---

