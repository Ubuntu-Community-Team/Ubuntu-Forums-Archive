---
title: "Skype on 64 bit Ubuntu 12.04"
date: 2015-01-27
forum: General Help
---

### Post by crazybear on 2015-01-27
I have seen many 'simple fixes' described on the internet. 'Just do X and voila you'll have working Skype on your Ubuntu 12.04. I once had working Skype on this OS, but that was over a year ago. I don't know what added program or change in the OS caused the failure, but it was sudden, complete and I've never been able to use Skype since. I have tried many things many times. Deleted all files and installed others. I've followed all the 'fixes' that seemed to make any sense, without success. It just won't launch and I need it. I have to reboot; boot into a Windoz disk and use it there - a pain - as I don't use Windoz but once in a blue moon. Please, if anyone has expertise or experience in this, let me know! Thanks in advance.

To my knowledge the correct and most recent files are installed. I have a 64-based system.

---

### Post by NilPointer on 2015-01-27
How exactly does it fail? Does it show some error? Have you tried to run it from terminal (it might spit error message there)? Not enough details to help.

---

### Post by Bucky Ball on 2015-01-27
Did you install it manually or install the version in the repos? Go the latter as that is fully supported and has the best chance of working.

---

### Post by crazybear on 2015-01-27
> **NilPointer said:**
> How exactly does it fail? Does it show some error? Have you tried to run it from terminal (it might spit error message there)? Not enough details to help.

It does stone dead NOTHING. It will not start - not even the tinyiest bit by launcher nor command line. I don't even know how to make it show an error message. It acts as if it is not there...but it is.

---

### Post by crazybear on 2015-01-27
> **Bucky Ball said:**
> Did you install it manually or install the version in the repos? Go the latter as that is fully supported and has the best chance of working.

As I mentioned [or hinted] I have tried everything over 40 times. Both would be the answer. I find nothing works - thus the post. The current 'installation' is via the repos [via Package Manager with proper settings, I believe]....but I get nothing. Not one thing. Again, I don't know how to test it in any way.

Currently installed are: skype 4.3.0.37-Oubuntu0.12.04.1 and skype-bin:i386 4.3.0.37-Oubuntu0.12.04.1

