---
title: "Xubuntu Trusty Cold Boot Failure"
date: 2014-07-27
forum: General Help
---

### Post by viking777 on 2014-07-27
I have Xubuntu 14.04 installed on a Fujitsu Lifebook laptop. I installed it when trusty was first released, and all was well, but lately I get a failure to boot nearly every time I do a cold boot. It is ONLY cold boots that are affected, not reboots, and it seems to be related in some way to the length of time the machine is switched off for, though I haven't narrowed that down to a specific time yet, but as an example if you shut down for 5 minutes and then boot up, it starts normally. Also it only affects Xubuntu (I also have Mint17 and Manjaro installed they both boot normally cold or otherwise). I don't use splash screens so I can see a repeating pattern of error messages flashing before me which are nearly all similar to this:

```
Jul 27 11:15:32 fujitsu kernel: [ 4604.450289] task: ffff8800ad9b0000 ti: ffff880192c1e000 task.ti: ffff880192c1e000
Jul 27 11:15:32 fujitsu kernel: [ 4604.450335] RIP: 0010:[<ffffffffa07fb184>]  [<ffffffffa07fb184>] rfs_fsrename+0x334/0x6c0 [redirfs]
Jul 27 11:15:32 fujitsu kernel: [ 4604.450381] RSP: 0018:ffff880192c1fc18  EFLAGS: 00010246
Jul 27 11:15:32 fujitsu kernel: [ 4604.450409] RAX: 0000000000000000 RBX: ffff88016bbc5cf0 RCX: 0000000000000000
Jul 27 11:15:32 fujitsu kernel: [ 4604.450453] RDX: 000004300e938077 RSI: ffff8800ad9b0000 RDI: ffff8801909bc300
Jul 27 11:15:32 fujitsu kernel: [ 4604.450485] RBP: ffff880192c1fc78 R08: ffff880192c1e000 R09: 0000000000000000
Jul 27 11:15:32 fujitsu kernel: [ 4604.450516] R10: 0000000000000000 R11: ffffea000656e9c0 R12: ffff8800bd4489c0
Jul 27 11:15:32 fujitsu kernel: [ 4604.450546] R13: ffff88016bbc5cf0 R14: 0000000000000000 R15: ffff8800bd4489c0
Jul 27 11:15:32 fujitsu kernel: [ 4604.450575] FS:  00007f4b62d84700(0000) GS:ffff88019f240000(0000) knlGS:0000000000000000
Jul 27 11:15:32 fujitsu kernel: [ 4604.450608] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jul 27 11:15:32 fujitsu kernel: [ 4604.450631] CR2: 0000000000000000 CR3: 00000000d3e64000 CR4: 00000000001407e0
Jul 27 11:15:32 fujitsu kernel: [ 4604.450660] Stack:
Jul 27 11:15:32 fujitsu kernel: [ 4604.450669]  ffff8801400b5918 ffff880177b0ebc8 ffff880073995d00 ffff88016bbc8780
Jul 27 11:15:32 fujitsu kernel: [ 4604.450702]  0000000000000000 ffff8801909bc300 ffff880065f70180 ffff88016bbc5540
Jul 27 11:15:32 fujitsu kernel: [ 4604.450734]  ffff8800bd4489c0 ffff88016bbc5cf0 ffff88016bbc8480 ffff8800bd4489c0
Jul 27 11:15:32 fujitsu kernel: [ 4604.450766] Call Trace:
Jul 27 11:15:32 fujitsu kernel: [ 4604.450782]  [<ffffffffa07ff03b>] rfs_rename+0x2ab/0x320 [redirfs]
Jul 27 11:15:32 fujitsu kernel: [ 4604.450811]  [<ffffffff817224f2>] ? mutex_lock+0x12/0x2f
Jul 27 11:15:32 fujitsu kernel: [ 4604.450836]  [<ffffffff811ca1fb>] vfs_rename+0x54b/0x5d0
Jul 27 11:15:32 fujitsu kernel: [ 4604.450859]  [<ffffffff811cd465>] SYSC_renameat+0x3b5/0x410
Jul 27 11:15:32 fujitsu kernel: [ 4604.450886]  [<ffffffff81020d45>] ? syscall_trace_enter+0x145/0x250
Jul 27 11:15:32 fujitsu kernel: [ 4604.450912]  [<ffffffff811ce67b>] SyS_rename+0x1b/0x20
Jul 27 11:15:32 fujitsu kernel: [ 4604.450935]  [<ffffffff8172c87f>] tracesys+0xe1/0xe6
Jul 27 11:15:32 fujitsu kernel: [ 4604.450956] Code: a0 4a 8b 34 e0 e8 7d 0e 00 00 85 c0 41 89 c6 0f 85 d0 fe ff ff 83 c3 01 41 3b 5d 08 7c b9 45 31 f6 e9 bf fe ff ff 90 48 8b 40 50 <48> 8b 38 e8 94 5f 00 00 49 89 c5 e9 d5 fd ff ff 48 83 7d c0 00 
Jul 27 11:15:32 fujitsu kernel: [ 4604.451079] RIP  [<ffffffffa07fb184>] rfs_fsrename+0x334/0x6c0 [redirfs]
Jul 27 11:15:32 fujitsu kernel: [ 4604.451108]  RSP <ffff880192c1fc18>
Jul 27 11:15:32 fujitsu kernel: [ 4604.451123] CR2: 0000000000000000
Jul 27 11:15:32 fujitsu kernel: [ 4604.456896] ---[ end trace 9568477d23da88d6 ]---
```

