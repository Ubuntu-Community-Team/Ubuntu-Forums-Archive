---
title: "Transferring Video Files To External HDD."
date: 2013-01-11
forum: General Help
---

### Post by BlinkinCat on 2013-01-11
Hi all,

I have a 250 GiB External HDD which I want to use to store some Videos. The problem is, I suspect I may have incorrectly formatted the HD in the past (about 1 year ago)

Just in case I am mistaken, I would appreciate some help.

1. What should the Partition be formatted in ? (Presently in Ex3)
2. Drag and Drop the Files doesn't appear to work.
3. In fact, no option to create a folder appears in HD.
4. Are there any steps I can take to rectify the situation ?
5. Should I be using the terminal ?
6. Any other tips would be appreciated.

Thank you - :p

---

### Post by dannyboy79 on 2013-01-11
what computer OS do you intend to hook this to so you can play the videos back? That will determine what filesystem you should format it in.

use the "mount" command to see what the drive is being mounted as, that will show it's mount options and where its being mounted. then you can see who owns it and what the permissions are which is probably why you can't create a folder in it, you don't have the permission

the steps to rectify the situation will depend on how you answer my above questions.

the terminal is normally the easiest place to work because commands are easily copy and pasted versus trying to describe what you see etc etc.

---

### Post by Elfy on 2013-01-11
> **BlinkinCat said:**
> ...
2. Drag and Drop the Files doesn't appear to work...

Can be a bit odd in Xubuntu anyway so I'd not count that as an issue just yet - well you can, but it's likely to not be part of the others :)

I'd agree the remainder would make me think of permissions

---

### Post by BlinkinCat on 2013-01-11
Hi Danny,

The OS for playback is Xubuntu 12.04 - I don't think the filetype for the videos matters.  I am not that bright Danny, but I will try to decipher what you say about permissions.

Cheers - :p

---

### Post by BlinkinCat on 2013-01-11
Hi again,

Permissions for the HDD show as owner root (root) with no other highlights.

Does this help ?

---

### Post by BlinkinCat on 2013-01-11
I'm a bit stuck on using the "mount" command - where ?

---

### Post by CharlesA on 2013-01-11
> **BlinkinCat said:**
> I'm a bit stuck on using the "mount" command - where ?

You should be able to just run:

```
mount
```

To list what is currently mounted and where they are mounted.

---

### Post by Elfy on 2013-01-11
> **BlinkinCat said:**
> I'm a bit stuck on using the "mount" command - where ?

Terminal

but you've already deduced that the drives are owned by root.

Might be useful to help you get the permissions sorted out.

---

### Post by BlinkinCat on 2013-01-11
/dev/sdb1 on /media/ba3a98a9-ca4b-4f93-8871-d36429f7baf0 type ext3 (rw,nosuid,nodev,uhelper=udisks)

Thanks Gents - :p

---

### Post by CharlesA on 2013-01-11
It should assign the right permissions if it is mounted in /media and is an EXT3 drive.

Have you tried copying the files via rsync or cp from a terminal?

---

### Post by BlinkinCat on 2013-01-11
> **CharlesA said:**
> It should assign the right permissions if it is mounted in /media and is an EXT3 drive.

Have you tried copying the files via rsync or cp from a terminal?

No Charles,

If File was on geoff/videos/folder name/filename what would the cp command be ? I would prefer to have been able to create folders in the HDD but not able to in normal way - can I do this ? via sudo? I really appreciate all the time you have spent with me Charles.

---

### Post by CharlesA on 2013-01-11
> **BlinkinCat said:**
> No Charles,

If File was on geoff/videos/folder name/filename what would the cp command be ? I would prefer to have been able to create folders in the HDD but not able to in normal way - can I do this ? via sudo? I really appreciate all the time you have spent with me Charles.

```
mkdir /media/ba3a98a9-ca4b-4f93-8871-d36429f7baf0/foldername
```

Should let you create a folder. It is strange that you were unable to create the folder from the GUI.

---

### Post by mysteriousdarren on 2013-01-11
Look at my past threads, I went through this same problem myself. Not the creating folders but the other copy and permission problems. Good luck.

---

### Post by BlinkinCat on 2013-01-11
Hi Charles,

Enough is enough - you have been more than generous with your time. I will take it from here hopefully - I will experiment until I get it right.

BTW, I thought I was onto a good thing, my ISP provides 300 GiB (near enough for me) at $15/month - unfortunately though only through PC or Mac.

I was wondering if I set up a virtual machine it would do the job.

All the best Charles and many thanks.

---

### Post by BlinkinCat on 2013-01-11
> **mysteriousdarren said:**
> Look at my past threads, I went through this same problem myself. Not the creating folders but the other copy and permission problems. Good luck.

Thanks for your kind words mysteriousdarren - they are much appreciated.

Cheers - :D

---