If I now type 'skype' into terminal, I get: 
[COLOR=#0000cd][SIZE=3]/bin/bash: n LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype: No such file or directory[/SIZE]

[/COLOR][COLOR=#800080]i DON'T KNOW WHAT THE FIRST PART INDICATES, BUT i WENT TO USR/BIN/SKYPE AND THERE IS NOT THE DIAMOND SHAPE EXECUTE FILE I'D EXPECT, BUT SOME OTHER KIND OF FILE I CAN'T OPEN OR READ, BUT IT IS NOT AN EXEC FILE FOR SURE.

Somewhere in the many hundreds of posts I've read of others travails over this [all others solving it somehow - me, never having ;-(] I remember someone once pointing out when removing all to start over one had to remove some file[s] hidden somewhere that don't get removed if you simply remove all 'skype' exec files....and I think long long ago, I even tried that...but now don't remember what that was nor where it is - I believe some skype configuration file, maybe.[/COLOR]

---

### Post by sudodus on 2015-01-27
It is the same version that works (from the repos without tweaks) in my Ubuntu 12.04.5 LTS (32-bit).

- Are you running the 64-bit version of 12.04.5 LTS?
- Is it an installed system or are you running Ubuntu live (booted from DVD or USB)?

- What happens when you try to start skype from a terminal window?

```
skype
```

Is something printed to the terminal window. Does it get stuck and unresponsive, or does it return to prompt?

---

### Post by crazybear on 2015-01-27
Additionally, I checked on libv4l-0:i386 and got:

libv4l-0:i386 is already the newest version.
libv4l-0:i386 set to manually installed.

---

### Post by crazybear on 2015-01-27
> **sudodus said:**
> It is the same version that works (from the repos without tweaks) in my Ubuntu 12.04.5 LTS (32-bit).

- Are you running the 64-bit version of 12.04.5 LTS?
- Is it an installed system or are you running Ubuntu live (booted from DVD or USB)?

- What happens when you try to start skype from a terminal window?

```
skype
```

Is something printed to the terminal window. Does it get stuck and unresponsive, or does it return to prompt?

All of the above questions I have already answered, but one: it is an installed system, up and running for several years and all else (of importance) working.

---

### Post by crazybear on 2015-01-27
Don't know what this means, but running apt-get update I got:

W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/source/Sources](http://download.skype.com/linux/repos/debian/dists/stable/non-free/source/Sources)  404  Not Found [IP: 92.122.213.234 80]

so, I unchecked it from source list....but where am I to get new versions?

---

### Post by Adam_GUI on 2015-01-27
Current version Skype (4.3.0.37-1_i386) can be gotten from Microsoft Here:
[http://www.skype.com/en/download-skype/skype-for-computer/]("http://www.skype.com/en/download-skype/skype-for-computer/")

There's a drop-down.  You'll want Ubuntu 12.04 (Multiarch).

From the sound of things, you'll want to purge Skype from whatever package manager you're using before 
attempting to install the new version.

---

### Post by crazybear on 2015-01-27
> **Adam_GUI said:**
> Current version Skype (4.3.0.37-1_i386) can be gotten from Microsoft Here:
[http://www.skype.com/en/download-skype/skype-for-computer/](http://www.skype.com/en/download-skype/skype-for-computer/)

There's a drop-down.  You'll want Ubuntu 12.04 (Multiarch).

From the sound of things, you'll want to purge Skype from whatever package manager you're using before 
attempting to install the new version.

I have done exactly this.....more than 20 times - perhaps twice that. I've tried all combinations and permutations I can think of and it never works [any more]....used to a year ago.
I think that maybe the 'purge' is never complete, as I mentioned above...but am not sure. what I am sure about is doing the purge and re-install like I have 20+ times before will not work, for sure.

---

### Post by crazybear on 2015-01-27
OK, just tried it....COMPLETELY deleted the two files mentioned above and installed the one suggested above..and as I said - it will not [and did not] work. One of you suggests I use via the channel, the other suggests I use the downloaded newer version...but neither works and trust me, I've tried this over and over and over...with all combinations and permutations. I get nothing working

And now, when I type skype into terminal I get the same reply as I did with the other configuration and other installation files

/bin/bash: n LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype: No such file or directory

Sorry, I sound frustrated...only sound that way, because I am. I think there is something unusual [not other people's normal problem with Skype] going on here...but I don't know what it is. I have periodically tried over a YEAR many times to fix this...then give up...now, I'm using skype a lot again and hate having to shut down Ubuntu and boot to another disk [Win-7] in order to get on skype. Help!....even if I hate skype because the NSA watches it all...but others don't wanna use the other alternatives.

---

### Post by Adam_GUI on 2015-01-27
Well, stab in the dark here, but, do you have the ia32-libs installed?

---

### Post by crazybear on 2015-01-27
Yeah, that was installed long, long ago. Again, for a long while Skype worked on this OS...then suddenly it stopped, and NEVER would start again. I don't know how to find what caused the change. Can anyone make head or tails of why there is no execution file for skype on my computer?! [I think]. At /usr/bin/skype there is a file - it is listed as a shared library of 34.2 MB last modified on May 22, 2014 - but I can assure everyone I didn't have Skype LONG before that date...that is likely some re-install effort. Stranger still, when I try to open it with gedit, it is blank!???! Something 34 MB can't be blank....is there another editor that would open it...or should I erase it or?! I really am at a loss.

---

### Post by sudodus on 2015-01-27
[https://help.ubuntu.com/community/Skype#Installing_Skype](https://help.ubuntu.com/community/Skype#Installing_Skype)

This link described what to do (it should be enough). The web page is fairly up to date, edited 2014-12-05. I have not tried skype in 64-bit systems, but the instructions ask you to enable multiarch

  [s]```
sudo dpkg --add-architecture i386
```[/s]

***Edit***: I tried it now in an Ubuntu 12.04 64-bit system. The command above did not work, but was not necessary. The file **multiarch** according to the following link was already there. You should check that you have it too, and with the correct content (according to the following link)

[http://askubuntu.com/questions/423083/cant-run-dpkg-add-architecture-i386-on-12-04-64-bit-to-run-eclipse-adt](http://askubuntu.com/questions/423083/cant-run-dpkg-add-architecture-i386-on-12-04-64-bit-to-run-eclipse-adt)

---

### Post by sudodus on 2015-01-27
So to make it clear. I installed skype according to the two links in my previous post, and it started to work without any problems. Now I should add that it is a very basic Ubuntu Unity 12.04.4 LTS system (a test system without extra packages installed). I can check if it works also after updating/upgrading to the current status (and 12.04.5) ... and yes, it works when every package is up to date :-)

If it does not work according to the links in post #15, I think you should make a fresh install of Ubuntu or maybe a second Ubuntu system (triple boot U1+U2+W). I think there is something in your installed system, that stops skype from working.

Maybe you know that you have something special installed, for example some PPA or some package that is installed manually from a deb package or maybe compiled from source code (instead of installed from the repositories).

---

### Post by crazybear on 2015-01-27
> **sudodus said:**
> [https://help.ubuntu.com/community/Skype#Installing_Skype](https://help.ubuntu.com/community/Skype#Installing_Skype)

This link described what to do (it should be enough). The web page is fairly up to date, edited 2014-12-05. I have not tried skype in 64-bit systems, but the instructions ask you to enable multiarch

  [s]```
sudo dpkg --add-architecture i386
```[/s]

***Edit***: I tried it now in an Ubuntu 12.04 64-bit system. The command above did not work, but was not necessary. The file **multiarch** according to the following link was already there. You should check that you have it too, and with the correct content (according to the following link)

[http://askubuntu.com/questions/423083/cant-run-dpkg-add-architecture-i386-on-12-04-64-bit-to-run-eclipse-adt](http://askubuntu.com/questions/423083/cant-run-dpkg-add-architecture-i386-on-12-04-64-bit-to-run-eclipse-adt)


Thanks, but no cigar on that one. I get the same response to typing in skype in terminal. I am NOT going to even begin to start to consider to contemplate a new install of my OS. I have a very complex system and it will stay as is - sorry. It also won't upgrade to 14.04, but that is another matter I don't want to get into here. I'll keep plugging away at fixing this or very reluctantly having to reboot to my Win-7 disk when I need to Skype [about all I use windows for now].  I'm sure I have multiarchitecture enabled in the entire OS. Yes, I have some very special programs that a wiz Linux geek installed on it for me and I'd not dare remove nor try to repeat. Sadly, they are not available anymore. I REALLY appreciate the suggestions. 

Anyone have any idea why I get that [to me] odd reply in terminal in response to  trying to run Skype? Strangely it never changes with the different configurations of skype installations I've tried.

---

### Post by 3246251196 on 2015-01-27
Can you not - in the mean time - run a virtual machine with your windoz on it so you do not have to reboot? Or does this not work for some reason ?

---

### Post by monkeybrain20122 on 2015-01-27
> If I now type 'skype' into terminal, I get: 
[COLOR=#0000cd][SIZE=3]/bin/bash: n LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype: No such file or directory[/SIZE][/COLOR]

Looks like you have applied some fixes or workarounds to trouble shoot your webcam before. Did you replace some files when you set up skype several years ago, like creating a bash script and have the skype.desktop link to it?

---

### Post by Bucky Ball on 2015-01-27
From this in one of your earlier posts:

```
W: Failed to fetch http://download.skype.com/linux/repo...source/Sources 404 Not Found [IP: 92.122.213.234 80]
```

You have manually installed Skype from a third-party repo. What I am saying is, and said in my first post, go to your Software and Updates>Other Software, and enable Canonical Partners, update, open Software Centre, and install Skype from there (the official repositories). 

Delete all other Skype(s) and the repos you've manually installed first to stop confusion.

---

### Post by crazybear on 2015-01-28
> **3246251196 said:**
> Can you not - in the mean time - run a virtual machine with your windoz on it so you do not have to reboot? Or does this not work for some reason ?

Hmmm....interesting idea. I've never tried making a VM, and not sure how to..but know instructions exist and I have the software installed. My second concern, after if I can effect that VM, is how much storage space on my Ubuntu disk that will take.

---

### Post by crazybear on 2015-01-28
> **monkeybrain20122 said:**
> Looks like you have applied some fixes or workarounds to trouble shoot your webcam before. Did you replace some files when you set up skype several years ago, like creating a bash script and have the skype.desktop link to it?

Not that I recall. I only remember in Skype assigning which microphone and which device was to be used for the webcam [but I have and had only one of each - which are actually in the same device]. I don't remember making any 'fancy' script nor asking a program to...but perhaps it happened without my being aware of it. 


On the Skype launcher now the command line reads:  env PULSE_LATENCY_MSEC=60 skype %U

---

### Post by crazybear on 2015-01-28
> **Bucky Ball said:**
> From this in one of your earlier posts:

```
W: Failed to fetch http://download.skype.com/linux/repo...source/Sources 404 Not Found [IP: 92.122.213.234 80]
```

You have manually installed Skype from a third-party repo. What I am saying is, and said in my first post, go to your Software and Updates>Other Software, and enable Canonical Partners, update, open Software Centre, and install Skype from there (the official repositories). 

Delete all other Skype(s) and the repos you've manually installed first to stop confusion.

I'm not sure I follow what I'm sure you think it intuitively obvious. Other Software, Canonical Partners has always been checked. I assume that apt-get install skype would be what you mean for 'install Skype from there'. I have tried this and never got a positive result. I have also tried installing the newer package on the Skype site with gdebi. Both have been suggested to me as the best alternative. ;-) 

I'll check which ppa's now are checked for Skype and report. I agree, it seems logical to only have one at any given time.
Checked are: launchpad.net/skype-wrapper/ppa/ubuntu precise (2) - I see no other Skype-related items checked or listed [OK or not OK?, in your opinion]
I don't think it matters, but I have Ubuntu 12.04.5 and I had a big struggle installing the latest AMD drivers for my video card; but think I recall that was all after loosing ability to use Skype.

---

### Post by crazybear on 2015-01-28
What to me [and I am NO expert on Linux/Ubuntu!] seems strange is this part of the response when I type Skype into terminal:  [SIZE=3][COLOR=#0000cd]/usr/bin/skype: No such file or directory
[/COLOR][SIZE=2][COLOR=#800080]However, when I run apt-get install skype, I get:   [/COLOR][/SIZE][COLOR=#0000cd]skype is already the newest version.0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

To, me, these two seem at odds.....but what do I know. I suppose, as mentioned earlier, some thing [oh, my OS has SO MANY 'somethings' installed!] could be blocking Skype opening, but would it make the execution file not be 'there'?...when it is thought to be 'there' (somewhere?) by the system.....I think.

Now, I had the 'bright' idea to search for all files in OS named 'skype'. There are many, I think most are unimportant. these three screen shots may include important ones or give someone a hint of the problem. Would any of these be 'amenable' to being edited and changed - or looked at?!  [/COLOR][/SIZE][ATTACH=CONFIG]259556[/ATTACH][ATTACH=CONFIG]259555[/ATTACH][ATTACH=CONFIG]259554[/ATTACH][SIZE=3][COLOR=#0000cd]

[/COLOR][/SIZE]

---

### Post by mastablasta on 2015-01-28
> **crazybear said:**
> 
Checked are: launchpad.net/skype-wrapper/ppa/ubuntu precise (2) - I see no other Skype-related items checked or listed [OK or not OK?, in your opinion]

not OK. if means that when you apt-get install you are actually installing from the PPA not official repos.

> 
I don't think it matters, but I have Ubuntu 12.04.5 and I had a big struggle installing the latest AMD drivers for my video card; but think I recall that was all after loosing ability to use Skype.
what is the card? use opensource drivers instead. use newer kernel if necessary (see hardware enablement) or PPA.

---

### Post by crazybear on 2015-01-28
> **mastablasta said:**
> not OK. if means that when you apt-get install you are actually installing from the PPA not official repos.


what is the card? use opensource drivers instead. use newer kernel if necessary (see hardware enablement) or PPA.

Removed check marks on those two PPA's. Would I have to remove and re-install? How much  to remove - the two or more than the two?
Problem is I removed 'Skype' and then re-installed skype; but nothing changed...and I got the exact same strange response in terminal........

I don't think the video driver is the issue; Skype was not working before that battle. Others indicated the AMD driver would be best. [so, who to believe?] It is a MSI Radeon HD-7970 [bit older, high-end, I bought not long ago hardly used]
I think I always get the latest kernels.

---

### Post by crazybear on 2015-01-29
One thing I didn't mention, I don't think if relevant, but may be, is that I do NOT use UNITY desktop - I use Gnome classic -but Skype was working in that environment until it stopped.
I don't know how I'd eliminate ALL skype files...I believe there are 180+ various ones [most not important] and start over. Most do NOT get deleted when I 'remove' the two main files by terminal or Synaptic.

---

### Post by Ashley_Bailey on 2015-01-29
Have you checked into these system requirements [http://www.skype.com/en/download-skype/skype-for-linux/](http://www.skype.com/en/download-skype/skype-for-linux/) and tried again?

---

### Post by mastablasta on 2015-01-29
yeah you need to purge them and remove them compeltelly. then start fresh. Gnome classic doesn't matter. AMD drivers are better. 

Sometimes the preload command can work. Also I found good advice on Skype Linux forums. it takes some time to get a response but eventually it will come. also I have Skype on Linux PC's and all use AMD cards so I doubt the card is the issue. but then again they are not the same model cards as yours.

---

### Post by crazybear on 2015-01-29
> **mastablasta said:**
> yeah you need to purge them and remove them compeltelly. then start fresh. Gnome classic doesn't matter. AMD drivers are better. 

Sometimes the preload command can work. Also I found good advice on Skype Linux forums. it takes some time to get a response but eventually it will come. also I have Skype on Linux PC's and all use AMD cards so I doubt the card is the issue. but then again they are not the same model cards as yours.

I don't know how to completely purge all 180+ skype-related files.
Again, the video card is not the issue, I'm sure. The old one was AMD and the new one is as well. Long before I put in the new one and the newer driver, I lost Skype.

---

### Post by crazybear on 2015-01-29
> **Ashley_Bailey said:**
> Have you checked into these system requirements [http://www.skype.com/en/download-skype/skype-for-linux/](http://www.skype.com/en/download-skype/skype-for-linux/) and tried again?

I have all of those system requirements.

---

### Post by crazybear on 2015-01-31
I still do not have Skype! I do not know how to delete every file [well over 200] generated at various times that contain word 'skype' in them - to try installing without them.

---

### Post by sudodus on 2015-01-31
Have you got a good and current ***backup***?

In that case you can try a potentially ***dangerous*** command.

1. This command will list interactive remove commands for all files that contain the string 'skype' and 'Skype' in the file name

```
sudo find / -iname "*skype*" -exec echo rm -i {} \;
```

2. This command will ***run*** interactive remove commands for all files

```
sudo find / -iname "*skype*" -exec rm -i {} \;
```

3. Much faster but also more risky (copy and paste it to avoid typing errors). This will remove all those files at once
  
```
sudo find / -iname "*skype*" -exec rm {} \;
```

-o-

*But *

1. there might be files that belong to skype, but do not contain skype in the name,

2. there might be files that contain skype in the name, but belong to some other software,

3. there might be directories with several files, that belong to skype, and directories are not removed by these commands. But you will 'see' those with skype in the name and can treat them manually,

so this method may or may not work and it is ***risky***.

---

### Post by crazybear on 2015-01-31
> **Ashley_Bailey said:**
> Have you checked into these system requirements [http://www.skype.com/en/download-skype/skype-for-linux/](http://www.skype.com/en/download-skype/skype-for-linux/) and tried again?

Yes, and SKYPE USED TO RUN and I've not changed the system, but thanks.

---

### Post by crazybear on 2015-01-31
> **sudodus said:**
> Have you got a good and current ***backup***?

In that case you can try a potentially ***dangerous*** command.

1. This command will list interactive remove commands for all files that contain the string 'skype' and 'Skype' in the file name

```
sudo find / -iname "*skype*" -exec echo rm -i {} \;
```

2. This command will ***run*** interactive remove commands for all files

```
sudo find / -iname "*skype*" -exec rm -i {} \;
```

3. Much faster but also more risky (copy and paste it to avoid typing errors). This will remove all those files at once
  
```
sudo find / -iname "*skype*" -exec rm {} \;
```

-o-

*But *

1. there might be files that belong to skype, but do not contain skype in the name,

2. there might be files that contain skype in the name, but belong to some other software,

3. there might be directories with several files, that belong to skype, and directories are not removed by these commands. But you will 'see' those with skype in the name and can treat them manually,

so this method may or may not work and it is ***risky***.

No, that's WAY to risky for me. Won't go there! I know there are files of the types you mention: with and without skype in the name that are/aren't part of skype. Most of these, even to a novice like me, harmless and I'm sure not part of the problem, but I don't know which might be - and perhaps none are - but some other installed program along the line is blocking skype or causing it to be configured incorrectly. I don't know. I know I'm tired of having to close all down and reboot to another disk, then back again. But thanks.

---

### Post by crazybear on 2015-10-05
Just wanted to say that in all these months I have NOT found ANY way to use Skype on 12.04.5 It simply no longer works. It once did. Now not and I can't find a solution.

---

### Post by crazybear on 2015-11-15
> **crazybear said:**
> Just wanted to say that in all these months I have NOT found ANY way to use Skype on 12.04.5 It simply no longer works. It once did. Now not and I can't find a solution.

Hello all. I just revisited this entire thread. I tried everything mentioned that made sense to me again and tried to completely uninstall purge skype and re-install...and...NOTHING. It is now going on two years since skype worked on this system. I'm at wits end. Something in my system is preventing skype from starting and I don't know what or know how to find out what. I really need to be able to have skype work! [unless there is a similar program that would work]. Very frustrated....but thanks for the help and any possible future suggestions. No other programs fail to work or when they didn't work weren't 'fixable' - except Skype. It has been by a factor of 100x the most problematic program ever!

---

### Post by crazybear on 2015-11-15
when I try to launch Skype, I get this reply in terminal:

$ skype
/bin/bash: n LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype: No such file or directory

....but there is a 34.2 MB shared library at /usr/bin/skype

So, what is going on?!

---

### Post by crazybear on 2015-11-15
I'm beginning to think it has to do with two files that list the preload [apparently for the webcam]. Webcam is working on other programs and in other operating systems. Very confusing, as I see over 20 various suggestions as to what the lines should say, with NO explanation of why this one over the others. Lots of people saying 'it worked for me'....but none have worked for ME. 

Here is another variant of the MANY: [COLOR=#333333][FONT=sans-serif]LD_PRELOAD=/opt/lib32/usr/lib/libv4l/v4l1compat.so skype

Anyone know how to navigate this minefield of preload variations?[/FONT][/COLOR]

---

### Post by Bucky Ball on 2015-11-16
Does your webcam work with other apps, like Cheese for instance?

If your cam's not working with anything, might not have much to do with Skype per se, it might be that Skype is hitting the cam and objecting when you launch it. Check if other apps are doing the same and this is actually an issue with the webcam.

My only other suggestion would be to try in a newer release, but if it's hardware related, probably won't make any difference. Tried another camera? Tried launching Skype with the webcam unplugged? Booting the machine with the webcam unplugged then Skype?

Tried booting the machine with the webcam unplugged, plugging it in, issueing 'dmesg' in a terminal and check the output at the end referring to the cam and seeing if it is throwing an error or loading the drivers appropriately?

---

### Post by crazybear on 2015-11-16
> **Bucky Ball said:**
> Does your webcam work with other apps, like Cheese for instance?

If your cam's not working with anything, might not have much to do with Skype per se, it might be that Skype is hitting the cam and objecting when you launch it. Check if other apps are doing the same and this is actually an issue with the webcam.

My only other suggestion would be to try in a newer release, but if it's hardware related, probably won't make any difference. Tried another camera? Tried launching Skype with the webcam unplugged? Booting the machine with the webcam unplugged then Skype?

Tried booting the machine with the webcam unplugged, plugging it in, issuing 'dmesg' in a terminal and check the output at the end referring to the cam and seeing if it is throwing an error or loading the drivers appropriately?

Yes, my very good webcam works with Cheese etc. Also, as stated above this computer with this webcam USED to work with Skype. I don't know what changed it..but is was sudden and complete with some new program added or an update of something.....
I have the newest Skype release at the moment. Some suggest not using the latest - other do...I don't know. the PPA and repositories have slightly older ones usually.
I don't have another camera on hand to try, but will try loading without the webcam...but won't those lines for preload still then issue an error message?
Will report back after my attempts. What is so confusing it the literally 20+ formulations of different preload messages that 'worked for others'...but NO ONE even giving the basics of the logic of why one would work and the other not for a particular OS, webcam, skype version, et al....other than a very clear explanation of what to do if 64-bit and 32-bit. All skype programs are 32 bit and my computer is 64 bit...so I think that part I have correct; obviously something else is amiss......

---

### Post by Bucky Ball on 2015-11-16
I've only ever used Skype from the repos. I'd imagine this would cut out some variables as the one in the repos is known to work with your version of Ubuntu (if not necessarily with the way you have it configured or the hardware). That's about all I can add. Hope you find a fix for this ongoing issue eventually.

---

### Post by crazybear on 2015-11-16
Well, aside from not being sure how to make sure I'm getting it from the repos vs. ppa vs. synaptic [which takes it from?], I believe I've tried all variants, plus direct download and install from skype.
Remember, that I had it installed and working and I made NO change in skype when it stopped working - something else interfered with it and is still...what that working version was installed from I now do not remember. I'd guess I just did an apt-get install skype....but truly can't remember. 

I tried unplugging the webcam - but that made no difference. It gives me a preload error message that is strange, as I've removed those lines from the two files I'm aware of...but when I search for all files with skype in the name, there are about 50+ and many many remain even with a remove purge command. I've seen people on the internet who successfully installed from all the various places and packages - me not.

I believe I have once again purged all of skype and reinstalled using repos....same no reaction. It must have something to do with specific preload lines on unknown files. My guess.

---

### Post by Bucky Ball on 2015-11-16
Guess it would help to try and remember what you did prior to it starting to happen. Install something? An update? Upgrade hardware? Plug something in?

---

### Post by crazybear on 2015-11-16
> **Bucky Ball said:**
> Guess it would help to try and remember what you did prior to it starting to happen. Install something? An update? Upgrade hardware? Plug something in?

It isn't going to happen. First it now was two years ago....but I did nothing unusual. I have a lot of programs installed and almost every other day there are updates that I install. I don't use skype that much to have noticed the day something was installed that changed things anyway. There was a time I notices that skype was not working [it had stopped a few times before, but I was always able to reinstall or uninstall and then reinstall and get it to work again. This time and since - not. Luckily, I have another OS that I don't use, that has skype on it and is working - but I use the 12.04 most of the time [99%] and it is really a lot of trouble to shut down the computer and reboot to the other OS just to use skype and then come back and try to pick up where I was before, as I have three monitors and multiple desktops and a complex set up and really need it to  be stable and not have to close down and go to another little used OS.

It is unlikely it was new hardware, as there really hasn't been any that changed at that time.
Updates, as I say happen every day or every other day and I use skype about once every other week on average....so a week or two or three's updates could have happened and I didn't note it anyway - as I thought it was just another time when I could get it working with a bit of fussing about. This was not to be the case. 

I may have or may not have installed another program that is causing the problem - again no way to know or ever reconstruct at this point. The error messages have remained the same or almost the same and have to do with the preload file not existing, when I see it existing....but perhaps that means it is not the right preload working/structure. I don't know.

---

### Post by LukeMorrison on 2015-11-16
Have you tried creating a new Ubuntu user to determine if it is a systemwide issue or if it is only affecting your main user?

---

### Post by crazybear on 2015-11-17
> **LukeMorrison said:**
> Have you tried creating a new Ubuntu user to determine if it is a systemwide issue or if it is only affecting your main user?

Thanks, but I could send a skype to you on the working operating system - not on the one I'm trying to fix. I can NOT get skype to do ANYTHING. It won't start up with  or without a webcam.

No haven't tried 'new user', will try that, but if it works there, that doesn't tell me how to fix things. I have many many programs - too many to try removing and reinstalling one at a time.

I'm now looking at this and related...damn this can get complex!  [https://journalxtra.com/linux/skype-video-linux-always-hassle/](https://journalxtra.com/linux/skype-video-linux-always-hassle/)

---

### Post by crazybear on 2015-11-17
Well, Well, well....that page referenced about was the answer and Skype is not working. Anyone with similar problems should wade through this page [https://journalxtra.com/linux/skype-...always-hassle/]("https://journalxtra.com/linux/skype-video-linux-always-hassle/")  !!!!!

---

### Post by Bucky Ball on 2015-11-17
Do you mean Skype is now working?

---

### Post by crazybear on 2015-11-17
> **Bucky Ball said:**
> Do you mean Skype is now working?

yes,   now working normally. That page I referenced, for me, was the answer...after looking at hundreds of others that led nowhere for me. It is strange that is was apparently some preload lines related to the webcam - yet this is the same webcam I've always had. Anyway, that url really helped fix it in short order...I've spent perhaps 50 hours on this and had all but given up.

---

### Post by Bucky Ball on 2015-11-17
Thanks for verifying. Enjoy. :)

---

