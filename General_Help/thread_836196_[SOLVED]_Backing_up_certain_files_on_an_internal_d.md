---
title: "[SOLVED] Backing up certain files on an internal drive with a 7.04 (Feisty) CD"
date: 2008-06-21
forum: General Help
---

### Post by MaxGhost on 2008-06-21
In continuation to my last thread, [http://ubuntuforums.org/showthread.php?t=835940](http://ubuntuforums.org/showthread.php?t=835940)

I'm trying to move a bunch of files off this internal drive which is corrupt (or something) due to personal stupidity, (XP gave me a Blue Screen of Death) and get those files on-to my Seagate FreeAgent 250gb external usb drive. Ubuntu isn't giving me permission to write on the external drive cause I don't "own it". I installed the NTFS drivers with the help from some people in the other thread, props to them, but now what... I can't get any further. I tried going into the NTFS configuration tool, and enable write to external drive, but still no difference... kinda odd in my opinion.

Any ideas anyone? I'd like to get this over with a.s.a.p. so I can wipe this drive and re-install XP on it so it can stay as my on-the-side storage/blah desktop when my newly ordered Asus laptop comes in sometime next week. I'm leaving on a lengthy trip the 28th of June, and I want to get those precious files onto my laptop so I can do stuff on the trip.

MaxGhost

---

### Post by geo909 on 2008-06-21
Except from the permissions, make sure that the actual owner of the directory where your freeagent is mounted is you and not root. Go to /media do 
```
ls -l
``` to see who owns each directory.

Also, keep in mind that there are issues with "freeagent drive" HDs and linux: If you let your freeagent drive idle for 10 mins or so, it will get to a standby mode where it will be unusable unless you unmount it, unplug it and replug it in.

---

### Post by MaxGhost on 2008-06-21
> **geo909 said:**
> Except from the permissions, make sure that the actual owner of the directory where your freeagent is mounted is you and not root.

Also, keep in mind that there are issues with "freeagent drive" HDs and linux: If you let your freeagent drive idle for 10 mins or so, it will get to a standby mode where it will be unusable unless you unmount it, unplug it and replug it in.

hmmm good to know for the second part, but how do I make sure the owner of it is me and not the root? I think I have another external drive kicking somewhere... I'll try with that one I guess... transfer files from eachother after I guess.

---

### Post by geo909 on 2008-06-21
> **MaxGhost said:**
> hmmm good to know for the second part, but how do I make sure the owner of it is me and not the root? I think I have another external drive kicking somewhere... I'll try with that one I guess... transfer files from eachother after I guess.

 Post the output of the "ls -l" command in your /media folder while freeagent drive is mounted.

 Do not worry about the second problem. If you unplug and replug the drive you will have no problems. While the disk is being written or read, that is no "idle", so it won't hang out while you do some job or something!

 Really no problem, it's just annoying.

---

### Post by MaxGhost on 2008-06-21
> **geo909 said:**
> Post the output of the "ls -l" command in your /media folder while freeagent drive is mounted.

 Do not worry about the second problem. If you unplug and replug the drive you will have no problems. While the disk is being written or read, that is no "idle", so it won't hang out while you do some job or something!

 Really no problem, it's just annoying.

where's the media folder? O_o (sorry I'm a complete newb with linux)

---

### Post by geo909 on 2008-06-21
Mount your drive
Then open a terminal and do

```
cd /media
ls -l
```

---

### Post by MaxGhost on 2008-06-21
> **geo909 said:**
> Mount your drive
Then open a terminal and do

```
cd /media
ls -l
```

aha! I get it now! :D

output was
```
dr-xr-xr-x 1 root   root 12288 2008-05-24 12:50 250GB MaxGhost
```

---

### Post by geo909 on 2008-06-21
ok, first of all let's try

```
sudo chmod 777 MaxGhost
```

Do that while you are in /media

Can you write now in your disk?

---

### Post by MaxGhost on 2008-06-21
argh... I think I just screwed myself over by accident...

I tried to do this after not thinking and unplugging my drive without ejecting it...

```
ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda1 /mnt/ExtDrive -o force
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.
```

---

### Post by geo909 on 2008-06-21
I don't thing that is a great problem. I remember I had this with my freeagent drive but I don't remember what I did to fix it, it was easy though.

 If you have windows try to plug it in there and safely unplug it again as the message suggests.

