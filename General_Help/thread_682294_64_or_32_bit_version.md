---
title: "64 or 32 bit version?"
date: 2008-01-29
forum: General Help
---

### Post by Thrasonic on 2008-01-29
So I downloaded the AMD64 bit version of the Ubuntu 7.10 DVD and installed it on a 40 GB hard drive.  The install went well.  The first time I booted into the new OS, however, it locked up after a few seconds of getting into the desktop environment.  I powered off the PC and started it up and got back in fine and things have been working fine for about an hour now.  I've tried installing a couple of packages, including the version of Java available, and I'm getting the following error message often:

Could not commit changes - Adept Manager
There was an error commiting changes.  Possibly there was a problem downloading some packages or the commit would break packages.

I'm curious to know if this is normal or if perhaps my install is jacked up.  I have a AMD64 x2 processor, which is one reason I went with the AMD64 version of the OS.  I also figured that it would run faster/better since it's 64 bit versus 32 bit.  If I'm off here let me know.  Or in other words, if I wouldn't see any decent benefit from going with a 64 bit environment over a 32 bit environment let me nkow.  I'm not a developer, nor do I plan to do anything special with this OS.  I just plan to use it for every day basic stuff (word processing, web surfing, listening to music, etc.).

---

### Post by anemptygun on 2008-01-29
I have a intel core 2 duo. After playing with the 64 bit version I decided to go with the 32 bit version just because of the plethora of 32 bit compatible programs. My system still runs ultra speedy, so I don't see the benefit of the 64 bit version.

---

### Post by overdrank on 2008-01-29
> **Thrasonic said:**
> So I downloaded the AMD64 bit version of the Ubuntu 7.10 DVD and installed it on a 40 GB hard drive.  The install went well.  The first time I booted into the new OS, however, it locked up after a few seconds of getting into the desktop environment.  I powered off the PC and started it up and got back in fine and things have been working fine for about an hour now.  I've tried installing a couple of packages, including the version of Java available, and I'm getting the following error message often:

Could not commit changes - Adept Manager
There was an error commiting changes.  Possibly there was a problem downloading some packages or the commit would break packages.

I'm curious to know if this is normal or if perhaps my install is jacked up.  I have a AMD64 x2 processor, which is one reason I went with the AMD64 version of the OS.  I also figured that it would run faster/better since it's 64 bit versus 32 bit.  If I'm off here let me know.  Or in other words, if I wouldn't see any decent benefit from going with a 64 bit environment over a 32 bit environment let me nkow.  I'm not a developer, nor do I plan to do anything special with this OS.  I just plan to use it for every day basic stuff (word processing, web surfing, listening to music, etc.).

HI and I see you are using KDE and I personally like the 64 bit it is fast. Have you checked the cd for errors? I am currently not using the 64 bit but will install again after Hardy testing.

---

### Post by steveneddy on 2008-01-29
I don't know what could be available for 32 bit that you couldn't compile for 64 bit.

I run 64 bit and if it isn't offered, I compile it. It's what all the cool kids are doing.

---

### Post by bodhi.zazen on 2008-01-29
You should use 64 bit , unless there is a reason not to.

