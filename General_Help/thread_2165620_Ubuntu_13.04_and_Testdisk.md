---
title: "Ubuntu 13.04 and Testdisk"
date: 2013-08-05
forum: General Help
---

### Post by dj722000 on 2013-08-05
Does testdisk work under 13.04? I can not get it to do anything. I can not get it to install through terminal, wont run from the static file, nothing. Just sits there. Anyone have any ideas how to get this thing up and running?

---

### Post by bapoumba on 2013-08-05
Did you run it with sudo ?
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by dj722000 on 2013-08-05
Ya I tried that to. The problems starts when I try to install it CLI. It gives me an error that I cant install it. But now, I can open the downloaded folder, extract it and run testdisk_static. But I cant run photorec_static. Any ides on what is going on? Id really love to install it and play around with it.

---

### Post by bapoumba on 2013-08-05
```
bapoumba@SonyBlue:~$ apt-cache show testdisk
Package: testdisk
Priority: optional
Section: universe/admin
Installed-Size: 1201
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Jean-Michel Kelbert <kelbert@debian.org>
Architecture: i386
Version: 6.13-1ubuntu2

```

It's in universe, do you have these repos enabled ?

---

### Post by Bashing-om on 2013-08-05
dj722000;

See the above from bapoumba.
Also, do not these types of utilities require to be run with the target file system in an (un)mounted state ? (thus a bootable CD/medium)

