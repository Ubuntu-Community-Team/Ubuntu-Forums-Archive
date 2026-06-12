---
title: "Need help backing up Ubuntu!"
date: 2007-10-25
forum: General Help
---

### Post by UK-Wobbie on 2007-10-25
Hey Ubuntu fans.. ):P

I like to backup my Ubuntu computer on to my server but i am not having any luck on getting a tool to do it with!.. I like to make a full backup of my hard drive linux partition so i can reinstall my Ubuntu computer anytime when it breaks. :lolflag:

I been using some partition tools like.

"Qparted" I like it it's good and all and it do the stuff i like it to do.. But the only thing is! :(
 It will not work on this computer the Graphics are to low so i can not see what i am doing on it. :lolflag: Are they any tools like this? 

"Ghost4Linux" It's good and all but i do not know how to work it!

"PowerSuite 2007" Good for formating but anything like partition copy it do not know what the linux partition is! :(


So i am still looking for a good tool what is easy to use and can do the job of backing up on to a server ](*,)

Any one know anything what can do this?

Thanks :)

---

### Post by chrisccoulson on 2007-10-25
You don't need any fancy tools for copying partition images and stuff, for doing backups. Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

I have backed up and restored my system many times using this method. As an additional note, I exclude all temporary filesystems such as /dev, /var/run and /var/lock from the backup, in addition to the folders/filesystems that the author of that thread already specifies. Just remember to recreate those folders when you restore the backup. Once you've created your tar archive, just copy it onto your server.

The improtant thing is - if you're backing up the whole system, you MUST use a method that preserves permissions on all the files. Recreating permissions on a restored system would not be nice, and you'd probably end uyp re-installing.

If you like graphical tools, have you tried sbackup from the repositories? I've installed it before, but never got round to trying it out, so I'm not sure it's suited for full system backup (if thats what you're after).

I use grsync (GTK frontend for rsync) several times per month for backing up my /home partition to my external USB disk. I'm not sure whether this would be suited to a full system backup.

---

### Post by dasunst3r on 2007-10-25
Personally, I think /home is where it's at, and so I back up only that.  All the system-wide settings and stuff I can easily recreate.

---

### Post by chrisccoulson on 2007-10-25
Thats true, but I find it much quicker to just untar my system archive than to re-install the OS, re-install/compiile all of the apps I use and make all of the system-wide customizations I've got. I've got a system image on DVD that I could restore in 15 minutes if I need to, complete with all the apps I've currently got installed.

But yes, backing up /home is very important. Hence why I do it much more frequently

---

### Post by UK-Wobbie on 2007-10-25
> **chrisccoulson said:**
> You don't need any fancy tools for copying partition images and stuff, for doing backups. Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

I have backed up and restored my system many times using this method. As an additional note, I exclude all temporary filesystems such as /dev, /var/run and /var/lock from the backup, in addition to the folders that the author of that thread specifies. Just remember to recreate those folders when you restore the backup. Once you've created your tar archive, just copy it onto your server.

The improtant thing is - if you're backing up the whole system, you MUST use a method that preserves permissions on all the files.

If you like graphical tools, have you tried sbackup from the repositories? I've installed it before, but never got round to trying it out, so I'm not sure it's suited for full system backup (if thats what you're after).

I use grsync (GTK frontend for rsync) several times per month for backing up my /home partition to my external USB disk. I'm not sure whether this would be suited to a full system backup.

Hey thanks for your reply it has been a big help :)

i like something that is easy to use and do the job good as am not that good on some of the partition tools what are now out.. I like something that i can put in my CD/DVD drive and boot it up on computer start up.. I will have a go on that sbackup and see what it is like.. THANKS FOR YOUR HELP. :D

---

### Post by por100pre1 on 2007-10-25
I use Grsync to backup /home folder only and APTonCD to backup the installed program packages.

```
sudo aptitude install aptoncd grsync
```

---

### Post by chrisccoulson on 2007-10-25
No probs! Let me know what you decide on and how you get on

