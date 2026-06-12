---
title: "[SOLVED] ISO size for remastersys"
date: 2008-02-22
forum: General Help
---

### Post by meazz1 on 2008-02-22
I used the remastersys and created an ISO backup.
The ISO is only 9.9 mb.
I know for sure that all my applications and the distro should be way more than 9.9 mb.

I ran this command to create the image. 

[PHP]sudo remasystesys backup[/PHP]

any advise is appreciated.

---

### Post by meazz1 on 2008-02-22
bump !! any taker?

---

### Post by wjston on 2008-02-23
> **meazz1 said:**
> I used the remastersys and created an ISO backup.
The ISO is only 9.9 mb.
I know for sure that all my applications and the distro should be way more than 9.9 mb.

I ran this command to create the image. 

[PHP]sudo remasystesys backup[/PHP]

any advise is appreciated.

I am also trying to backup my system. I ended up with an iso size of 11MB after my system backup, which took approximately 2 hours. I tried the distribution option and ended up with an iso size of 1.7GB. The distribution copy boots ok; however, there is no option to install that I can see. My intent is to create a backup in the event I have to re-install and if I can resolve this issue, I will post back with an update.

---

### Post by wjston on 2008-02-23
> **wjston said:**
> I am also trying to backup my system. I ended up with an iso size of 11MB after my system backup. My intent is to create a backup in the event I have to re-install and if I can resolve this issue, I will post back with an update.

Good News. I have just successfully completed a working backup of my system. I read a few posts by the developer and I realized I hadn't removed my video files. Mkisofs is limited to a 4.7GB file size and if you have any large video files on your drive, you will not be able to create a successful backup. Try saving any large files to a separate drive first, and then try recreating your backup. If this is not possible, I would suggest burning them to DVD and then deleting them from the system (make sure you empty the trash can also) prior to creating the backup. Hope this helps.

---

### Post by meazz1 on 2008-02-24
> **wjston said:**
> Good News. I have just successfully completed a working backup of my system. I read a few posts by the developer and I realized I hadn't removed my video files. Mkisofs is limited to a 4.7GB file size and if you have any large video files on your drive, you will not be able to create a successful backup. Try saving any large files to a separate drive first, and then try recreating your backup. If this is not possible, I would suggest burning them to DVD and then deleting them from the system (make sure you empty the trash can also) prior to creating the backup. Hope this helps.

I have no video files and I am taking the "backup" command.
I have tried atleast four times and still ended up with 10 or 11 mb ISO size.

Need some help here.

---

### Post by wjston on 2008-02-24
> **meazz1 said:**
> I have no video files and I am taking the "backup" command.
I have tried atleast four times and still ended up with 10 or 11 mb ISO size.

Need some help here.

How much data is stored in your home folder? If that is large, it could be causing your issues. If not, I would then go to the developer's site and post your problem with remastersys there. He is very quick to respond and may be able to resolve this quickly. Here is the link and if it is your first time there, you will have to register to post: [http://loscompanion.com/forums/index.php?board=58.0](http://loscompanion.com/forums/index.php?board=58.0)