TBH I believe the kernel.log entries above came from a shut down since the start up ones are never logged - perhaps because I always have to force a shutown/reboot with the power button or I would wait all day. The above messsage repeats over and over and eventually changes to something like -

```
Lowering kernel.perf_event_max_sample_rate.
``` Whatever that is.

It then continues to lower this setting in steps until it gets down to a value of about 500 at which point it gives up with that and just repeats the previous message over and over until I have to force a shutdown.

I have also seen the message:

```
/dev/sda9 not found
```

on occasions, though much less frequently. (/dev/sda9 is the root partition).

I have performed endless disk and memory checks using a wide range of tools and every single one of them tells me that the partition and memory are perfect. Given that the message above is from kernel.log, it would seem to indicate that it is a kernel problem so I should mention that I have kernel 3.13.0-31 and 3.13.0-32, and that they are both affected.

It isn't a huge problem because it always starts normally the second time I boot it, but even so I would like to know if anyone shed any light on this weird behaviour.

BTW this has absolutely nothing to do with suspend or hibernate - I never use them.

---

### Post by Bashing-om on 2014-07-27
viking777; Hi !

How about this for a thought ?
A damaged initrd.img ?? If your previous kernel works you can rebuild the later initrd.img. e.g. (change the kernel version as appropriate):
```

sudo update-initramfs -u -k 2.6.35-28-generic

```
Else no kernel booting properly, try from a full CHange Root environment to rebuild initramfs.

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by viking777 on 2014-07-28
Thanks very much for the suggestion Bashing-om, I have rebuilt the initramfs for both installed kernels as you suggested and will let you know if it makes a difference. However, given that this error only occurs once or twice a day it might take me some time to decide if it is better or not.

Thanks anyway ;)

---

### Post by viking777 on 2014-07-28
Actually it didn't take too long to find out the answer, the very next cold boot the error returned. 

Thanks anyway, I realise what an obscure piece of nonsense this is, almost impossible to troubleshoot or I would have done it myself by now.

---

### Post by Bashing-om on 2014-07-28
viking777; Like this,

Situations like this are trying, to say the least but what an opportunity to learn !
There is no such thing as learning enough about this our operating system by choice. I do welcome the opportunity.

Presently, what we know is that there is a 'glitch' in the kernel activation process. We do not know where, why, or how. So, let's look and see what the system is telling.
Have some long patient reads in the log files ( best done from the log file viewer, if that is installed) .

For starters have a read in the log files: /var/log/dmesg, /var/log/kern.log, /var/log/syslog.

And we will discuss what you find of interest.

[INDENT][INDENT][INDENT]reading is good
[/INDENT][/INDENT][/INDENT]

---

