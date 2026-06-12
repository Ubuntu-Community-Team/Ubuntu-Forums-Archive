---
title: "install apps to other hardrive"
date: 2006-11-09
forum: General Help
---

### Post by feest on 2006-11-09
is it possible to install apps to an other drive or partition where ubuntu is installed?

---

### Post by bsussman on 2006-11-09
> **feest said:**
> is it possible to install apps to an other drive or partition where ubuntu is installed?

generally, appls follow the standards documented in [http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)

The placement is actually coded into the .deb packages and while you can modify this, it is not recommended.

What's your real question?  Phrase in the form "I want to do <x> because <y>"

---

### Post by feest on 2006-11-09
i have a hardrive thats has a few partitions orginally this was a 16gb ext3 partition and a 64gb ntfs partiton. by pressing the wrong key i removed the ntfs parttion with windows and now (i created a 30gb ext3 out of it) i want to use the partition for apps because my ext3 is running out of space.

this was no problem for wine or cedega apps but i also like playing native linux games so i want to install them also on that disk (sda4) so how do i do this?

---

### Post by dannyboy79 on 2006-11-09
i installed gxiso, which was installed by simply running a python script and now everything is in a folder within my home directory, my quesiton would be, so that I don't have to cd to the folder where the python script is located to actually run the program, how do I add it's location to where the system looks when I type in commands. for example, i know cp is a command stored in /bin/ but whenever I want to copy something I don't have to cd to /bin/ first, the system just knows where to look. so how to add a certain location to whatever this setting is called? also, would it just be better if I move the entire folder, "gxiso-1.5", into /usr/local or what? i guess since this wasn't installed from source or a deb, files just got put wherever and not in lie /lib/ or /usr/local/lib or /bin/ or /usr/local/lib. this is a question i'll have everytime I install a custom program??? thanks for any suggestions.

---

### Post by bsussman on 2006-11-09
> **feest said:**
> i have a hardrive thats has a few partitions orginally this was a 16gb ext3 partition and a 64gb ntfs partiton. by pressing the wrong key i removed the ntfs parttion with windows and now (i created a 30gb ext3 out of it) i want to use the partition for apps because my ext3 is running out of space.

this was no problem for wine or cedega apps but i also like playing native linux games so i want to install them also on that disk (sda4) so how do i do this?

This sounds like a challenge.

Without a consistent separate directory (for instance /usr/games or /x/y/z) to which they all install, it will be difficult to segregate them.  And if they install 'spread out', meaning some files here, some there, it is obviously a bigger challenge.

There is a directory called /usr/games