---

### Post by chrisccoulson on 2007-10-25
> **por100pre1 said:**
> I use Grsync to backup /home folder only and APTonCD to backup the installed program packages.

```
sudo aptitude install aptoncd grsync
```

How do you get on with APTonCD? Will it split the backup across multiple CDs/DVDs if your list of packages doesn't fit on a single disk? I've never tried using it before

---

### Post by chrisccoulson on 2007-10-25
Strangely enough, there's a thread over in the Hardy development forums about backup tools. I saw this link there: [https://wiki.ubuntu.com/TimeVault]("https://wiki.ubuntu.com/TimeVault").

Not sure how much use that would be...

---

### Post by UK-Wobbie on 2007-10-25
> **por100pre1 said:**
> I use Grsync to backup /home folder only and APTonCD to backup the installed program packages.

```
sudo aptitude install aptoncd grsync
```

Hey por100pre1,
I have had a go using aptoncd and it did work on some Ubuntu versions and on some of the new ones.. when it use to be done on the cd instill from "Synaptic Package Manager" It use to say that some of the files was not compatible.. So i do not use it any more :( Thanks for telling me anyway :)


chrisccoulson,
The sbackup looks head to use and it do not backup ever file i got :( .. I like something that can backup everything! Games,Music,Desktop,System files,
The lot :lolflag:

Thanks for telling me about sbackup :)

All i can do is keep on looking :lolflag: Thanks for your helps ;)

---

### Post by chrisccoulson on 2007-10-25
If you want to backup absolutely everything, then i highly recommend looking through that howto for  creating the tar archive. I have no experience with graphical tools that can do this easily...

---

### Post by UK-Wobbie on 2007-10-25
> **chrisccoulson said:**
> If you want to backup absolutely everything, then i highly recommend looking through that howto for  creating the tar archive. I have no experience with graphical tools that can do this easily...

Ok i will have a look!.. Thanks for your help you have been a big help on all of this. :mrgreen:

RW

---

### Post by por100pre1 on 2007-10-25
> **chrisccoulson said:**
> How do you get on with APTonCD? Will it split the backup across multiple CDs/DVDs if your list of packages doesn't fit on a single disk? I've never tried using it before

Yes, it will split the packages on multiple DVDs or CDs. Here I just use one DVD+RW. The program just create the ISO(s), you burn it (them) with your favorite burning program. For burning I use k3b.

---

### Post by tech9 on 2007-10-25
> **UK-Wobbie said:**
> Hey Ubuntu fans.. ):P

I like to backup my Ubuntu computer on to my server but i am not having any luck on getting a tool to do it with!.. I like to make a full backup of my hard drive linux partition so i can reinstall my Ubuntu computer anytime when it breaks. :lolflag:

I been using some partition tools like.

"Qparted" I like it it's good and all and it do the stuff i like it to do.. But the only thing is! :(
 It will not work on this computer the Graphics are to low so i can not see what i am doing on it. :lolflag: Are they any tools like this? 

"Ghost4Linux" It's good and all but i do not know how to work it!

"PowerSuite 2007" Good for formating but anything like partition copy it do not know what the linux partition is! :(


So i am still looking for a good tool what is easy to use and can do the job of backing up on to a server ](*,)

Any one know anything what can do this?

Thanks :)

see link...
[http://ubuntuforums.org/showthread.php?p=3631315#post3631315](http://ubuntuforums.org/showthread.php?p=3631315#post3631315)

---

### Post by UK-Wobbie on 2007-10-25
> **tech9 said:**
> see link...
[http://ubuntuforums.org/showthread.php?p=3631315#post3631315](http://ubuntuforums.org/showthread.php?p=3631315#post3631315)

Thanks tech9,

I have to give that a go sometime that may help me! :)

---

### Post by tech9 on 2007-10-25
> **UK-Wobbie said:**
> Thanks tech9,

I have to give that a go sometime that may help me! :)

no problem :)

Cheers

T9

---