### Post by viking777 on 2014-07-29
> Have some long patient reads in the log files 

Already done long before I started this thread my friend - every single log file in /var/log has been read through, the only results of any relevance at all are those given in my opening post. 

Out of interest the machine booted normally this morning after being off all night long, so it isn't even *every* cold boot that this is happening.:confused:

I thank you once again for your help.

Edit. As a possible workround I have decided to try a new kernel. I've installed 3.16.0-6 from Utopic. It works normally in all respects so far, but as to whether it will cure the boot problem or not I will either find out later today (if it is a failure) or I might have to wait a week or more (if it is a success).

In either case I will post back the results.

---

### Post by viking777 on 2014-07-29
Well that took even less time than the previous test. 

First cold boot - normal.
Second cold boot (30 mins later) - /dev/sda9 does not exist
Third cold boot (immediately after the second) - normal

So it is not the kernel then, this is just too crazy for words.

---

### Post by JKyleOKC on 2014-07-29
Is it always "sda9" that's not available? If so, what's different about that partition?

It sounds as if some sort of timing error could be at the bottom of things; could even be hardware related...

---

### Post by viking777 on 2014-07-29
Hello Jim, thanks for the reply.

Yes it is always sda9 that is the problem, but then again sda9 is the root partition for Xubuntu so it can't find its own root. 

I have done several tests on that partition (and I am 20 minutes away from finishing yet another one - smartctl long test) they never show any errors though.

Is there anything different about it? Not at all, a bog standard ext4 partition.

I really don't know what to make of it. Ultimately it might require a reinstallation, but I am reluctant to do that for a problem that only usually occurs once a day. To many 'personalisations' built into it - I would hate to start that business all over again!

---

### Post by viking777 on 2014-07-29
As expected the results of the smartctl long test for sda9 were absolutely normal, overall pass, every parameter way, way above the threshold value, no problem at all. Gparted, fsck and badblocks all agree with these findings, there is simply nothing wrong with this partition, unless all 4 of them are lying. Not likely though. 

Nothing wrong with memory either - a full memtest run already carried out and passed. This does not look like hardware failure to me.

---

### Post by viking777 on 2014-07-29
Well my last throw of the dice (for today) is to mess with grub. If it isn't hardware and it isn't kernel and it affects booting, then grub is a logical place to look. I started by reinstalling 'grub-common' which made no difference, so my latest try is to replace the default grub on the mbr (which used to be the Xubuntu grub but now is Mint17 grub). 

Again, it might take a little while to learn if this is successful or not, it probably won't be:(

---

### Post by Bashing-om on 2014-07-29
viking777; Yeah.

Grub is a maybe, worth trying ..

My method:
In terminal remove all grub, then reinstall grub2 and recreate the config files:
```

sudo apt-get remove --purge grub grub-pc grub-common
sudo apt-get install grub-pc
sudo grub-mkconfig
sudo update-grub
sudo grub-install /dev/sda

``` Remember to change 'sda' to that of the booting disk.

[INDENT][INDENT]maybe yes ?
[/INDENT][/INDENT]

---

### Post by viking777 on 2014-07-29
> **Bashing-om said:**
> viking777; Yeah.

Grub is a maybe, worth trying ..

My method:
In terminal remove all grub, then reinstall grub2 and recreate the config files:
```

sudo apt-get remove --purge grub grub-pc grub-common
sudo apt-get install grub-pc
sudo grub-mkconfig
sudo update-grub
sudo grub-install /dev/sda

``` Remember to change 'sda' to that of the booting disk.

[INDENT][INDENT]maybe yes ?
[/INDENT][/INDENT]

I will see how I get on using the Mint grub first, if that is successful I will have a go at a complete reinstall of grub on Xubuntu as you suggest. 

So far I have done 4 cold boots using the Mint grub and none of them have failed. The only thing is that there has not been very long between them and previously the length of time the machine spent switched off seemed to make a difference.

Time will tell. 

Thanks again for the reply.

---

### Post by Bashing-om on 2014-07-29
viking777; Hey !

