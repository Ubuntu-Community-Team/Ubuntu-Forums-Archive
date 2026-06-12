---
title: "problems with GParted"
date: 2007-07-15
forum: General Help
---

### Post by zerolink on 2007-07-15
well, the thing is that every time I start gparted, every time I apply a change to the partitions, gparted tries to mount all the partitions. Thats very annoying, and when I'm resizing a partition, It gives me an error, It says that the selected partition Its mounted, but GParted just mount it.

what's going on?, I gues this is not normal.


thx..

---

### Post by merlinus on 2007-07-15
Are you using the gparted live cd?

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by zerolink on 2007-07-17
no, no, I'm using gparted directly from ubuntu, but that does'n have anything to do with the problem , does it?

and, the problem is that gparted is mounting my partitions automaticly; if I would be running from the livecd It couldn't mount the partitions cause it wouldn't be in linux (well it would be cause of it use the linux kernel, but you understand me...;))

---

### Post by merlinus on 2007-07-17
The ubuntu version does not have all of the new features and capabilities.

Use the gparted live cd, and see if that makes a difference.

-merlin

---

### Post by zerolink on 2007-07-17
mmm.... you don't understand, that doesn't have anything to do with my problem, why dont you read my first post. I think that what's happening with my gparted it is not normal, and I don't need more features or capabilities...

the problem is something that shouldn't be happening (read first post).

---

### Post by merlinus on 2007-07-17
I did read your posts, and suggested a superior version of gparted.

It is YOU who is not listening.

If you try the latest version and the same thing occurs, then perhaps someone will be willing to assist.

Simply complaining and being unwilling to try something different will not likely get you anywhere.

And if you do not wish assistance, don't post in the General Help forum, and instead file a bug report at launchpad.

-merlin

---

### Post by ramjet_1953 on 2007-07-17
What your problem is, is that you CANNOT make any changes to a mounted HDD.

It's like trying to change a wheel on a car that is still being driven.

Take the advice that has been given to you and download the GParted live CD iso, burn it to a CD SLOWLY and then boot from that CD.