[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

---

### Post by dj722000 on 2013-08-05
If your asking me if there is a check mark by them, then yes there is.


I ran your command in your window and this is what I get for it; 

dj@dj-Satellite-L755D:~$ apt-cache show testdisk
N: Unable to locate package testdisk
E: No packages found
dj@dj-Satellite-L755D:~$ 

Obviously it isnt installed, I just have it downloaded, extracted it to my desktop,  I click on the testdisk_static and it starts, but the photorec_static wont do anything.

---

### Post by dj722000 on 2013-08-05
So your saying I need to burn it to a cd and run it from that? This is not what I have been seeing in other videos, they just install it and go to town looking at a different HDD that I am assuming isnt mounted as they are recovering deleted data from it. I think the later is what your trying to say?

---

### Post by dj722000 on 2013-08-05
Hmmm just went back into Ubuntu Software and the one for Installable from CD-ROM/DVD was unchecked. I checked it and it installed. I never did nothing with that, is it suppose to be checked? I dont recall that ever being checked before.

---

### Post by Bashing-om on 2013-08-05
dj722000; Hi !

Pleased you are making progress, look'n better all the time.

Software Center ...CD-ROM/DVD check box should normally be UNchecked...unless, as in perhaps this case, there is software on the install disk that is required. Generally the software available from the on-line repositories is to be preferred. If you leave the option checked, the package manager is going to be upset.

[INDENT][INDENT]be kind to your ubuntu[/INDENT][/INDENT]

---

### Post by dj722000 on 2013-08-05
Well thanks. Somedays it can get on my last nerve. LOL I even went a lot deeper and set up an Ubuntu Server 13.04 to store a lot of stuff I have. Now that is on my last nerve. But pluggin away.

 There is a problem with your theory though.........there is no Live CD in the drive. I just seen it was unchecked, I checked it and went back just for making me feeling better and tried to to install testdisk and away it went. Apparently there was some code it wanted maybe?

So on to your next statement....... "If you leave the option checked, the package manager is going to be upset." Why is this? Jupiter going to fall out of orbit and crash into Earth or something? LOL J/K

---

### Post by Bashing-om on 2013-08-05
dj722000;

Welll... it is like this .. the packages on the .iso file were current at the time the initial .iso file was made ... since that time many updates have been done. Those updated packages are available in the on-line repository, if you make that CD available (checked in the Software Center) then the package manager is going to look for that CD and all those old packages ...and the package manager can go berserk trying to reconcile - do a search on this forum as to how many times the advisement was that the CD/DVD avenue was enabled, and to disable it ! ...

As to what transpired that "apt-get install" failed to fetch until that option was enabled ... does not stand to reason ... Computers are finniky people ?

Perhaps you have not ran the command "sudo apt-get update" or the GUI equivalent in a while .. doing so syncs the system databases with the repository data base for what is available for update-to-be-installed. Maybe when you checked the CD/DVD box some file on the system was accessed to make a comparison ??
In working theory all that should have been needed was:
```

sudo apt-get update
sudo apt-get install testdisk

``` and the package manager should have gone to work and done it's thing -fetched and installed testdisk- ... no fuss, no muss.

I'll admit :
[INDENT][INDENT]sometime I do not know, other times I wonder[/INDENT][/INDENT]

---

### Post by dj722000 on 2013-08-05
Just so you feel at ease, I did uncheck it after it was installed. LOL I understand that logic, but I always run sudo apt-get update and sudo apt-get upgrade, at least once a day. When I first went to install it, I did the sudo apt-get update, then the sudo apt-get install testdisk. Then it failed. I searched the internet for the software and downloaded it, tried to make the tar unpack and tried to install it,errrr. To complicated, so I gave up. 

 I right clicked on it and seen I could extract it, so I did. I seen someone had posted that you could just click on the testdisk_static  after you extract it, to no avail, it wouldnt do anything. Neither one would start, thats when I turned to Ubuntu Forums, which by the way I am very happy it is back up and running. Alot of info that was almost comprimised by some jack wagon thinking there cool with a high school IQ! Enough of that subject. ....

 There is so much to learn with this Ubuntu, I like the fact it is free, I like the fact there is a lot of free software that is super powerful such as this one that I installed. I like this kind of stuff, makes one sorta feel acomplished without spending gobb loads of money, until something dumb happens and your left wondering......LOL But with it being free sometimes there is things that just mess with you. Thanks for the complement if it was one earlier, if not, Ill take it as one my friend. Keep Ubuntuing on!

---

### Post by dj722000 on 2013-08-05
On a last note however, since I just ran another sudo apt-get update; I now get all this crud at the end: 

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) raring Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release: The following signatures were invalid: BADSIG 1DF68602940F55D6 Launchpad PPA for Tomasz Makarewicz
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/Release](http://extras.ubuntu.com/ubuntu/dists/raring/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

Is there a way to clean this up? I keep removing them from the software updater, but they keep coming back. I am under the assumption they are under etc? Also, when it updates, it says somethign like get, hit and ign. I assume IGN is ignore? If so, can I remove them? If so, how. Just want to clean it up a little bit.

---

### Post by Bashing-om on 2013-08-05
dj722000; Wow ... when it rains it pours.

Let's see if we can validate the source once more:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192

```
for "1DF68602940F55D6 Launchpad PPA for Tomasz Makarewicz" how bout going back to his PPA page and download the key once more ?// The above code might work, just not to sure.

[INDENT]security do mean validation, huh
[/INDENT]

---

### Post by bapoumba on 2013-08-06
Thanks Bashing-om :)

---

### Post by dj722000 on 2013-08-06
> **Bashing-om said:**
> dj722000; Wow ... when it rains it pours.

Let's see if we can validate the source once more:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192

```
for "1DF68602940F55D6 Launchpad PPA for Tomasz Makarewicz" how bout going back to his PPA page and download the key once more ?// The above code might work, just not to sure.

[INDENT]security do mean validation, huh
[/INDENT]


Hey sorry. I had some stuff I needed to take care of last night. Anywho, I really do aprreciate all the help your giving. I tried running those two commands and nothing, still gives the errors. As far as going to get Tomasz PPA, I think I was trying to add a PPA  and it came up with an error and decided I didnt want it. I dont remember. LOL

---

### Post by oldos2er on 2013-08-06
To fix your BADSIG errors, try Method #1 here: [http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

---

### Post by Bashing-om on 2013-08-06
@bapoumba - With high regard, Thanks for what ? .. Just look'n to keep things moving ....
@oldos2er; Ann, as I live and learn ... bout the time I think I know something, I discover how little I actually know ...wonderful OS that we have !

@dj722000; What can I say ... open source and we are all in this together, What ever I can do to promote ubuntu is what needs doing. Helping others is one way I learn this operating system and please, Pass it on ! 
 In respect to the software sources, as you say you do not know ... it will behoove us at this time to take a look at what you have set for acquisition of software, see if we can see the source of the errors. Show us:
```

cat /etc/apt/sources.list
ls -la /etc/apt/sources.list.d ##a directory that hold other "get" files.

```

As others have noted:
[INDENT][INDENT]if it ain't broke, you have not tweaked it enough
[/INDENT][/INDENT]

---

### Post by dj722000 on 2013-08-06
> **oldos2er said:**
> To fix your BADSIG errors, try Method #1 here: [http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

Wow, it worked. Thanks a ton.

---

### Post by dj722000 on 2013-08-06
> **Bashing-om said:**
> @bapoumba - With high regard, Thanks for what ? .. Just look'n to keep things moving ....
@oldos2er; Ann, as I live and learn ... bout the time I think I know something, I discover how little I actually know ...wonderful OS that we have !

@dj722000; What can I say ... open source and we are all in this together, What ever I can do to promote ubuntu is what needs doing. Helping others is one way I learn this operating system and please, Pass it on ! 
 In respect to the software sources, as you say you do not know ... it will behoove us at this time to take a look at what you have set for acquisition of software, see if we can see the source of the errors. Show us:
```

cat /etc/apt/sources.list
ls -la /etc/apt/sources.list.d ##a directory that hold other "get" files.

```

As others have noted:
[INDENT][INDENT]if it ain't broke, you have not tweaked it enough
[/INDENT][/INDENT]

To late I think we posted at the same time. I already did the fix. I do thank you for your time and paitence though, very much appreciated.

To all who helped, it is very much appreciated for your help. Thank you.

---

