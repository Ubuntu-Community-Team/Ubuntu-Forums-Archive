---
title: "Ubuntu won't boot- error msg: &quot;fsck died with exit status 8??!!&quot;"
date: 2006-11-03
forum: General Help
---

### Post by bigjimlad on 2006-11-03
Help- I've ballsed up my ubuntu installation and haven't a notion how to get it going again...

Basically, I've my computer set to dual boot Windows XP and Ubuntu. I've just installed the new version of Ubuntu and had it all configured the way I like it, but hadn't partitioned my /home separately. I know- stupid, but, lessons learned and all that.

Anyway, I've a really old computer lying here that I wanted to run vector linux on, so I installed it's hard drive to my current computer as a slave and tried to install vector there, so I could then move it back to the old desktop (it doesn't have it's own CD drive so I couldn't install it in the normal manner- it's pretty old).

The whole installation seemed to hang after I'd partitioned hdb and while I was configuring the hardware, so I thought f*ck it, I'll try again later, took the CD out, and tried to boot into Ubuntu, when I got something along these lines:

fsck died with exit status 8
File system check failed.

Please repair the file system manually.
A maintenance shell will now be started.

What do I do to get it up and running again? I wasn't aware of having done anything that affected hda in the slightest. I thought maybe I ballsed up the boot loader or boot record or boot something, but XP is running fine- (ubuntu and xp were both on hda), it's just ubuntu that won't boot.

Please tell me there's a solution to this- I haven't lost anything vitally important apart from a few emails but I really don't want to have to reinstall and configure everything again, since I went through all this only a couple of days ago.

---

### Post by blabla on 2006-11-03
Baffling this one. I'd agree with you that hda couldn't have been touched. This leaves only the possibility that the Ubuntu file system was b*ggered before... 

BTW, what file system you using? Did you shut down properly the last time you used Ubuntu? Have you tried a manual repair?

Let us know, this is intriguing. 

Also, can you access hda/Ubuntu_partition with a live CD?

---

### Post by bigjimlad on 2006-11-03
Not sure what you mean by filesystem, /home is ext3 if that's what you mean? Sorry I'm not an expert. As far as I know I logged off properly..

Ubuntu live Cd doesn't see hda at all, good old knoppix does though.

How would I go about doing a manual install? I've googled it but if some one could point me in the direction of a good website to talk me through it that'd be great.

---

### Post by ingo on 2006-11-03
> **bigjimlad said:**
> Not sure what you mean by filesystem, /home is ext3 if that's what you mean? Sorry I'm not an expert. As far as I know I logged off properly..

Ubuntu live Cd doesn't see hda at all, good old knoppix does though.

How would I go about doing a manual install? I've googled it but if some one could point me in the direction of a good website to talk me through it that'd be great.

Well, you appear to be expert enough to know what ext3 is :p Other file systems include reiser, fat, nfts, etc.

A manual repair would involve going into the maintenance shell, logging in as root and entering the following command:

$ fsck.ext3 /dev/hda_your_partition -p

But before doing that I'd read the man page for fsck.ext3. Not sure whether that is included in the maintenance shell, but a quick google will sort you out. Try

$ man fsck.ext3 

anyway (as root).

HTH

---

### Post by bigjimlad on 2006-11-03
Thanks for the quick reply,

I tried


$ man fsck.ext3 

and it was fruitless,

then I tried


$ fsck.ext3 /dev/hda2 -p

And was told

/dev/hda2 recovering journal
/dev/hda2 clean 127356/331946 files 1312323/6086561 blocks

That's it, straight back to the command line.
Tried rebooting after this, and I'm back to the same error.

Is there something I'm missing?

---

### Post by ingo on 2006-11-03
Yeah, not surprised the man pages are not part of the maintenance shell...

So hda2 appears to be clean.

Oh dear, I just checked what error 8 stands for. This is what GRUB itself says:

8 : Kernel must be loaded before bootingThis error is returned if GRUB is told to execute the boot sequence without having a kernel to start.       I was on totally the wrong track (my own fault for getting posts confused! Sorry about that).

So all you need is the path to the kernel and Bob's your uncle. Have a look at this great little howto