Another thing comes to mind. in respect to grub.
I too had "mysterious" anomalies with my system. I do multi-boot and after I had painstakingly (RE-)installed grub multiple times in multiple operating systems, I found I HAD to disable grub's 30_os-prober file to prevent recursions in the grub.cfg file.

Since straightening up the grubs, and disabling 30_os-prober - in all other OS other than the primary -, I have had no further problems.

[INDENT][INDENT]it's them little things
[INDENT][INDENT][INDENT][INDENT]gotta watch out for
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by viking777 on 2014-07-30
> **Bashing-om said:**
> viking777; Hey !

Since straightening up the grubs, and disabling 30_os-prober - in all other OS other than the primary -, I have had no further problems.


That is interesting and easy to accomplish, although I have to say I don't quite understand how that would make a difference, but hey, anything is worth a try, and there is plenty I don't understand, especially regarding grub! I will look into that if all else fails.

BTW I had a perfectly good cold boot this morning after being switched off all night. One boot is not enough to declare a success, but it is hopeful at the moment anyway.

---

### Post by viking777 on 2014-07-30
I decided to give Bahing-om's grub reinstall a try to see if I could get back to using Xubuntu's grub. I ran into a problem because attempting to use this method resulted in apt wanting to remove 17 other programs at the same time. Even worse than that it insisted that it had to install 20 other programs to replace the 20 it was removing. Even worse than that the 20 it wanted to use as replacements were mostly efi programs!!!!! I have had 'dealings' with efi on this machine (it shipped with it enabled) and it nearly drove me into an asylum trying to sort them out. The thought of reinstalling them makes me shudder in horror - I would rather pull my own teeth out one by one:eek:

So in case anyone else is reading this thread and is in a similar position I offer my workround. The original method is:


```
sudo apt-get remove --purge grub grub-pc grub-common
sudo apt-get install grub-pc
sudo grub-mkconfig
sudo update-grub
sudo grub-install /dev/sda

```

The revised method is 

```
sudo dpkg -r --force-depends grub-pc grub-common

```

NB The package 'grub' is not installed on my system, it has been replaced by grub-common.

