---
title: "Writing to ntfs resets automagically"
date: 2015-04-12
forum: General Help
---

### Post by andrehsu6 on 2015-04-12
Reading of a ntfs drive is fine, but when I write to it, it appears as though if it written the data correctly. But on windows, it appears as if nothing happened. Then when you reboot again into linux, it appears in the way it appeared in windows, as though if nothing happened. Very strange indeed. Mounted C: in /media/OS and D: in /media/Data

---

### Post by Vladlenin5000 on 2015-04-12
You shouldn't be writing to the Windows system partition, Windows doesn't like it. That said, how are you monting whatever NTFS partition with that peculiar issue?

---

### Post by andrehsu6 on 2015-04-12
> **Vladlenin5000 said:**
> You shouldn't be writing to the Windows system partition, Windows doesn't like it. That said, how are you monting whatever NTFS partition with that peculiar issue?
I mounted it in the install process, so I assume via fstab

> **Vladlenin5000 said:**
> You shouldn't be writing to the Windows system partition, Windows doesn't like it. My user profile on windows was recently corrupted after I did something in linux. Is that related? I though people said ntfs-io support in linux is good.

Also, does using ntfsprogs or ntfs-3g matter?

---

### Post by Impavidus on 2015-04-12
If you want to share files between Ubuntu and Windows there isn't really any other option than storing them on NTFS. Have you made sure both Ubuntu and Windows are properly shut down? If (less likely) you don't properly shut down Ubuntu, the changes may not be written to disk and Windows won't see them, if (more likely) Windows wasn't properly shut down before, but in some kind of hibernation (like Windows 8's fast startup), it doesn't reread the disk, but just assumes no files have changed.

It's easy to damage Windows files from Linux. The safeguards Windows puts in place don't work when you access the partition from Linux. I'd advise not to mount the Windows C partition (or just in read only mode), but only a shared data partition. Windows may call that one the "D drive", or some other letter. This is less likely to cause any corruption.

---

### Post by Holger_Gehrke on 2015-04-12
Are you using Windows 8 and have not disabled Fast Boot ? If that's the case please see [this]("http://askubuntu.com/questions/452071/why-disable-fast-boot-on-windows-8-when-having-dual-booting").

---

### Post by haplorrhine on 2015-04-12
> **andrehsu6 said:**
> Reading of a ntfs drive is fine, but when I write to it, it appears as though if it written the data correctly. But on windows, it appears as if nothing happened. Then when you reboot again into linux, it appears in the way it appeared in windows, as though if nothing happened. Very strange indeed. Mounted C: in /media/OS and D: in /media/Data

I didn't follow at first.  So Windows isn't seeing - and seems to be reversing - the changes made by Ubuntu?

If the disk space usage reverses too, then Ubuntu probably isn't writing to it.

---

### Post by Morbius1 on 2015-04-12
Can we go back the the very first response you got and post the output of the following command so that you can answer the question of how it was mounted:
```
cat /etc/fstab
```
And can you give an example of the file name of something you saved in Linux that Windows cannot deal with.

---

### Post by andrehsu6 on 2015-04-12
I restarted windows to boot into grub, so fast boot really shouldn't matter.

Windows seem to be reversing it. Only when you view the files in Windows do they reset to how it was last time windows was booted.

Annnndd it fixes itself. Solved I guess?

---

### Post by Holger_Gehrke on 2015-04-13
If fastboot is active, windows writes its internal state to the hibernation file during shutdown and restores it on boot. This includes information about the filesystems, like filenames, used and free block, what files blocks belong to. On reboot it gets that information from the file instead of collecting it from all over the disk.. This works fine as long as nothing changes while windows is not running ...

---

### Post by coffeecat on 2015-04-13
> **andrehsu6] I restarted windows to boot into grub, so fast boot really shouldn't matter. [/quote]

That is a mistaken assumption.