This is the link to my post and resolution: [http://loscompanion.com/forums/index.php?PHPSESSID=fad6de3dc71bc69631bf3fd6cd3b9ba5&topic=3111.0](http://loscompanion.com/forums/index.php?PHPSESSID=fad6de3dc71bc69631bf3fd6cd3b9ba5&topic=3111.0)

---

### Post by UK-Wobbie on 2008-02-24
> **meazz1 said:**
> I used the remastersys and created an ISO backup.
The ISO is only 9.9 mb.
I know for sure that all my applications and the distro should be way more than 9.9 mb.

I ran this command to create the image. 

[PHP]sudo remasystesys backup[/PHP]

any advise is appreciated.

I am getting the same thing :lolflag:
It was 9.4MBs the ISO :(
And my System it self is 19GBs!

I was like hmm 9.4MBs is that GBs, So i burned it to a disk to have a look and it was fast on buring so i know it was not right!
So i do not know what to do now only keep having a go and see what i get at the end! :(
But i do not know what to do if the ISO image did come out as something like 19GBs, How can i burn that to a 4GB DVD disk? lol

I do not know but as it got something to do with the size of your hard drive?
As the DVD is only 4GBs, If you got a lot of work on your computer.
It may have problems putting all the data in to the DVD that's why it's taking ages on doing so and not working!
Coming out as dumb ISO size numbers lol

---

### Post by meazz1 on 2008-02-25
> **wjston said:**
> How much data is stored in your home folder? If that is large, it could be causing your issues. If not, I would then go to the developer's site and post your problem with remastersys there. He is very quick to respond and may be able to resolve this quickly. Here is the link and if it is your first time there, you will have to register to post: [http://loscompanion.com/forums/index.php?board=58.0](http://loscompanion.com/forums/index.php?board=58.0)

This is the link to my post and resolution: [http://loscompanion.com/forums/index.php?PHPSESSID=fad6de3dc71bc69631bf3fd6cd3b9ba5&topic=3111.0](http://loscompanion.com/forums/index.php?PHPSESSID=fad6de3dc71bc69631bf3fd6cd3b9ba5&topic=3111.0)

Thanks for your reply.

I looked around in the developer's site and I think I know what the issue is.
I have a 160 gig of 2nd hdd that holds music. I also have the symbolic link shortcut on my desktop for that 160 gig drive. I think this drive is causing the problem.

I will unmount the the drive and than try to create a image again.

Any advice, does this sound like a reasonable path ?

---

### Post by UK-Wobbie on 2008-02-25
> **meazz1 said:**
> Thanks for your reply.

I looked around in the developer's site and I think I know what the issue is.
I have a 160 gig of 2nd hdd that holds music. I also have the symbolic link shortcut on my desktop for that 160 gig drive. I think this drive is causing the problem.

I will unmount the the drive and than try to create a image again.

Any advice, does this sound like a reasonable path ?

I have got a 160GB and a 2nd 80GB hard drive,
The 1st time i did a backup of my System it worked!  And i have not got a lot of stuff in the 2nd drive only some files.

The 2st time i did a backup it stopped working, And the ISO image is 9.4Mbs.
And i know what may have made it like that!  Having a lot of stuff on the 1st drive, The 160 GB one.

I say it's Wine installing all the games :lolflag: Saying putting a 19GB of files on to a 4GB disk it will not fit!

So that may be why it's not working.

Have you got a lot of programs on your 1st drive?
As the tool with not backup any files on 2nd drives.

---

### Post by meazz1 on 2008-02-25
Yes, there are a lot of apps installed.
I will verify the size of the 1st hdd tonight when I get home.

---

### Post by wjston on 2008-02-25
> **meazz1 said:**
> Thanks for your reply.

I looked around in the developer's site and I think I know what the issue is.
I have a 160 gig of 2nd hdd that holds music. I also have the symbolic link shortcut on my desktop for that 160 gig drive. I think this drive is causing the problem.

I will unmount the the drive and than try to create a image again.

Any advice, does this sound like a reasonable path ?

Your welcome.
I think that would be a reasonable assumption. The developer's directions are to create an image of a fresh install. I would try unmounting your extra drive and post your results.

---

### Post by meazz1 on 2008-02-26
> **wjston said:**
> Your welcome.
I think that would be a reasonable assumption. The developer's directions are to create an image of a fresh install. I would try unmounting your extra drive and post your results.

I guess, it's too late for me to create a "Backup" now so late in the game.

I moved all my data and music to the 2nd hdd and freed up about 10 gig.

still the primary hdd size is 7.8 gig and I don't know what else I can move.

So I am stuck here.

---

### Post by wjston on 2008-02-26
> **meazz1 said:**
> I guess, it's too late for me to create a "Backup" now so late in the game.

I moved all my data and music to the 2nd hdd and freed up about 10 gig.

still the primary hdd size is 7.8 gig and I don't know what else I can move.

So I am stuck here.

Have you tried to make a backup? My primary is 6.4 Gig and I was able to create my backup - 1.7 GB  onto a DVD.

---

### Post by meazz1 on 2008-02-27
> **meazz1 said:**
> Thanks for your reply.

I looked around in the developer's site and I think I know what the issue is.
I have a 160 gig of 2nd hdd that holds music. I also have the symbolic link shortcut on my desktop for that 160 gig drive. I think this drive is causing the problem.

I will unmount the the drive and than try to create a image again.

Any advice, does this sound like a reasonable path ?

Ok, the problem is resolved now.

Thanks for the developers link. I also moved all my music to the 2nd hdd and ended up with a 7.8 gig of primary drive. Initially I thought it was too much of size to be compressed by remastersys.

so, I posted my issue there. The feed back I got was that the compression ration is high and remastersys should be able to compress it down for a dvd iso.

well, after all said and done, I ended up with a 1.6 gig of iso, which really works out for me.

I burned it to a DVD and ran the liveDVD in my VMWare box. All is good now.

thanks

---

### Post by wjston on 2008-02-27
> **meazz1 said:**
> Ok, the problem is resolved now.

Thanks for the developers link. I also moved all my music to the 2nd hdd and ended up with a 7.8 gig of primary drive. Initially I thought it was too much of size to be compressed by remastersys.

so, I posted my issue there. The feed back I got was that the compression ration is high and remastersys should be able to compress it down for a dvd iso.

well, after all said and done, I ended up with a 1.6 gig of iso, which really works out for me.

I burned it to a DVD and ran the liveDVD in my VMWare box. All is good now.

thanks

Great news! I am glad you resolved your backup issues. Hopefully, we will not have to use the backup but, you never know.

---

### Post by zahris on 2008-02-28
i'm trying create a backup of my current instalation using "remastersys backup" too

but when i used it as a live-cd the system cannot be loaded. and its automaticaly logon as user "ubuntu" how can i change the default user with my own user.

---

### Post by meazz1 on 2008-02-28
> **zahris said:**
> i'm trying create a backup of my current instalation using "remastersys backup" too

but when i used it as a live-cd the system cannot be loaded. and its automaticaly logon as user "ubuntu" how can i change the default user with my own user.

I really don't have an answer, but do you have the latest version of the app?

---

### Post by wjston on 2008-02-28
> **zahris said:**
> i'm trying create a backup of my current instalation using "remastersys backup" too

but when i used it as a live-cd the system cannot be loaded. and its automaticaly logon as user "ubuntu" how can i change the default user with my own user.

Go to "Change config file......"
This will open a new window where you can specify your username and name for the iso.

---

