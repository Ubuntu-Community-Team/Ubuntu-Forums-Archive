---
title: "Downloader for X bug"
date: 2007-10-10
forum: General Help
---

### Post by tommy666 on 2007-10-10
I recently installed the gutsy beta and found that downloader for x (d4x) can no longer download from rapidshare.com. Other websites seem to work fine. I think the problem relates to the program adding an extra slash next to the first single slash in the link

ie [http://rapidshare.com/files/9999999/file.rar](http://rapidshare.com/files/9999999/file.rar) beceomes [http://rapidshare.com//files/9999999/file.rar](http://rapidshare.com//files/9999999/file.rar)

the error in the log is HTTP/1.1 404 not found, which is the same error firefox gives if I type the link with the extra slash.

I can't be certain that the problem is gutsy but the day before when I used it in fiesty it worked fine. I don't know if it used to add that slash. I can download from the site fine in firefox.

My housemate is running gutsy kubuntu and has the same problem.

Has anyone else had this problem, or at least know of another good linux download manager that works with rapidshare.com (Aria doesnt)?

Any insights would be appreciated. I can find nothing of the problem on google.

---

### Post by eviltandem on 2007-10-12
I am having this exact problem but with everything.  No matter what I do it adds an extra / to the first / it finds (after [http://)](http://)).

I thought I'd get smart and remove the first / to make it http:/ hoping that it would put the / there instead.  But no, it then decides that the entire download is actually an ftp, it removes the :/ entirely and rewrites the entire string to be ftp://

---

### Post by eviltandem on 2007-10-12
Whatever it is it's clearly broken.  If I click a file, go to properties, do nothing but click OK, it adds another one.  Everytime you click OK in properties it adds another one, no matter what you were doing.

---

### Post by ceb0 on 2007-10-13
Yep, I've got this problem too in Kubuntu gutsy.  It was driving me nuts because I can't find another downloader comparable to d4x.  In fact, download managers seem to me to be one area in linux where there isn't very much choice.  Strange that, seeing as how we have to download these huge iso files every few months.

Anyways, I tried various things to fix it.  Removed and installed feisty packages - didn't help.  Compiled from source - very difficult due to 'deprecated gtk' or some such error.  Resolved with a debian patch I found somewhere, but still didn't work.  Also, removed the hidden ntrc folder and tried both these again.  But it just doesn't work.

I posted this on the kubuntu forums a few days ago but so far no-one has a solution there (actually no-one has even replied).  For most people this isn't really a problem I guess, but I really hope this is fixable.  Actually, what I really hope is that someone could create something even better, as it seems that d4x hasn't been worked on for a while, the website has a note up saying it's moving to a new server but it's been like that for a long, long time.

If anyone finds a solution, then my gutsy experience will be complete.

---

### Post by JanneB on 2007-10-13
Same problem here:(

---

### Post by eviltandem on 2007-10-14
I suppose it's funny and sad.  I have installed every version of ubuntu since the beginning.  Every single one has something that doesn't work...

This tool works just fine in feisty...

---

### Post by JanneB on 2007-10-14
I just installed Debian Lenny (testing) on another computer for test. I don't know if it is bad news or good news but downloader for x behaves just the same on that system. :-? I suppose this means that it is not a problem jut with Gutsy but something more generall for debian based distros. Anyone knows if it works with a modern instalation of gentoo, slack or something else?

---

### Post by RobotJox on 2007-10-14
Same problem here :mad:

Is there any alternative download manager that supports rapidshare? Wxd doesn't, it seems...

---

### Post by tommy666 on 2007-10-15
Well at least the fact that lots of us have the problem makes it more likely that it will be fixed eventually

---

### Post by tommy666 on 2007-10-15
Does anyone know the best way to bring this to the attention of someone who can do something about it?

---

### Post by JanneB on 2007-10-15
[http://ubuntuforums.org/showthread.php?t=573534](http://ubuntuforums.org/showthread.php?t=573534) Maybe this would be a good place to report it?

---

### Post by JanneB on 2007-10-15
I have posted a bug report on Launchpad. Tommy 666 I hope it was ok that I used your error description in your first post as description of bug. 
//greetings Janne

---

### Post by RobotJox on 2007-10-15
Janne, could you pleast post a link to the bug report - I don´ t seem to be able to find it.
thanks

---

### Post by JanneB on 2007-10-15
[https://bugs.launchpad.net/bugs/153004](https://bugs.launchpad.net/bugs/153004)

---

### Post by ceb0 on 2007-10-16
Seems some Gentoo users have had the same issue and solved it, although this is way to difficult for me to contemplate, it might help someone else pinpoint the prob.

[http://forums.gentoo.org/viewtopic-t-572684-highlight-d4x.html](http://forums.gentoo.org/viewtopic-t-572684-highlight-d4x.html)

I just need to sort this out, and a little glitch with thinliquidfilm, and my gutsy is good to go.

---

### Post by JanneB on 2007-10-16
This is not a solution to the problem with d4x but I have found a way to get the KDE download manager **kget** to work with Rapidshare premium accounts. If you use kubuntu it's quite simple, if you use Ubuntu then you will have to install som Kde software and I have not tested if it works under Gnome but I can't really see why not. The key is to get your rs username and password into kdewalletmanager, then kget will use it to retrieve account information and be able to download from rapidshare.

**Applications needed**; kdewalletmanager, konqueror (may work without) and kget.

1) Use konqueror and go to [www.rapidshare.com](www.rapidshare.com)

2) Log in to premium zone with your username and password. Kdewalletmanager will start and ask if you want to save the password, click yes.

3) Now when username and password is stored in kdewalletmanager you can close konqueror and use firefox + flashget or copy + past into kget and kget will download your files from rapidshare.

For Gnomeusers it should be possible to manually add your account information in kdewallet manager  so kget can use it, but I have not tested it so I can't promise it will work.

Greetings
//Janne

---

### Post by maybeway36 on 2007-10-16
Konqueror works with KGet too, so as long as it's installed, you can use that.

---

### Post by RobotJox on 2007-10-17
Janne's solution works perfectly as described with Firefox and flashgot on Gnome - thanks a bunch!!

---

### Post by friderman on 2007-10-22
Thank you JanneB! 
Perfect solution!
=D>

---

### Post by bitebitter on 2007-10-25
Just another alternative, and you don't need to install kde stuffs: you just use wget. If you google for "wget download rapidshare" you will find at least  a couple of simple solutions

---

### Post by tommy666 on 2007-10-25
Downloader for x is still a better manager than kget or wget, as neither of these support segmented downloads. I would much rather get d4x working than settle for these.

---

### Post by crazybus on 2007-10-26
I would also like to see a fix or workaround soon.  I use d4x to download audiobooks and I have around 200 non-working items in the queue. :)

---

### Post by anco on 2007-10-27
Few days ago upgraded too... bit disappointing for me 955GM videocard has major bugs with this version, suspend en screensaver result in total lockup. Today I started D4X and it doesn't even start it is the screen comes up for less than half a second and it dies directly. I tried reinstalling, but nothing helps. D4X is more than dead for me at the moment.

When I start d4x from commandline I get this error...
mcop warning: user defined signal handler found for SIG_PIPE, overriding
Creating link /home/anco/.kde/socket-anco-laptop.
can't create mcop directory

I've no clue and it sure is since gutsy upgrade. For me it was the best downloader for linux after trying the few available last two years...

I hope that some developers get some time to do their hobby soon. Thanks anyhow.

---

### Post by ceb0 on 2007-11-06
Looks like our fix is finally here.  Check out that bug report at:

[https://bugs.launchpad.net/ubuntu/+source/d4x/+bug/155368](https://bugs.launchpad.net/ubuntu/+source/d4x/+bug/155368)

I downloaded the new packages and ... bingo, rapidshare downloading, no worries.  As one of the posters says though, any links you've already got in there will need to have their ////////////////////s removed manually, but once they're gone, you d4x works again.  Thank you very much Dennis Frank Mogensen.  Care to have a look at thinliquidfilm ...

---

### Post by d4xbugfixed on 2008-05-21
solution:
I also have a similar problem with Fedora 9 x86-64 with d4x.2.5.7.1-8.fc9.
I have a old, working on Suse 9.3, d4x2.5.0.final. I have copy this working version to the computer installed fedora 9, with some library files (.so), it works fine for me now on Fedora 9. Hope this help you.

---

