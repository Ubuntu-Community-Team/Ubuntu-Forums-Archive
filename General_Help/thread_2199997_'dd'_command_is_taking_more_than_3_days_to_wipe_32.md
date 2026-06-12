---
title: "'dd' command is taking more than 3 days to wipe 320GB HDD"
date: 2014-01-17
forum: General Help
---

### Post by amjjawad on 2014-01-17
Hi,

I am using 'dd' command to wipe a 320GB HDD and write 0's using Lubuntu 13.10 LiveUSB.

It has been 'more' than 3 days now and there is absolutely no hope the process will finish any time soon. The machine does response to anything as far as I can tell but I don't want to do anything and waste the 3 days of waiting. 

My Q is: is this normal? I have done this before (not with 320GB though) and it never took all these days so what do I have to do? suggestions are highly appreciated.

Thank you!

---

### Post by CaptainMark on 2014-01-17
Well a good start would be to tell us what command you used, if it uses /dev/random which is a popular one to totally blitz a hard drive then this will only work whilst you are using the machine because /dev/random generates entropy from mouse and keyboard input (and various other user controlled events) so if your doing nothing on the machine it can't continue.

---

### Post by amjjawad on 2014-01-17
> **CaptainMark said:**
> Well a good start would be to tell us what command you used, if it uses /dev/random which is a popular one to totally blitz a hard drive then this will only work whilst you are using the machine because /dev/random generates entropy from mouse and keyboard input (and various other user controlled events) so if your doing nothing on the machine it can't continue.

Hi and thanks for your reply.

```
dd if=/dev/zero of=/dev/sdX
```

---

