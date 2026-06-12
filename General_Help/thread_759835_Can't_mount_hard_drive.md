---
title: "Can't mount hard drive"
date: 2008-04-19
forum: General Help
---

### Post by Eric Weir on 2008-04-19
I just replaced a 10 GB HD with a 40 GB HD and did a fresh install of Kubuntu 7.10. Now I've put the 10 GB back in as a slave, so I can copy my data files and old confuguration files for future reference in case I need them. 

When I tried to mount the 10 GB drive from within Konqueror I got the following message: "hal-storage-fixed-mount refused uid 1000."

How do I get the drive mounted?

Thanks,

---

### Post by Diabolis on 2008-04-19
there are already some threads in the forums that deal with this problem, you should read them.

---

### Post by T-Virus on 2008-04-19
How exactly are you trying to mount? I believe that mounting hard drive requires root access. Try this:

```

sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1

```

That's in case if the hard drive you want to mount is recognised as "sdb1".

---

### Post by glennzo on 2008-04-19
How about **sudo /sbin/fdisk -l** to see what partition / drive he needs to mount? Kind of eliminates some of the guess work.

---

### Post by Eric Weir on 2008-04-19
> **Diabolis said:**
> there are already some threads in the forums that deal with this problem, you should read them.
Several were displayed after I entered the title for my post. I read one. It was related, but not directly. When I tried to go back to the page where the others were listed, they were gone. The only thing left was the message composition window. 

I could have found the other threads. I might have figured out how to solve the problem myself. It would have taken me a while. I'm trying to do several things at once. Going through this process is time consuming, and often confusing. I decided to pose my question. I got a direct answer. 

Both ways lead to learning, one perhaps of a deeper kind, to understanding of the system. I would like to understand, but my immediate need is just to be able to use the system. If it is considered rude or unethical to ask questions without having gone to some lengths to try to solve the problem myself first, I will change my behavior. 

I might also just get frustrated and go out and by a Mac.

---

### Post by Eric Weir on 2008-04-19
> **T-Virus said:**
> How exactly are you trying to mount? I believe that mounting hard drive requires root access. Try this:

```

sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1

```That's in case if the hard drive you want to mount is recognised as "sdb1".

> **glennzo said:**
> How about **sudo /sbin/fdisk -l** to see what partition / drive he needs to mount? Kind of eliminates some of the guess work. 


Thanks to both of you. I did what glennzo suggested, then used that in the commands suggested by T-virus. No surprise, it worked.

Sincerely,

---

### Post by Ziggy72 on 2008-04-19
That was well said EricWeir!:) Did you actually solve the original problem?

---

### Post by Eric Weir on 2008-04-19
> **Ziggy72 said:**
> That was well said EricWeir!:) Did you actually solve the original problem?
Yes, I did. Or rather, glennzo and T-virus did.

And I really would like to understand. I certainly understand more than I did eight months ago. But I've got a long way to go> Meantime other things beckon.

Regards,

---

### Post by T-Virus on 2008-04-20
Great that it worked Eric.

> Yes, I did. Or rather, glennzo and T-virus did.

And I really would like to understand. I certainly understand more than I did eight months ago. But I've got a long way to go> Meantime other things beckon.

Regards,

As I understood you'd like to know what those commands posted mean? Well those are rather simple:

```
sudo mkdir /media/sdb1
```

Makes a directory called "sdb1" in /media.

```
sudo mount /dev/sdb1 /media/sdb1
```

mounts device /dev/sdb1 at the mount point you just created.

Cheers mate :)

---

### Post by glennzo on 2008-04-20
Eric, as far as the **mkdir** command goes when it relates to mounting a partition, you can mkdir anything. In other words it doesn't have to be mkdir /media/sdb1. It can be mkdir /media/ericweir, mkdir /media/olddisk, etc. The ericweir or olddisk part is just a name. I have a couple partitions on my system for XP, Vista and Ubuntu (I'm running Fedora right now). They are, as you may have guessed, /media/xp, /media/vista and /media/ubuntu. Just thought this may enlighten a bit.

---

### Post by T-Virus on 2008-04-20
> **glennzo said:**
> Eric, as far as the **mkdir** command goes when it relates to mounting a partition, you can mkdir anything. In other words it doesn't have to be mkdir /media/sdb1. It can be mkdir /media/ericweir, mkdir /media/olddisk, etc. The ericweir or olddisk part is just a name. I have a couple partitions on my system for XP, Vista and Ubuntu (I'm running Fedora right now). They are, as you may have guessed, /media/xp, /media/vista and /media/ubuntu. Just thought this may enlighten a bit.

Ah yes, I just like using names in old fashion way. :)

---

### Post by Eric Weir on 2008-04-20
> **Eric Weir said:**
> I did what glennzo suggested, then used that in the commands suggested by T-virus. No surprise, it worked.

Nothing quite like quoting yourself. But there's a reason.

When I just rebooted the system for the first time today, I found that the drive was again unmounted. How do I mount it so that it stays mounted?

Thanks,

---

### Post by T-Virus on 2008-04-21
I believe you're using Gnome? I'm not really familiar with it. KDE has this nifty app in System Settings called "Disk and Filesystem" which helps you mounting drives.

Well better wait for some Gnome users here.

---

### Post by Eric Weir on 2008-04-21
> **T-Virus said:**
> I believe you're using Gnome? I'm not really familiar with it. KDE has this nifty app in System Settings called "Disk and Filesystem" which helps you mounting drives.

Nope. Actually I'm KDE, too. I gave "file and disk systems" a try. I had no idea where to mount it. Tried /home, but it was already taken. Tried /media/hdb1, which seems to have worked. We'll see if it sticks after the next reboot.