[QUOTE=Holger_Gehrke said:**
> Are you using Windows 8 and have not disabled Fast Boot ? If that's the case please see [this]("http://askubuntu.com/questions/452071/why-disable-fast-boot-on-windows-8-when-having-dual-booting").

@andrehsu6, did you read the link that Holger_Gehrke posted? Are you using Windows 8? If so, you need to disable fast boot.

And if you hibernate Windows 7 and then write to a NTFS partition from Ubuntu, the next time you boot into Windows it will delete the files you wrote from Ubuntu. General principle: if you share a NTFS partition between Windows and Ubuntu (or any Linux distro), you must always shut Windows down properly. In Windows 8, that means disabling fast boot.

---

### Post by andrehsu6 on 2015-04-13
I have always assumed that the kernel is restarted during a restart. Is there  a source to confirm what you said? Also, when I  mounted it myself, it didn't throw any warnings about windows not shutting down. (warnings that appear when I shutdown instead of reboot)

[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
This pages notes how fast boot doesn't affect restarts.

---

### Post by Holger_Gehrke on 2015-04-13
From the horses mouth: [http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)

---

### Post by Vladlenin5000 on 2015-04-13
Nothing you linked is relevant for the issue in discussion. All that assumes, as usual, Windows as the only OS and, as such, the partially hibernated partitions can't possibly be accessed let alone written to unless in proper Windows OS section. 
A smart person would actually read and try to understand what has been said which is (should be) quite easy to understand. But you have a lot of misconceptions, as pointed out already.

---

### Post by andrehsu6 on 2015-04-13
How quick of people to jump to insults. Well, insults aside, lets look at the link "[http://blogs.msdn.com/b/b8/archive/2...windows-8.aspx]("http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx")". It is apparent you did not bother to read the article and decide to jump to conclusions. If you had read it, you would have seen at the bottom:
[IMG]http://i.imgur.com/VzIjBGT.png[/IMG]
That it says restart is **effectively a cold boot.**
So thank you for supporting what I said.
And if anyone was noticing, I clearly stated how the warning when mounting NTFS** does** exist when I do a shutdown, but **doen't **appear when I do a restart.

---

### Post by Vladlenin5000 on 2015-04-13
My last post can be constructed as an insult if - and only if - the cap fits.
Now, if you want to keep doing things the way you think is right, don't listen to others because you know everything already, why bother posting?

---

### Post by andrehsu6 on 2015-04-13
Its not that I am unwilling to change, its that there is substantial evidence to suggest that fast boot isn't the culprit,and instead the problem might lie somewhere else.

---

### Post by coffeecat on 2015-04-13
andrehsu6, you an argue to the contrary as much as you want, but you have a choice. Either accept the advice you have been given, disable fast boot in Windows 8 and see if that solves your problem. Or you can ignore the advice of people who have hands on experience with Windows 8 and Ubuntu dual-boots (myself included) and go your own way.

I disabled fast boot in Windows 8 and that solved all the issues I was seeing with the shared NTFS partition.

---

### Post by andrehsu6 on 2015-04-13
I am unable to test whether or not disabling fast boot affects NTFS IO, since I have did a full disk reinstall(due to other reasons)
Thx anyway.

---

### Post by andrehsu6 on 2015-04-27
So I disabled fast startup and the issue persists.
Windows 8.1
Ubuntu 15.04 Vivid Vervet

---

### Post by coffeecat on 2015-04-27
Did you select shutdown or reboot from Windows 8? If you select reboot, it doesn't shutdown properly even if you disable fast boot. If you wish to go from Windows to Ubuntu you must shutdown Windows and then cold start Ubuntu.

---

### Post by andrehsu6 on 2015-04-27
> **coffeecat said:**
> Did you select shutdown or reboot from Windows 8? If you select reboot, it doesn't shutdown properly even if you disable fast boot. If you wish to go from Windows to Ubuntu you must shutdown Windows and then cold start Ubuntu.
Did both reboot and shutdown, writing file between each attempt. All the files disappear upon booting into windows

---

### Post by andrehsu6 on 2015-04-28
Help...

---

### Post by Mark Phelps on 2015-04-28
Folks kept telling you to disable Fast Boot -- which is NOT the problem as it is unrelated to hibernation.  You then said you disabled FastStartup -- which IS the problem.  So, which actually got disabled, Fast Boot or FastStartup?

---

### Post by andrehsu6 on 2015-04-28
They are the same thing, assuming you are talking about this: [http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)

---

### Post by andrehsu6 on 2015-04-28
Picture for clarification:
[IMG]http://i.imgur.com/YzB5thf.png[/IMG]

---

### Post by coffeecat on 2015-04-28
You appear to have disabled fast startup correctly according to your screenshot. That should prevent Windows from deleting files saved to a NTFS partition shared with Windows 8. So...

What is the partition you are writing to from Ubuntu? 

How are you mounting it from Ubuntu? You were asked this earlier in the thread but I can't see that you ever answered this point.

---

### Post by Mark Phelps on 2015-04-28
> **andrehsu6 said:**
> They are the same thing, assuming you are talking about this: [http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)

Despite what that says, they are NOT the same.  Fast Boot is a BIOS/UEFI option; FastStartup is a Windows option.  While they may result in the same thing, they are configured separately.

But ... your screenshot shows you have disabled FastStartup.  Just be sure to use ShutDown to end the Windows session, as using Restart ignores the FastStartup setting.

---

### Post by andrehsu6 on 2015-04-28
> **coffeecat said:**
> You appear to have disabled fast startup correctly according to your screenshot. That should prevent Windows from deleting files saved to a NTFS partition shared with Windows 8. So...

What is the partition you are writing to from Ubuntu? 

How are you mounting it from Ubuntu? You were asked this earlier in the thread but I can't see that you ever answered this point.
I wrote to both the OS drive C: and my data drive D:, and they both reseted upon booting into windows.
I mounted it during the ubuntu install, one in /media/OS and the other in /media/Data, so here is the content of the fstab file.\/
```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=60fc342b-166a-44e5-86b6-b34772da764d /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=FC02-2C32  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sda7 during installation
UUID=b6cbf28e-c360-441f-bf6a-0a0417b4c39f /home           ext4    defaults        0       2
# /media/Data was on /dev/sda5 during installation
UUID=1A5CD6655CD63AE9 /media/Data     ntfs    defaults,umask=007,gid=46 0       0
# /media/OS was on /dev/sda4 during installation
UUID=2824375D24372D66 /media/OS       ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda8 during installation
UUID=5e463ef4-8d33-4bea-9525-e24f2d44166e none            swap    sw              0       0
```

---

### Post by Morbius1 on 2015-04-29
> UUID=1A5CD6655CD63AE9 /media/Data     ntfs    defaults,umask=007,gid=46 0       0
Let's focus on this partition since you really shouldn't be writing to your Windows OS partition anyway. That looks fine except it's missing an option and it's something I asked about in my first response. What are the names of the files you are saving in Linux to this partition? 

If they contain some of these characters Windows doesn't know what to do with the file:
> ” * / : < > ? \ |
You can prevent that from happening by adding another option to the list:
> UUID=1A5CD6655CD63AE9 /media/Data     ntfs    defaults,umask=007,gid=46[COLOR=#0000cd]**,windows_names**[/COLOR] 0       0
Then unmount the partition:
```
sudo umount /media/Data
```
And remount it with this:
```
sudo mount -a
```

Note: This isn't magic. It's not going to fix what is already there. All it will do is prevent you from saving a file in Linux with a name that contains those "special" characters.

---

### Post by andrehsu6 on 2015-04-29
> **Morbius1 said:**
> -snip-
It doesn't work, even when I name files using windows's naming convention.
Specifically "hope this works.txt"
Is there a specific reason not to write to C: other than "its not a good idea"?
How about the user folder? (C:\Users\USERNAME)

---

### Post by Morbius1 on 2015-04-29
> **andrehsu6 said:**
> It doesn't work
"It doesn't work" meaning that if you were to save a file with a name containing special characters you don't get an error message telling you so?

If that's the case your system really is hosed up. Can't reproduce that symptom but if I had to guess there is something wrong with your install of ntfs-3g.

If you mean it had no affect as you indicated by saving a file with no special characters ( but with spaces in the name ) then this was not the issue to begin with. Can't reproduce that symptom either.

Hmm.....

---

### Post by andrehsu6 on 2015-04-29
> **Morbius1 said:**
> "It doesn't work" meaning that if you were to save a file with a name containing special characters you don't get an error message telling you so?

If that's the case your system really is hosed up. Can't reproduce that symptom but if I had to guess there is something wrong with your install of ntfs-3g.

If you mean it had no affect as you indicated by saving a file with no special characters ( but with spaces in the name ) then this was not the issue to begin with. Can't reproduce that symptom either.

Hmm.....
It means it says the name is invalid if I have special characters, and even if the file is named correctly, it still resets upon booting into windows.
Does it matter that I am on a laptop?

---

### Post by coffeecat on 2015-04-29
I'm going to ask what may seem like a silly question only because if you have disabled fast start-up, you should not be seeing this problem. 

Going back to the picture you posted in your post #25. Did you remember to click on the "save changes" button after you unticked "Turn on fast start-up"?

I only ask because I doubt whether there are many here who haven't at some point forgotten to save configuration changes and wondered why the change hasn't taken effect.

---

### Post by andrehsu6 on 2015-04-29
> **coffeecat said:**
> I'm going to ask what may seem like a silly question only because if you have disabled fast start-up, you should not be seeing this problem. 

Going back to the picture you posted in your post #25. Did you remember to click on the "save changes" button after you unticked "Turn on fast start-up"?

I only ask because I doubt whether there are many here who haven't at some point forgotten to save configuration changes and wondered why the change hasn't taken effect.
Yes, I did click save changes.

---

### Post by andrehsu6 on 2015-05-02
So for some strange reason, a file that previously disappeared now reappeared in windows. This seemed to have happened after a hibernation. Does it matter that I am using expresscache on windows?

---

### Post by andrehsu6 on 2015-05-02
Hibernate doesn't seem to work for windows
If you were to hibernate, then boot up into grub, then choose windows, a new session would be started. The thing is that windows sessions started with this method will not reset the files.
Help?

---

### Post by andrehsu6 on 2015-05-08
Someone suggested that it might be due to missing libraries or permission settings that prevent the files from showing in windows. Solving these might be the solution?

---

### Post by Morbius1 on 2015-05-08
You wrote - in chronological order:
> My user profile on windows was recently corrupted after I did something in linux.
Then you marked this solved:
> Re: [SOLVED] Writing to ntfs resets automagically 
But you continued to write to the OS partition:
> I wrote to both the OS drive C: and my data drive D:
Then this happened:
> So for some strange reason, a file that previously disappeared now reappeared in windows.
And this:
> Hibernate doesn't seem to work for windows
If you were to hibernate, then boot up into grub, then choose windows, a new session would be started. The thing is that windows sessions started with this method will not reset the files.
And finally this:
> Someone suggested that it might be due to missing libraries or permission settings that prevent the files from showing in windows. Solving these might be the solution? 

When you implement the changes that "Someone" suggested let us know how it worked out.

If it doesn't then I would suggest you ask your question in a Windows forum or at least get back in touch with this "Someone" person..

---

### Post by andrehsu6 on 2015-05-08
> **Morbius1 said:**
> ...
I did ask on a windows forum.
First went to answer.microsoft.com, they said it was more of a IT pro question, so I went to technet.
Technet said Microsoft doesn't support linux writing to windows, and that they are windows IT pros, so they couldn't help me. It was he who mentioned that it might be due to permissions.

---

### Post by Morbius1 on 2015-05-08
> Does it matter that I am using expresscache on windows? 

From [https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1280574](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1280574)
> I have Ubuntu 13.10 and Windows 8.1 installed, both 64-bit (dual boot).  Whenever I create or copy files to any of the NTFS partitions from  Ubuntu, these files get deleted once I login to Windows. When I login to  Ubuntu again, the files are not there. I shut down Windows properly and  do not hibernate. I have disabled fast startup option in Windows, and  Fastboot from BIOS. So it is not a hibernation problem. The same problem  occurred when using Linux Mint.
.....
OK, so after some research I found the following:
I have SSD caching enabled in Windows, but through a program called ExpressCache
....
That was it ! I uninstalled ExpressCache and the problem was gone, so  was SSD caching. I tried re-installing it but the problem occurred  again. I think I will have to give up SSD caching :(
And from the good people who invented ntfs-3g: [http://www.tuxera.com/community/ntfs-3g-faq/#locale3](http://www.tuxera.com/community/ntfs-3g-faq/#locale3)
> If your computer has a SSD plugged in, it might be used by Windows as a  cache controlled either by the hardware (“Intel Fast Response  Technology”) or by software (“Expresscache”, “ReadyCache”, etc.). This  feature is generally not compatible with both Windows and Linux and you  may have to disable it.

---

### Post by andrehsu6 on 2015-05-09
So apparently the problem was because of express cache. Thanks to anyone who helped.

---