### Post by Topsiho on 2014-01-17
I can't answer your question, but either your information is incomplete or it is wrong.
You state that the output goes into /dev/sdX, where it should be the /dev that represents the hard disk you want to wipe (be very careful here, and first determine whether this is /dev/sdb or /dev/sdc or so, so you don't wipe the disk that contains your system).

The dd command is dangerous and should be used very carefully.

Topsiho

---

### Post by amjjawad on 2014-01-17
> **Topsiho said:**
> I can't answer your question, but either your information is incomplete or it is wrong.
You state that the output goes into /dev/sdX, where it should be the /dev that represents the hard disk you want to wipe (be very careful here, and first determine whether this is /dev/sdb or /dev/sdc or so, so you don't wipe the disk that contains your system).

The dd command is dangerous and should be used very carefully.

Topsiho

Hi and thanks for posting.

Because it is dangerous (which I'm fully aware of), I didn't wish to replace X with the correct drive letter and decided to choose the general "X" instead. I don't want anyone to try that and then everything will disappear.

There is only one drive so I'd assume you know now what I am talking about :)

---

### Post by jeanjd63 on 2014-01-17
Hello

You can try :
**[COLOR=#000000][FONT=Ubuntu Mono]dd if=/dev/zero of=/dev/sdX [/FONT][/COLOR]bs=4096**

---

### Post by coffeecat on 2014-01-17
I think your 3 days have been wasted already - zeroing a 320GB drive should take hours, not days.

If you want to start over and get some feedback from the terminal, I'd suggest using shred. There are ways of getting verbose output from dd I believe, but not straightforwardly, whereas shred has a -v option built in. For a single pass writing zeroes, you could do it this way:

```
sudo shred -vzn 0 /dev/sdX
```

Obviously, substitute your actual device for sdX. The Options:

-v - verbose output - you can actually see whether something is happening.
-z - add a final overwrite with zeros.
-n - overwrite N times instead of the default (3). If you make this zero, then you get just the one pass with zeroes.

---

### Post by amjjawad on 2014-01-17
> **jeanjd63 said:**
> Hello

You can try :
**[COLOR=#000000][FONT=Ubuntu Mono]dd if=/dev/zero of=/dev/sdX [/FONT][/COLOR]bs=4096**

Hi and thanks for posting.

I have always tried 'dd' this way:
```
dd if=/dev/zero of=/dev/sdX 
```
And it always worked.

It is just this time, something is odd and wrong.

---

### Post by amjjawad on 2014-01-17
> **coffeecat said:**
> I think your 3 days have been wasted already - zeroing a 320GB drive should take hours, not days.

Hi and thanks for posting.

Seriously? oh, this is really bad. I should have asked this 2 days ago :(
How can we tell whether it is doing nothing or not? anyway to check without cancelling or stopping it?

> If you want to start over and get some feedback from the terminal, I'd suggest using shred. There are ways of getting verbose output from dd I believe, but not straightforwardly, whereas shred has a -v option built in. For a single pass writing zeroes, you could do it this way:

```
sudo shred -vzn 0 /dev/sdX
```

Obviously, substitute your actual device for sdX. The Options:

-v - verbose output - you can actually see whether something is happening.
-z - add a final overwrite with zeros.
-n - overwrite N times instead of the default (3). If you make this zero, then you get just the one pass with zeroes.

If that will work 'faster' and 'better' than my way, I'm indeed interested to try this one.

I am sorry, I might be mistaken for not mentioning this but the reason why I am trying 'dd' is there are 1421 bad sectors and that machine is running Windows but it was keep stop working and my neighbour gave it to me to check and I was trying to convert it to Linux but thought to fix the bad sector before.

Yes, I have tried 'dd' with a very very old 4.1 GB HDD which had bad sector and it got fixed with 'dd', the same command that I am trying with this 320GB HDD.

So, what shall I do now?

---

### Post by slooksterpsv on 2014-01-17
Are you running dd or sudo dd or are you running dd as root? Without root or acting as root (sudo) it won't do anything as root is needed to fully access the drive. A plain user can only access what permissions it was given to which isn't block level writing.

---

### Post by amjjawad on 2014-01-17
> **slooksterpsv said:**
> Are you running dd or sudo dd or are you running dd as root? Without root or acting as root (sudo) it won't do anything as root is needed to fully access the drive. A plain user can only access what permissions it was given to which isn't block level writing.

Of course I'm using 'sudo', otherwise, it would never be executed on the first place ;)
If you try 'dd' without 'sudo', it will never work.

I didn't mention that because I thought it is very obvious and no need to mention that. Sorry if that caused some confusion.

---

### Post by slooksterpsv on 2014-01-17
Not a problem just wanted to work from the basics up. IIRC last time I tried to wipe a drive I had, executing just dd if of without the bs portion didn't work, or it just sat there. I wonder if dd changed to where its now a requirement to specify some block size for an empty device where as dd'ing an iso may take the ISOs layout and lay it out according to that.

---

### Post by Highup on 2014-01-17
[SIZE=2]Greetings,

you can try following:
- Open a second terminal and get the Process id of your job.
- Then use the command:
```
kill -USR1 <process id>
```
to show you information.

Hope this helps.[/SIZE]

---

### Post by amjjawad on 2014-01-17
> **coffeecat said:**
> I think your 3 days have been wasted already - zeroing a 320GB drive should take hours, not days.

If you want to start over and get some feedback from the terminal, I'd suggest using shred. There are ways of getting verbose output from dd I believe, but not straightforwardly, whereas shred has a -v option built in. For a single pass writing zeroes, you could do it this way:

```
sudo shred -vzn 0 /dev/sdX
```

Obviously, substitute your actual device for sdX. The Options:

-v - verbose output - you can actually see whether something is happening.
-z - add a final overwrite with zeros.
-n - overwrite N times instead of the default (3). If you make this zero, then you get just the one pass with zeroes.

Hi,

I have stopped 'dd', rebooted and now, I am running the command you suggested.

Let's see if that will make any difference and fix the original issue.

Thank you!

---

### Post by 3rdalbum on 2014-01-17
DD will not fix bad sectors, sorry. 1,400 bad sectors is a sign that the drive has failed aand can't be repaired.

That's why DD would not finish. It was trying to write to disk and being slowed down by the failed writes. Want confirmation? Try DD again, but keep an eye on the output of dmesg. It will spit out a stream of errors.

The disk is dead. Bin it.

---

### Post by amjjawad on 2014-01-17
> **amjjawad said:**
> Hi,

I have stopped 'dd', rebooted and now, I am running the command you suggested.

Let's see if that will make any difference and fix the original issue.

Thank you!

Hi again,

It is over now, how can I check the HDD whether it has bad sector still or it is fine now? of course, after using 'shred', new partition table must be created and that is done. But I didn't create any partition yet, just a partition table.

What is the 'best' way to check the HDD now?

If we got a confirmation from the next test that the HDD is still failure, I will tell my neighbour so he will consider to replace the HDD.

---

### Post by amjjawad on 2014-01-17
Okay, I guess I found the answer for my own Q.

I am trying to install Lubuntu 13.10 from the same LiveUSB I was using and it is stuck now on "creating ext4 file system..."

I guess I have no other choice but to tell my neighbour the bad news :(

Sorry, not trying to insist or anything but is there any any chance at all to fix the bad sectors?

---

### Post by slooksterpsv on 2014-01-17
You should be able to run badblocks to have it search for an mark bad blocks on the disk.

Another recommendation is to download and install gparted, run it and partition the drives manually instead of the installer changing the partition scheme.

---

### Post by fantab on 2014-01-17
> **3rdalbum said:**
> DD will not fix bad sectors, sorry. 1,400 bad sectors is a sign that the drive has failed aand can't be repaired.

That's why DD would not finish. It was trying to write to disk and being slowed down by the failed writes. Want confirmation? Try DD again, but keep an eye on the output of dmesg. It will spit out a stream of errors.

The disk is dead. Bin it.

> **amjjawad said:**
> .......... is there any any chance at all to fix the bad sectors?

HDD manufacturer's have their own tools to fix bad sectors, but most of these tools are Windows dependent.
So you can check the HDD manufacturer's webpage for such tools and try them from Windows PC.

But seriously, 1,400 bad sectors is not good.

Good Luck.

---

### Post by amjjawad on 2014-01-18
> **slooksterpsv said:**
> You should be able to run badblocks to have it search for an mark bad blocks on the disk.

I had to give up so I shall try this one, let's see if that will make any difference :)
Thanks for positing! 

> Another recommendation is to download and install gparted, run it and partition the drives manually instead of the installer changing the partition scheme.
I don't think that will fix the bad sectors/blocks. The problem is not to install or not, the current problem is to whether be able to fix the bad sectors or not.

Thank you!

---

### Post by amjjawad on 2014-01-18
Hi,

I did run:
```
sudo badblocks -sv /dev/sda1
```

Before that, I have created one partition (ext4) because it seems the commands I tired didn't work unless there is a partition.

It is working, I can see the progress but super slow. 6hours and 45mins so far and it is only 4.86% done.

---

### Post by Elfy on 2014-01-19
At some point you have to decide whether to give up and get them to put their hand in their pocket. 

Appears that you've been fiddling about with this drive for almost a week - perhaps the time has arrived ;)

[http://superuser.com/questions/240641/how-long-does-badblocks-take-on-a-1tb-drive](http://superuser.com/questions/240641/how-long-does-badblocks-take-on-a-1tb-drive)

---

### Post by Topsiho on 2014-01-19
Why not check the hard disk using the disk tool or disk utility, or whatever it is called? (I use the Dutch version of Ubuntu, in which it is called Schijfgereedschap).
Then you see, if the disk supports S.M.A.R.T. immediately whether the disk is healthy or not (it is not, I bet).
If I had a disk with 1400 bad blocks, I would ditch it. And: (mechanical) hard disks are very cheap these days (where I live).

Topsiho

---

### Post by amjjawad on 2014-02-05
Hi,

I forgot to update this thread.

HDD is dead and they brought me new one and the machine is up and running now. They insisted to have Windows and I insisted to show them Linux so we agreed to dual-boot Windows 7 with Xubuntu 12.04.3 :)

Thank you everyone!

P.S.
There was another machine with a HDD that has lots of Bad Sector but I managed to use badblock to find the bad ones and never used it. The bad sectors are at the last 20GB of the HDD and it's been many weeks that machine is up and running. As for this HDD in this thread, it is dead. Nothing can be done. The first 20GB is fine but after that, there are problems.

---