This might be what's called "hijacking a thread," but since you're KDE, I have another issue. I want to get networking set up between this Kubuntu desktop and a laptop running XP through a router.

I thought the first thing to do would be to see what the current setup is, but I can't get Knetworkmanager to run. Whether I try to run it from the menu or the command line, absolutely nothing happens. 

Any clues?

---

### Post by Eric Weir on 2008-04-21
> **T-Virus said:**
> I believe you're using Gnome? I'm not really familiar with it. KDE has this nifty app in System Settings called "Disk and Filesystem" which helps you mounting drives.

Nope. Actually I'm KDE, too. I gave "file and disk systems" a try. I had no idea where to mount it. Tried /home, but it was already taken. Tried /media/hdb1, which seems to have worked. We'll see if it sticks after the next reboot.

This might be what's called "hijacking a thread," but since you're KDE, I have another issue. I want to get networking set up between the Kubuntu desktop and a laptop running XP through a router.

I thought the first thing to do would be to see what the current setup is, but I can't get Knetworkmanager to run. Whether I try to run it from the menu or the command line, absolutely nothing happens. 

Any clues?

---

### Post by glennzo on 2008-04-21
Eric, have you added the mounts to /etc/fstab? If not, create a new line for each partition that you want mounted at boot. For example, if you're dealing with /dev/sdb1 and are mounting it to /media/windows then the line would be
**/dev/sdb1 /media/windows ntfs-3g defaults 0 0**
If it's an EXT3 partition then the line would be[B]
/dev/sdb1 /media/windows ext3 defaults 0 0[/B]
Guess it wouldn't be EXT3 if it was Windows though, would it now?
Doesn't matter if you use Gnome or KDE or XFCE, etc.

---

### Post by T-Virus on 2008-04-21
> **Eric Weir said:**
> Nope. Actually I'm KDE, too. I gave "file and disk systems" a try. I had no idea where to mount it. Tried /home, but it was already taken. Tried /media/hdb1, which seems to have worked. We'll see if it sticks after the next reboot.

This might be what's called "hijacking a thread," but since you're KDE, I have another issue. I want to get networking set up between the Kubuntu desktop and a laptop running XP through a router.

I thought the first thing to do would be to see what the current setup is, but I can't get Knetworkmanager to run. Whether I try to run it from the menu or the command line, absolutely nothing happens. 

Any clues?

Hmm I haven't seen Microsoft OS in a long time. Anyway I tried running knetworkmanager myself right now and it didn't worked. I checked adept manager and it wasn't installed.

Maybe you're missing that package too?

---

### Post by T-Virus on 2008-04-23
So how did that went? Problem solved?

---

### Post by Eric Weir on 2008-04-23
> **T-Virus said:**
> So how did that went? Problem solved?

Not sure which problem you're asking about, getting the hd mounted or running KNetworkManager. Discouraging to hear that it wouldn't run for you either. It's not clear it's essential to getting my [K]ubuntu sytem networked. The entire area of networking is so confusing. I've got a [hardcopy] folder of printouts on setting up networking in Samba, networking [K]ubuntu as a client to a Windows [Samba] server, alternatives to Samba, etc., etc., etc. As I say, very confusing to this nongeek.

Still being frustrated by drive mounting. When I went to access it this morning, it was not mounted again. Went back into disks and file systems and may have finally succeeded in getting the drive permanently mounted. Then when I went to rename some files on the drive in preparation for backing up my /etc and /home folders to it I got "permission denied." Managed to get around that by running dolphin as root. I'd like to just be able to rename, move, copy files and folders on *my* system without having to give myself permission all the time.

All that said, I am in the process of downloading Ubuntu right now. I think I may have gotten myself in over my head with Kubuntu. I went to it shortly after my first install of Ubuntu last August [1] because I didn't like Ubuntu's color scheme, and [2] because I wanted to have more control over how application windows behaved. But I've begun to suspect that Kubuntu's amazing configurability is really beyond me at this point.

I feel like a traitor. When I get attached to something, even if it's a less than ideal something, I don't like letting go of it. But I think I'm gonna give Ubuntu a try again, to see if maybe it isn't a little easier for me, if the solutions it provides aren't actually acceptable, or maybe even better than what I could come up with on Kubuntu.

In any case, I haven't done much configuration of this installation of Kubuntu, so I'm not going to lose much. 

Another confession: if I'm frustrated by Ubuntu the way I have been by Kubuntu, I'm probably going to get myself a Mac.

This recent flurry of installing larger hard drives and doing a fresh new Kubuntu-only install was motivated by the fact that *everything* on my [K]ubuntu system had gotten excruciatingly slow. Judging form the way Thunderbird has been behaving since the new install, there's not going to be a huge improvement.

Forgive my rant. As I imagine is clear, I'm a very frustrated little boy. I love the open source idea, but I'm beginning to wonder if I'm up to it.

Regards,

---

### Post by Eric Weir on 2008-04-23
> **glennzo said:**
> Eric, have you added the mounts to /etc/fstab? If not, create a new line for each partition that you want mounted at boot. For example, if you're dealing with /dev/sdb1 and are mounting it to /media/windows then the line would be
**/dev/sdb1 /media/windows ntfs-3g defaults 0 0**
If it's an EXT3 partition then the line would be[B]
/dev/sdb1 /media/windows ext3 defaults 0 0[/B]
Guess it wouldn't be EXT3 if it was Windows though, would it now?
Doesn't matter if you use Gnome or KDE or XFCE, etc.
Are you suggesting this as a solution to the problem of getting my second hd permanently mounted, or as a way of getting networking going with my XP laptop? 

Is it possible to mount another machine, or drives or a printer on another machine?

Forgive my ignorance about all this stuff.

Regards,

---

