---
title: "[SOLVED] How do I get rid of Ubuntu and reinstall Windows XP?"
date: 2008-03-19
forum: General Help
---

### Post by north-east-angler on 2008-03-19
Hello everyone, i am a noob at computers and ive had nothing but bother with this. i dont like ubuntu no offence to the makers and nor do i like the person that installed it, i have a e-system notebook celeron m (i use it to do coursework)


1. the dude whoinstalled it didnt make a back up copy of Windows XP And he did a complete partition (?)
2. I cant play music,or open frostwire i have tried to use the guides here to no prevail
3. I WANT MY XP BACK AND CANT.

Any ideas

Will i just smash my computer up and get a new one with the garuntee i got.

OR AM I STUCK WITH THIS FOREVER:(

Thanks for your understanding, 
Andrew.

---

### Post by heartburnkid on 2008-03-19
OK, step one, keep your cool.  It's OK.  We can help.

As far as going back to XP goes, unless you have your original install disc, you're probably boned.  Sorry to say it.

What make and model # of notebook do you have?  What happens when you try to play your music files?  Please give as much information as you can, and the folks here will help you as much as they can.  They're good people.  I'm still very noobish myself, but I'll do what I can to help as well.  Since it seems you're stuck with Ubuntu for now, let's see what we can do to get it working for you.

Who knows?  You might even come to like it once we get the kinks out.

---

### Post by Shazaam on 2008-03-19
A few questions first.......
1. Do you have a retail (store bought) disk of Win XP?
2. Do you feel up to a bit of calm troubleshooting?
3. Is the pc still under warranty?

---

### Post by tgalati4 on 2008-03-19
What happened to the original Windows XP installation?  Your computer should have come with a restore disk.

---

### Post by phil90 on 2008-03-19
Well I don't understand why you cannot reinstall Windows. Just put the CD in and lets go install it.


Your problems dont' see to be anyhinh that cannot easily be solved and are most likely user issues.

Would need to know more tought

Did you install the required Codecs to play your music ?
How did you install Frostwire? Do you have Java? last time I checked it does require Java

---

### Post by north-east-angler on 2008-03-19
HI Shazaam,

1. Yes its a retail version. I baught it at PC world. it came already setup. i got 2 discs. Microsoft works  and notebook supporting utility i didnt see anything with Windows XP on
2. Yes by thesounds ofit imstuckwith this.
3. Yes life time warranty

---

### Post by kaurman on 2008-03-19
Hi,

If you are interested in playing mp3 files, this is easy:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

There are also plenty of filesharing clients available for ubuntu. (including Frostwire)

Maybe you should still give ubuntu a try.

---

### Post by phil90 on 2008-03-19
> **north-east-angler said:**
> HI Shazaam,

1. Yes its a retail version. I baught it at PC world. it came already setup. i got 2 discs. Microsoft works  and notebook supporting utility i didnt see anything with Windows XP on
2. Yes by thesounds ofit imstuckwith this.
3. Yes life time warranty

What you have a lifetime warranty on your computer???

I will buy computer there if  it is any good

You support utility might be the Windows. Last time I bought a computer I think cd where I had windows on was called Applications recovery

---

### Post by north-east-angler on 2008-03-19
> **kaurman said:**
> Hi,

If you are interested in playing mp3 files, this is easy:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

There are also plenty of filesharing clients available for ubuntu. (including Frostwire)

Maybe you should still give ubuntu a try.

Hi,

I'm morethan willing to give it a try, but as far as ive seen it involves alot of use with "Terminal" it also wont install.EXE files

---

### Post by north-east-angler on 2008-03-19
Currently getting thismessage when trying to open synaptic

E:DPKG WAS INTERUPTEDYOU MUSTMANUALLY RUN DPKG CONFIGURE A to correct the problem

---

### Post by aysiu on 2008-03-19
> **north-east-angler said:**
> Hi,

I'm morethan willing to give it a try, but as far as ive seen it involves alot of use with "Terminal" it also wont install.EXE files
It doesn't really involve the terminal if you don't want it to:
[http://www.psychocats.net/ubuntu/nonfree](http://www.psychocats.net/ubuntu/nonfree)

And Windows won't install .deb files, so why would you expect Ubuntu to install .exe files?

By the way, Microsoft has some instructions for you on removing Linux and reinstalling XP:
[http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458)

---

### Post by Shazaam on 2008-03-19
Never mind, I'm not fast enough. :)

---

### Post by north-east-angler on 2008-03-19
> **phil90 said:**
> What you have a lifetime warranty on your computer???

I will buy computer there if  it is any good

You support utility might be the Windows. Last time I bought a computer I think cd where I had windows on was called Applications recovery

when i put the disk in it wont run the autorun or the installbecause of .EXE

---

### Post by phil90 on 2008-03-19
> **north-east-angler said:**
> Currently getting thismessage when trying to open synaptic

E:DPKG WAS INTERUPTEDYOU MUSTMANUALLY RUN DPKG CONFIGURE A to correct the problem

Click on applications - accessories - terminal

and then type the command it tells you to use.

sudo dpkg --configure -a 

and then 

sudo apt-get update

---

### Post by aysiu on 2008-03-19
> **phil90 said:**
> Click on applications - accessories - terminal

and then type the command it tells you to use.

sudo dpkg --configure -a Better yet--instead of typing the command, copy and paste it with your mouse: ```
sudo dpkg --configure -a
```

---

### Post by kaurman on 2008-03-19
I am not sure but I think that you should be able to boot from the recovery disk.
That means that you must leave the disk in the drive and restart the machine.

If that doesn't work, then note that the cd drive must be read before the HD with ubuntu. That can be set in BIOS.

---

### Post by north-east-angler on 2008-03-19
> **phil90 said:**
> Click on applications - accessories - terminal

and then type the command it tells you to use.

sudo dpkg --configure -a 

and then 

sudo apt-get update

:confused::cry:


andrew@andrew-laptop:~$ sudo dpkg --configure -a
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

---

### Post by phil90 on 2008-03-19
> **north-east-angler said:**
> Currently getting thismessage when trying to open synaptic

E:DPKG WAS INTERUPTEDYOU MUSTMANUALLY RUN DPKG CONFIGURE A to correct the problem

> **north-east-angler said:**
> when i put the disk in it wont run the autorun or the installbecause of .EXE


Ok I just want to make sure of something do we continue with Ubuntu or do you want to install Windows.

If  the cd is windows then just restart your computer and leave the cd inside the drive and it will boot into the windows installation program. As long as your system boot the CD at start up but if it does not you need to go to change it.
To do it you need to read on your screen when it starts you usually need to press something like DEL , F8 , or something like that then when you are in the BIos you change the boot order and put you cd drive to boot before the drive and you save and restard and if It is a Windows CD it will boot into the installer.

You can also open the Cd to see what file it contains from Ubuntu to make sure it is a Windows CD

---

### Post by aysiu on 2008-03-19
Here's a screenshot tutorial on setting your BIOS to boot from CD:
[http://www.hiren.info/pages/bios-boot-cdrom](http://www.hiren.info/pages/bios-boot-cdrom)

---

### Post by north-east-angler on 2008-03-19
> **phil90 said:**
> Ok I just want to make sure of something do we continue with Ubuntu or do you want to install Windows.

If  the cd is windows then just restart your computer and leave the cd inside the drive and it will boot into the windows installation program. As long as your system boot the CD at start up but if it does not you need to go to change it.
To do it you need to read on your screen when it starts you usually need to press something like DEL , F8 , or something like that then when you are in the BIos you change the boot order and put you cd drive to boot before the drive and you save and restard and if It is a Windows CD it will boot into the installer.

You can also open the Cd to see what file it contains from Ubuntu to make sure it is a Windows CD

Thanks, imgoing to give this ago, But for future reference. what files (names) would i be looking for in the CD-rom

---

### Post by mattk132 on 2008-03-19
First, if the only problem is mp3's just use a program called Banshee.  It can be downloaded using synaptic.  Just put in the disk that says windows install or something like that.  Just boot off the disk.  When this happens it should say "inspecting system's configuration".  Then, it should come up with a blue screen.  Then just follow the onscreen instructions.

---

### Post by phil90 on 2008-03-19
> **north-east-angler said:**
> :confused::cry:


andrew@andrew-laptop:~$ sudo dpkg --configure -a
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]


That would explain why the Frostwire was not working.

Ok you can try Medibuntu to solve you codec problem and also it should solve your music problem and also most of the other codec you might need
[[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


To solve the java problem for Frostwire you should install the java from the repository that the easiest way
In the terminal 

sudo apt-get install sun-java6-bin sun-java6-jre

---

### Post by phil90 on 2008-03-19
> **north-east-angler said:**
> Thanks, imgoing to give this ago, But for future reference. what files (names) would i be looking for in the CD-rom

Unfortunately I would not know but there would most likely be lots of files called Windows or Win something. I am currently looking at my cd and I know mine is different from the others because my computer manufacture did customize it. 

I see files like Win51  ,  Win51ic , , There is a doc folder and when I go in  there is a windows logo .gif files that sort of give me clue that it is a Windows cd :) there is also a guide in HTML that is called setup windows XP so that gives me another clue.  I found a system32 folder wich is a folder that is present in a windows installation so I guess it is a Windows cd

I am sure that if you look you can have a good idea wether or not it is a windows cd or not

---

### Post by Nathan_M on 2008-03-19
Hi north-east-angler,
It sounds like a few things need clarifying. Sorry if bits of it sound patronising, but I'm going to try to explain everything click-by-click, so that I can be sure you'll be able to follow.

**Reinstalling Windows**
You said you have two discs... MS Works (ignore this one), and the "notebook supporting utility" (this might be it, but it doesn't sound likely). If you do have a Windows XP disc, there shouldn't be a problem. Insert the disc in the drive and restart. If you are presented with step-by-step instructions for reinstalling Windows (something like these screenshots: [http://content.techrepublic.com.com/2346-10878_11-5181.html](http://content.techrepublic.com.com/2346-10878_11-5181.html)), then great. Go ahead and do it. Try doing this with the notebook support utility disc and see what happens. You shouldn't have to be looking for any files on the disc, it should happen automatically when you restart. (Note to other helpers: Since somebody managed to install Ubuntu, I think it's reasonable to assume the BIOS is already set to boot from CD.)
If you don't have a Windows XP disc, we can't help you... chances are PC World, in their "wisdom" didn't give you one, and you're going to have to take advantage of that warranty and get them to help you.

**But please give Ubuntu another try first...**
Don't be put off by the terminal. I know people are telling you to type things that seem like another language, but soon you'll grow to understand some of the things you type, and you'll understand just how useful it really is.
The first thing you said you want to do is play your music. Click Applications > Accessories > Terminal. Now type, or copy and paste, this code:
```
sudo apt-get install ubuntu-restricted-extras
```
Wait until that finishes running, and you get the line 
andrew@andrew-laptop:~$ again. (If the window turns blue and grey at any time, press return to accept the terms. The whole thing might take a few minutes.) Now insert a music CD or browse to where your music is and double click a file and see what happens. Report back here if it works or not (along with the exact text of any errors), then we'll see if we can help you with other problems.

Hope this has helped.
-Nathan

---

### Post by north-east-angler on 2008-03-21
HI nathan, The utility support wasnt the install disk for XP,

and when trying to run the code you entredfor me i get the following message

[COLOR="Red"]andrew@andrew-laptop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for andrew:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.[/COLOR] 

And frostwire still wont work

---

### Post by mattk132 on 2008-03-21
All that this means is when you were installing a package you quit the installation to fix this run that command.  sudo dpkg --configure -a.  This will finish installing whatever package was interrupted.:)

---

### Post by north-east-angler on 2008-03-21
> **mattk132 said:**
> All that this means is when you were installing a package you quit the installation to fix this run that command.  sudo dpkg --configure -a.  This will finish installing whatever package was interrupted.:)
OMFG thanks very much

---

### Post by north-east-angler on 2008-03-21
> **north-east-angler said:**
> OMFG thanks very much
ive already downlaoded the package now what?

Setting up sun-java5-doc (1.5.0-13-0ubuntu1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

---

### Post by mattk132 on 2008-03-23
Just follow directions.  Copy the .zip file to /tmp as a root.:)

---

### Post by IsawSp4rks on 2008-03-23
> **Nathan_M said:**
> (Note to other helpers: Since somebody managed to install Ubuntu, I think it's reasonable to assume the BIOS is already set to boot from CD.)

He already stated in his initial post that Ubuntu was installed for him by someone else and also stated that he was a complete noob (no offence at all the OP).

[quote=From Page 1]1. the dude whoinstalled it didnt make a back up copy of Windows XP And he did a complete partition (?)[/quote]

It's important and advisable to read the first post in a thread you're responding to.

---

### Post by favoritefood0 on 2008-03-23
Almost all of your problems could be fixed by just redownloading the ubuntu live CD, and reinstalling it yourself. Then we can go from there. Make sure you back up all your important files.

---

### Post by linuxtoindia on 2008-03-23
if you want to remove  everything then wipe the hard disk with seagate disk utility disk and start installing xp..
and if you had bought it !
then ask microsoft for the another cd.. with the same build as a warrantee with the same key ,, or just get a cd with the same build and then put the serial key u wud have got before,,thats it install it!

and before all this .....wait


you can enjoy,work,rely more on ubuntu!-the best linux..
just u have to get the codecs for the mp3 and mpeg videos,, get them by synaptic..
u will be able to play mp3, and see movies in any format media!
''no virus,fast , easy-computing!

---