This may be where you want to mount your filesystem, after carefully copying all contents from the directory to your new filesystem.  The tutorial on moving /home is very good and you can just substituet /usr/games for /home -  I am having trouble location it right now :( - AH - [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) is what I was looking for.

---

### Post by dannyboy79 on 2006-11-09
> **feest said:**
> i have a hardrive thats has a few partitions orginally this was a 16gb ext3 partition and a 64gb ntfs partiton. by pressing the wrong key i removed the ntfs parttion with windows and now (i created a 30gb ext3 out of it) i want to use the partition for apps because my ext3 is running out of space.

this was no problem for wine or cedega apps but i also like playing native linux games so i want to install them also on that disk (sda4) so how do i do this?

you should have no problem simply making your root partition larger using the extra space you have. this shouldn't affect any data you have on your root partition. so bascially you are "growing" your root partition and you might as well get rid of the extra 30gb ext3 partition  and just combine it with your rootpartition. you can use gparted or qtparted, and if you are worried about accidentally messing up your root partition, just use part image to back it up first. i believe knoppix has part image on it otherwise you can download  it and put it on a bootable floppy or bootable cd because you have to run it while your root partition is NOT mounted. also, to clear up space on your root partition you can do a sudo apt-get autoclean which will remove all archive .deb's that were downloaded or even sudo apt-get clean. if you are curious about it, just do man apt-get, this is what it states:
clean  clean  clears  out  the local repository of retrieved package files. It removes everything but the lock file from
              /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When APT is used as a dselect(8) method, clean  is
              run  automatically.  Those who do not use dselect will likely want to run apt-get clean from time to time to free
              up disk space.

       autoclean
              Like clean, autoclean clears out the local repository of retrieved package files. The difference is that it  only
              removes  package files that can no longer be downloaded, and are largely useless. This allows a cache to be mainâ
              tained over a long period without it growing out of control. The configuration option  APT::Clean-Installed  will
              prevent installed packages from being erased if it is set to off.
what have you done with the extra 34gb of space? you stated that you have 16gb partition which is most likely "/" (where you're whole system is stored) then you said you used to have a 64gb partition that was ntfs and now it is 30gb ext3, well where are you mounting it or is that why you are asking? then of course like I already asked, what are you doing with the other 30gb? you should just add all 64gb to your "/" partition by growing it. or if you want, make /home a seperate parition like the other guy is saying, that's how I have mine. I actually have /, /boot, and /home as 1 hard drive and then /home/daniel/300gb-ext3 is a 300gb hard drive and /home/daniel/400gb-ext3 is a 400gb hard drive and /home/daniel/fat32 is a 240gb fat32 hard drive partition and /home/daniel/ntfs is 60gb ntfs hard drive partition. if you have any questions for me I'd be glad to answer them.

---

### Post by feest on 2006-11-09
okay your right its true an ext partition can be resized without the loss of damage but can i also use 2 hdd's as one partition without the use of raid? i guess not and when i run out of total space can i install to the other disk? will this happen if i compile apps from a diffrent location?

---

### Post by bsussman on 2006-11-09
> **feest said:**
> okay your right its true an ext partition can be resized without the loss of damage but can i also use 2 hdd's as one partition without the use of raid? i guess not and when i run out of total space can i install to the other disk? will this happen if i compile apps from a diffrent location?

  You are correct -  filesystems are limited to one 'disk' ('disk' is a stretchy term but you get it :) )  The traditional space stretcher is to use mountpoints but this will not work for stretching a single mountpoint :( .

compile doesnt really equate to install.  The linux standard install strategy  just expects certain things to be in certain locations.

In some builds, it is possible to specify where to install but we are, at that point, outside of the package manager, in buildfromsource land.

---

### Post by dannyboy79 on 2006-11-09
> **bsussman said:**
> In some builds, it is possible to specify where to install but we are, at that point, outside of the package manager, in buildfromsource land.

I beg to differ, this is actually the best and easiest time to specify the install location, when you compile from source otherwise when you install from synaptic or from a .deb, it just puts it where it's already been told within the .deb. During the configure stage you would put prefix, so the command would look something like this

./configure --prefix=/opt/elmer ; make ; make install

if you wanted the stuff stored within /opt/elmer.

---

### Post by bsussman on 2006-11-09
> **dannyboy79 said:**
> I beg to differ, this is actually the best and easiest time to specify the install location
Agreed, and, in my opinion, very inadvisable for a beginner to use, as it makes future (inevitable) support challenging because nobody I know would think to ask 'did you specify a prefix when you built?'. And please note that I referenced this in my comment.
> 
when you compile from source otherwise when you install from synaptic or from a .deb,
Last time I looked, a build/install from source does not use synaptic, though checkinstall does make it easier to do this.  This was part of my point :)

Additionally, when you use synaptic you are installing from a .deb so the last 5 words quoted above make no sense.   There is no or to it - synaptic = using .deb - perhaps you meant "synaptic or apt-get".

I am not trying to be annoying - precision in terminology is essential in these conversations.
Without talking down to anybody, an appreciation for the level of skill on the part of the questioner is also important.

---

### Post by dannyboy79 on 2006-11-09
> **bsussman said:**
>  Agreed, and, in my opinion, very inadvisable for a beginner to use, as it makes future (inevitable) support challenging because nobody I know would think to ask 'did you specify a prefix when you built?'. 
That's his question! He is asking about installing apps to other locations, I am merely answering the question in the Thread subject line.
  
> **bsussman said:**
>  And please note that I referenced this in my comment.
What are you referring to?

> **bsussman said:**
> Last time I looked, a build/install from source does not use synaptic, though checkinstall does make it easier to do this.  This was part of my point :) 
A misplaced comma made you read the sentence completely wrong. I moved the comma, now read it and it'll make more sence. "I beg to differ, this is actually the best and easiest time to specify the install location when you compile from source, otherwise when you install from synaptic or from a .deb, it just puts it where it's already been told within the .deb."

> **bsussman said:**
> Additionally, when you use synaptic you are installing from a .deb so the last 5 words quoted above make no sense. 
Last 5 words would be "synaptic or from a .deb" They make perfect sense to me, you can install a .deb WITHOUT using synaptic, or did you now know this?


> **bsussman said:**
>  There is no or to it - synaptic = using .deb - perhaps you meant "synaptic or apt-get".
I have no idea what you are saying here??

> **bsussman said:**
> I am not trying to be annoying - precision in terminology is essential in these conversations.
Without talking down to anybody, an appreciation for the level of skill on the part of the questioner is also important. 
Agreed, that's why YOU shouldn't write stuff like, "There is no or to it"

---

### Post by PriceChild on 2006-11-09
> **dannyboy79 said:**
> 
	 	 		 			 				> Originally Posted by **bsussman** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://www.ubuntuforums.org/showthread.php?p=1737474#post1737474") 				
 				[I]I am not trying to be annoying - precision in terminology is essential in these conversations.
Without talking down to anybody, an appreciation for the level of skill on the part of the questioner is also important.Agreed, that's why YOU shouldn't write stuff like, "There is no or to it"Please stay on topic both of you and refrain from personal attacks.
[/I]

---

### Post by feest on 2006-11-10
> **dannyboy79 said:**
> I beg to differ, this is actually the best and easiest time to specify the install location, when you compile from source otherwise when you install from synaptic or from a .deb, it just puts it where it's already been told within the .deb. During the configure stage you would put prefix, so the command would look something like this

./configure --prefix=/opt/elmer ; make ; make install

if you wanted the stuff stored within /opt/elmer.

so if i want to install an app to sda4 i just do:

```
tar xvfz /home/sven/Desktop/<filename>
cd <directory in tarball>
./configure --prefix=/media/sda4/apps-native/<appname>
make
make install
```

is that correct?

---

### Post by dannyboy79 on 2006-11-10
well, that is if that folder (=/media/sda4/apps-native/<appname>)is there and there is a partition mounted to it, than yes, I believe that's how it works. I have never done it but have read about it. just gogle configure with prefix if you want to learn about it before you do it.

---