---

### Post by MaxGhost on 2008-06-21
> **geo909 said:**
> I don't thing that is a great problem. I remember I had this with my freeagent drive but I don't remember what I did to fix it, it was easy though.

 If you have windows try to plug it in there and safely unplug it again as the message suggests.

The problem IS Windows... I get the Blue Screen of Death when I boot it up... so I had to use this linux CD to try to get the files off this drive... don't want to bring it to the shop, I wanna do it myself :D

Should I just restart my comp and reboot linux? or what?

---

### Post by geo909 on 2008-06-21
Understand.. 
So did you manage to mount your disk?

---

### Post by MaxGhost on 2008-06-21
No I didn't yet... I'll reboot my comp and I'll be back in 5-10 mins... i'll see if that helps it...

---

### Post by MaxGhost on 2008-06-21
K I'm back... I did what you said (it's mounted correctly)

```
ubuntu@ubuntu:/media$ sudo chmod 777 MaxGhost
chmod: cannot access `MaxGhost': No such file or directory
```

btw, the actual name of my drive is '250GB MaxGhost' but when I tried that it took it as 2 different items... do I have to rename the drive?

Edit: well I can't rename... permissions won't let me... so how do I 'simulate' a space in the command line?

---

### Post by MaxGhost on 2008-06-21
bump?

---

### Post by geo909 on 2008-06-21
Replace the *MaxGhost* with the name of the folder that you mount your drive into..
I thought you was mounting the disk to \media\MaxGhost

---

### Post by MaxGhost on 2008-06-21
Ah! ok... but trying to mount it again, I got this:

```
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda1 /mnt/ExtDrive -o force
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by MaxGhost on 2008-06-21
bump.

---

### Post by MaxGhost on 2008-06-21
O_o ba-ump I really need an answer with this!

---

### Post by geo909 on 2008-06-21
> **MaxGhost said:**
> O_o ba-ump I really need an answer with this!

Ok,ok pal (we're friends now ;))..

You have let your disk idle for 10 minutes or more. Told you those "freeagent" drives
have this issue when let idle. Just plug it out, replug it in and mount it.

---

### Post by MaxGhost on 2008-06-21
Didn't help... wow I'm annoyed as hell right now... all I want is to get my files off my damn hard-drive!!! 

now my internal drive can't be mounted... "Cannot mount volume"

I still can't write anything onto my external drive... this is really damn complicated for me!

---

### Post by geo909 on 2008-06-22
> Didn't help...
 Well, that was exactly the message I had when I had my disk plugged in and idle for a while and then was trying to mount it..
 Don't know what's happening with you. Maybe that faulty eject and then trying to mount the disk with the *-o force* option did something?
Don't know..

> now my internal drive can't be mounted... "Cannot mount volume"
I still can't write anything onto my external drive... this is really damn complicated for me!

 Ok, please answer the questions below because you wrote too many things together and I'm confused:

1) What do you mean by "you still can't write anything onto my external drive"? Did you manage to mount it or not? Didn't you say that it didn't work?