### Post by BlinkinCat on 2013-01-11
geoff@ABC:~$ mkdir /media/ba3a98a9-ca4b-4f93-8871-d36429f7baf0/Actors
mkdir: cannot create directory `/media/ba3a98a9-ca4b-4f93-8871-d36429f7baf0/Actors': Permission denied

If anyone other than CharlesA (he has done enough helping me in another thread) could answer why the above command doesn't create a folder by the name of Actors in the mounted /media drive I would appreciate some help. It also seems to be tied up with my being unable to create a folder via the GUI either. Could I have done something incorrectly in the Disk Utility ?

Cheers - :)

---

### Post by CharlesA on 2013-01-11
> **BlinkinCat said:**
> Hi Charles,

Enough is enough - you have been more than generous with your time. I will take it from here hopefully - I will experiment until I get it right.

BTW, I thought I was onto a good thing, my ISP provides 300 GiB (near enough for me) at $15/month - unfortunately though only through PC or Mac.

I was wondering if I set up a virtual machine it would do the job.

All the best Charles and many thanks.

Nice. Do you know if they use a client or how it works?

> **BlinkinCat said:**
> geoff@ABC:~$ mkdir /media/ba3a98a9-ca4b-4f93-8871-d36429f7baf0/Actors
mkdir: cannot create directory `/media/ba3a98a9-ca4b-4f93-8871-d36429f7baf0/Actors': Permission denied

If anyone other than CharlesA (he has done enough helping me in another thread) could answer why the above command doesn't create a folder by the name of Actors in the mounted /media drive I would appreciate some help. It also seems to be tied up with my being unable to create a folder via the GUI either. Could I have done something incorrectly in the Disk Utility ?

Cheers - :)

Too late!

Run this:

```
ls -ld /media/ba3a98a9-ca4b-4f93-8871-d36429f7baf0
```

It's probably going to be rwxr-xr-x root root, so you can either chmod it to 777 or chown it to your user.

```
sudo chmod 777 /media/ba3a98a9-ca4b-4f93-8871-d36429f7baf0
```

---

### Post by BlinkinCat on 2013-01-11
> **CharlesA said:**
> Nice. Do you know if they use a client or how it works?



Not sure Charles - I was a little put off when they quoted minimum requirements for PC.
It's known as Optus Smart Safe.

I'll get to with those commands - :P

---

### Post by BlinkinCat on 2013-01-11
geoff@ABC:~$ ls -ld /media/ba3a98a9-ca4b-4f93-8871-d36429f7baf0
drwxr-xr-x 3 root root 4096 Jan 12 06:48 /media/ba3a98a9-ca4b-4f93-8871-d36429f7baf0

First one it looks only a little different than your prediction.

Total - 

geoff@ABC:~$ ls -ld /media/ba3a98a9-ca4b-4f93-8871-d36429f7baf0
drwxr-xr-x 3 root root 4096 Jan 12 06:48 /media/ba3a98a9-ca4b-4f93-8871-d36429f7baf0
geoff@ABC:~$ sudo chmod 777 /media/ba3a98a9-ca4b-4f93-8871-d36429f7baf0
[sudo] password for geoff: 
geoff@ABC:~$

---

### Post by BlinkinCat on 2013-01-11
Can I ask what now ?

---

### Post by CharlesA on 2013-01-11
Try copying the files now. ;)

EDIT: If you are thinking of doing an online backup, check out [CrashPlan]("http://www.crashplan.com/consumer/compare.html")

They support Windows/Mac/*nix and I've been using them with good results so far. I'm not sure how the AU pricing is, but it might be cheaper than Optus Smart Safe.

---

### Post by BlinkinCat on 2013-01-11
> **BlinkinCat said:**
> Can I ask what now ?


I shouldn't have asked that silly question - I'm on my way thanks to you Charles.

I can now create a Folder via GUI - :popcorn:

Copying a movie file may take a little longer ?

---

### Post by BlinkinCat on 2013-01-11
A full Movie copied in about 20 seconds - to say I'm rapt would be an understatement

Thanks very much for your help Charles - I will experiment with cp at my leisure.

I will mark as Solved.

Cheers - ;)

---

### Post by BlinkinCat on 2013-01-11
> **CharlesA said:**
> Try copying the files now. ;)

EDIT: If you are thinking of doing an online backup, check out [CrashPlan]("http://www.crashplan.com/consumer/compare.html")

They support Windows/Mac/*nix and I've been using them with good results so far. I'm not sure how the AU pricing is, but it might be cheaper than Optus Smart Safe.

Thanks very much for the tip Charles - all the best - :)

---

### Post by CharlesA on 2013-01-11
> **BlinkinCat said:**
> A full Movie copied in about 20 seconds - to say I'm rapt would be an understatement

Thanks very much for your help Charles - I will experiment with cp at my leisure.

I will mark as Solved.

Cheers - ;)

Glad you got it sorted. I am kinda curious why it didn't set the right permissions, but at least it is working now. :)

> **BlinkinCat said:**
> Thanks very much for the tip Charles - all the best - :)

Welcome. :)

---