You can get the iso from here: [http://gparted.sourceforge.net](http://gparted.sourceforge.net)

Regards,
Roger :cool:

---

### Post by mali2297 on 2007-07-22
> **zerolink said:**
> well, the thing is that every time I start gparted, every time I apply a change to the partitions, gparted tries to mount all the partitions. Thats very annoying, and when I'm resizing a partition, It gives me an error, It says that the selected partition Its mounted, but GParted just mount it.

what's going on?, I gues this is not normal.


thx..

Have you tried to disable automount drives in
System --> Preferences --> Removable Drives and Media?

I'm not certain but it might enable you to make changes to partitions that you're not using. I agree that you should be able to do that without a live CD. If you want to make changes to the present root partition, you must however use a live CD or boot from another partition.

---

### Post by mdurham on 2007-07-22
My gparted does the same thing in Gutsy, it mounts the unmounted partitions and then tells me it can't continue with the operation on a mounted partition. Bloody crazy! I don't want the partitions mounted anyway.

---

### Post by zerolink on 2007-07-23
well, it seems like almost no one understand my problem, at list I'm not alone: mdurham has exactly the same problem than me. 

For those who keep tellin me how the mount and unmount stuff works, like ramjet_1953, i have to tell them that I know that, I know about that stuff, I KNOW that you can't make changes to a mounted partition. 
Is that so hard to understand what the problem is?  ; lets put it this way: I have the root ext3 partition, and another ext3 unmounted, I start gparted, and the first thing it does is MOUNT that unmounted and unused partition, so thats the annoying; but i want to work with that partition, so I UNMOUNT it, i made the changes and click "Apply changes", so it start to work on the partition, but in some point of the work it mount that partition that is working with, there is when it gives the error that you CANNOT make any changes to a mounted HDD.


well, I hope you can see that I make no mistake, and there should be no need to use the livecd edition of gparted.

_**mdurham:**_
If i solve the problem I'll send you a message.

---

### Post by dabl on 2007-07-23
> **zerolink said:**
> 
well, I hope you can see that I make no mistake

I agree -- it looks like you have followed the procedure correctly, made no mistakes, and there must be some bug in the Ubuntu implementation of GParted. So on this, we'll say "You were right!"

>  and there should be no need to use the livecd edition of gparted.

Well, "should be no ..." and "is no ..." are two different states of reality, aren't they?  If it's a bug in the Ubuntu installer's implementation of GParted, then it probably does not exist in the GParted Live CD, and you could have had that disk partitioned 5 days ago.  That's quite a bit of time to lose, just to be right, at least in my world. :(

---

### Post by stchman on 2007-07-23
> **zerolink said:**
> well, the thing is that every time I start gparted, every time I apply a change to the partitions, gparted tries to mount all the partitions. Thats very annoying, and when I'm resizing a partition, It gives me an error, It says that the selected partition Its mounted, but GParted just mount it.

what's going on?, I gues this is not normal.


thx..

That can be corrected by going to System--->Preferences--->Removable drives and media.

Uncheck the mount partitions portion under the Storage tab.

---

### Post by dannyboy79 on 2007-07-23
is he saying that he's running from a livecd? If not, then that's his problem. You can't boot into ubuntu running from the hard drive because it needs the / partition to be mounted in order for Ubuntu to work! So I am honestly surprised that it's letting you unmount it to begin with

If that's not true, and you're saying that you're using a live cd, then you make sure that your partition's aren't mounted, then you open gparted from the Gutsy Livecd, than you make changes to partitions, then you hit apply, then it says that you can't make changes on a moutned paritition, than I agree, that's a problem! Gparted should NOT be automounting your partitions EVEN if you have the Mount Removable Drives and MEdia checked unless of course your / partition is located on a usb external drive or similar.

---

### Post by zerolink on 2007-07-23
I'm am not running from the livecd, BUT I AM NOT MAKING CHANGES TO THE ROOT PARTITION, it's another partition.

---

### Post by dannyboy79 on 2007-07-24
> **zerolink said:**
> I'm am not running from the livecd, BUT I AM NOT MAKING CHANGES TO THE ROOT PARTITION, it's another partition.


you exact words from previous page, "lets put it this way: I have the root ext3 partition, and another ext3 unmounted,"

I would say that you are trying to unmount the root partition. What's the exact mount location of the partition that you label, "another ext3" and maybe we can help.

---

### Post by zerolink on 2007-07-24
OMFG!!    

I am NOT tryiing to unmount the root partition!! 
why can't you understand the problem: gparted is mounting the unmounted partition without my agree, without i even need them to be mounted, instead I need them (the unmounted partitions) to keep unmounted so I can make changes on them.


at this time I have only one ext3 partition( the root partition) and I keep it mounted , I wont be able to unmount it anyway; I have another , an ext2 partition, its unmounted, and everytime I start gparted, or I made changes to such partition , I keeps mounting it, that is the problem, it's bothering me very much...


thx for your concern...

---

### Post by fredj on 2007-07-24
Well we all understand the problem, what we don't understand is what you want to do. Are you more concerned 
with resizing your partition or with getting something that doesn't work to work. If it is the latter then it looks
like you are on your own.

Other people here have made the mistake of thinking that you just want a way to resize a partition that 
ACTUALLY works (a natural mistake on their part) but obviously this isn't what you want.
File a bug report!

---

### Post by mdurham on 2007-07-25
zerolink, why not start a new/different thread on this as it appears that the current contributors can't read.
Cheers, Mike

---

### Post by dannyboy79 on 2007-07-25
> **mdurham said:**
> zerolink, why not start a new/different thread on this as it appears that the current contributors can't read.
Cheers, Mike

actually I can read just fine, and as you saw above, I actually quoted him stating that he was trying to unmount his / partition. Instead of trolling and telling us we can't read, why don't you actually try to help. Otherwise it benefits no one when you post as you have.

zerolink, I suggest that you file a bug report. As long as you're actually unmounting the partition prior to going into Gparted from within a Hard Drive installed Ubuntu, then you're correct, Gparted should NOT be remounting the partition UNLESS there's some other activity going on in the background that is causing the partition to be remounted.

---

### Post by mdurham on 2007-07-25
dayyboy79, I should have used the word 'understand' and not 'read', it wasn't a troll!
I get the impression from > OMFG!!

I am NOT tryiing to unmount the root partition!!  that he is very frustrated trying to get his message across about his problem and nobody seems to understand it. I think I understand but don't have any solution to offer. All I could do was say that I have the same problem so that he would know he is not alone. I can't imagine why Gparted automatically mounts partitions when not instructed to.
Cheers, Mike

---

### Post by dannyboy79 on 2007-07-26
there already is a bug about this. It states it's with Xubuntu Feisty but I wouldn't be surprised if others experience it.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107259](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107259)

---

### Post by louieb on 2007-07-26
> **zerolink said:**
> mmm.... you don't understand, that doesn't have anything to do with my problem, why dont you read my first post... is something that shouldn't be happening (read first post).
I read your post.  Calm down zerolink .May not be correct or it could be it was designed to work that way. Thats how it has worked since Dapper. Life is tough but you have to deal with it.
>  what's going on?, I gues this is not normal. Is not GParted thats mounting the partition Its the hardware detection module. It sees activity on a storage device that not mounted and without thinking it runs some code that says oh I need to mount this and it does. 

Now how to deal with it.[LIST]
[*]Go to System>Preferences>Removable drives. And uncheck the  auto mount options.
[*]Use the Gparted Live CD or System Rescue live CD.
[*]File a bug report and wait until Gutsy comes out an see if someone has gotten  around to changing the way it works.[/LIST]

---

### Post by zerolink on 2007-07-28
> **louieb said:**
> 
 Is not GParted thats mounting the partition Its the hardware detection module. It sees activity on a storage device that not mounted and without thinking it runs some code that says oh I need to mount this and it does. 



That really make very sense to me, I'm trying to solve it right now.

thx

---

### Post by benx009 on 2007-07-28
> **zerolink said:**
> well, the thing is that every time I start gparted, every time I apply a change to the partitions, gparted tries to mount all the partitions. Thats very annoying, and when I'm resizing a partition, It gives me an error, It says that the selected partition Its mounted, but GParted just mount it.

what's going on?, I gues this is not normal.


thx..

yes this happens to me on a ubuntu feisty live session too.  have no idea why though...

---

### Post by rbmorse on 2007-07-28
None of which changes the fact that the easiest way to ***actually do what you want to do*** is use the gParted LiveCD. The rest is all bug report and doesn't do anything to your partitions

---

### Post by Commodore Guff on 2007-08-01
I just experienced the same problem, and boy, I got a kick out of this thread.

There was one helpful reply, though (well, another one with the same instructions, too):  just change the system preferences to not automatically mount drives.  This would seem to be a problem with that, not gparted.

One should not need a LiveCD just to manage non-root filesystems.

---

### Post by dannyboy79 on 2007-08-02
> **Commodore Guff said:**
> I just experienced the same problem, and boy, I got a kick out of this thread.

There was one helpful reply, though (well, another one with the same instructions, too):  just change the system preferences to not automatically mount drives.  This would seem to be a problem with that, not gparted.

One should not need a LiveCD just to manage non-root filesystems.

he's not saying that you do, he's merely pointing out that if the person wants to get the job done, then use the livecd. complaining about it and whining in here doesn't help. File a bug report, use another method and move on.

---

### Post by Commodore Guff on 2007-08-02
> **dannyboy79 said:**
> he's not saying that you do, he's merely pointing out that if the person wants to get the job done, then use the livecd. complaining about it and whining in here doesn't help. File a bug report, use another method and move on.
The thing is, no one even attempted to *solve* the problem (save for the one or two users I mentioned).  It was an extremely easy fix, too.

---

### Post by dannyboy79 on 2007-08-03
well if the "problem" was to uncheck the auto mount removeable media, then obviously the "problem" is NOT with Gparted as the title of this thread states.

---

