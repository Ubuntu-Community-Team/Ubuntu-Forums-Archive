---
title: "Erratic boot-up performance with new Kylin 20.10 release"
date: 2020-12-04
forum: General Help
---

### Post by davepool on 2020-12-04
I'd been using the previous 20.04 release with no real problems.  Then last week I installed the new 20.10 release. This release boots up just fine. Unless it doesn't. Many start-ups are clean and straightforward. But perhaps a third or more of them produce this:

> You are in emergency mode. After logging in, type “journalctl -xb” to view system logs, “systemctl reboot” to reboot, ”systemctl default” or “exit” to boot into default mode.
Press Enter for maintenance
(or press Control-d to continue):

All I've done to this point is press Control-d, which produces 

> Reloading system manager configuration
Starting default target


...and, after a few seconds, usually takes me to log-in with no additional errors and a fault-free session from there. Usually, out of curiosity, I re-boot to see what happens on the next start up...and it's always clean. Once I pressed Enter for maintenance and just got a blank black screen....so I forced a shutdown with the power button and then re-started. Annnnd that boot-up was trouble-free.

Any ideas what's going on here and why it should be so erratic?

(ADDITIONAL INFO ADDED ABOUT AN HOUR LATER)

Anticipating that someone might ask me to run the command to view the system logs, here's the result:

-- Logs begin at Thu 2020-12-03 22:07:41 MST, end at Fri 2020-12-04 14:49:14 MS>
Dec 04 14:46:13 Lenovo-FLEX-3 kernel: microcode: microcode updated early to rev>
Dec 04 14:46:13 Lenovo-FLEX-3 kernel: Linux version 5.8.0-31-generic (buildd@lg>
Dec 04 14:46:13 Lenovo-FLEX-3 kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-5.>
Dec 04 14:46:13 Lenovo-FLEX-3 kernel: KERNEL supported cpus:
Dec 04 14:46:13 Lenovo-FLEX-3 kernel:   Intel GenuineIntel
Dec 04 14:46:13 Lenovo-FLEX-3 kernel:   AMD AuthenticAMD
Dec 04 14:46:13 Lenovo-FLEX-3 kernel:   Hygon HygonGenuine
Dec 04 14:46:13 Lenovo-FLEX-3 kernel:   Centaur CentaurHauls
Dec 04 14:46:13 Lenovo-FLEX-3 kernel:   zhaoxin   Shanghai  
Dec 04 14:46:13 Lenovo-FLEX-3 kernel: x86/fpu: x87 FPU will use FXSAVE
Dec 04 14:46:13 Lenovo-FLEX-3 kernel: BIOS-provided physical RAM map:
Dec 04 14:46:13 Lenovo-FLEX-3 kernel: BIOS-e820: [mem 0x0000000000000000-0x0000>
Dec 04 14:46:13 Lenovo-FLEX-3 kernel: BIOS-e820: [mem 0x000000000006f000-0x0000>
Dec 04 14:46:13 Lenovo-FLEX-3 kernel: BIOS-e820: [mem 0x0000000000070000-0x0000>
Dec 04 14:46:13 Lenovo-FLEX-3 kernel: BIOS-e820: [mem 0x0000000000086000-0x0000>
Dec 04 14:46:13 Lenovo-FLEX-3 kernel: BIOS-e820: [mem 0x0000000000100000-0x0000>
Dec 04 14:46:13 Lenovo-FLEX-3 kernel: BIOS-e820: [mem 0x0000000020000000-0x0000>
Dec 04 14:46:13 Lenovo-FLEX-3 kernel: BIOS-e820: [mem 0x0000000020100000-0x0000>
Dec 04 14:46:13 Lenovo-FLEX-3 kernel: BIOS-e820: [mem 0x00000000b8148000-0x0000>
Dec 04 14:46:13 Lenovo-FLEX-3 kernel: BIOS-e820: [mem 0x00000000b8a58000-0x0000>
Dec 04 14:46:13 Lenovo-FLEX-3 kernel: BIOS-e820: [mem 0x00000000b8b58000-0x0000>
Dec 04 14:46:13 Lenovo-FLEX-3 kernel: BIOS-e820: [mem 0x00000000b8b98000-0x0000>
lines 1-23

---

### Post by mattis13 on 2020-12-05
sudo lsblk to list partitons.
then
fsck.ext4 /dev/sda3 where sda3 is your partition. If you use old paartition EXT3 then fsck.ext3 /dev/sda3

It should check & fix the disk for any curruptions etc.   I have a USB key with fsck and ocasianlly boot from it and run fsck to fix partitions on my PC

---

### Post by davepool on 2020-12-05
Thanks for the reply...

But I get a major warning about how I'm going to cause great damage to my file system. A quick search about fsck stressed that you should always unmount a partition before running fsck with the command:

sudo unmount /dev/sda[X] (which does not appear in your instructions)

However, when I tried that, the response was: 

sudo: unmount: command not found.

Dead end?

---

### Post by deadflowr on 2020-12-05
The system log journalctl command utilizes less (or maybe it's more) so you need to keep pressing the down key or enter to scroll down the output.
You can also look at older boot logs by running with a -X (replace X with a number like
```
journalctl -xb -1
``` 
to view the last boot before the current, -2 for 2 boots earlier and so on.

---

### Post by tea for one on 2020-12-06
> **davepool said:**
> Thanks for the reply...

But I get a major warning about how I'm going to cause great damage to my file system. A quick search about fsck stressed that you should always unmount a partition before running fsck with the command:

sudo unmount /dev/sda[X] (which does not appear in your instructions)

However, when I tried that, the response was: 

sudo: unmount: command not found.

Dead end?

The command to [COLOR="#0000FF"]unmount[/COLOR] does not have the [COLOR="#0000FF"]n[/COLOR]

```
sudo umount /dev/partition
```

---

### Post by davepool on 2020-12-06
Thanks, tea for one...I later discovered that small and slightly annoying fact! ;) [HEADSLAP] When I read that command in the article's instructions, I saw what I expected to see, not what was there.

Okay, that bit of poor comprehension "fixed," the command 

sudo umount /dev/sda[x] produces this:

umount: /: target is busy

Let me ask you (which is to say everyone) this: Ubuntu Kylin is on a dual-install device: I have EndeavourOS on it as well. Would it be easier to just boot up in that and then run fsck on the Kylin partition from there (thereby guaranteeing that the Kylin partition is neither mounted nor busy)?

---

### Post by tea for one on 2020-12-06
> **davepool said:**
>  When I read that command in the article's instructions, I saw what I expected to see, not what was there.

Yes, I regularly misread text with the same expectation as you - brain and eye co-ordination not in sync...........;)

Anyway, as you have discovered, you cannot run [COLOR="#0000FF"]fsck[/COLOR] on a mounted partition. Generally, you use a [COLOR="#0000FF"]live [/COLOR] session.

You can probably run it from your Endeavour partition with Ubuntu Kylin unmounted (assuming Endeavour OS uses the same command)

Try it and see what happens - either it will be OK or you'll see an error message.

---

### Post by davepool on 2020-12-06
> **tea for one said:**
> 
You can probably run it from your Endeavour partition with Ubuntu Kylin unmounted (assuming Endeavour OS uses the same command)

Try it and see what happens - either it will be OK or you'll see an error message.

Okay, I tried it. First, the command worked (or at least there was no error). Whatever fsck did or did not do, it happened in the blink of an eye. Again, no error...but nothing in the terminal to suggest work done.

Nevertheless, I re-booted into Kylin and got the same "Press Control-d to continue" as before.

So, again consulting with some online info, I decided to run fsck in Recovery Mode. From GRUB, I chose Advanced Options, then Recovery Mode. Ultimately, that produced the Recovery Menu (file system state: read-only).  Among the choices there was fsck, which I selected and tabbed to OK.

This produced "Continuing will remount your / filesystem in read/write mode and mode and mount any other filesystem defined in /etc/fstab. Do you wish to continue."

Even though continuing seemed rather pointless (dooming me to an endless cycle), choosing No was also not likely to get me anywhere.  So, "Yes." as expected, produced a few lines in terminal mode that confirmed my Kylin partition was now mounted and the requested "Enter" took me back to the Recovery Menu (see above: endless cycle).

So, to recap, 1) I'm not even sure fsck did anything when it was run from EndeavourOS (blink of any eye, terminal prompt returns) and 2) I'm not sure how to crack this running in Recovery Mode (I suspect you'll mention "Live" session again, which I can do...but once I saw that it could also be done at boot-up by choosing Recovery Mode, that seemed easier and more expedient. But what do I know?)


[ADDED AFTER ORIGINAL POST]

Perhaps I can get this in before you read the above.  I went ahead and did a Live session and this time when I ran fsck I got:

> /dev/sda10: clean, 329077/5947392 files, 4148391/23771648 blocks

In addition, however, when I closed that Live session and re-booted into Kylin, I got the familiar "Press Control-d to continue"

So perhaps whatever is causing these intermittent boot-up failures in Kylin is caused by something OTHER than what fsck can correct, no?  However, in the course of my reading (on linuxize.com) I had seen this: 

[COLOR=#1F2937][FONT=Roboto]fsck cannot check the root file system on a running machine because it cannot be unmounted.[/FONT][/COLOR]
[COLOR=#1F2937][FONT=Roboto]If you want to check or repair the root file system, you have several options at your disposal. You can set the fsck to run on boot, boot the system in recovery mode, or use a live CD.[/FONT][/COLOR]

And so here is where I further reveal the limits of my Linux knowledge. Is the root file system somewhere *other* that the partition where Kylin is installed? When I ran fsck this last time (and got "clean" results) it was in the /sda10 partition where Kylin resides. From that Live session should I have run it somewhere else?

[COLOR=#1F2937][FONT=Roboto]
[/FONT][/COLOR]

---

### Post by davepool on 2020-12-06
> **deadflowr said:**
> The system log journalctl command utilizes less (or maybe it's more) so you need to keep pressing the down key or enter to scroll down the output.
You can also look at older boot logs by running with a -X (replace X with a number like
```
journalctl -xb -1
``` 
to view the last boot before the current, -2 for 2 boots earlier and so on.

Thanks for that reply, @deadflowr. I didn't mean to ignore the content you provided (very helpful!) but I confess to jumping all over the fsck utility and how to run that (although, so far, it seems to have given my Kylin install a "clean" bill of health...so that's good, but of no help with my erratic start-ups). So, yeah, mea culpa.

Problem is....even with that advice to check system logs and your assistance on how to page them....I still have no idea why I would want to look at them or what I should be looking for.

---

### Post by davepool on 2020-12-07
Follow-up, @tea for one

Now that I've seen the report that fsck produces, I recognize it from what I see on the screen with every startup! It's the second line to appear on the screen!  So...after all that, fsck was running automatically at startup???

I think I kinda "kissed it off" in the original post but....I *did* have Kylin 20.04 and that version/installation *never* gave me a bit of trouble on start up. And what I didn't tell you is: as soon as 20.10 started displaying this problem, I briefly returned to 20.04 where, again, there were no problems at startup. But, having seen just a taste of the improvements in 20.10, I went back to it and *RE*-installed it...at which point the startup notifications returned.  So....I already *have* done a clean re-install to see if that would change anything.  And it didn't.

---

### Post by tea for one on 2020-12-07
I only jumped into the thread to help you with [COLOR="#0000FF"]umount[/COLOR], but, nevertheless, let's see what transpires.

You currently have Ubuntu Kylin 20.10 installed and it still stutters occasionally during boot, possibly due to fsck in action.

I hope that you are using UEFI mode and that you have an EFI partition? (This can be corrupted with a forced shutdown as mentioned in your post no. 1)

File system check can be prevented at boot with a grub parameter - would you be interested in trying this?

It may help with Ubuntu Kylin 20.10 but I think that you already know what to do..............
> I briefly returned to 20.04 where, again, there were no problems at startup
if you want to persevere with Ubuntu Kylin 20.10, I'm happy to help you check your EFI partition and add the grub parameter.

---

### Post by davepool on 2020-12-07
Well, I have a /sys/firmware/efi folder, so there's that. 

Gnome-disks shows that the actual partition that Kylin is in (/sda10) is a Linux Filesystem partition...but also shows that /sda1 is an EFI system.  

Hope that info helps.  And thanks for your willingness to continue here...I don't think it occurred to me (obviously) that your reply was only to correct the umount/unmount misunderstanding.

---

### Post by tea for one on 2020-12-08
After booting into Ubuntu Kylin, you can unmount and repair (if necessary) your EFI partition using gnome-disk-utility.
Hover your mouse over the controls under the Volumes (i.e.partitions).
The third control (gear wheel) is Additional Options including Check and Repair

Assuming Ubuntu Kylin controls grub, you can add this parameter to prevent [COLOR="#0000FF"]fsck[/COLOR] during boot.
```
sudo nano /etc/default/grub
```
Then add the parameter [COLOR="#0000FF"]fastboot[/COLOR]
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_DISTRIBUTOR="Ubuntu 20.04"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="#0000FF"]fastboot[/COLOR]"
GRUB_CMDLINE_LINUX=""
```
Don't forget
```
sudo update-grub
```
I noticed that you have 10 partitions (or more), therefore it is not completely obvious how you have set up your PC
Therefore, be judicious and cautious with grub commands in order to select the correct OS which controls grub.

Lastly, [COLOR="#FF0000"]back up[/COLOR] your data before considering my suggestion.

Good luck

---

### Post by davepool on 2020-12-08
I'll be getting into your instructions later this morning.

Meantime, I wanted to share with you the message I get during start-up when "Press Control-d to continue" does NOT result in a successfui boot:

> Reloading system manager configuration
Starting default target
Failed to start default target: Transaction for graphical.target.start is destructive (emergency.target has 'start' job queued, but 'stop' is included in transaction).


Does that happen to tell you anything?  The only thing I can do at that point is a hard shut down, followed by a restart (which is usually successful in the post-Ctrl-d operation).

---

### Post by davepool on 2020-12-08
Okay, here's the report on the steps you gave me (and thanks for those!):

gnome-disks Check Filesystem said there was nothing wrong. Nevertheless, I ran Repair Filesystem anyway....and it came back with a report that the file system had been repaired. That strikes me as odd but, then again, this is the first time I've run any of those checks. I might've thought that no repair would produce something like "no repair necessary" and the fact that it said it had *repaired* the file system means something there needed repair.  But I dunno.

Anyway, I made the edit to grub, updated grub and then shut down for a full re-start. That got me again to "You are in emergency mode..." all the way to "Press Control-d to continue"....only it didn't fail, it went on to the splash screen and login. So I tried again...and the next reboot's response to the Ctrl-d was the now-familiar "Failed to start default target:" message.

So, initial indicators seem to be that there's no problem with the file system (either the EFI or the partition where Kylin resides) and nothing has changed in terms of winding up in emergency mode with every try.

---

### Post by davepool on 2020-12-09
Well, failing any other explanation for what I'm experiencing, I guess I'm inclined to leave Kylin 20.10 installed and just cross my fingers in the hope that updates to come might address the problem. It's not like this distro is one that I depend on. It's not even the only Ubuntu distro I have (the other would be Kubuntu) over a total of 3 laptops.

---

