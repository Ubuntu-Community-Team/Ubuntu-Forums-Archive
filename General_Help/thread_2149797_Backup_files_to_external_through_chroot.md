---
title: "Backup files to external through chroot?"
date: 2013-05-30
forum: General Help
---

### Post by lemonoid on 2013-05-30
Okay so I had a problem, that either nobody wanted to help me fix or either just didn't know how to answer my question. I accidentally deleted the contents of /lib/modules. I found a lot of answers through searching and I had successfully booted up into a live session and chroot'd into my filesystem. And I actually have the module package which is 3.2.0-40-generic-pae on my external, but I don't know how to copy it from my external into my chroot'd filesystem. My external is labeled My Passport, so in commands I can't use that because of the space in the name. So if I could figure out how to copy that package from my external into my filesystem, I think that may work. I could then use insmod (i believe) to load the modules individually once I boot back into the system. My previous question was what package I could download and install now that I have access to the internet, someone suggested linux-kernel-headers and I tried that, and it said it was the newest versiona already and wouldn't install. So all I need to know is either
1. What package I can download and install to replace my modules
or
2. How to copy files to and from My Passport (possibly how to change the name of the external) so I can either backup my files and re-install Ubuntu, or copy the 3.2.40-generic-pae package from the external and then load the modules into the system.

About question 2, if I can indeed copy the module package back into /lib/modules, if I do so, then reboot my filesystem, will the kernel automatically load the modules or will I have to go in and load them one by one using insmod?

Thank you for your help. The last time I posted, I got NO answers, so I figured I'd go again, and this time it's a little bit simpler, and I have two different options, so that gives me twice the possibility for a known answer to my problem, as either would work.

