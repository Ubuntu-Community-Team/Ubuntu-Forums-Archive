---
title: "Do I really have to fsck everytime I boot the machine?"
date: 2006-12-27
forum: General Help
---

### Post by Fibonacci on 2006-12-27
Hello,

I recently noticed that everytime I boot Ubuntu, it runs fsck on all the existing partitions. Of course, it does take some time (not that it's the most of my boot time, but still), so I would like to know: is it really necessary? And if not, how can I prevent fsck from running?

Thanks in advance,

-Fibo

---

### Post by az on 2006-12-27
> **Fibonacci said:**
> Hello,

I recently noticed that everytime I boot Ubuntu, it runs fsck on all the existing partitions. Of course, it does take some time (not that it's the most of my boot time, but still), so I would like to know: is it really necessary? And if not, how can I prevent fsck from running?

Thanks in advance,

-Fibo

Your filesystem should be checked automaticaly every thrity times it is mounted.  If it is doing it every time you boot, there is a problem.  What happens if you check it while you are at the desktop, any errors?

---

### Post by Fibonacci on 2006-12-27
> **azz said:**
> What happens if you check it while you are at the desktop, any errors?

None that I can see.

EDIT: did you mean, actually running fsck while logged in?

---

### Post by jamadagni on 2006-12-27
This is happening because the last columns in /etc/fstab are by default set to 2, which forces such a check. Change it to 0 if you don't want it to be checked. But root partition (and /home and /boot if any) must *always* be checked. Root must have 1 in that column always.

P.S: Edit system files at your own risk.

---

### Post by Fibonacci on 2006-12-27
> **jamadagni said:**
> This is happening because the last columns in /etc/fstab are by default set to 2, which forces such a check. Change it to 0 if you don't want it to be checked. But root partition (and /home and /boot if any) must *always* be checked. Root must have 1 in that column always.

They're all actually set to 1:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=b1c9ae04-50dc-4513-9a52-ef3b7c8a0640 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=A680C6F080C6C651 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb5
UUID=7439-2E24  /media/hdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=4455-2CA9  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/swapfile       swap            swap    defaults
```
What does that mean?

> **jamadagni said:**
> P.S: Edit system files at your own risk.

Wouldn't be the first system file I edit, but I know little about the syntax of fstab. Any help would be appreciated.

---

### Post by jimbob on 2006-12-27
Your swap file entry loks very strange.  Why doesn't it have a UUID spec like everything else?

Is this something you added?

---

### Post by Fibonacci on 2006-12-27
> **jimbob said:**
> Your swap file entry loks very strange.  Why doesn't it have a UUID spec like everything else?

Is this something you added?

Yes, the swapfile was something I added. And it's an actual file on /.

---

### Post by AgenT on 2006-12-27
Do note change your fstab file! You **DO NOT** want to disable fdisk. It is enabled for a *very* good reason. 

My advice to you is just download and install [Bonager: The Boot Scan Manager]("http://www.ubuntuforums.org/showthread.php?t=295262"). Then on your first boot, force a scan using Bonager. This should reset the scan on all hard drives and from that point on Bonager will tell you when the next scan is about to occur and let you postpone it if you want.

---

### Post by Fibonacci on 2006-12-27
> **AgenT said:**
> Do note change your fstab file! You **DO NOT** want to disable fdisk. It is enabled there for a good reason.

My advice to you is just download and install [Bonager: The Boot Scan Manager]("http://www.ubuntuforums.org/showthread.php?t=295262"). Then on your first boot, force a scan using Bonager. This should reset the scan on all hard drives and from that point on Bonager will tell you when the next scan is about to occur and let you postpone it if you want.

Didn't want to *install* anything to *remove* the forced fsck on each boot... but I can leave with it if there's no other option.

---

### Post by dannyboy79 on 2006-12-27
it's perfectly fine to change your fstab! here, check out this webpage, it's bascially the man page for tune2fs, which will tell you how to change the frequency of when a fsck is performed after a certain amount of reboots. [http://www.die.net/doc/linux/man/man8/tune2fs.8.html](http://www.die.net/doc/linux/man/man8/tune2fs.8.html)
i am not sure how to set the amount of times the filesystem is mounted and then checked for vat or ntfs though. I just changed all my vfat and ntfs partitions to 0 and then I set a reminder in /etc/cron.monthly to email me that I should check them! but never change your root partition from 1, always leave that at 1 so it gets checks after the amount of boots has been met. like someone else said, it's usually every 30, i am not sure why yours is checking everytime? your tune2fs -i setting for your partitions somehow must have been changed?

oh, I am only suggesting the above because you don't want to install bonager, but I would do it the bonager way first!

---

### Post by Fibonacci on 2006-12-27
> **dannyboy79 said:**
> ... like someone else said, it's usually every 30, i am not sure why yours is checking everytime? your tune2fs -i setting for your partitions somehow must have been changed?

How? I didn't even knew that existed until I read your message...

> **dannyboy79 said:**
> oh, I am only suggesting the above because you don't want to install bonager, but I would do it the bonager way first!

Now, if I were sure that Bonager was GPL...

---

### Post by dannyboy79 on 2006-12-27
isn't all software available in the repos GPL? If not, then why don't we have to pay for it?

---

### Post by Fibonacci on 2006-12-27
> **dannyboy79 said:**
> isn't all software available in the repos GPL?

Is Bonager in the repos? Strange, apt-cache search didn't find it. Besides, I don't think the nVidia drivers are GPL (or even open source) at all, even though they *are* in the repos.

> **dannyboy79 said:**
> If not, then why don't we have to pay for it?

... because it's available for free?

---

### Post by raul_ on 2006-12-27
i change my fstab all the time :) just stopped to say that you don't need to use UUID in your fstab file

---

### Post by Fibonacci on 2006-12-27
> **raul_ said:**
> i change my fstab all the time :) just stopped to say that you don't need to use UUID in your fstab file

I didn't write it, the Ubuntu installer did...

---

### Post by dannyboy79 on 2006-12-27
> **Fibonacci said:**
> Is Bonager in the repos? Strange, apt-cache search didn't find it. Besides, I don't think the nVidia drivers are GPL (or even open source) at all, even though they *are* in the repos.



... because it's available for free?

do you have all the repos uncommented in your sources.list? not sure which one it's in but it's in there. I always do a sudo aptitude search bonager (using aptitude will find all dependencies as well finding the main app where apt-get sometimes doesn't. at least I thought I read that somewhere. or maybe it was if you install something with apt-get, it'll install the dependencies but then can't uninstall them when you do apt-get uninstall but aptitude can. not exactly sure why aptitude is better but I am pretty sure it is)

> **Fibonacci said:**
>  ... because it's available for free?
real funny! when I said, "well then why don't we have to pay for it" I meant that if something isn't GPL'd than shouldn't you have to pay for it? I don't know how the whole license thing works.

---

### Post by Fibonacci on 2006-12-27
> **dannyboy79 said:**
> do you have all the repos uncommented in your sources.list?

main, restricted, universe, and multiverse? Yes, I do have all of them uncommented.

> **dannyboy79 said:**
> not sure which one it's in but it's in there. I always do a sudo aptitude search bonager (using aptitude will find all dependencies as well finding the main app where apt-get sometimes doesn't. at least I thought I read that somewhere. or maybe it was if you install something with apt-get, it'll install the dependencies but then can't uninstall them when you do apt-get uninstall but aptitude can. not exactly sure why aptitude is better but I am pretty sure it is)

Still no dice - doesn't appear in aptitude search either.

> **dannyboy79 said:**
> real funny! when I said, "well then why don't we have to pay for it" I meant that if something isn't GPL'd than shouldn't you have to pay for it? I don't know how the whole license thing works.

Think "free speech", not "free beer". There is GPL'd software you have to pay for (e.g.: Red Hat, SuSE, even Emacs in its early days), and proprietary software that is given away for free (Flash, Skype, some proprietary drivers).

---

### Post by az on 2006-12-27
> **Fibonacci said:**
> 

Now, if I were sure that Bonager was GPL...

It doesn't seem to be distributed anywhere else than that thread.  There is no source code or licence.

If it is GPLed, the source should be made available.  This does not seem to be the case.


[QUOTE=dannyboy79]
isn't all software available in the repos GPL? If not, then why don't we have to pay for it? [/QUOTE]

Everything in main and universe is free-libre.  Anything that is not GPL-compliant is in multiverse or commencial.

---

### Post by Fibonacci on 2006-12-27
> **azz said:**
> It doesn't seem to be distributed anywhere else than that thread.  There is no source code or licence.

If it is GPLed, the source should be made available.  This does not seem to be the case.

Which is why I don't want to install it. But the tune2fs solution doesn't seem to work for FAT32 filesystems, and I don't know how to program cron jobs, so...

> **azz said:**
> Everything in main and universe is free-libre.  Anything that is not GPL-compliant is in multiverse or commencial.

OR restricted.

---

### Post by dannyboy79 on 2006-12-27
that's exactly what I was saying. you use fsck to check vfat. I would also like to point out that we are all trying to help you and you keep telling us that you don't want to do this and you don't want to do that. Ok then, don't do any of it but don't keep asking us to help you. ok? Also what's so bad about installing non-gpl'd stuff? it's not like we're asking you to install win32codecs which IS ILLEGAL in the US! using cron to email you reminding you to run fsck on your fat32 partitions is pretty easy.

---

### Post by Fibonacci on 2006-12-27
> **dannyboy79 said:**
> that's exactly what I was saying. you use fsck to check vfat. I would also like to point out that we are all trying to help you and you keep telling us that you don't want to do this and you don't want to do that. Ok then, don't do any of it but don't keep asking us to help you. ok?

Only thing I don't want to do is to install a nonfree program to get rid of fsck. I would gladly do it by hand if you or someone else told me how.

> **dannyboy79 said:**
> Also what's so bad about installing non-gpl'd stuff? it's not like we're asking you to install win32codecs which IS ILLEGAL in the US!

I don't think any of that is illegal here, but I don't want proprietary software for a task I can (apparently) do by hand.

> **dannyboy79 said:**
> using cron to email you reminding you to run fsck on your fat32 partitions is pretty easy.

It is if you know how to do it, of course. But I don't.

---

### Post by dannyboy79 on 2006-12-27
> **Fibonacci said:**
>  Only thing I don't want to do is to install a nonfree program to get rid of fsck. I would gladly do it by hand if you or someone else told me how.
Bonager doesn't get rid of fsck. It merely gives you the opportunity to postpone it. That is what I read. I don't use it because I have already explained what I do.



> **Fibonacci said:**
>   I don't think any of that is illegal here, but I don't want proprietary software for a task I can (apparently) do by hand.
Well, based on your answer below, it doesn't sound like you want to learn how to do anything if you don't already know how to do it! So the easiest thing to do is install Bonager and follow what was previsouly posted or LEARN how to do something you can do by hand.



> **Fibonacci said:**
>  It is if you know how to do it, of course. But I don't. 
I just started using linux in march of this year, I chose Ubuntu as my first distro and have stuck with it. You think I just picked up linux and knew how to do everything. NO, I didn't. I took peoples suggestions and gogled and read thru hours of forums and tried my best and most of the time I got, then when I get stuck I come here for help. WHen I do come here for help, I use peoples help instead of saying, "I don't want to do that". Why come for help if you don't want to listen? All the answers and suggestions have been given to you in this thread. I suggest you read it and do what you want to do but I am done with this thread as other's most likely could use my help more than you are. Good Luck.

---

### Post by Fibonacci on 2006-12-27
> **dannyboy79 said:**
> Bonager doesn't get rid of fsck. It merely gives you the opportunity to postpone it. That is what I read. I don't use it because I have already explained what I do.

Well, based on your answer below, it doesn't sound like you want to learn how to do anything if you don't already know how to do it! So the easiest thing to do is install Bonager and follow what was previsouly posted or LEARN how to do something you can do by hand.

I just started using linux in march of this year, I chose Ubuntu as my first distro and have stuck with it. You think I just picked up linux and knew how to do everything. NO, I didn't. I took peoples suggestions and gogled and read thru hours of forums and tried my best and most of the time I got, then when I get stuck I come here for help. WHen I do come here for help, I use peoples help instead of saying, "I don't want to do that". Why come for help if you don't want to listen? All the answers and suggestions have been given to you in this thread. I suggest you read it and do what you want to do but I am done with this thread as other's most likely could use my help more than you are. Good Luck.

Well, thank you for teaching me how to set up a Cron job to remind me of running fsck every month. You have been most helpful.

---

### Post by AgenT on 2006-12-27
While it is pretty easy and straightforward to disable or change the boot scan settings, it should not be done. Ubuntu developers are well aware that this is "annoying" but they are not willing to change the default behaviour for very good reasons. And while there may be a time where the default settings are changed in Ubuntu, they will not be much different from what they are now. The same goes for Debian and even the people behind ext3 and tune2fs. If anyone wants more detailed (and highly technical) information, just ask. But please be courteous and search before asking.

The point is: do not change the default settings.

**Bonager is [freedom software]("http://www.fsf.org/licensing/essays/free-sw.html")**. 100%. Plain and simple. 

Bonager is GPL'ed and has always been licensed under GPLv2 from the very first release. How do I know? I am the author of Bonager. All the source code files even have the standard GPL license preamble.

If you still have doubts, download the deb file and extract it (before installing it). Look at the source code. Look at the License file. And if you are still in doubt, look at the official UbuntuForums thread. I will update it with information about this as I was not aware that people could actually be sceptical whether or not Bonager is freedom software.

And Bonager is not available in any repository. It will, however, be submitted to Debian and Ubuntu at a later time.

UPDATE: Bonager does NOT get rid of the fsck. This was done on purpose. That is easy to do in itself. What Bonager does is allow you to force a scan to reset the fsck counter back to 0, postpone a scan and warns you of upcoming scans. Please read the description in the thread for more details of what Bonager does.

It is very true that no seperate source code package is provided. There is a really good reason for this: no part of Bonager is in binary format. Bonager is coded in Python and Bash, both not requiring compilation. The result of this is: if you have the program, you have the source code. There is no difference between the two. The source code *is* the program.

---

### Post by az on 2006-12-27
> **AgenT said:**
> 
It is very true that no seperate source code package is provided. There is a really good reason for this: no part of Bonager is in binary format. Bonager is coded in Python and Bash, both not requiring compilation. The result of this is: if you have the program, you have the source code. There is no difference between the two. The source code *is* the program.

To be fair, a deb package is not a traditional way to ditribute the source code.  A tarball is usually more hack-the-source friendly.  As well, I hardly think anyone will want to have to install a deb (or extract it) just to read the licence file.  You should post that more publicly.

Maybe post your orig.tar.gz and .dsc files so that anyone can fetch then and hack them, too?  I mean, the dependencies are not even displayed...

Edit:

I think you app is great.  It's useful and seems well done.  I'm extatic that you are distributing it under the GPL.  Howerver, I would never download and install a deb like that.   For all I know, it's built with checkinstall....

---

### Post by AgenT on 2006-12-28
> **azz said:**
> To be fair, a deb package is not a traditional way to ditribute the source code. A tarball is usually more hack-the-source friendly.You should note that a deb file is just a plain ar archive file with a renamed extension. And the the deb file archive, when extracted, will provide all the files that the orig.tar.gz archive has because nothing is compiled. But you are correct, a tar is more widespread.

> **azz said:**
> As well, I hardly think anyone will want to have to install a deb (or extract it) just to read the licence file. You should post that more publicly.Already did that, see my post above.

> **azz said:**
>  Maybe post your orig.tar.gz and .dsc files so that anyone can fetch then and hack them, too? I mean, the dependencies are not even displayed...What do you mean by "the dependencies are not even displayed"? The dependencies are in the control file as well as posted on the first post of the official Bonager thread. It has been like that for a long time now. Where else do you think the dependencies should be listed?

> **azz said:**
> I think you app is great. It's useful and seems well done. I'm extatic that you are distributing it under the GPL.Thank you.

> **azz said:**
> Howerver, I would never download and install a deb like that. For all I know, it's built with checkinstall....Again, a deb file is an ar archive. It takes as much effort to extract an ar archive as it does a tar. You can even use the GNOME fileroller to extract it. ar is available on just about every Linux system because it is part of the GNU utitlites. If you can tar, you can ar (that should be a slogan!).

Another reason for not including the orig.tar.gz and .dsc files is the forum file upload limit. Only 5 files maximum per post. There are ways of getting around that, but it's a hassle when doing updates.

If you really are desperate for the orig.tar.gz file, just PM me and I will send it to you.

Please post all further inquiries about Bonager in the [official Bonager thread]("http://www.ubuntuforums.org/showthread.php?t=295262").

---

### Post by dannyboy79 on 2006-12-28
> **Fibonacci said:**
> Well, thank you for teaching me how to set up a Cron job to remind me of running fsck every month. You have been most helpful.

You never asked me, you simply said you wouldn't do it that way. Now that you're being very rude and sarcastic you won't be recieving any more help from me. Why don't you help yourself and learn how to do it instead of just asking someone to tell you how to do it? What a mind bending suggestion!!!

---

### Post by Fibonacci on 2006-12-28
> **dannyboy79 said:**
> You never asked me, you simply said you wouldn't do it that way.

Oh really? When?

> **dannyboy79 said:**
> Now that you're being very rude and sarcastic you won't be recieving any more help from me.

If you didn't want to help you could have said so from the beginning.

> **dannyboy79 said:**
> Why don't you help yourself and learn how to do it instead of just asking someone to tell you how to do it? What a mind bending suggestion!!!

1- Because I don't know where to learn.
2- Because I thought you would be so kind as to share your knowledge.
3- Because now that I know that Bonager is free software, I'll stick with that and report if it works or not.

---

### Post by AgenT on 2006-12-28
Double post, please see reply #26.

---

### Post by dannyboy79 on 2006-12-28
> **Fibonacci said:**
>  Oh really? When? 
"Which is why I don't want to install it. But the tune2fs solution doesn't seem to work for FAT32 filesystems, **and I don't know how to program cron jobs, so...**"
You made this statement previously, I read this as basically stating that since you don't know how to do it you aren't going to do it that way.

> **Fibonacci said:**
>  If you didn't want to help you could have said so from the beginning. 
In the begining I wanted to help hence why I gave you a solution to the problem, as soon as you started being the way your being, ignorant and sarcastic, I have decided that others could use my help more.

> **Fibonacci said:**
> 
1- Because I don't know where to learn. 
goggle is your friend or these forums which I thought was why you were here.
> **Fibonacci said:**
> 2- Because I thought you would be so kind as to share your knowledge.
I wouldv'e but you never asked, you stated that since you didn't know how to do it you weren't going to do it that way.
> **Fibonacci said:**
> 3- Because now that I know that Bonager is free software, I'll stick with that and report if it works or not. 
I am glad you finally are going with a solution instead of just shoot down everyones suggestions and attempts to help you.

I strongly suggest that when you come here for help in the future, listen to what people are telling you and instead of just wanting everyone to hold your hand you use your own intellect and search out the answer in the vast highway of knowledge known as the internet, a great car to navigate this highway of knowledge is called GOGGLE. You can find any answer to any question with some time and patience. Good luck to you and I hope you have a safe and enjoyable New Year.

---

### Post by az on 2006-12-28
> **AgenT said:**
> You should note that a deb file is just a plain ar archive file with a renamed extension. But you are correct, a tar is more widespread.

A deb also runs scripts when you install it.  I don't want to run (or even just download) a deb without knowing how its' built.

While it's easy to look inside a deb package, its' purpose is to install a binary.  It's not the right tool for distributing source.

> **AgenT said:**
> 
Another reason for not including the orig.tar.gz and .dsc files is the forum file upload limit. Only 5 files maximum per post. Yes there are ways of getting around that, but it's a hassle.



Launchpad?

[https://launchpad.net/](https://launchpad.net/)

[https://launchpad.net/products/bzr](https://launchpad.net/products/bzr)

---

### Post by Fibonacci on 2006-12-28
> **dannyboy79 said:**
> "Which is why I don't want to install it. But the tune2fs solution doesn't seem to work for FAT32 filesystems, **and I don't know how to program cron jobs, so...**"
You made this statement previously, I read this as basically stating that since you don't know how to do it you aren't going to do it that way.

Well, I said I didn't know, not that I didn't want to. I never meant to say I wasn't going to do it the Cron way - in fact I *wanted* to do it the Cron way.

> **dannyboy79 said:**
> In the begining I wanted to help hence why I gave you a solution to the problem, as soon as you started being the way your being, ignorant and sarcastic, I have decided that others could use my help more.

So now I'm the one that's ignorant and sarcastic? Okay...

> **dannyboy79 said:**
> goggle is your friend or these forums which I thought was why you were here.

I asked because I didn't find what I was looking for in Google OR in these forums. If there's already a thread discussing my problem I apologise for wasting your time, and ask you to kindly provide a link to said thread.

> **dannyboy79 said:**
> I wouldv'e but you never asked, you stated that since you didn't know how to do it you weren't going to do it that way.

Once again: I never stated I wasn't going to do it that way.

> **dannyboy79 said:**
> I am glad you finally are going with a solution instead of just shoot down everyones suggestions and attempts to help you.

I strongly suggest that when you come here for help in the future, listen to what people are telling you and instead of just wanting everyone to hold your hand you use your own intellect and search out the answer in the vast highway of knowledge known as the internet, a great car to navigate this highway of knowledge is called GOGGLE. You can find any answer to any question with some time and patience. Good luck to you and I hope you have a safe and enjoyable New Year.

I would have never asked if I had found an answer to my problem either on Google or here. But sure, next time someone tells me to program a Cron job, I'll listen - perhaps I might hear how to do so.
Happy new year to you all too.

---

### Post by raul_ on 2006-12-28
C'mon, don't stress about it. "calma hermano" (sorry i'm portuguese, my spanish is lousy. as fas as we are concerned, spanish is a bad copy of portuguese...of course the spanish say the same). There are a lot of duplicate threads. I have posted problems that i later solved on google. Sometimes we just don't know what to ask or search. Don't be afraid to ask twice if you don't understand a reply, or google about it. The forum members will be glad to help the users step by step

---

### Post by Fibonacci on 2006-12-28
Just tried Bonager, but still no dice - fsck still scans all partitions upon boot. They're all reported as "clean", by the way (something I forgot to mention on my first post).
So any other suggestions would be appreciated.

> **raul_ said:**
> C'mon, don't stress about it. "calma hermano" (sorry i'm portuguese, my spanish is lousy. as fas as we are concerned, spanish is a bad copy of portuguese...of course the spanish say the same). There are a lot of duplicate threads. I have posted problems that i later solved on google. Sometimes we just don't know what to ask or search. Don't be afraid to ask twice if you don't understand a reply, or google about it. The forum members will be glad to help the users step by step

I sure hope so. And by the way, your Spanish is better than my Portuguese :P

---

### Post by dannyboy79 on 2006-12-28
do what I suggested, change your fstab so that only root is checked every 30 boots, you change this option using tune2fs and the -i option I believe. You can do man tune2fs to double check this. then for your other partitions, make them 0 in field 6 within your fstab file and then make a cron job to send you an email once a week or once a month to tell you to run fsck on your other partitions. there is a way to envoke fsck upon next bootup but you'll have to gogle that as I am not sure how to do this. i simply umount the partitions and then run fsck on my drives then. the cron thing help thread is here, it's about the 4th or 5th post I believe, where they start talking about it emailing you instead of having the message displayed on the screen. [http://www.ubuntuforums.org/showthread.php?t=213024&highlight=have+cron+send+me+an+email](http://www.ubuntuforums.org/showthread.php?t=213024&highlight=have+cron+send+me+an+email)
good luck.

or PM AgenT and he should be able to help you figure out Bonager as he is the author/developer of it.

---

### Post by Fibonacci on 2006-12-28
> **dannyboy79 said:**
> do what I suggested, change your fstab so that only root is checked every 30 boots, you change this option using tune2fs and the -i option I believe. You can do man tune2fs to double check this.

Fine. Do I change its fstab entry too?

> **dannyboy79 said:**
> then for your other partitions, make them 0 in field 6 within your fstab file and then make a cron job to send you an email once a week or once a month to tell you to run fsck on your other partitions.

I'm reading man crontab right now, but still, any help here would be appreciated.

> **dannyboy79 said:**
> there is a way to envoke fsck upon next bootup but you'll have to gogle that as I am not sure how to do this.

I think that much can be handled by Bonager.

> **dannyboy79 said:**
> i simply umount the partitions and then run fsck on my drives then. the cron thing help thread is here, it's about the 4th or 5th post I believe, where they start talking about it emailing you instead of having the message displayed on the screen. [http://www.ubuntuforums.org/showthread.php?t=213024&highlight=have+cron+send+me+an+email](http://www.ubuntuforums.org/showthread.php?t=213024&highlight=have+cron+send+me+an+email)
good luck.

Thank you!

> **dannyboy79 said:**
> or PM AgenT and he should be able to help you figure out Bonager as he is the author/developer of it.

Will try that too if it doesn't work manually.

---

### Post by Fibonacci on 2006-12-28
Oh, now that I remember it my ISP does block port 25, which seems to be necessary for it to send me emails...

---

### Post by dannyboy79 on 2006-12-28
you would want to leave field 6 within the fstab for roots partition at 1. which means it will be checked at bootup at a set interval. now I am not sure why your computer is checking every single time you bootup, that it NOT the default behaviour of Ubuntu but you can maybe change it back to 30 by using the tune2fs -i 30 option.

as far as the cron thing, I believe you do have to setup either postfix or sendmail. I installed sendmail and told it to use the mail server of my isp I believe. all I know is that I did sudo aptitude install sendmail and that was about it I am pretty sure. I don't run an email server nor do I want to. I simply wanted cron jobs emailed to me because I use cron for running tripwire, rkhunter, and chkrootkit jobs.

This is copied and pasted from that link I provided:
I just thought I'd put in one other suggestion. This may or may not be what you want to do, but with my 'reminder' cron jobs, instead of having it send a message to the screen or console, I have it send me an email message instead.

This is pretty easy to do using the mail command; you just say 
Code:
sh ~/[yourscript] 2>&1 | mail -s "Daily Reminder" [youremail]@[whatever].com

This requires that you have postfix working and that your ISP doesn't block outgoing connections on port 25, or that you've configured postfix to use your ISP's mail server instead.

I use scripts like this to send me reminders (I can even have it send me text messages to my cellphone via email) and also to run batch operations and email me the results at night (e.g. rsync jobs).

The little 'mail' program doesn't get a lot of respect, but it sure is handy.

---

### Post by dannyboy79 on 2006-12-28
> **Fibonacci said:**
> Oh, now that I remember it my ISP does block port 25, which seems to be necessary for it to send me emails...


or that you've configured postfix (or sendmail which is what I did) to use your ISP's mail server instead. remember, I don't have a mail server. i am pretty sure sendmail just uses smtp-server.wi.rr.com to send the mail.

---

### Post by Fibonacci on 2006-12-28
> **dannyboy79 said:**
> you would want to leave field 6 within the fstab for roots partition at 1. which means it will be checked at bootup at a set interval. now I am not sure why your computer is checking every single time you bootup, that it NOT the default behaviour of Ubuntu but you can maybe change it back to 30 by using the tune2fs -i 30 option.

Thank you, I ran tune2fs -c 30 /dev/hdb1, and it seems to have worked.

> **dannyboy79 said:**
> as far as the cron thing, I believe you do have to setup either postfix or sendmail. I installed sendmail and told it to use the mail server of my isp I believe. all I know is that I did sudo aptitude install sendmail and that was about it I am pretty sure. I don't run an email server nor do I want to. I simply wanted cron jobs emailed to me because I use cron for running tripwire, rkhunter, and chkrootkit jobs.

bash: mail: command not found
It seems I need to install another package. Would you know which one?


UPDATE: No it didn't work.
Even after tune2fs, when leaving the last column set to 1 for both the root partition and some other filesystem, the fsck results are displayed for both root AND that other filesystem on every boot. When leaving it at 1 only for the root partition no results are displayed, but I'm pretty sure fsck still checks the root partition upon booting.

---

### Post by Fibonacci on 2006-12-28
Ran Bonager, and forced a fsck on the root partition. It took about twice what it normally takes, also displaying a progress bar and more detailed results than it had done before, when fsck only reported the filesystems as "clean" on every boot.
I think that what it's doing on the boot sequence is not the normal fsck scan, perhaps only a fast scan if such a thing is possible (I have never used fsck before). And /etc/fstab has been the only means of disabling it so far - but then, I think setting the last column on the root partition to 0 is worse than having it fsck every time I boot, right?

---

### Post by dannyboy79 on 2006-12-28
> **Fibonacci said:**
> Thank you, I ran tune2fs -c 30 /dev/hdb1, and it seems to have worked.



bash: mail: command not found
It seems I need to install another package. Would you know which one?


UPDATE: No it didn't work.
Even after tune2fs, when leaving the last column set to 1 for both the root partition and some other filesystem, the fsck results are displayed for both root AND that other filesystem on every boot. When leaving it at 1 only for the root partition no results are displayed, but I'm pretty sure fsck still checks the root partition upon booting.

you have to install sendmail or postfix like I had stated. i thought I read in the man pages for tune2fs that the -i option would set the interval at which fsck would run. I have no idea what the -c option does? so this may be your problem.

---

### Post by dannyboy79 on 2006-12-28
> **Fibonacci said:**
> Ran Bonager, and forced a fsck on the root partition. It took about twice what it normally takes, also displaying a progress bar and more detailed results than it had done before, when fsck only reported the filesystems as "clean" on every boot.
I think that what it's doing on the boot sequence is not the normal fsck scan, perhaps only a fast scan if such a thing is possible (I have never used fsck before). And /etc/fstab has been the only means of disabling it so far - but then, I think setting the last column on the root partition to 0 is worse than having it fsck every time I boot, right?
oh yeah, never ever change the root partition to 0, leave it at 1. i stated in the last post why I believe it is still running at every boot, you need to use the -i option. read man again.

---

### Post by Fibonacci on 2006-12-28
> **dannyboy79 said:**
> you have to install sendmail or postfix like I had stated. i thought I read in the man pages for tune2fs that the -i option would set the interval at which fsck would run. I have no idea what the -c option does? so this may be your problem.

From the man page:
```
       -c max-mount-counts
              Adjust  the  number of mounts after which the filesystem will be checked by e2fsck(8).  If max-mount-counts
              is 0 or -1, the number of times the filesystem is mounted will be disregarded by e2fsck(8) and the  kernel.
(...)
       -i  interval-between-checks[d|m|w]
              Adjust  the maximal time between two filesystem checks.  No postfix or d result in days, m in months, and w
              in weeks.  A value of zero will disable the time-dependent checking.
```

So -i is for time, while -c is for mounts. I think -c 30 is what you intended me to do. Ain't it? But it still runs every boot.

---

### Post by dannyboy79 on 2006-12-28
well here are 2 more things I found when I gogled your main problem. try these out:


2.10 How do I stop my system from fscking on each reboot? Dale Lutz, [email]dal@wimsey.com[/email] 
Q: How do I stop e2fsck from checking my disk every time I boot up. 

A: When you rebuild the kernel, the filesystem is marked as 'dirty' and so your disk will be checked with each boot. The fix is to run: 

rdev -R /zImage 1 

This fixes the kernel so that it is no longer convinced that the filesystem is dirty. 

Note: If using lilo, then add read-only to your linux setup in your lilo config file (Usually /etc/lilo.conf) 


2.11 How to avoid fscks caused by "device busy" at reboot time. Jon Tombs, [email]jon@gtex02.us.es[/email] 
If you often get device busy errors on shutdown that leave the filesystem in need of an fsck upon reboot, here is a simple fix: 

To /etc/rc.d/init.d/halt or /etc/rc.d/rc.0, add the line 

mount -o remount,ro /mount.dir

for all your mounted filesystems except /, before the call to umount -a. This means if, for some reason, shutdown fails to kill all processes and umount the disks they will still be clean on reboot. Saves a lot of time at reboot for me.

otherwise I can't help you anymore. sorry man. like the posts state, it's possible that when your computer is shutting down, it's not doing it properly which causes the fsck every bootup. not sure. I wish I could of more help but I give up. don't forget, gogle is your friend, hell, I found those 2 things and I only spent 10 minutes looking thru the gogle results of stop fsck at every boot up. god luck again.

---

### Post by Fibonacci on 2006-12-28
> **dannyboy79 said:**
> 2.10 How do I stop my system from fscking on each reboot? Dale Lutz, [email]dal@wimsey.com[/email] 
Q: How do I stop e2fsck from checking my disk every time I boot up. 

A: When you rebuild the kernel, the filesystem is marked as 'dirty' and so your disk will be checked with each boot. The fix is to run: 

rdev -R /zImage 1 

This fixes the kernel so that it is no longer convinced that the filesystem is dirty. 

Note: If using lilo, then add read-only to your linux setup in your lilo config file (Usually /etc/lilo.conf) 

/zImage: No file or directory.

> **dannyboy79 said:**
> 2.11 How to avoid fscks caused by "device busy" at reboot time. Jon Tombs, [email]jon@gtex02.us.es[/email] 
If you often get device busy errors on shutdown that leave the filesystem in need of an fsck upon reboot, here is a simple fix: 

To /etc/rc.d/init.d/halt or /etc/rc.d/rc.0, add the line 

mount -o remount,ro /mount.dir

for all your mounted filesystems except /, before the call to umount -a. This means if, for some reason, shutdown fails to kill all processes and umount the disks they will still be clean on reboot. Saves a lot of time at reboot for me.

Fortunately that's not happening to me.

> **dannyboy79 said:**
> otherwise I can't help you anymore. sorry man. like the posts state, it's possible that when your computer is shutting down, it's not doing it properly which causes the fsck every bootup. not sure. I wish I could of more help but I give up. don't forget, gogle is your friend, hell, I found those 2 things and I only spent 10 minutes looking thru the gogle results of stop fsck at every boot up. god luck again.

Well, thanks anyway. I'll see what I can do, and post here my results.

---

### Post by Fibonacci on 2006-12-29
Well, I guess I'm screwed - [this bug has already been reported]("https://launchpad.net/distros/ubuntu/+source/e2fsprogs/+bug/63175"), and not yet fixed.

Thank you all for your help anyway.

---

### Post by dannyboy79 on 2006-12-29
i am sorry to hear this! i suppose if you reboot that much you could always change the fstab entry to 0 or 2 for root but I can't believe you reboot that much that it would annoy you? i actually only reboot my machine once a week. sorry you couldn't get this resolved.

---

### Post by Fibonacci on 2006-12-30
I almost never actually reboot. However, I do *boot* almost once a day, and the long boot time is slightly annoying (but, believe it or not, the Windows boot time is still longer than that :P). I could live with that, especially since no fsck at all would be worse; but I'm concerned that so much fsck'ing would wear the disks too much.

---

### Post by dannyboy79 on 2007-01-01
ok well now you mincing words, My point is why are you BOOTING so much??? Why are you shutting your computer off? Anyway, you could always do what I suggested as far as turning off fsck and run it every once in a while if you're worried about the disk usage.

---

### Post by FLPCGuy on 2007-01-01
> **dannyboy79 said:**
> ...Why are you shutting your computer off? 

Now here's an argument I've seen many times before.  I've been a computer tech for over 16 years and maintained thousands of PC's for their entire lifetime.  I have often been asked whether it is a good idea to turn off a PC when not in use or leave it running.

There is the issue of wear and tear (expansion/contraction) from the considerable temperature change in the CPU and to a lesser extent other components, the wasted time waiting for a reboot (especially Windoze, typically at 4:15 plus prior to 2000/XP), the excessive wear on the power supply and case fan armatures and of course the hard drive spinning at 7200 rpm's on it's shock mounted bearings for 12 to 16 hours unattended.  There is also the issue of staying connected to the Internet unattended all those hours if you are paranoid about security. But these days I'm convinced that one issue trumps all of those.  

Consider how many hundreds of pounds of extra pollutants would be dumped into the atmosphere and all the energy wasted obtaining, transporting, and consuming the energy to generate the extra electricity a thousand idle PCs waste sitting idle overnight, or 10,000, or 100 million.  

In case you hadn't noticed, the arctic is melting.  A huge chunk of ice the size of 42 football fields broke off last week according to news reports.  I'm sitting here on New years Day in North Florida where it is still 75 degrees outside (normally 60) and wondering just how hot it will be by May.

 Please...TURN THE DAMN THING OFF WHEN NOT BEING USED!

BTW   tune2fs -c 30 /dev/hdb1 works for me too.

---

### Post by dannyboy79 on 2007-01-01
> **FLPCGuy said:**
>   Please...TURN THE DAMN THING OFF WHEN NOT BEING USED!

BTW   tune2fs -c 30 /dev/hdb1 works for me too.

You being in charge of computers should very well know that you can't shut off "SERVERS" if you need to access them!!!! Also, I work at a company with over 23,000 full time emplyees and they don't require us to ever shut off our computers and I am talking about business machines NOT servers so if all you say was that big of a deal I am sure that a company with this high a profile would be requiring everyone to shut off their machines don't you think? I run a FTP server as well as a SSH server so that I can adminster it from whereever I am. 

I do agree with you that if a machine is not a server than you should shut it off but obviously people aren't worried about it as much as you.

---

### Post by FLPCGuy on 2007-01-01
> **dannyboy79 said:**
> ...

I do agree with you that if a machine is not a server than you should shut it off but obviously people aren't worried about it as much as you.


That's the problem!   The rest of the world is amazed at how wasteful and inconsiderate we Americans are.

"not being used" doesn't usually apply to servers though I probably could have consolidated about 50 servers into a couple with the virtual server software available these days. *[ How about...Idle cycles are the devils workshop?]*

And you would be surprised at how little common sense has to do with running a corporation or a govt.

---

### Post by mvo on 2007-03-12
> **Fibonacci said:**
> Hello,

I recently noticed that everytime I boot Ubuntu, it runs fsck on all the existing partitions. Of course, it does take some time (not that it's the most of my boot time, but still), so I would like to know: is it really necessary? And if not, how can I prevent fsck from running?

Thanks in advance,

-Fibo

Sorry for this rather late reply, but could you please check the last comment in [https://bugs.beta.launchpad.net/ubuntu/+source/e2fsprogs/+bug/63175](https://bugs.beta.launchpad.net/ubuntu/+source/e2fsprogs/+bug/63175) ? 

If you (or someone else) can still reproduce this problem I would really appreciate the output of:
$ cat /var/log/fsck/*
$ sudo tune2fs -l /dev/-insert-device-here-
$ date

(attached to the bugreport or mailed to me directly).  

Thanks,
 Michael

If you worked around the problem by changing the last column for your root (/) partition from "1" to "0"in /etc/fstab you may have to undo this change to reproduce the problem again.

---

### Post by Fibonacci on 2007-03-13
> **mvo said:**
> Sorry for this rather late reply, but could you please check the last comment in [https://bugs.beta.launchpad.net/ubuntu/+source/e2fsprogs/+bug/63175](https://bugs.beta.launchpad.net/ubuntu/+source/e2fsprogs/+bug/63175) ? 

"This site is accessible by launchpad admins and members of the Launchpad Beta Testers  team only."

> **mvo said:**
> If you (or someone else) can still reproduce this problem I would really appreciate the output of:
$ cat /var/log/fsck/*

```
Log of fsck -C -R -A -a 
Tue Mar 13 03:55:03 2007

fsck 1.39 (29-May-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda1: 220649 files, 3665979/15312004 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hdb5: 122194 files, 1681108/1876384 clusters

Tue Mar 13 03:56:11 2007
----------------
Log of fsck -C -a -t ext3 /dev/hdb1 
Tue Mar 13 03:55:03 2007

fsck 1.39 (29-May-2006)
/dev/hdb1: clean, 296511/2496960 files, 2196210/4992190 blocks

Tue Mar 13 03:55:03 2007
----------------
```

> **mvo said:**
> $ sudo tune2fs -l /dev/-insert-device-here-

```
tune2fs 1.39 (29-May-2006)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          b1c9ae04-50dc-4513-9a52-ef3b7c8a0640
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal filetype needs_recovery sparse_super
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              2496960
Block count:              4992190
Reserved block count:     249609
Free blocks:              2795980
Free inodes:              2200449
First block:              0
Block size:               4096
Fragment size:            4096
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16320
Inode blocks per group:   510
Last mount time:          Tue Mar 13 03:55:03 2007
Last write time:          Tue Mar 13 03:55:03 2007
Mount count:              25
Maximum mount count:      30
Last checked:             Tue Feb 27 13:35:24 2007
Check interval:           0 (<none>)
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
Journal backup:           inode blocks
```

(tried only on the root partition)

> **mvo said:**
> $ date

```
mar mar 13 04:27:46 COT 2007
```

> **mvo said:**
> (attached to the bugreport or mailed to me directly).  

Can't enter the URL you provided, so I'm just posting the results here.

> **mvo said:**
> If you worked around the problem by changing the last column for your root (/) partition from "1" to "0"in /etc/fstab you may have to undo this change to reproduce the problem again.

Nope, my fstab is still intact.

---