[http://www.smop.co.uk/node/43](http://www.smop.co.uk/node/43)

and come back in case of any questions.

HTH

---

### Post by ingo on 2006-11-04
morning bigjimlad, any news yet on the Ubuntu front?

PS.: what I forgot to say about the link is that you should only follow it until you have found and booted Ubuntu.

---

### Post by bigjimlad on 2006-11-05
Hello Ingo,

I noticed a line when I'm at the maintenance shell saying something along the lines of "control D" to continue booting, can't remember the wording exactly but if I press that a couple of times it will boot back into ubuntu, so I've saved my files at least.

But I'm still getting the error anytime I boot, so I'm still trying to figure it out. I tried using the link you gave me, but at this stage

[INDENT]geometry (hd0)[/INDENT]

grub always replies 

[INDENT]Error 21: Selected disk does not exist[/INDENT]

I've tried this command for hd0, hd1, hd2, hda, hdb, any little combination i can think of, and always get the same error message.

On another forum, I saw someone had a similar problem and fixed it by going through the installation process again, but leaving all partitions as they were and just letting grub reinstall itself (if that's the correct way of putting it? I'm sure you know what I mean).

I'll probably try this late but I'm still backing up /home so I can't do it right now.

Frustrating, though every time something goes wrong you learn a bit more in the process of fixing it.

---

### Post by ingo on 2006-11-05
Disk does not exist? Weird...

The quickest way I know of reinstalling GRUB is to download the first Open Suse CD. Go through the install process and at some stage you will be asked whether you want to install or "Other". Select "Other", go into "Repair", select "Expert Tools" and there you will find "Reinstall Bootloader", i.e. GRUB.

It will then identify your bootable partitions. With Open Suse 10.1 you can only choose one, but I believe 9.2 & 9.3 will list all available boot partitions in your GRUB. 

I am sure there are better ways of reinstalling GRUB, but that's what I've been doing when things went out of control.

Better luck next time :)

Ingo

---

### Post by ingo on 2006-11-05
hang on, check this

[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

you can reinstall grub from you existing ubuntu live cd :)

---

### Post by Watergeus on 2006-11-05
Kind of funny...have exactly the same problem after installing Debian on another partition. Had too many problems with Edgy Eft. Decided to go with Debian untill the Edgy "Soft Lockup detected" is solved using the same /home.

Probably the cause is that while installing Debian I installed a new grub instead of extending my normal one.
I can start Debian, but not Ubuntu at this moment.

Did you try to use the grub-command line as root (aka sudo?). It worked for me. Just typing 'geometry (hd'  and 'tab' was enough to get some results. 

Will try the last suggestion with the Debian-netinstall disk as I don't have the Ubuntu disk with me...

Paul.

This with the Debian-netinstall didn't work.

---

### Post by Watergeus on 2006-11-06
Solved my problem by having a closer look to my /etc/fstab.

They say, if I remember correctly, that you should maintain this file manually. After I installed Debian on another partition, there was something wrong with the update of it.

This is how, for a part my /etc/fstab looks at this moment.

# /dev/sda5 = Ubuntu part (ext 32, 20Gb)
UUID=a124ac36-cbae-409e-8f72-23ef3879f9ae       /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1  = Dell toolbox (fat16, 47Mb)
UUID=07D6-0703                                  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1

I was used seeing only the lines like:
/dev/sda1    /media/sda1   vfat   defaults,utf8,umask=007,gid=46  0  1

And now I see that the understandable /dev/sda is replaced by UUID's. This is new in Ubuntu Edgy. See [http://lems.kiskeyix.org/puntoyaparte/article.php?story_id=66](http://lems.kiskeyix.org/puntoyaparte/article.php?story_id=66) for a short explanation of the pro's. 

When I installed Debian, Debian changed the UUID's back to the /dev/sda for my Ubuntu partition and commenting the UUID-line. Uncommenting the UUID line and commenting the /dev/sda line was enough not to the the "exit status 8" any more.

---

### Post by bigjimlad on 2006-11-07
Sweet jebus those posts might as well have been written in japanese haha...

It's all a learning curve I suppose. Thanks for the reply, I'll have a stab at that stuff now.

---

### Post by ingo on 2006-11-07
> **ingo said:**
> hang on, check this

[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

you can reinstall grub from you existing ubuntu live cd :)

you stick with the link above and you'll be alright...

---

### Post by bigjimlad on 2006-11-09
.

---

### Post by Krymzon on 2007-06-26
> **Watergeus said:**
> Solved my problem by having a closer look to my /etc/fstab.

They say, if I remember correctly, that you should maintain this file manually. After I installed Debian on another partition, there was something wrong with the update of it.

This is how, for a part my /etc/fstab looks at this moment.

# /dev/sda5 = Ubuntu part (ext 32, 20Gb)
UUID=a124ac36-cbae-409e-8f72-23ef3879f9ae       /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1  = Dell toolbox (fat16, 47Mb)
UUID=07D6-0703                                  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1

I was used seeing only the lines like:
/dev/sda1    /media/sda1   vfat   defaults,utf8,umask=007,gid=46  0  1

And now I see that the understandable /dev/sda is replaced by UUID's. This is new in Ubuntu Edgy. See [http://lems.kiskeyix.org/puntoyaparte/article.php?story_id=66](http://lems.kiskeyix.org/puntoyaparte/article.php?story_id=66) for a short explanation of the pro's. 