Edit: Referencing what someone said to me before (if you don't have current backups of your data then it must not be important to you), my data is very important to me, I just am not as fortunate as everyone to have terabytes of space to backup all my data to, as I share a computer, and don't have much internal space, and I do have an external where I backup certain imporant data to, but I don't do it every single time I download important data.
    
I recently backed up a lot of my data, that's actually WHAT I was doing when I messed up my /libs/modules, because I was backing up some Android development (due to low storage space) and saw that /lib/modules was taking up a lot of space on my system, and I actually have a /lib/modules folder for developing Android kernels, so I got mixed up on which /lib folder I was in. The first thing I was backing up was my Android development, then going to personal data, and that's when my system broke (that's how I have a backup of the 3.2.40-generic-pae)

---

### Post by lemonoid on 2013-05-30
I could always just re-install Ubuntu without worrying about my data, as I have MOST of it backed up, but I think learning how to do either of the things above would help me learn and grow in my knowledge of the Ubuntu system, and Linux as well. I've been working on Ubuntu for two years now and learned many things along the way and had to fix many things, but chroot and having to move around between filesystems is something I've never had to do, so I've avoided it so I wouldn't mess anything up just for play, but now that I mostly HAVE to learn, I'd like to.

---

### Post by Bashing-om on 2013-05-30
[COLOR=#000000]lemonoid;
I do not mind lending a hand in your endeavor. I too am always open to a learning experience.
Easy approach:
With your "my passport" device attached, can you access it in the file manager of the liveCD ?
Secondly is the liveCD the same version as your install - that may later become important -?
Just to copy files one may not have to resort to "chroot", maybe simply mounting the external partition(s),from the liveCD, will be good enough. 
I anticipate that in the graphical file manager (nautilus) to be able to mount both partitions and copy the files straight across with root's privileges.

The modules are just files, if the scripts are "inplace" to parse them, the system should never even know they were gone.
[/COLOR][INDENT][COLOR=#000000]
that is what I think

[/COLOR][/INDENT]

---

### Post by Irihapeti on 2013-05-30
The liveCD and the chrooted system don't have to be the same version. (I've chrooted into 13.10 from 12.04 many times.) But they do need to be the same architecture e.g. both 32 bit or 64 bit.

---

### Post by lemonoid on 2013-05-31
> **Bashing-om said:**
> [COLOR=#000000]lemonoid;
I do not mind lending a hand in your endeavor. I too am always open to a learning experience.
Easy approach:
With your "my passport" device attached, can you access it in the file manager of the liveCD ?
Secondly is the liveCD the same version as your install - that may later become important -?
Just to copy files one may not have to resort to "chroot", maybe simply mounting the external partition(s),from the liveCD, will be good enough. 
I anticipate that in the graphical file manager (nautilus) to be able to mount both partitions and copy the files straight across with root's privileges.

The modules are just files, if the scripts are "inplace" to parse them, the system should never even know they were gone.
[/COLOR][INDENT][COLOR=#000000]
that is what I think

[/COLOR][/INDENT]


thank you for your response, and to the person below. to answer the question at hand, I orignally had made a 13.04 live USB to see how well it would run on my system, I was using that at first, but I really think my graphics card or some other piece of hardware is too old to smoothly run 13.04, so I remade 12.04 USB and that's what I'm currently using. 

Second of all, yes I can access 'my passport' through the LiveUSB, the modules work perfectly live, that's how I'm on the internet now.

---

### Post by Bashing-om on 2013-05-31
[COLOR=#000000]lemonoid; Hey ---
In the liveDVD open "nautilus"-> key combo ctl+alt+t yields a terminal
terminal command:
```
sudo nautilus
``` nautilus opens; 
 .. in the left pane are all the partitions the system is aware of, find the partition to be copied to, and open the directory to be copied to///
now while still there -same routine, find the partition of the files to be copied and the directory where they are ... 
two tabs are now open in the file manager (nautilus) drag one of these tabs to the desk top,
start choosing files -in the to be copied window - and drag them into the other window (that is open where ya want the final destination to be, where you opened it at). When done copying,close all out, close applications and reboot into the install.  What do you now have ?
[/COLOR][INDENT=2][COLOR=#000000]
should workie great, last long time[/COLOR][/INDENT]

---

### Post by lemonoid on 2013-05-31
> **Bashing-om said:**
> [COLOR=#000000]lemonoid; Hey ---
In the liveDVD open "nautilus"-> key combo ctl+alt+t yields a terminal
terminal command:
```
sudo nautilus
``` nautilus opens; 
 .. in the left pane are all the partitions the system is aware of, find the partition to be copied to, and open the directory to be copied to///
now while still there -same routine, find the partition of the files to be copied and the directory where they are ... 
two tabs are now open in the file manager (nautilus) drag one of these tabs to the desk top,
start choosing files -in the to be copied window - and drag them into the other window (that is open where ya want the final destination to be, where you opened it at). When done copying,close all out, close applications and reboot into the install.  What do you now have ?
[/COLOR][INDENT=2][COLOR=#000000]
should workie great, last long time[/COLOR][/INDENT]

okay, I thought about this but for some reason last night it wasn't showing my other filesystem, I'll go look now and do that, I thought it could be that easy but wasn't sure. But before so, you're saying, I take the module folder I copied onto my external '3.2.40-generic-pae' and copy and paste it into my main filesystem correct? Should I try to copy it straight into /lib/modules or should I just copy it into my home folder, reboot, and then use the terminal to move it to /lib/modules (I copy all my files through terminal)

---

### Post by lemonoid on 2013-05-31
okay, I tried through Nautilus to drop and drag into my filesystem, and its giving me the response that I do not have the permissions. Do you think it would work if I mounted that filesystem and chroot'd. Because then I would have root, but I don't know if I'd only have it through the terminal. I guess if that wouldn't work then I'm lost again, because I don't know how to gain permissions to my other system through nautilus.

UPDATE: Ok so I had an idea and tried it, and so far its working. Through Nautilus, I was able to copy and paste the module folder (3.2.40-generic-pae) to my Windows filesystem. When I boot into my other filesystem, I should be able to copy it from my Windows filesystem to my broken system correct? Or did deleting modules somehow block me gaining access to my Windows from my broken system? I mean the modules are mainly for hardware correct? Not filesystems? So the Windows system should load on my filesystem, correct agian right?

---

### Post by Bashing-om on 2013-05-31
[COLOR=#000000]lemonoid; Hi !
Ya gotta open nautilus from terminal with "sudo" to gain that level of authorization>
```
sudo nautilus
``` and then you are going to open those two directories, compare them for the different FILES.
Else to copy the whole directory best I can advise is to "chroot" and 
```
sudo cp -Rp <path_of_copy_from/directory> <path_to_location/directory>
```... ya must be sure absolutely sure of your paths and directories; linux assumes that you know what you are doing and does not permit for mistakes ! What is done is done !
This for guidance:
```
man cp
``` there does exist other means to copy a directory, however, "cp" works.
[/COLOR][INDENT][COLOR=#000000]
'nuff said ? else, more coming[/COLOR][/INDENT]

---

### Post by Irihapeti on 2013-05-31
If that doesn't work, I think it should be fixable fairly easily through a chroot (did some experiments on a test install). But I'll wait to see what happens with the copying method first.

---

### Post by lemonoid on 2013-05-31
I gained permissions of Guest by going into my main account and the command line and giving access to my home folder from my guest account. For some reason in my Guest account, I could access my Windows which is weird, bc I couldn't access it in my regular account. So I had my module folder copied to Windows, which I then copied to my Guest home folder. After I gained access to my main accounts folder, I copied such folder into that home folder. I logged into my main account, and through the terminal moved the module folder into /lib/modules. I restarted the computer, and I regained access to my Windows partition, but its still not reading my wireless adapter and still not reading my external HDD. The weird thing is, I'm accessing my external through USB, this entire time, I have been able to use my keyboard and mouse through USB, but nothing else works. I'm wondering if I deleted some type of specific wireless or USB modules. I see the USB folder in /modules/3.2.0-40-generic-pae, however I don't see wlan0 (idk if that's where wireless access goes). So I copied the module folder from my live session into Windows, now that I have access to Windows, I'll copy THAT module directory over, and move it to /lib/modules. Maybe this will fix my current problem, as I know nothing has been deleted out of this module folder and everything worked like a charm in my live session. I will come back with an update report. Hopefully, as I'm thinking it may, this will solve my problem, but I deleted every other module folder when I deleted the first one, so I'm not sure if anything will stay broken. I just imagine that a module folder in a Live USB that allows everything to work, will do the same copy it into ../modules/ and reboot.

---

### Post by lemonoid on 2013-05-31
UPDATE TO PREVIOUS POST:
I successfully moved the modules provided in the live session to my filesystem. However, things still aren't working all the way. I have 3.2.0-29 (from live) and 3.2.0-40. My next question to solving this would be, would the modules in -40 override the ones in -29 from working properly? I could delete the directory 3.2.0-40 and then once I'm back on the net, run an update and let that update my modules. Or is this a bigger problem, do I need to somehow recover ALL the module directories I deleted (10+ directories, 14gb) which I won't be able to do because I don't remember all of them. I guess if I had to, I can just boot live, access my Windows, backup my data and re-install Ubuntu, but as I said before I love learning and by solving this problem without just taking the easy way out I'll have learned a lot, and believe it or not I actually already have. I was also thinking about the possibility that I may have to insmod specific modules to get things back working, just the ones I need to get on the net, and then like I said run an update, and let that fix everything. If anyone has any feedback or help at this point, thank you. If I don't figure it out by bedtime I'l probably just backup my data and re-install.

EDIT: by the way, there is now the build option in 3.2.0-29, is there any way to use this to my advantage.

---

### Post by Irihapeti on 2013-05-31
How long to your bedtime? If you feel up to it, we could try the chroot thing. If not, now that you know how to get your data, you could just reinstall and save the chroot for another day.

---

### Post by lemonoid on 2013-06-01
> **Irihapeti said:**
> How long to your bedtime? If you feel up to it, we could try the chroot thing. If not, now that you know how to get your data, you could just reinstall and save the chroot for another day.
i forgot its friday. no bedtime really. couple hours. so if you're down to help me let's hop to it.

---

### Post by Irihapeti on 2013-06-01
First of all, I'll give you an overview of what I have in mind (and have just tested).

You chroot into your install and then reinstall your linux-image.

If there happens to have been a kernel update in the last day or so, would that be a problem?

---

### Post by lemonoid on 2013-06-01
> **Irihapeti said:**
> First of all, I'll give you an overview of what I have in mind (and have just tested).

You chroot into your install and then reinstall your linux-image.

If there happens to have been a kernel update in the last day or so, would that be a problem?

ok. I can chroot in. Then, how do I reinstall the image? and as far as kernel update, I have no clue that's sort of what I was askin before, if one set of kernel modules would block others from working. and i've had this problem for about 2 weeks now. so i have no clue about kernel update. I can get on the site and check changelog and dates to see when last change was.

---

### Post by Irihapeti on 2013-06-01
Some people don't like to update the kernel. That was my only concern. If you're happy to go ahead with updates, no problem.

I'm not sure exactly how you've done your chroots previously. There seem to be several different ways. This is the way I prefer to do it.

First, get a root shell.

```
sudo -i
```

That saves typing "sudo" all the time. You do need to be careful from now on, until we finish, though.

Mount the drive your system is on. I usually like to use /mnt, simply because it's less typing. :)

So I'd use:

```
mount /dev/sdxy /mnt 
```
Change sdxy to whatever your drive is. If you want to find out, use
```
blkid
```
and you get a list.

Then do these commands, one at a time.

```
mount -o bind /dev /mnt/dev
mount -o bind /dev/pts /mnt/dev/pts
mount -o bind /proc /mnt/proc
mount -o bind /sys /mnt/sys

chroot /mnt

```

Let me know when you've done that and we'll go on to the next bit.

---

### Post by lemonoid on 2013-06-01
thats exactly how i do it, just mount /dev/sda6 /mnt, same sudo -i, and mounting processes for dev,proc,sys,dev/pts, and chroot /mnt.

---

### Post by lemonoid on 2013-06-01
for some reason my system isn't booting to a live session now, its like its bypassing the liveUSB, but I know its not a USB problem because the mouse and keyboard still work, so although I just plugged it into this Windows laptop and it shows it as an Ubuntu LiveUSB, I'm going to re-do the USB real quick using unetbootin and make the disk again, let my computer rest for a minute because it gets tempermental, and hopefully by the time I"m done making the USB again, letting it rest and having a newly made live session will work. I have no clue why else it would be bypassing the live boot. so give me about 5-10 min

---

### Post by Irihapeti on 2013-06-01
Not a problem. I'll wait.

---

### Post by lemonoid on 2013-06-01
ok it worked. its booting into live right now. after that I'll mount my filesystem, and all the other necessities, then chroot in. if you wanna go ahead and post a next step you can. by the time you do that i'll be done and waiting

update: everything is mounted now. internet is up and going, so if I need to download any images or updates I can, just need to know what to do.

---

### Post by Irihapeti on 2013-06-01
Right, so you are chrooted into the system you want to repair?

To be really safe, let's delete /lib/modules so that there's no junk left around. The ones you copied there belong to an earlier kernel version.
```
rm -r /lib/modules
```

Then, check that you can get on the internet from the chroot. Occasionally, something goes wrong and it doesn't work.

Easiest way is
```

ping -c 5 google.com
```

If that works successfully, then:

```

apt-get update
apt-get dist-upgrade

```
Note: dist-upgrade does NOT take you to the next Ubuntu version. It just means that if any updates want to install new packages, they can.

You should see a list of packages to be installed. I'm betting there's a new kernel among them, if your system has been out of action for a fortnight.

Once that's done, you can check that /lib/modules exists, if you really want.

If you can't get onto the internet from the chroot, post back and we'll try plan B.

---

### Post by lemonoid on 2013-06-01
> **Irihapeti said:**
> Right, so you are chrooted into the system you want to repair?

To be really safe, let's delete /lib/modules so that there's no junk left around. The ones you copied there belong to an earlier kernel version.
```
rm -r /lib/modules
```

Then, check that you can get on the internet from the chroot. Occasionally, something goes wrong and it doesn't work.

Easiest way is
```

ping -c 5 google.com
```

If that works successfully, then:

```

apt-get update
apt-get dist-upgrade

```
Note: dist-upgrade does NOT take you to the next Ubuntu version. It just means that if any updates want to install new packages, they can.

You should see a list of packages to be installed. I'm betting there's a new kernel among them, if your system has been out of action for a fortnight.

Once that's done, you can check that /lib/modules exists, if you really want.

If you can't get onto the internet from the chroot, post back and we'll try plan B.
ok. right now i'm connected to the internet but I haven't deleted anything yet. i'll ping first just to make sure, then delete the modules, n ping again. then i'll run the apt-gets. be back in two minutes.

---

### Post by lemonoid on 2013-06-01
ok good. it pinged perfectly after removing modules, and ran apt-get update, then apt-get dist-upgrade, and before I typed Y i looked at the packages, there is INDEED a linux-image, linux-headers, and the generic-pae package which is title like that of the modules i've deleted. after this, I should 'exit' and reboot into my normal system right? after I check my modules of course.

---

### Post by Irihapeti on 2013-06-01
Yes, that should be it. Go ahead and reboot.

But I'll be sitting here with fingers crossed until I hear back. :)

---

### Post by lemonoid on 2013-06-01
the modules are there, 3.2.0-45-generic-pae. going to reboot now. fingers crossed as well.

---

### Post by lemonoid on 2013-06-01
ugh my computer is being mad again. sometimes when i try to boot it, it won't connect to the display for some reason and seems to stay in a deep sleep although I can clearly see the blue lights come on and hear the processor n fans running. i may have to let it sit for another minute. its killing me.

---

### Post by Irihapeti on 2013-06-01
Anything happening yet?:?:

---

### Post by lemonoid on 2013-06-01
EVERYTHING WORKS!!!!! THANK YOUU!!!! Where were you days ago lol. thank you for testin it out for me and showin me what to do. I knew I could do it from a chroot'd system, and I tried every single thing but that apt-get distro-upgrade, so thank you. I learned a lot getting up to that point and now I know if I ever am missing some system packages I can possibly get them through that distro-upgrade. Thank you so much.

---

### Post by lemonoid on 2013-06-01
issue Resolved. i don't know how to mark Solved. But this definitely is. And I saved everything I did in a word file so maybe I can help someone with similar issues later. That's why I didn't wanna just re-install, I learned a bit more about the system than if I just would've popped in the USB and installed over my current system.

---

### Post by Irihapeti on 2013-06-01
:popcorn:
Cheers! Great news!

Thank you as well for being willing to do something new. I've learned from this exercise, too. Win all round!

---

### Post by Irihapeti on 2013-06-01
To mark it solved: [http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730](http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730)

---

### Post by lemonoid on 2013-06-01
> **Irihapeti said:**
> :popcorn:
Cheers! Great news!

Thank you as well for being willing to do something new. I've learned from this exercise, too. Win all round!

I'm always wanting to learn more and more, after over two years of being in the Linux community and using  many distros, Ubuntu is always my go-to (a lot of that has to do with Android reasons, but I love it) and I love learning how things work, and how to fix things when I unfortunately occasionally break them. I'm glad we both could learn a little bit. Win for us! I'll see you around, and thanks again. Time to shut down and go to bed. lol if its broke in the morning I'll be back to this thread.

---