This will give several warnings, but will continue to do as you ask it (isn't that a change! )

After this run 

```
sudo apt-get -f install
```

Which will reinstall grub-pc and grub-common (you can't use apt-get install for this it will just tell you your system is broken).

Then carry on with 

```
sudo grub-mkconfig
sudo update-grub
sudo grub-install /dev/sda
```

And the job is done. 

It booted normally first time, but as I keep saying I will have to wait and see if it is ultimately successful or not.

---

### Post by viking777 on 2014-07-30
Wow, you never need be bored if you own a Linux computer!

I have tried both of Bashing-om's suggestions now, the grub reinstall and disabling the 30_os-prober for the other 2 installed distros and during one of the many boots I have carried out in order to verify if the problem has been solved or not, my external monitor failed. 

After much panic and swapping of computers, tv's, monitors and cables it eventually transpired that the monitor's power cable was faulty. Luckily I had a spare one and the monitor is now back to normal again. 

It suddenly struck me though, could a failing power cable to an external monitor be the cause of the boot problems I have been experiencing?

It doesn't seem that likely to me, but computers are strange object with a logic that very few understand, so maybe it could have been the problem.

Anyway I will have to wait and see, so far the boot problem has not recurred, but it is too early to tell for sure if anything has worked or not.

EDIT. Absolutely none of this effort has made the slightest difference, it just failed to boot again - I give up now.

---

### Post by Bashing-om on 2014-07-30
viking777; sheesssh !

Don't know what I can say ...
Even after all my years messing about it is a fact that each system has a personality all it's own .
And, yeah, grub is very intricate and I do have a failure to comprehend what is going on at the kernel space level as to how and what gets built; and of course UEFI is a horse of a different color, booting EFI requires a different file structure. //I firmly believe it is a better structure, but it is not on my system(s), and I have no way to get any hands on experience with it //

Maybe useful to look at your file structure ( partitioning ), look at it with a different set of eyes, maybe something will jump out at us - doubtful - but, who knows.
And as well look at how the file systems are mounted. There must be a cause, and a failure to communicate in the operating system - somewhere !
```

sudo blkid
sudo fdisk-lu
sudo parted -l
cat /etc/fstab
mount

```

What else we might do, is boot the system in text mode, pause the boot message output on-screen and try and read the messages.
The process: bios -> grub -> kernel -> init -> modules. Find where we have that failure to communicate .

faint heart,
[INDENT][INDENT]never won fair lady
[/INDENT][/INDENT]

---

### Post by siepo on 2014-07-30
Just clutching at straws, but maybe you could give the computer more time to warm up by specifying a longer grub timeout in /etc/default/grub (followed by re-running update-grub)?

---

### Post by viking777 on 2014-07-31
Thank you both for the replies. 

I will be away from my computer for a while, so I don't have time to mess with things right now, maybe later, although I have to say that I have reverted to using MInt's grub on the mbr and so far have had no problems booting at all. Early days of course. It really doesn't matter to me which version of grub is doing the booting as long as it boots - and so far it does. Of course if the faultless boots continue then that must strongly suggest a problem with Ubuntu's grub (despite the comprehensive reinstallation) rather than Ubuntu itself or my filesystems. Anyway, time alone will tell, and I'll let you know.

---

### Post by viking777 on 2014-08-01
I just may have solved this - although I don't really have enough time to test it thoroughly right now. 

The clue came from the fact that when I switched to using Mint's grub on the mbr, Ubuntu booted normally every time. This led me to look into the differences between the grub files on Mint and those on Ubuntu. One of the most obvious differences was the on Ubuntu's /etc/default/grub I had uncommented the line:  ```
#GRUB_DISABLE_LINUX_UUID="true"
```.  I remember doing this some time ago, I don't like UUID's and use labels as much as possible, but grub obviously doesn't 'do' labels and reverted to a grub.cfg entry of ```
root=/dev/sda9
``` instead of ```
root=UUID=xxxxxxetc
```. I don't know why, but it seems that on some occasions it was unable to find /dev/sda9, whereas so far it has had no problems finding the partitions UUID.

This may be the problem but I'll have to wait and see.

---

### Post by JKyleOKC on 2014-08-01
That probably is the answer. The partition numbers in the /dev/sda9 construction are assigned automagically during the early stages of the boot process. Upon discovering one or more disk controllers in the system, the program queries each of them in turn, partition by partition, and upon getting a response assigns a number to that partition.

If the one that's normally "9" in your system takes a bit longer to wake up from the cold, and there are additional partitions that get higher numbers, then the numbering sequence will end up being different that time. Preventing this problem is the primary reason that UUIDs are preferred; they won't be affected by slower or faster wakeup times.

It's also possible that some timeout value is too short for SDA9 to always respond in time; if that's the case, increasing the timeout might correct things -- but I have no idea where that value could be changed, or if it's even adjustable. It's definitely NOT the Grub timeout values -- the partition numbers are assigned long before grub gets launched.

Grub itself uses a multi-stage technique because older systems did not provide enough space in their boot areas to hold the entire program. Thus the "overflow" is stored on the main system partition rather than in the boot area, and consequently if the system partition gets a "wrong" number, grub cannot find its back half and errors out.

Putting the comment character back in /etc/default/grub, then re-running the update process, should fix things for you. You can still use labels everywhere else, and the details of grub usually happen behind the curtain...

---

### Post by viking777 on 2014-08-09
Thought you might like to know, after adjusting grub as per my last post I went away for a while. As soon as I booted on my return, the boot failed with the same error as detailed in the opening post. I went back to Linux Mint grub on the mbr and since then I have had no further failures.

So, to recap:

1) There is something wrong with Xubuntu's grub on my system. 
2) I have no idea what it is, and therefore cannot repair it. 
3) If I use Mint 17 grub on the mbr Xubuntu boots perfectly every time.
4) As I have a 100% successful workround, I have lost patience in trying to troubleshoot the problem, I have simply spent too much time on it already.
5) It will almost certainly fix itself next time I install Xubuntu.

So thanks to everyone who tried to help. It is definitely not solved, but I think I will leave it here. If Mint's grub ever fails I might get back to you. 

Thanks once again, 

viking.

---