2) If I correctly understood, you use an ubuntu live CD. Now, you do understand that after rebooting no settings are saved including the things that you installed. If you had to install something in order to get to mount your drive (don't know, that was a previous adventure of yours) you will have to reinstall everything any time you boot to your live cd.

 Now, If I were in your situation I would try a something different. Though, if you decide to follow that I don't guarantee that it will work so do not blame me for losing your time, OK? We all have our schedule and I am running a period of exams, so..

 So this is what I would do; 

I would go [here]("http://www.puppylinux.org/"). 
Then follow the *Download Puppy Linux4.0 (Dingo)* link and choose a link to download the iso (the HTTP/FTP link will work). 
This is a live CD distribution which is very light (the iso is 88MB)and have graphical tools to 
mount/unmount things while you have root privileges by default. It is also very fast, I guess you 
have spent much time waiting ubuntu live cd to boot. Now find a burner and burn the iso to a cd. 
Boot your PC from the cd and wait Puppy to run. You will have to set up some settings like language 
and screen resolution and stuff. Just follow the defaults.
 When you are up and running you will find a *"mount"* icon on your desktop. Clicking on that will 
result a menu to open that lets you mount or unmount every disk the system detects by clicking a button.
 Try to mount your internal and external disks by clicking the corresponding buttons. Have the freeagent 
drive just plugged in to avoid standby problems like before. Now, If I remember correctly, there will 
also be a button that opens the folder the disk is mounted. Open the related folders and try to 
drag 'n drop the files you want from one to another.

 Tell me in case you do decide to try the puppy live cd solution.

---

### Post by cariboo on 2008-06-22
First off you've got way more patience then I do. I would have reformated the drive after the first day. If you are running on the liveCd you should be able to run ntfsfix /dev/sda to repair the problem.

Another thing is  to find a copy of Hiren's Boot Disk, it is loaded with so many recovrey and diagnostic programs that sometimes it's hard to decide what program to use. I hear it might be a available through mininova.org


Jim

---

### Post by MaxGhost on 2008-06-22
Thanks for the compliment cariboo :P -- I did run that, it fixed it... I just improvised and typed that, and it helped.

geo, yeah I know that with the live CD you re-install everything... only thing I did was install the ntfs drivers.

Right now I can see all the files from both drives, I got full access to my internal drive. (I can move, delete, write, read, etc. on it) But I have read-only access only with my external drive.

I think I will try puppy linux... I'll let you all know how it goes!

---

### Post by geo909 on 2008-06-22
In case you see that before you try Puppy:

1) Did you try the chmod 777 thing I was talking about? I remember we had reached a point that I told yyou to do so and then the other problems came up. So I missed the series of events.

2) If you have already tried it and it has not worked, also try
```
sudo chown -hR *yourusername* *mountfolder*
```

-I don't remember what the username is in the live cd by default.
 To find out type ```
whoami
``` in a terminal.
-Instead of *mountfolder* type the folder where the disk is mounted.
 That would be /media/MaxGhost or whatever you typed when you mount it.

3) If that doesn't work, as a last resort try *again* the chmod thing as I said in
the previous post. (The reason I tell you to do it again is because the result is 
different now that you did the chown thing).

The reason I told you to try puppy instead was before I thought you were in a situation that nothing was mounted etc..
Now that things work, try this before if you see it on time.

---

### Post by MaxGhost on 2008-06-22
umm... too late? I just burned puppy linux on a cd (second try, first didn`t work and sent me to windows... which gave me a BSOD)... and it's WORKING!!! WOOOOT! *hugs* :D

I`m copying files to my external drive as we speak!

One problem tho... Internet doesn't work with puppy linux... so I'm using another computer to type this right now... If I could've, I would have popped in my hard-drive in this computer, but there's some odd lock-kinda thing in the front of the case that doesn't let me open it... bah! Atleast Puppy linux is working! thanks!

---

### Post by geo909 on 2008-06-22
> **MaxGhost said:**
> umm... too late? I just burned puppy linux on a cd (second try, first didn`t work and sent me to windows... which gave me a BSOD)... and it's WORKING!!! WOOOOT! *hugs* :D

I`m copying files to my external drive as we speak!

One problem tho... Internet doesn't work with puppy linux... so I'm using another computer to type this right now... If I could've, I would have popped in my hard-drive in this computer, but there's some odd lock-kinda thing in the front of the case that doesn't let me open it... bah! Atleast Puppy linux is working! thanks!

 Finally! Glad it worked for you. Connecting to internet should be as easy as mounting a disk on Puppy Linux. Just click the connect button and follow the defaults.. 
Puppy Linux is one of the best distros around in its category (mini distros). Maybe THE best.

---

### Post by MaxGhost on 2008-06-22
yeah it's still not working (internet I mean)... automatically connects with Ubuntu... wish it did too :P

Meh. It's only a small price to pay to be able to transfer files ridiculously easily! :D

1 Question tho... is there a way to say "yes to all" in puppy linux? when I copy files, and I realise "oops not what I wanted to do" then when I go to overwrite, I need to hit "yes" each time over and over, and where theres thousands of files, it gets annoying... any ideas?

---

### Post by geo909 on 2008-06-22
Btw you should mark thread as [SOLVED]

---

### Post by MaxGhost on 2008-06-22
good point... will do... btw just got the internet to work... had to tinker abit :P

---

