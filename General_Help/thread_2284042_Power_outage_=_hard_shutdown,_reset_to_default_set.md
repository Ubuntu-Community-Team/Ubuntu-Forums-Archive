---
title: "Power outage = hard shutdown, reset to default settings, time wrong and Questions"
date: 2015-06-26
forum: General Help
---

### Post by mikodo on 2015-06-26
I apologize for the stupid title. 

As above, power outage last nite.

This morning I get a "Beep" on startup and a flash of Megatrends? something  and I think F1 to enter whatever that is and F2 to Run and install default settings, (it was fast).

I hit F2 and booted in Xubuntu 14.04

Time was set at 2001 and I couldn't use the browser.

Went into BIOS and reset time and date and Region.

Changed my clock settings to correct also.

Question:

Is that basically what an install of Ubuntu does, and am I back to the default install settings?

Thank you.

---

### Post by Bashing-om on 2015-06-26
mikodo; Hi !

As you know a power outage leaves a lot of files open, and thus the file system in an inconsistent state. No telling what may now perchance.
Did you run a file system check/repair when you 1st fired the system back up ?
A quick way to get a hint on the state of the file system: from terminal:
```

sudo touch /forcefsck
sudo shutdown -r now

```
To set the file system check flag for next boot; and then to reboot the system.

[INDENT][INDENT]power outage 
[INDENT][INDENT]scary situation
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mikodo on 2015-06-26
Thank you, for the reply.
> **Bashing-om said:**
> 
Did you run a file system check/repair when you 1st fired the system back up ?
No I didn't. Don't know how to do that for my desktop machine.

I ran your commands, and all it said on reboot was, that it was checking the disk for errors, with no report back after 10 seconds. Then booted right into the desktop.

Anything else I should try, sir?

---

### Post by oldfred on 2015-06-26
If BIOS is from 2001, it could be the little coin battery on motherboard. 
Reset to default BIOS settings after power cycle is often the only way to tell battery is not working.

Ubuntu does not modify any BIOS settings.

---

### Post by mikodo on 2015-06-26
> **oldfred said:**
> If BIOS is from 2001, it could be the little coin battery on motherboard. 
Reset to default BIOS settings after power cycle is often the only way to tell battery is not working.

Ubuntu does not modify any BIOS settings.

Oh, Okay. Thanks Fred.

I will have to attend to replacing the battery when I can.

regards.

---

### Post by mikodo on 2015-06-26
I poked around and found forcefsck in my /. It's and empty file. I hope that means there is no errors.

---

### Post by Bashing-om on 2015-06-26
mikodo; Yeah;

If you saw no reports of errors when /forcefsck ran, chances are good the file system is intact.

That file is but a "placeholder" to see if the flag is set .
If you have fsck logging enabled, one might find logs in the " /var/log/fsck/checkfs " file.

If you want to verify/see fsck run/results then boot up a liveDVD ( as the target file system must be in an UN-mounted state).
In this live envirnment run terminal commands:
#From liveDVD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
To check the linux partitions - Not Windows !
```

sudo fdisk -lu ##to identify target partition(s)
sudo e2fsck -C0 -p -f -v /dev/sda1

```

#if errors: -y auto answers yes for fixes needing response see: man e2fsck
```

sudo e2fsck -f -y -v /dev/sdb1

```

When it comes to the file system
[INDENT][INDENT][INDENT]there is nothing "too safe"
[/INDENT][/INDENT][/INDENT]

---

### Post by mikodo on 2015-06-26
[QUOTE=Bashing-om;13310790
mikodo's placeholder[/QUOTE]

Thanks a bunch! :)

I'm in the middle of a lot of stuff right now. I will do what you said above the quote, and if there are any more problems well ...

I'll ask. lol[INDENT][INDENT][INDENT]

[/INDENT]
[/INDENT]
[/INDENT]

---

### Post by mikodo on 2015-06-26
> **Bashing-om said:**
> ```
sudo fdisk -lu 
sudo e2fsck -C0 -p -f -v /dev/sda1
```

I think I'm good.