When I installed Debian, Debian changed the UUID's back to the /dev/sda for my Ubuntu partition and commenting the UUID-line. Uncommenting the UUID line and commenting the /dev/sda line was enough not to the the "exit status 8" any more.

I've just had a very similar problem. Installed Feisty on a clean computer a week ago and added Debian Etch today. Ubuntu's GRUB is in the Master Boot Record, Debian's on its partition. 

My mistake was to make Debian reformat the clear partition Ubuntu prepared for it. Until I read your post I hadn't known Ubuntu switched to using UUIDs in /etc/fstab. Reformatting by Debian caused UUID to change and, as Ubuntu tried to mount Debian's partition using the old UUID, it resulted in the *fsck died with exit status 8*

Thank you very much for posting your solution! I've just commented out the line with the old UUID and now both systems run great :D

BTW, I find it **bad** that problems with mounting an unneeded partition make system fail like this. Terminal asking me to use apt-get to install apt-get, vi not available... Even after proceeding with normal boot it was bad. It didn't even try to mount my /home and I thought this partition had been damaged.

---

### Post by irlandes on 2008-02-18
> **Krymzon said:**
> I've just had a very similar problem. Installed Feisty on a clean computer a week ago and added Debian Etch today. Ubuntu's GRUB is in the Master Boot Record, Debian's on its partition. 

My mistake was to make Debian reformat the clear partition Ubuntu prepared for it. Until I read your post I hadn't known Ubuntu switched to using UUIDs in /etc/fstab. Reformatting by Debian caused UUID to change and, as Ubuntu tried to mount Debian's partition using the old UUID, it resulted in the *fsck died with exit status 8*

Thank you very much for posting your solution! I've just commented out the line with the old UUID and now both systems run great :D

BTW, I find it **bad** that problems with mounting an unneeded partition make system fail like this. Terminal asking me to use apt-get to install apt-get, vi not available... Even after proceeding with normal boot it was bad. It didn't even try to mount my /home and I thought this partition had been damaged.

Since this was not clear to me -- my solution did not involve commenting and uncommenting lines, though the end result was the same -- I am going to add my experience.

I had  this problem in Mexico last fall when I loaded Kubuntu on an e-machine, which already had Mandriva 2007.  when it booted, error 8, and give me a maintenance shell. I worked around it. Now that I know what is wrong, it will be quick to fix when I get back to Mexico.

Yesterday, I had this problem when I installed Kubuntu 7.10 on sda8, with Mandriva LE 2005 on sda5; and Kubuntu 7.04 on sda7, sda11 a large FAT 32 partition for storage, sda1 XP, and a couple partitions waiting for a distro.  Fsck error 8, shell, CTRL-D did not work, I had to type:  shutdown -r now    at the prompt, then it booted. Sigh!

Also, all my /mnt links from sda7 Kubuntu 7.04 were dead.  I had no links to storage at all.

When I boot Mandriva, it comes up. When I boot XP, it comes up.  When I boot Kubuntu 7.10 it comes up.  When I boot 7.04, it doesn't come up, but has error 8. Thus, the error is NOT grub at all.

I ran sudo /sbin/vol_id -u /dev/sdaN  through all N partitions, and compared the volume i.d. for each to that supplied in the sda7 Kubuntu 7.04 /etc/fstab   (N = partition number)

The uuid for sda8, which now controls the grub, has changed because of the formatting of that partition during installation, and thus is different from /etc/fstab that was made previously when I installed Kubuntu 7.04 last year.

I remarked  out the old UUID number in /etc/fstab of sda7, Kubuntu 7.04, typed in the new, correct UUID which I obtained from:  

sudo /sbin/vol_id -u /dev/sda7

and when I re-booted it worked perfectly.  Of course, this was no simple task, because it took me a while to spot a typo so it kept crashing the same.

My simple minded confusion was, there was nothing to uncomment, so I did not understand what the problem was. I know, I know...   :)

So, this is NOT a grub issue, it is most distinctly a UUID change on the partition where the new Kubuntu is installed, and the old /etc/fstab's, if they use UUID's must all reflect that UUID change, or fsck crashes when it hits the erroneous volume ID and leaves a total mess of things.

I note with interest while checking /boot/grub/menu.lst that the installer sort of goes crazy and adds a whole string of unneeded grub call-outs which happen to be filled with errors. I am going back next and clean up that  mess.

My late father used to have a saying:  Don't look a gift horse in the mouth.  So, while I hate to criticize an organization that is giving  us an excellent free distro, even in some cases paying shipping to get it to people, I do consider this a bug to harm a previously installed distro already on the system.  The idea is okay, but maybe there should be an error message addition to give people a clue to a known problem, if there is no easy fix.

---