Discussion thread : Advantages / Disadvantages : [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by anemptygun on 2008-01-30
> **steveneddy said:**
> 
I run 64 bit and if it isn't offered, I compile it. It's what all the cool kids are doing.

I guess I'm not that far along yet...

---

### Post by Kilz on 2008-01-30
> **anemptygun said:**
> I have a intel core 2 duo. After playing with the 64 bit version I decided to go with the 32 bit version just because of the plethora of 32 bit compatible programs. My system still runs ultra speedy, so I don't see the benefit of the 64 bit version.

There is no difference in the number of packages in the repositories between the 64bit and 32bit versions. 32bit applications can be installed to the 64bit version with a little work (following a howto). Please list all applications you could not install to the 64bit version.

---

### Post by supertails on 2008-01-30
32 bit are for 32 bit computers and the 64 bit is for 64 bit computers.

---

### Post by Thrasonic on 2008-01-30
> **overdrank said:**
> HI and I see you are using KDE and I personally like the 64 bit it is fast. Have you checked the cd for errors? I am currently not using the 64 bit but will install again after Hardy testing.

Good question.  When I burned the DVD I had the burning software verify it, so I assume that's what you're talking about.  It would appear the DVD is fine.

---

### Post by Thrasonic on 2008-01-30
Good morning all.  Thanks for the many responses.  It appears that sticking with the 64 bit version is a fine idea so I'll do that.  Any ideas on the error message I'm receiving?  I've tried installing a few things.  Some went through fine and others did not.  I installed Firefox fine through the packages, but as I said the version of Java available in the package manager didn't work nor did some 3d chess program.  If you think that maybe it's just a bug or something silly let me know.  I'll just ignore it for now, I suppose, until (and if) it becomes a constant problem.

---

### Post by bodhi.zazen on 2008-01-30
> **Kilz said:**
> There is no difference in the number of packages in the repositories between the 64bit and 32bit versions. 32bit applications can be installed to the 64bit version with a little work (following a howto). Please list all applications you could not install to the 64bit version.

I know you have strong feeling on this issue, please see the link I posted. This link goes through some of the issues often asked by 64-bit users and is quite informative. If you want a list of issues you can dig your teeth into, please start there.

Obviously 64 bit is not for everyone, Please do not antagonize users because you disagree with their choices.

---

### Post by Thrasonic on 2008-01-30
> **Kilz said:**
> There is no difference in the number of packages in the repositories between the 64bit and 32bit versions. 32bit applications can be installed to the 64bit version with a little work (following a howto). Please list all applications you could not install to the 64bit version.

So could that be why some packages aren't installing automatically, like the 3d chess one and the Java version available from the adept package manager?  Because the versions offered aren't 64 bit but 32 bit versions?

---

### Post by Kilz on 2008-01-30
> **bodhi.zazen said:**
> I know you have strong feeling on this issue, please see the link I posted. This link goes through some of the issues often asked by 64-bit users and is quite informative. If you want a list of issues you can dig your teeth into, please start there.

Obviously 64 bit is not for everyone, Please do not antagonize users because you disagree with their choices.


Thanks for that link, but I already knew about it. In fact most of the links used to prove points in it contain posts by me.
I am not out to force anyone to use anything. What I would like is some information when someone makes a statement that something doesnt work, or is missing. Often these statements are not given with any information as to what they think is missing. They are then pointed to when someone asks questions.

> **Thrasonic said:**
> So could that be why some packages aren't installing automatically, like the 3d chess one and the Java version available from the adept package manager?  Because the versions offered aren't 64 bit but 32 bit versions?
Java is available in 64bit. Can you please give the exact name of the 3d chess game?

---

### Post by anemptygun on 2008-01-31
> **Kilz said:**
> There is no difference in the number of packages in the repositories between the 64bit and 32bit versions. 32bit applications can be installed to the 64bit version with a little work (following a howto). Please list all applications you could not install to the 64bit version. 

I stand corrected.

---

### Post by Thrasonic on 2008-01-31
> **Kilz said:**
> Thanks for that link, but I already knew about it. In fact most of the links used to prove points in it contain posts by me.
I am not out to force anyone to use anything. What I would like is some information when someone makes a statement that something doesnt work, or is missing. Often these statements are not given with any information as to what they think is missing. They are then pointed to when someone asks questions.


Java is available in 64bit. Can you please give the exact name of the 3d chess game?

Hi Kilz, the 3dchess game is literally called "3dchess" in the repository or pacakages or whatevery they're called.  If I open package manager and search for 3dchess that's what comes up.

FYI, just for fun (and since I had an hour) I installed the 32 bit version over the 64 bit (used the entire hard disk for the install so no more 64 - it was blown away) and tried to install the Java RTE as well as 3dchess.  3dchess did install but Java did not.  I got that same error message as before.  So I'm guessing it's not specific to the 64 bit version, and I'm also guessing it's not the DVD since I have one DVD with the 64 bit version and one with the 32 bit version.  As I said in an earlier post I did choose "Verify disc" or whatever verify option was available in the DVD burning software to make it verify that the disc burned properly.

Now, Kilz, let me ask another question.  I know that you've said any 32 bit application can run on the 64 bit version of Ubuntu if you recompile it or something.  I don't really plan to use any applications that aren't installed by default except maybe one or two, literally.  I'm a total newbie so I don't know what all the available applications are.  Maybe later on once I get a handle on Linux I'll look into more applications, but for now it seems like I really only need what comes auto-installed, plus Firefox, plus Java and Flash and Shockwave, basically the stuff needed to get the true multimedia, web surfing, audio listening experience.  Does that make sense?  Thus, it seems that 64 bit would work for me just as well as 32 bit.  So is 64 bit computing inherently better or faster or something?  Is there a reason I should go with the 64 bit OS considering I'll just be using the OS and apps for fairly basic, standard work?

---

### Post by Kilz on 2008-02-01
> **Thrasonic said:**
> Hi Kilz, the 3dchess game is literally called "3dchess" in the repository or pacakages or whatevery they're called.  If I open package manager and search for 3dchess that's what comes up.

FYI, just for fun (and since I had an hour) I installed the 32 bit version over the 64 bit (used the entire hard disk for the install so no more 64 - it was blown away) and tried to install the Java RTE as well as 3dchess.  3dchess did install but Java did not.  I got that same error message as before.  So I'm guessing it's not specific to the 64 bit version, and I'm also guessing it's not the DVD since I have one DVD with the 64 bit version and one with the 32 bit version.  As I said in an earlier post I did choose "Verify disc" or whatever verify option was available in the DVD burning software to make it verify that the disc burned properly.

Now, Kilz, let me ask another question.  I know that you've said any 32 bit application can run on the 64 bit version of Ubuntu if you recompile it or something.  I don't really plan to use any applications that aren't installed by default except maybe one or two, literally.  I'm a total newbie so I don't know what all the available applications are.  Maybe later on once I get a handle on Linux I'll look into more applications, but for now it seems like I really only need what comes auto-installed, plus Firefox, plus Java and Flash and Shockwave, basically the stuff needed to get the true multimedia, web surfing, audio listening experience.  Does that make sense?  Thus, it seems that 64 bit would work for me just as well as 32 bit.  So is 64 bit computing inherently better or faster or something?  Is there a reason I should go with the 64 bit OS considering I'll just be using the OS and apps for fairly basic, standard work?

Will you rip cd's? Edit pictures? Backup DVD's? They all get a performance boost, and are normal activities. Everything you mention Is possible, except shockwave. Shockwave isnt available in Linux at all, only flash.
But look, you went and proved that problems followed you from 64bit to 32bit. We as 64bit users have to stop asking if there is a reason to install the operating system designed for our hardware. Instead in my and others opinion should ask Why not ?
To often old information and misinformation plays a key in leading a 64bit user to use the operating system that isnt designed to make full use of the hardware they bought. There is no reason not to run the 64bit version.
Is there java?
[http://packages.ubuntu.com/gutsy/interpreters/icedtea-java7-jre](http://packages.ubuntu.com/gutsy/interpreters/icedtea-java7-jre)
[http://packages.ubuntu.com/gutsy/devel/icedtea-java7-plugin](http://packages.ubuntu.com/gutsy/devel/icedtea-java7-plugin)
[http://packages.ubuntu.com/gutsy/interpreters/java-gcj-compat](http://packages.ubuntu.com/gutsy/interpreters/java-gcj-compat)
[http://packages.ubuntu.com/gutsy/libs/sun-java5-jre](http://packages.ubuntu.com/gutsy/libs/sun-java5-jre)
[http://packages.ubuntu.com/gutsy/libs/sun-java6-jre](http://packages.ubuntu.com/gutsy/libs/sun-java6-jre)
Yes, why you couldn't find it is unknown, the listings are from the Ubuntu repository listing site. You found a package that doesn't work (3dchess), they may exist for any version. But you might want to open a terminal and type in 3Dc. Its a 3d chess game like on StarTrek not a pretty looking chess set with 3d pieces.
If you cant find a 64bit version, its not necessary to compile a 32bit application, it will run [following the instructions on this thread.]("http://ubuntuforums.org/showthread.php?t=474790").
In the end its up to you, but me, I wouldn't buy a corvette and pull out half of the spark pulg wires.

---

### Post by Thrasonic on 2008-02-01
> **Kilz said:**
> Will you rip cd's? Edit pictures? Backup DVD's? They all get a performance boost, and are normal activities. Everything you mention Is possible, except shockwave. Shockwave isnt available in Linux at all, only flash.
But look, you went and proved that problems followed you from 64bit to 32bit. We as 64bit users have to stop asking if there is a reason to install the operating system designed for our hardware. Instead in my and others opinion should ask Why not ?
To often old information and misinformation plays a key in leading a 64bit user to use the operating system that isnt designed to make full use of the hardware they bought. There is no reason not to run the 64bit version.
Is there java?
[http://packages.ubuntu.com/gutsy/interpreters/icedtea-java7-jre](http://packages.ubuntu.com/gutsy/interpreters/icedtea-java7-jre)
[http://packages.ubuntu.com/gutsy/devel/icedtea-java7-plugin](http://packages.ubuntu.com/gutsy/devel/icedtea-java7-plugin)
[http://packages.ubuntu.com/gutsy/interpreters/java-gcj-compat](http://packages.ubuntu.com/gutsy/interpreters/java-gcj-compat)
[http://packages.ubuntu.com/gutsy/libs/sun-java5-jre](http://packages.ubuntu.com/gutsy/libs/sun-java5-jre)
[http://packages.ubuntu.com/gutsy/libs/sun-java6-jre](http://packages.ubuntu.com/gutsy/libs/sun-java6-jre)
Yes, why you couldn't find it is unknown, the listings are from the Ubuntu repository listing site. You found a package that doesn't work (3dchess), they may exist for any version.
If you cant find a 64bit version, its not necessary to compile a 32bit application, it will run [following the instructions on this thread.]("http://ubuntuforums.org/showthread.php?t=474790").
In the end its up to you, but me, I wouldn't buy a corvette and pull out half of the spark pulg wires.

Kilz, thanks for giving me your opinion on the matter and your line of thought.  I like it and I see no reason to go with the 32 bit version.  Like I said, I don't plan to do anything much with this machine.  Just typical use from a newbie.  I think I'll reinstall the 64 bit version and start playing around with it.  My goal is to get to a point where I only need Windows for the gaming I do.  Thanks for the help.

---

### Post by Kilz on 2008-02-01
Glad to hear it. In the future , you may want to post 64bit issues to [the 64bit sub forum. ]("http://ubuntuforums.org/forumdisplay.php?f=134")That way you can get help from other 64bit users that may have had similar issues and know how to solve them.

---

### Post by Thrasonic on 2008-02-01
> **Kilz said:**
> Glad to hear it. In the future , you may want to post 64bit issues to [the 64bit sub forum. ]("http://ubuntuforums.org/forumdisplay.php?f=134")That way you can get help from other 64bit users that may have had similar issues and know how to solve them.

I'll keep that in mind.  Thanks for all your help.

---

### Post by SammyBoy247 on 2008-02-08
Kilz is almost always right on 64bit issues and it's in part thanks to his posts that I made the switch to 64 some six months ago and I haven't looked back.

I was initially put off by the widespread misinformation about lack of software, lack of development and only small gains in performance all of which are completely untrue.  There are a few tiny issues but nothing to right home about.

Check out the 64bit users forum for all the information and support you could ever need.

At the end off the day if you have a 64bit chip sitting in your machine and you are running a 32 bit architechture you have issues of a different kind.

If you've got it flaunt it - as it were.

---