Here is a link to the commands in Ubuntu pastebin: [http://paste.ubuntu.com/11781765/](http://paste.ubuntu.com/11781765/)

---

### Post by Bashing-om on 2015-06-26
mikodo; Yepper;

I see no evil there.

[INDENT][INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT][/INDENT]

---

### Post by mikodo on 2015-06-29
Well, I did what Fred said to do in the thread and replaced the motherboard battery. Then changed the date and times to correct settings in BIOS and desktop clock.

Time seems not to be an issue anymore. Thanks Fred.

But, while I was doing this I noticed that the disk is being checked for errors, with each boot now.

I tried this and got:
```
mikodo@mikodo:~$ sudo tune2fs -c 30 /dev/sda1
[sudo] password for mikodo: 
tune2fs 1.42.9 (4-Feb-2014)
Setting maximal mount count to 30
mikodo@mikodo:~$
```
Rebooted a couple more times, and it continues to check the disk for errors on startup.

That might be the incorrect command or options. I dunno.

What should I do?

Edit. I am going to stop messing with this, until I get a knowledgeable response on what to try as, I break things on my own.

Thank you.

---

### Post by oldfred on 2015-06-29
I would try this, but also check in Disks and upper right corner the Smart Status.


 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by mikodo on 2015-06-30
> **oldfred said:**
> I would try this, but also check in Disks and upper right corner the Smart Status.


 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1
Thanks again, Fred.

I've been doing other things and just a bit ago saw this.

I don't know what "Disks and upper right corner the Smart Status" is. I think the Gnome Disk Utility, found in Unity installs. I don't have it but, I can install it.

I'm really tired now. I'll look into running those tomorrow.

---

### Post by mikodo on 2015-06-30
Hi.

I gotta go. I didn't have time to read about and run the commands, Fred suggested in Post # 12 yet.

When booting the computer this afternoon from cold start, I got a message to send a ?apport message to Ubuntu about a crash. I tried to save it.

I think this is it.

[http://paste.ubuntu.com/11801007/](http://paste.ubuntu.com/11801007/)

I thought it might have some significance to what is happening now. I dunno. 

Thanks.

---

### Post by Bashing-om on 2015-06-30
mikodo; Hi !

Let's reserve judgement to after the file system checks are completed as per oldfred's directive.

Then to check the health of the hard drive physically there is the CLI way rather then the GUI.
```

sudo apt-get install smartmontools
sduo parted -l ## to identify the internal harddrive, here shown as 'sda'
sudo smartctl -t long /dev/sda
sudo smartctl -a -d ata /dev/sda ## To display detailed SMART information

```
That you might find easier to deal with.

[INDENT][INDENT]to soon to tell
[/INDENT][/INDENT]

---

### Post by mikodo on 2015-07-01
Hi, folks! Thanks, for the help.

I apologize for, taking so long to get back to this thread. I was having problems with my backup scenarios and was working on that, until 04:00 this morning. I finally gave up on fixing what was wrong this afternoon, and deleted and ran them fresh again. I'm good for now but, know how I can do better, with more time to do so.

Please see, the output of commands:  [http://paste.ubuntu.com/11807895/](http://paste.ubuntu.com/11807895/)

> **oldfred said:**
> 
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Fred. I ran the first command sudo e2fsck -C0 -p -f -v /dev/sda1  but, found no errors, so didn't run the second. Should I have, anyway?

> **Bashing-om said:**
> mikodo
```

sudo apt-get install smartmontools
sduo parted -l ## to identify the internal harddrive, here shown as 'sda'
sudo smartctl -t long /dev/sda
sudo smartctl -a -d ata /dev/sda ## To display detailed SMART information

```

Bashing-om. It appears the disk is alright.

Any ideas, on what to do next, folks?

---

### Post by Bashing-om on 2015-07-01
mikodo; Yeah ;

All looks good to me.

Reboot and let's see what the condition our condition is in.

Then is the package manager in a happy state ?
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Do you still have the condition of the system running a file system check at each boot up ? - or any other abnormalities -

[INDENT][INDENT]look'n good
[/INDENT][/INDENT]

---

### Post by mikodo on 2015-07-02
> **Bashing-om said:**
> mikodo; Yeah;

Oh, just about every day I do, 

> sudo apt-get update && sudo apt-get dist-upgrade

I'll try running the 3 commands as you mentioned in sequence, to see if anything has changed since, I ran the other this afternoon. If so, I'll report back.

Oh, the other thing about crashing, went away.

Just the < 10 seconds of disk checking on reboots or cold start remains. It's not a big deal really, if everything is good with the disk. Just odd, that it started right after the power outage. It seems too much, to be a coincidence of the "stars lining up together".

Thanks.

Edit: There were no updates or anything reported with the 3 commands, one by one. Rebooted, and I still have the checking. C'est la vie!

---

### Post by Bashing-om on 2015-07-02
mikodo; Welp ;

Marked this down as something to investigate.

Now I have an opportunity to progress up that curve of learning.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by oldfred on 2015-07-02
Old systems used to do a RAM memory test on startup, and that setting is in BIOS. 
Is that what you are seeing?

When you replaced battery in motherboard, BIOS was reset to all its defaults. Perhaps you changed that RAM test setting years ago?

I had issues of BIOS updates always resetting to defaults, so I took pictures of all settings, so I could remember what I changed.

---

### Post by CharlesA on 2015-07-02
> **oldfred said:**
> Old systems used to do a RAM memory test on startup, and that setting is in BIOS. 
Is that what you are seeing?

When you replaced battery in motherboard, BIOS was reset to all its defaults. Perhaps you changed that RAM test setting years ago?

I had issues of BIOS updates always resetting to defaults, so I took pictures of all settings, so I could remember what I changed.

Agreed. It should be listed as "Fast Boot" or something similar.

On the rare occasion I need to reset the BIOS, I have to grab the manual and figure out what I turned off and what I changed. I should probably take pictures the next time I am in there.

---

### Post by mikodo on 2015-07-02
You folks have, "gone above and beyond the Call of duty" with this and are still, from what I read below. Not, that it hasn't been anything but, love of this technology and helping others. You know what I mean.
> **Bashing-om said:**
> 

Marked this down as something to investigate.

Now I have an opportunity to progress up that curve of learning.[INDENT][INDENT]inquiring minds want to know
[/INDENT]
[/INDENT]

Bashing-om. Have fun!

Thanks.
> **oldfred said:**
> Old systems used to do a RAM memory test on startup, and that setting is in BIOS. 
Is that what you are seeing?

When you replaced battery in motherboard, BIOS was reset to all its defaults. Perhaps you changed that RAM test setting years ago?

I had issues of BIOS updates always resetting to defaults, so I took pictures of all settings, so I could remember what I changed.
Fred. All I changed in the BIOS 'this time" was to set the time. After placing in the new battery, I never saw that ?Megatrends page flash on again at boot and things have  been fine in that regard since, ... time etc. There's a very good chance I messed up the BIOS in the past cause, I have screwed with it for a number of reasons. I dunno. I prefer to leave it alone these days. I see the checking its' disk dialogue", every time I boot. Which is usually more than, one per day.

Thanks, to you too!

---

### Post by Bashing-om on 2015-07-03
mikodo; Hey ;

In my poking about; I find with 15.04 - systemd - that we woiud have to force a file system check in a different manner. I take it though from the outputs you are infact running release 14.04.

As 14.04 what returns:
```

sudo dumpe2fs -h /dev/sda1 | grep -i 'mount count'

```
to see the frequency number and the current mount count for that specific partition. 'sda1' is the booting partition for ubuntu, yes ? 
and we need to look at what is set in "/etc/fstab" for checking the file systems:
```

cat /etc/fstab

```

And I do continue to hunt for the source of the hooks that call the file system consistency checker .

Edit ! Found one .
What is set :
```

cat /etc/default/rcS

```


[INDENT][INDENT]who what where when and why
[/INDENT][/INDENT]

---

### Post by mikodo on 2015-07-03
Hi Bashing-om!

You were serious about, "marking this down to something to investigate ..." 

Here. This is cleaner:  [http://paste.ubuntu.com/11818897/](http://paste.ubuntu.com/11818897/)

How do I make sure I have the time right in BIOS?

Thanks.

---

### Post by Bashing-om on 2015-07-04
mikodo; Hummm ...

No fault found in any of those outputs. All I can conclude is "something" is setting the dirty bit in the partition table,
What returns:
```

sudo tune2fs -l /dev/sda1

```
to find out the filesystem configuration .

As to bios settings, each and every manufacturer has a different bios. All I can suggest is that you boot up to the bios setting utility, find the time item, change as required and make sure that the change is written (saved) to CMOS.

You are not dual booting this system with Windows are you ? Such that Windows and ubuntu are in conflict with who controls the hardware clock ?

[INDENT][INDENT]about the time I think I know
[INDENT][INDENT]I get blocked by my ignorance
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mikodo on 2015-07-04
Hi!
> **Bashing-om said:**
> 

No fault found in any of those outputs. All I can conclude is "something" is setting the dirty bit in the partition table,
What returns:
```

sudo tune2fs -l /dev/sda1

```
to find out the filesystem configuration .
Out put here: [http://paste.ubuntu.com/11819006/](http://paste.ubuntu.com/11819006/)

Only Xubuntu 14.04.2 install. Nothing else.

---

### Post by mikodo on 2015-07-04
I went into the BIOS and the time is correct, to  UTC. My desktop clock, is following the same, to my geolocation.

I'm guessing with the new CMOS, the sytem is righting them. I dunno.

---

### Post by Bashing-om on 2015-07-04
mikodo; Sheesshh ..,

Comparing your 'tune2fs' to mine, I see nothing to be concerned about. I can not see where that the system would run a file system check at each boot up. Are you certain and for sure what you are seeing is the system ( ubuntu) conducting a file system check ? As there is that option in bios to check the memory and display what it is checking at each boot up. Is this what you are seeing rather then the system's checks ?

As to the time coordinates that bios is set to. most generally it is UTC, but not necessarily so, one needs to check and see what the manufacturer recommends for their purpose. The operating system will translate that time from the hardware clock (BIOS) to the purpose of the system. As the time is as you expect in the operating system, I would not be concerned that the bios time is not set correctly.

A complexity of systems
[INDENT][INDENT][INDENT]is this little kernel of ours
[/INDENT][/INDENT][/INDENT]

---

### Post by mikodo on 2015-07-04
> **Bashing-om said:**
> mikodo; Sheesshh ..,

Comparing your 'tune2fs' to mine, I see nothing to be concerned about. I can not see where that the system would run a file system check at each boot up. Are you certain and for sure what you are seeing is the system ( ubuntu) conducting a file system check ? As there is that option in bios to check the memory and display what it is checking at each boot up. Is this what you are seeing rather then the system's checks ?

As to the time coordinates that bios is set to. most generally it is UTC, but not necessarily so, one needs to check and see what the manufacturer recommends for their purpose. The operating system will translate that time from the hardware clock (BIOS) to the purpose of the system. As the time is as you expect in the operating system, I would not be concerned that the bios time is not set correctly.

A complexity of systems[INDENT][INDENT][INDENT]is this little kernel of ours
[/INDENT]
[/INDENT]
[/INDENT]


Hi, Bashing-om.

Yelp! Your persistence is unfathomable. 


I wonder if what I am seeing at each boot, before the OS enters the DE is not related to file system checks, (e2fsck).

I think we are using file system check commands to try to address why  the system is "checking the disk drive", each time. 

All that I am seeing "now' is a Disk Drive Check.

Almost verbatim:

Checking the disk drive for errors.
Press C to cancel all checks.
Routine Disk Drive check.

That's all.

History as I remember it:

Initially, Hard shutdown on Power outage.

On startups and reboots I would see a American Megatrends screen, that had two options. F1 to enter it for changing settings, (I think) and F2 to set to default. I kept hitting F2 each time it displayed and the system would carry on in the boot process.

Megatrends is the company that developed this BIOS.  [https://en.wikipedia.org/wiki/American_Megatrends](https://en.wikipedia.org/wiki/American_Megatrends) 

After putting in the new CMOS, I stopped seeing the Megatrends screen.

Then, I noticed I was having the Disk Drive Checks each startup.

(Just now I tried different key combinations on cold startup and reboots to enter get the Megatrends screen and options and I couldn't do it).

I can enter th BIOS Setup Utility easily, as it displays each time on startups what can be used. In the BIOS, it has American Megatrends Inc. displayed on the bottom of page.

In the BIOS Setup Utility, I see no options (maybe I just haven't seen it yet), to  ascertain how to answer your question of, "Are you certain and for sure what you are seeing is the system ( ubuntu) conducting a file system check ?As there is that option in bios to check the memory and display what it is checking at each boot up. Is  this what you are seeing rather then the system's checks ?" I will look closer again, and if there is that option in the BIOS Setup Utility and will try to find the key combination, that gives me the option to see the Megatrends Screen and see if there is anything in it by hitting FI.

Even if I could get back to Megatrends display page and be able to go into manually setting it up, I wouldn't. Their resources on the internet are possibly pretty sparse and I'm, "not up for that challenge".



Thank you.

---

### Post by Bashing-om on 2015-07-04
mikodo; Welp;

Upfront; I am in this for what I can learn as my 1st priority. Your situation has my attention and my focus.
I am trying to think things through - in my own slow plodding way.

Later when I reboot, I will look at my bios utility . It is Phoenix , but 'may' have some similarities.
In my bios I can toggle bios' screen on/off, and toggle checking the system ram ( memory), amongst all the other hundreds of setting options.

As everything starts with bios, what it discovers and hands off to the operating system, it is vital what is set in bios.
> 
 F2 to set to default. I kept hitting F2 each time it displayed and the system would carry on in the boot process.

Resetting to the bios defaults each time is not a good indication. One should only have to change a setting, save (write) the changes to CMOS once per change. Then with these changes in effect ( and effective) The system boots with bios as is - intervention should not be required again.

Speaking of what is set; do you have deviations from the default boot parameters ?
In the install, what returns from terminal command:
```

grep BOOT_IMAGE /var/log/kern.log

```
Which will tell us what the kernel is booting.

The process:
bios -> grub -> kernel -> userspace -> desired layers on the kernel -> desired modules attached to the kernel .

The process is simple
[INDENT][INDENT][INDENT]how it happens is the complexity
[INDENT][INDENT][INDENT][INDENT]where is that failure to communicate ?
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mikodo on 2015-07-04
Hi Bashiing-om.

I apologize, for being tardy with your request. I've been playing in the BIOS Setup Utility. I did learn some things, and have a couple of questions about it. But, first my results from:```
grep BOOT_IMAGE /var/log/kern.log
```
[http://paste.ubuntu.com/11823907/](http://paste.ubuntu.com/11823907/)

Edit:

I was able to reproduce the American Megatrends screen, I saw with the "beep" before I replaced the CMOS.

I  went into the BIOS Setup utility and enabled, "Boot-time Diagnostic  Screen" and in subsequent boots, got the Megatrends Screen with that. It  mostly showed my system, a couple of commands like before to enable  default settings and run set-up, (that just took me to the BIOS Setup Utility). And, my internal devices and ports.  That's all. So, that is solved, with nothing to report more.

In the BIOS Setup utility, I found this and I don't know what it is:
1. onboard LAN = enabled
2. Onboard LAN Boot ROM = disabled.
I left those like they are, but I wondered if that is what Fred is talking about.

and

A section that states:

After AC Power Failure with three settings one can toggle to set.
1. Stay Off = what was set as, and I left it as that.
2. Auto
3. Power On.

I don't know if that should be what the default is, or changed.

Other than that, I don't see anything in the BIOS Setup Utility, that gives any clues about what is running for checks, to answer this of your's: > Are you certain and for sure what you are seeing is the system ( ubuntu)  conducting a file system check ? As there is that option in bios to  check the memory and display what it is checking at each boot up. Is  this what you are seeing rather then the system's checks ?

hmm.

Any chance, I have a "dumbed down"' version of the BIOS with this Megatrends set up BIOS? I have never owned another computer, that I can compare it to. And, I have never seen anyone else's.

I'm off into the abyss err... I mean the BIOS, to look some more.

Here in Saskatoon, ~300,000 metro  people, have so much smoke in the air from forest fires that' though there are not any clouds reported by Environment Canada for here, we can't see the sky for smoke and it is reported that the visibility in the countryside to be from 1 - 2 miles looking around. There are now 100 Forest Fires burning in Saskatchewan, with the closest just 150 miles from here, that is twice the size of Saskatoon. I've heard reports of the smoke reaching far into south-eastern states now. Staying in and playing on the computer is, infinitely  better than being outside.

---

### Post by Bashing-om on 2015-07-04
mikodo; Well ...

So much for that thought, default boot options and nothing there to re-direct what the kernel does in booting.

Back to bios ??

> 
n the BIOS Setup utility, I found this and I don't know what it is:

"1. onboard LAN = enabled" : Do you have other machines connected to the router and desire to exchange files ? NO ? then set this option to 'disabled' . No point in leaving a hole that might be exploited.
"2. Onboard LAN Boot ROM = disabled." Unless it is your desire to boot this system up from remote, leave this option as 'disabled'.

> 
after AC Power Failure with three settings one can toggle to set.

After power is restored from that loss of power condition, what do you want the system to do ?
I personally prefer to manually take matters into my hands, boot up the system, run the file system check seeing and being aware of what problems might exist. I do suggest to leave that option "  stay off = what was set as and I left it as that." Where you must push the power button to start up the system.

Let's determine definitively when and from where the 'check' condition arises.
Reboot the system and as soon as the bios screen clears, depress and hold the right -shift- key -> grub boot menu.
Any sign of that check request yet ?
OK, proceed to boot.. with the top most entry in the list selected ( asterisk) press the enter key -> Do you boot to the GUI ? Any request for a disk check ?

Do we want to look at the boot messages ? We can see the system boot messages as it boots . Several things we can do at this point to effect how the system boots. Depending on what the objective is .

We want to isolate where in the boot process the 'check disk' advisory happens.
During bios post ? Before grub starts, while grub runs ? before the kernel loads ? after the kernel has loaded ? 
I bet we can find out !


[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by mikodo on 2015-07-04
Bashing-om. 

One more thing. What is XD (Execute Disable) = enabled        mean? It is set at enabled. 

"Reboot the system and as soon as the bios screen clears, depress and hold the right -shift- key -> grub boot menu.
Any sign of that check request yet ? NO
OK, proceed to boot.. with the top most entry in the list selected (  asterisk) press the enter key -> Do you boot to the GUI ? I GET THE XUBUNTU LOGO WITH THE CHECKING THE DISK FOR ERRORS .. ROUTINE DISK CHECK. THEN < 10 SECONDS, BOOTS INTO THE DESKTOP.

---

### Post by Bashing-om on 2015-07-04
mikodo; Hummm ...

Seems it is coming from the kernel as it starts.

OK, does the same thing result when booting an older kernel ? ( select a different kernel from the grub boot menu)/
Looking to see if perhaps we should rebuild the kernel image.

And as to XD , new one on me .. right off hand I do not know.

[INDENT][INDENT]in that process of fault isolation
[/INDENT][/INDENT]

---

### Post by mikodo on 2015-07-04
Bashing-om. No help.

[QUOTE=Bashing-om;13315267]OK, does the same thing result when booting an older kernel ? ( select a different kernel from the grub boot menu)/
Looking to see if perhaps we should rebuild the kernel image.[QUOTE]

This install is just short of two months.

I only have the two kernels listed when I choose Advanced Options

Was running 3.13.0-55-generic
and choose the earlier one,
3.13.0-54-generic 

And I get the same "Checking disk for errors" as before.

Thanks.

---

### Post by Bashing-om on 2015-07-04
mikodo; Well.

Throw my last idea out the window also.
I sleep on this, see what else I can come up with.

cause and
[INDENT][INDENT][INDENT]effect
[/INDENT][/INDENT][/INDENT]

---

### Post by mikodo on 2015-07-05
Bashing-om.

Cause and effect: Something is amiss, by my hand I fear.

If any more ideas come to mind, I would welcome them.

---

### Post by oldfred on 2015-07-05
I might try the full fsck that was suggested in Post #7 by Bashing-om. But do you have more than one ext4 partition in fstab? Like a separate /home or data partition(s)? If so be sure to run the commands on every ext formatted partition.

---

### Post by mikodo on 2015-07-05
> **oldfred said:**
> I might try the full fsck that was suggested in Post #7 by Bashing-om. But do you have more than one ext4 partition in fstab? Like a separate /home or data partition(s)? If so be sure to run the commands on every ext formatted partition.

Hi Fred.

I am going to follow up with this. For now I can't. Maybe, tomorrow or the next day. One of our cars broke down last night and I'm trying to get it fixed or attended to. My wife needs her car.

Side bar: 

I finally got this New install, with it's New platter disk all set up like I wanted with my Xubuntu DE. Before this power outage and what is happening now, my plan was for this past week was to actually follow your directions to make a separate data partition and symblink it to my /mnt. But, I think I need to see if there are problems with this install or disk, before  going on with the symlinking. This will be my first time, besides trials and documentation. I have all your directions and am excited about getting it done. But, first things first, as they say ...

Edit:

 Hi Fred. It is my wife's car's alternator. I can't do anything more today. So, I took the time to read your Post.

1. I think I did run the command of Post #7 suggested by Bashing-om. Did you mean this one or, is there one I might be missing:

[http://paste.ubuntu.com/11781765/](http://paste.ubuntu.com/11781765/)

 2. The only partition I have in fstab is seen below. Please note the error. I saw it before and wondered about it but, not knowing what it means, I let it go. 

Not in /etc/fstab but, I did stick a logical partition (Ext4) in a large extended one, on my internal drive and made a backup data using the GUI app Back In Time, after I was having trouble with my backup scenarios with my rsync commands,  (I have another on an external disk). I will be redoing the rsync one, after I make my data partition to be symblinked to my /mnt. But, for now here is my fstab:


```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=55c1f9c5-5f2f-4429-a84f-0cf1e6bd83c0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e1183843-1fcb-46fe-bda9-c6c1d31f4658 none            swap    sw              0       0
```

Thanks.

---

### Post by mikodo on 2015-07-05
Hi.

What do you folks think.

I don't want to re-install (and reconfigure the DE again to my liking). 16.04 is coming soon, and I intend to fresh install it. I stick to the LTS's. Could I just go ahead and try leaving this install on disk and use it as my only OS until, I fresh install 16.04, (with data properly backed up). Or, do you think it is best I reinstall now, over this one? I don't know how serious the problem I am having now is. I want to move ahead and start with the symlinked data partition. Like all of us, my time allotment for computer use, is limited. 

I hope your best guesses are, that it will probably be all right to keep this install, until 16.04.

Thank you.

---

### Post by Bashing-om on 2015-07-05
mikodo; Hey;

So far as I am aware the only thing not normal at this time is the system running a file system advisory at each boot. That little thing should not be a hindrance to normal operations .
Presently I continue to see if I can discover a means to find out the why:
looking at 'mountall' as 'mountall' is responsible for mounting file-systems in the correct order, and running fsck on file-systems. I said earlier I suspected corruption... if 'mountall' is failing it *may* be due to a fsck failing; though all indications are that the file system is intact .
I rarely poke at things in the dark - with out good cause and I hesitate to make my next recommendation with out a bit more knowledge on my part as to what the operating system is doing. How to find out what I need to find out, now that is the task..

[INDENT][INDENT]inquiring minds want to know[/INDENT][/INDENT]

---

### Post by oldfred on 2015-07-05
You only have the one ext4 partition for fsck to be running on.

But I do not understand why it is wanting to run all the time. Not sure if a reinstall would help. As file corruption is usually the reason for fsck and the fsck fixes it.

I have seen errors on empty extended partitions. Perhaps it does not like an empty extended partition. Try just creating & formatting a logical partition inside sda2, does not have to be large, just something.

---

### Post by mikodo on 2015-07-06
> **oldfred said:**
> You only have the one ext4 partition for fsck to be running on.

But I do not understand why it is wanting to run all the time. Not sure if a reinstall would help. As file corruption is usually the reason for fsck and the fsck fixes it.

I have seen errors on empty extended partitions. Perhaps it does not like an empty extended partition. Try just creating & formatting a logical partition inside sda2, does not have to be large, just something.I apologize Fred. I fear I am not being clear. I have a logical partition (sda5) in the extended partition, (sda2) with the data in from backup with one of my BIT runs. There is also a backup of it too,  to an old external drive. I'm waiting for a newly ordered external drive to backup with, as I don't trust the old one anymore. So, I stuck my backup data in my new internal drive too for now, as a safety precaution.

So, I will run the fsck on the logical partition (Ext4) (sda5). Correct?

I haven't run fsck on the extended partition.

---

### Post by mikodo on 2015-07-06
> **oldfred said:**
>  Try just creating & formatting a logical partition inside sda2, does not have to be large, just something.
Thanks Fred. 

Here are results of [/dev/sda2] the extended partitiion

amd

[/dev/sda5] the logical partition in it:

```

xubuntu@xubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda2
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?
xubuntu@xubuntu:~$ 
xubuntu@xubuntu:~$ 
xubuntu@xubuntu:~$ sudo e2fsck -f -y -v /dev/sda2
e2fsck 1.42 (29-Nov-2011)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?
xubuntu@xubuntu:~$ 
xubuntu@xubuntu:~$ 
xubuntu@xubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda5
                                                                               
   13418 inodes used (0.28%)
     944 non-contiguous files (7.0%)
      13 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 13388/20
13583419 blocks used (69.72%)
       0 bad blocks
       1 large file

   10934 regular files
    2472 directories
       0 character device files
       0 block device files
       0 fifos
   21766 links
       3 symbolic links (2 fast symbolic links)
       0 sockets
--------
   35175 files
xubuntu@xubuntu:~$ 
xubuntu@xubuntu:~$ 
xubuntu@xubuntu:~$ sudo e2fsck -f -y -v /dev/sda5
e2fsck 1.42 (29-Nov-2011)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

   13418 inodes used (0.28%)
     944 non-contiguous files (7.0%)
      13 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 13388/20
13583419 blocks used (69.72%)
       0 bad blocks
       1 large file

   10934 regular files
    2472 directories
       0 character device files
       0 block device files
       0 fifos
   21766 links
       3 symbolic links (2 fast symbolic links)
       0 sockets
--------
   35175 files
xubuntu@xubuntu:~$ 

```

What the heck is a zero-length partitiion. Just how an extended partition reads with this?

Thanks.

---

### Post by mikodo on 2015-07-06
> **Bashing-om said:**
>  ... what you said and I read ... How to find out what I need to find out, now that is the task..
Hi Bashing-om.

I am encouraged on two fronts. 

1. You believe the problem as you understand it, (not me), shouldn't be a hindrance to normal operations. 

2. You and Fred remain interested in this, and in helping along the way.

I will keep the install then and go forward, and not worry. Besides ... why worry?

---

### Post by CharlesA on 2015-07-06
If you try to stick to LTS releases, I'd wait until 16.04 releases unless you want to run 14.04.

---

### Post by mikodo on 2015-07-06
> **CharlesA said:**
> If you try to stick to LTS releases, I'd wait until 16.04 releases unless you want to run 14.04.
Thank you, for your advice. I saw your post earlier so, I assume you are following along and are informed.

I play at this sporadically, and it's easier for me with LTS releases.

---

### Post by oldfred on 2015-07-06
You cannot run fsck on an extended partition, it is more like just a container for logical partitions.
Either create a logical partition inside it, or just delete it as it has no partitions in it now.

---

### Post by mikodo on 2015-07-06
> **oldfred said:**
> You cannot run fsck on an extended partition, it is more like just a container for logical partitions.
Either create a logical partition inside it, or just delete it as it has no partitions in it now.

Hi Fred. 

Good to know why that shows like that on an extended partition. 

The extended partition, does have a logical Ext4 data partition inside  it though. I guess an e2fsck check on extended partitions, doesn't  show that it has a logical partition with data inside it.

As you saw, I ran the e2fsck check for it too, (/dev/sda5), with no errors that I can see.

Thanks.

---

### Post by oldfred on 2015-07-06
I am running out of ideas?

---

### Post by Bashing-om on 2015-07-06
mikodo; Like a dog with a bone:

As oldfred NOR CharlesA can advise in this situation; It is indeed something novel. Both have been around for quite some time and are intimate with this our operating system of choice.

I do have another "thought" in mind; but I do not know if it would be effective, or what it would tell us.
Maybe, just a maybe, spare off the superblock ?? But as advised, I can not justify this measure.

As I can; I will see what I can learn about 'mountall' and how it may affect the file system check routine.

[INDENT][INDENT]it just ain't over
[INDENT][INDENT][INDENT]'til it is over
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by CharlesA on 2015-07-06
FYI: /dev/sda5 is usually reserved for swap space. I can see it in the contents of /etc/fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=55c1f9c5-5f2f-4429-a84f-0cf1e6bd83c0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e1183843-1fcb-46fe-bda9-c6c1d31f4658 none            **swap**    sw              0       0
```

It should be ok since an extended partition is just a container as oldfred said, and the point on that container is to hold the swap partition.

---

### Post by mikodo on 2015-07-06
> **CharlesA said:**
> <Snip>FYI: /dev/sda5 is usually reserved for swap space. I can see it in the contents of /etc/fstab ...
It should be ok since an extended partition is just a container as oldfred said, and the point on that container is to hold the swap partition.

Hi Charles.

That's interesting. I did have a swap on initial install, and when I was changing my backup scenarios because of problems, (at my own hand, it turns out), I was doing that during the time right after the power outage, and then decided I didn't need a swap partition and made a bigger extended partition in it's place and a quick logical backup partition to my internal drive, as a second backup to my data, as I was having problems with my external drive. (longer story, I found it was my problem not usb drive's but, when I made that new extended partition with a new logical partition in it, it is sda5 that the temporary data is in. I don't need it now, as I have the usb drive housing the data again too. I would just want to double check it again to be sure it is recoverable. Clear as mud???). oh, and the data in sda5 is owned by /  if that is of any consequence.


Could it be ... as you said "it should be ok ..." that the problem does arise from that. I'm ready to delete that extended partition right now if, in doing so it might show us a difference in behavior in these disk checks. I wouldn't be so willing to do that once my logical symlinked data partition to my /mnt is there, as was my plan. 

What do you think about me trying that?  and/or  ... I can make a new smaller primary partition for swap, or logical one in a new extended partition ... whatever. 

I'll wait and see if you or anyone else thinks there is merit in doing something like above. It's a small matter to try it, now.

Thank you.

---

### Post by oldfred on 2015-07-06
We are down to all sorts of testing, because all the standard fixes do not seem to be working.
So if willing to try various things that will not cause you to lose data, the by all means experiment.

---

### Post by Bashing-om on 2015-07-06
mikodo; Yeah ;
> 
oldfred
Re: Power outage = hard shutdown, reset to default settings, time wrong and Questions

We are down to all sorts of testing, because all the standard fixes do not seem to be working.
So if willing to try various things that will not cause you to lose data, the by all means experiment.

+1 from me .

When punting, reduce to simplest terms . We all want to know the why of this situation.

[INDENT][INDENT]in for a penny, in for a pound
[/INDENT][/INDENT]

---

### Post by CharlesA on 2015-07-06
> **oldfred said:**
> We are down to all sorts of testing, because all the standard fixes do not seem to be working.
So if willing to try various things that will not cause you to lose data, the by all means experiment.

Agreed.

Just back up any data if needed.

---

### Post by mikodo on 2015-07-06
Thank you, all!

My new usb hard drive is supposed to be here between the the 6th and 8th. I think I might wait until then and backup with that. I think somehow I messed up the ownership and perms on the old one. I'm leaving things alone for now with the internal drive, until I can get some sleep at least.

I got a rebuilt alternator into my wife's car and took it for a spin after charging the battery today. It's good.

At least, I got something done.

When I'm tired, I can bust my knuckles on car and it's "no harm, no foul". It's not the same with this technology. lol

Tomorrow's another day.

---

### Post by oldfred on 2015-07-07
A user is trying to boot without battery & getting fsck on every boot.

[http://ubuntuforums.org/showthread.php?t=2285629](http://ubuntuforums.org/showthread.php?t=2285629)

---

### Post by mikodo on 2015-07-07
Hi Fred.

```
more /var/log/syslog
```

That is a huge file! I don't know what to look for. I don't know how to paste by keyboard to Ubuntu Pastebin or even if I should even paste the whole log anyways. It might choke it or something being so large. lol. (I always just save the output to mouse pad, go the Ubuntu Pastebin website and copy it in). 

Anyways, what's this from Calgary about? My ISP?

```
Jul  6 10:51:09 mikodo kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jul  6 10:51:09 mikodo kernel: [    0.000000] Checking aperture...
Jul  6 10:51:09 mikodo kernel: [    0.000000] No AGP bridge found
Jul  6 10:51:09 mikodo kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Jul  6 10:51:09 mikodo kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jul  6 10:51:09 mikodo kernel: [    0.000000] Memory: 4016940K/4184376K available (7392K kernel code, 1146K rwdata, 3408K rodata, 1336K init, 1448K bss, 167436K reser
ved)

```

Thanks.

I'm off to do other things.

---

### Post by oldfred on 2015-07-07
There are several posts in various forums of all versions of Linux with similar error message. Does not seem related to anything, just a warning?
One was related to IOMMU settings which are related to USB ports. Do you have a BIOS setting on IOMMU or USB ports?

---

### Post by mikodo on 2015-07-07
Do you have a BIOS setting on IOMMU or USB ports?

I dunno. I'll try to look later.

Thanks.

---

### Post by mikodo on 2015-07-07
> **oldfred said:**
> There are several posts in various forums of all versions of Linux with similar error message. Does not seem related to anything, just a warning?
One was related to IOMMU settings which are related to USB ports. Do you have a BIOS setting on IOMMU or USB ports?

Hi Fred.

Just got back from the gym.

I had to read what IOMMU was.

Answer to your question, I see nothing in The BIOS Settings Utility, that specifically says IOMMU. But, a couple of days ago when I was going back and forth into it, I enabled = Virtualization Technology, in case I wanted to use it with VBox again. I disabled it just now, as I don't have any plans to use that in the foreseeable future.

From reading, I (sorta) understand that IOMMU can be allowed to use PAE 32-but kernels. I did use those before I went to 64-bit ones. And I know that if I wished I could use PCI Express for a GPU with my motherboard, if I wanted to but, never have. (just onboard Intel graphics).

Please let me know of anything I should be concerned about.

Thanks, again.




Other than that, I"m waaaay over my head, and stopped reading links when I started reading from Wikipedia about IOMMU's:

  [https://en.wikipedia.org/wiki/IOMMU](https://en.wikipedia.org/wiki/IOMMU)

"Memory is protected from malicious devices that are attempting DMA attacks and faulty devices that are attempting errant memory transfers
 because a device cannot read or write to memory that has not been explicitly allocated (mapped) for it. The memory protection is based on 
the fact that OS running on the CPU (see figure) exclusively controls both the MMU and the IOMMU. The devices are physically unable to circumvent 
or corrupt configured memory management tables.
        In virtualization, guest operating systems can use hardware that is not specifically made for virtualization. Higher performance hardware 
such as graphics cards use DMA to access memory directly; in a virtual environment all memory addresses are re-mapped by the virtual machine software,
 which causes DMA devices to fail. The IOMMU handles this re-mapping, allowing the native device drivers to be used in a guest operating system.
    In some architectures IOMMU also performs hardware interrupt re-mapping, in a manner similar to standard memory address re-mapping.
    Peripheral memory paging can be supported by an IOMMU. A peripheral using the PCI-SIG PCIe Address Translation Services (ATS) 
Page Request Interface (PRI) extension can detect and signal the need for memory manager services.

---

### Post by oldfred on 2015-07-07
You now know more about IOMMU than the rest of us. :)

I just know it was a setting on some new motherboards that had to be changed. Or a boot parameter.
But do not think directly related to issue.

But surprised another thread with similar issue, but he had no battery on motherboard.

---

### Post by mikodo on 2015-07-07
Fred. 

I'm glad you think that. Ya, surprising you found that, while searching.

Thank you, for that.

> **oldfred said:**
> 
But do not think directly related to issue.
But surprised another thread with similar issue, but he had no battery on motherboard.

---

### Post by oldfred on 2015-07-08
User in other thread seems knowledgeable.

It's not an disk error. When the Ubuntu's init scripts detect a BIOS  date previous to the last date saved on disk, launch a fsck.

So when battery was not working did some files get updated with bad dates, so you still get fsck on every reboot?

---

### Post by mikodo on 2015-07-09
> **oldfred said:**
> It's not an disk error. When the Ubuntu's init scripts detect a BIOS  date previous to the last date saved on disk, launch a fsck.

So when battery was not working did some files get updated with bad dates, so you still get fsck on every reboot?

Hi, Fred.

Sounds, very plausible.

Thanks.

---

### Post by mikodo on 2015-07-10
Wiped and recreated blank data partition
Added to /etc/fstab using UUID i.e.
 UUID=adsfasdfa-daf-afd-8153-adfadsfadsf    /media/username/DataP    ext4    defaults    0       1

fsck startup autocheck errors corrected.

---

### Post by mikodo on 2015-07-10
Hi everyone!

The previous post was written by a tech, per my request,  that came into my home. He couldn't get the second internal partition  to read and write. Read only. He believes there is file corruption, probably due to the hard shut down.

Though, I will still have problems with this installs with any new internal partitions not providing  "write" to them, he documented an easy work around for me, for the remainder of this install.

Edit: I hadn't edited /etc/fstab with the UUID, for the hasty internal partition I made. Now I know better. With that, there  are no new fsck on startup. ](*,)

Like others, he believes I can continue with this install, without any further actions. He says the new internal disk checks out fine.

And Fred, he made an internal disk data partition,  that is seen through a symbolic link from my /home and did rsync backups of it  to my "old" usb drive, and a thumb drive to take to a friend's house, for off-site safe keeping of my data. I had messed up the mount-point, and partitioning for the old usb hard-drive, (he didn't recommend using the new one I bought). He gave lots of good advice. I can return the new usb drive, for full refund as, I hadn't even taken it out of its packaging.

Next, is a Battery Backup, that has auto shutdown.

Thanks, for all the help with this.

---

### Post by Bashing-om on 2015-07-10
mikodo; Outstanding !

You do good work. Gratifying to know was a "bad" partition at fault .

When this is said and done from the others, 
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And hey
[INDENT][INDENT][INDENT]look forward to our next adventure
[/INDENT][/INDENT][/INDENT]

---

### Post by mikodo on 2015-07-10
> **Bashing-om said:**
> mikodo; Outstanding !

You do good work. Gratifying to know was a "bad" partition at fault .

When this is said and done from the others, 
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And hey[INDENT][INDENT][INDENT]look forward to our next adventure
[/INDENT]
[/INDENT]
[/INDENT]


Hi Bashing-om.

Thank you, for the kind comments. I feel a little better about my causing so much work for you and everyone else. I am not sure of all the mistakes I made, but they were a few.

But, you took it in good spirit.

Yes, I will mark it as solved after a while.

My best.

---

