---
title: "I can't make work AVG antivirus"
date: 2013-08-09
forum: General Help
---

### Post by viriatovigo on 2013-08-09
After following the instructions to download AVG from                          [COLOR=#000080]_[[COLOR=#000000][FONT=monospace]www.techienote.com/2012/10/how-to-install-avg-free-antivirus-software-on-ubuntu-12-10-12-04.html[/FONT][/COLOR]]("http://www.techienote.com/2012/10/how-to-install-avg-free-antivirus-software-on-ubuntu-12-10-12-04.html")_[/COLOR]  , then keeping within its advice, I did proceed to 

      [FONT=monospace]   sudo dpkg -i avg2012flx-r1795-a5274.i386.deb[/FONT]  [FONT=monospace]

with the result of:[/FONT]

          dpkg: error processing avg2012flx-r1795-a5274.i386.deb (--install):

      cannot access archive: No such file or directory

      Errors were encountered while processing:

      avg2012flx-r1795-a5274.i386.deb


So I did click in the download and did managed to install it, but when I did try to start a scan on the terminal...

      sudo avgscan ~  

the result was:

          AVG command line Anti-Virus scanner

     Copyright (c) 2013 AVG Technologies CZ

     Virus database version: 3209/6565

    Virus database release date: Fri, 09 Aug 2013 18:20:00 +0100

     [~100.0%] /home/tino//home/tino/  Object scan failed; Permission denied 

        Files scanned     :  0(0) 

          Infections found  :  0(0)

     PUPs found        :  0

     Files healed      :  0

     Warnings reported :  0

     Errors reported   :  1


[SIZE=2]**What on Earth I am doing wrong this time??????**[/SIZE]

---

### Post by Mark Phelps on 2013-08-09
Why are you even bothering with this? As far as I know, AVG is a Windows antivirus product, not Linux.  If you are installing it in Linux to run it against Windows on the same PC, there are better solutions than what you are attempting.

---

### Post by RadicaX on 2013-08-09
you scanned your home folder looking at the command. try this.

sudo avgscan /Downloads

When you did the ~ that just means scan home folder, but I think there is a input to scan all of it. like -r or something. The permission denied was just because you were not super user it looks like. 

So do that and copy and paste results please.

---

### Post by 3rdalbum on 2013-08-10
> **RadicaX said:**
> you scanned your home folder looking at the command. try this.

sudo avgscan /Downloads

When you did the ~ that just means scan home folder, but I think there is a input to scan all of it. like -r or something. The permission denied was just because you were not super user it looks like. 

So do that and copy and paste results please.

You're close, but not quite right. Have a look at the error message again, and have a look at the command you suggested and think about exactly what directory you've specified.

AVG is saying "I can't find the directory /home/tino//home/tino". There is, of course, no such directory. The reason it's trying to look for this directory is because you've specified for it to search "~", and AVG assumes that because that path doesn't start with a slash, it must be something inside your home folder.

Long story short, if you just put "sudo avgscan" it should search your home directory.

The reason why your command-line attempt at installing the software didn't work is because your terminal wasn't inside the same directory as the Deb file. 

Scanning your Linux home directory for viruses is a bit like getting a dentist to look at your feet. There are no Linux viruses in the wild at the moment, and there haven't been for a number of years. AVG will only look for old Linux viruses (which you will not have - they are as extinct as the wooly mammoth) and Windows viruses, which won't infect Linux anyway.

It's been commonly said that the best use for Linux antivirus is to stop yourself from inadvertantly downloading a file infected with a Windows virus, and then passing that file onto a Windows user, but viruses these days do not infect the kinds of files you would share with anyone. Viruses only infect system files, and what's the liklihood you'll have any Windows system files sitting in your home directory? Practically nil.

You can safely remove the anti-virus software, it's totally unnecessary.

---

### Post by Rebelli0us on 2013-08-10
AVG linux will scan both ext4 and NTFS partitions.  Mine worked fine at first, but now It often crashes when scanning inside the linux file system but will find Windows virus in other partitions.

---

### Post by viriatovigo on 2013-08-10
Thank you to every one.

So I'll keep going with ClamTk that doesn't work at all until there is a proper anti virus for Linux. Most of the files that say are trouble (like Adobe Reader...) can not be sent to quarantine or deleted (ClamTk doesn't allow to do it). Other files can be quarantined but it never says if the problem as been resolved as other anti viruses do. In the other hand, in the end, says that I have not threats, but if I back up the full system and I do scan it with Panda Anti virus in a my laptop with Mac or any PC with Windows, it says that there is a trojan and that Panda did took rid of it. Right... (3rdalbum: " Windows viruses, which won't infect Linux anyway" - So trojans are only for Windows??? Then, How got into my Ubuntu Linux? I have nothing that smells Microsoft at all in my PC nor in my laptop where I am using AppelMac).

I've been with Panda for about 20 years with no problems at all but, unfortunately, Panda have not version for Linux and they told me that they have not intention to do so in a foreseeable future just because there is not market enough.

Mark Phelps: AVG **it is** **not** a Micrososfot product but a product **for** Windows, Linux and AppleMac: [http://en.wikipedia.org/wiki/AVG_%28software%29](http://en.wikipedia.org/wiki/AVG_%28software%29)

3rdalbum: " Long story short, if you just put "sudo avgscan" it should search your home directory" - It is what I did if you check my post...

RadicaX: "The permission denied was just because you were not super user it looks like" - Since when? I've been always writing the commands starting with "sudo" (as can be seen in my post) and -until now- always seem that I was a super user, Why not in a sudden? 

I'll keep trying Linux until becomes a user friendly system, but for business I'll keep using AppleMac by now. In business things need to be done yesterday, I have not time for writing a copy of the  Peace and War book in the terminal each time that I get a problem while a customer is waiting. Never mind to explain to my staff about to keep writing in the terminal mostly 3 times per day, they have a job to do most of the times within a pretty tight deadline.

All the best.

Tino

---

### Post by RadicaX on 2013-08-10
> **3rdalbum said:**
> You're close, but not quite right. Have a look at the error message again, and have a look at the command you suggested and think about exactly what directory you've specified.

AVG is saying "I can't find the directory /home/tino//home/tino". There is, of course, no such directory. The reason it's trying to look for this directory is because you've specified for it to search "~", and AVG assumes that because that path doesn't start with a slash, it must be something inside your home folder.

Long story short, if you just put "sudo avgscan" it should search your home directory.

The reason why your command-line attempt at installing the software didn't work is because your terminal wasn't inside the same directory as the Deb file. 

Scanning your Linux home directory for viruses is a bit like getting a dentist to look at your feet. There are no Linux viruses in the wild at the moment, and there haven't been for a number of years. AVG will only look for old Linux viruses (which you will not have - they are as extinct as the wooly mammoth) and Windows viruses, which won't infect Linux anyway.

It's been commonly said that the best use for Linux antivirus is to stop yourself from inadvertantly downloading a file infected with a Windows virus, and then passing that file onto a Windows user, but viruses these days do not infect the kinds of files you would share with anyone. Viruses only infect system files, and what's the liklihood you'll have any Windows system files sitting in your home directory? Practically nil.

You can safely remove the anti-virus software, it's totally unnecessary.

Thank you, Am going to take note of that for next time, I had figured it was something like that, but I went about it wrong haha. 

Viral, the quote explains what happen there, that was my mistake, sorry about that. Now if your anti-virus is pulling up results, it could be something called false positives, especially if it is getting adobe reader. Lastly, just because they say it is for Linux, does not mean it is useful to Linux. Firewalls are more important in the Linux world. 

Next, when he told you to use sudo avgscan, you had a slightly different. You did it sudo avgscan ~ which is different than sudo avgscan.

I have found Ubuntu to be pretty user-friendly, but you have to practice it and learn the ropes a bit. Anyway, glad you are not giving up on it, keep at it and you will learn it more, and sooner or later most likely just switch to it.

---

### Post by viriatovigo on 2013-08-10
Ta RadicaX.

Of course! You bet! Just because I have not time (and not patience...) due to business commitments doesn't mean that I am going to give up. Not the son of my father.

I believe that Linux OS is the safest for a business environment, but still has a long way to go to catch up with the easy, fast and friendly -and professional- way in which Apple works.

Anyway... time to time... We'll get there sooner or later.

By the way... Just 4 hours ago Panda detected** again** the trojan AdInjector.B in the Ubuntu back up and I infer that went trough the Skype connection (that **yes**, Mark Phelps, Skype **belongs** to Microsoft since April last year). 

So, sorry 3rdalbum*,* but your "You can safely remove the anti-virus software, it's totally unnecessary" must be a joke. Linux gets viruses as anyone else. And hackers as the Forum well knows. I don't know what makes you believe that Linux is safer that the CIA and FBI's systems when they've been broken into more than once lately. And the MI5 in this side of the pond too...

All the best.

Tino

---

### Post by Hylas de Niall on 2013-08-10
> **viriatovigo said:**
> Ta RadicaX.
So, sorry 3rdalbum*,* but your "You can safely remove the anti-virus software, it's totally unnecessary" must be a joke. Linux gets viruses as anyone else. And hackers as the Forum well knows. I don't know what makes you believe that Linux is safer that the CIA and FBI's systems when they've been broken into more than once lately. And the MI5 in this side of the pond too...

All the best.

Tino

Forum hacks and OS viruses are completely different things, and you might profit from taking on board the advice of seasoned linux users instead of worrying that your linux system has been compromised by softwares that target microsoft software.

Just my 2p worth.

---

### Post by ant2 on 2013-08-10
Of course a lot of 'hacking' relies on social engineering and there isn't any software developed to protect from that.

---

### Post by RadicaX on 2013-08-10
> **ant2 said:**
> Of course a lot of 'hacking' relies on social engineering and there isn't any software developed to protect from that.

And that my friend is the most truth in hacking there is. What is beyond me, is that the FBI and CIA have there important stuff more than once on the internet, or banks go on the internet. I understand ease of use, and making things easier, but when do we draw the line? When do we put Security over ease of use? I do not like the thought that one super hacker can go about and shut off whole cities power sources and stuff, or take control of dogs, and do not care to see a world much like the one in the game WatchDogs, which we seem to already be in. Do we really need to have our fridge online? And this does not even touch into privacy, uhg, that is a whole other can of worms. How much more secure would Windows be, if they gave up some of their user friendliness? And I say give up, but how about focus on it?

Just a bit of food for thought. I hear if you use a computer CLI straight, you right then and there knock a lot of vulnerabilities out, due to not having a GUI. The more programs you have, and the more you opt for laziness over safety, the more likely you are to be hacked, period. 

Anyway, Tino, have you thought to try some other anti-virus too? Maybe one with a GUI like ClamTK? And maybe if you change the DE for your Ubuntu, or try another Ubuntu, like Kubuntu, or Xubuntu, maybe it will be a bit more friendly to use? If you are keeping at it, regardless, you will get better at it. 

Anti-viruses here, just tend to look for Windows Viruses, (which seems to be what your thing is finding then.) Which do not hurt us, it can hurt other windows users. But with how fast things are changing on Linux, it makes it pretty safe, if a virus comes out for it, patches are released super quick and tend to be useless after that. More importantly, you should look into setting up a firewall, do things to prevent them in the first place. 

I would delete the virus then if you found it, it does not hurt you, but hey, you could infect someone else.

Anyway, hope it gets more to your liking sooner or later.

---

### Post by 3rdalbum on 2013-08-10
1. Linux doesn't understand Windows code. Rven if it did, Windows programs dont understand the functions available on Linux or how to do anything on Linux. Linux doesn't run Windows programs. No Windows virus can infect your Linux system. AdInjector is definitely a Windows virus.

It's possible you have been e-mailed this virus or you have downloaded this virus, but it has definitely not infected your system. Viruses aren't magical or alive, they are just malicious programs and don't have the capacity to figure out how to run on a totally alien platform.

2. "Threats" is different to "viruses". Most anti-virus software will flag tracking cookies as "threats". I once saw it flag Adobe Dreamweaver as a "threat" because it comes with a JavaScript template that could potentially be a little bit annoying if you put it in a web page and misused it.

My point is, those "threats" were not only harmless but they were MEANT to be on my system. You have to do some research to determine if it's a false positive. Of course you can't "quarantine " a tracking cookie.

3. Linux seems hard at first, but only because it is so different to any other operating system. It's actually really easy to use once you know a little bit. Your terminal use is probably unnecessary, I rarely use the terminal for anything that can't be done in the GUI.

My father is in his sixties. He has used Linux since 2009 and prefers it to even OS X, which he uses at his workplace. He's no hardcore computer expert, he was just willing to learn.

4. You can probably safely assume that people who have been posting here for nearly eight years are probably going to give you fairly decent information :-)

---

### Post by viriatovigo on 2013-08-11
Thank you every one.

I'll take notice of all your comments and I'll look at them with calm and I'll try to be more patient, what is easy to say than to do for a typical Mediterranean old bloke.

I've never been too clever on spite of that I have started on computers on 1973 with an IBM 3060 30, but I am too old to get up to date with this. It is a challenge for me to keep up to day what is good to keep my brain moving,  but that's all. Specially after a stroke while driving 6 years ago that let my "pot" practically out of service for awhile. And that I am 65...

Anyway, thank you to everybody and sorry to bother you with all my crap. Long time ago I did start with RedHat and, at that time, was already too much for me and I gave up but still I have the book and the CD.

All the best.

Tino

---

### Post by RadicaX on 2013-08-11
Do not let it worry you, feel free to ask questions and such. And do not mind to much how people reply, just take note of it, because it can be and is often useful.

---

