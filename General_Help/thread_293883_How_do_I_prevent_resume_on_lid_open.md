---
title: "How do I prevent resume on lid open?"
date: 2006-11-05
forum: General Help
---

### Post by reacocard on 2006-11-05
The lid switch on my laptop is a little erratic, so it wakes up from sleep if it's moved while it's closed. How can I disable resuming on lid open?

---

### Post by tweedledee on 2008-05-13
> **reacocard said:**
> The lid switch on my laptop is a little erratic, so it wakes up from sleep if it's moved while it's closed. How can I disable resuming on lid open?

I realize that this question is 18 months old, but no matter how hard I looked for the answer, it took me a while, and Google kept this question near the top of most search results.  So, having found the answer, I'll post an answer here in the event it is useful to others.

First, this involves playing with /proc, which is essentially the running kernel.  There is the potential (however unlikely) you could cause your computer to crash.  Therefore, until you've tested step 1 (which is non-permanent and resets when the computer reboots), do not proceed.

The trick is in the "file" (really kernel setting) /proc/acpi/wakeup.  This is true on Debian as well, and probably most Linux systems (although the location/setting may change in future kernels).

**Step 1**. Testing to make sure you can change the lid setting.

**a** Test to make sure you can see a "LID" line when you execute```
cat /proc/acpi/wakeup
```in a terminal.  Lines with an asterik (*) next to them are ones you can toggle (I'll get to that in a minute); ones that say *disabled* are off, ones that say *enabled* are on.  There will probably also be something like "S3" or "S4", which is irrelevant at the moment (it has to do with the "deepest" suspend/hibernate/shutdown mode this toggle regulates; S5 is "off").  If this file isn't found on your system (e.g., if you get an error and "ls /proc/acpi" doesn't show the "wakeup" file), this solution probably won't help you.

**b** Assuming that the "LID" setting was "enabled" (if it was disabled, again this solution won't help, although it might if you are trying to turn ON this feature) and that it had an asterik (*) next to it, you can proceed.

**c** In a terminal, switch to root; in Ubuntu, execute
```
sudo -i
```and enter your password.  Then type```
echo " LID" > /proc/acpi/wakeup
```in the terminal.  The space in " LID" is important; all events in that file are 4 characters.  This command should toggle the setting on/off.

**d** Execute ```
cat /proc/acpi/wakeup
``` to ensure the LID setting changed, and THAT NO OTHER SETTING CHANGED.  Some laptops (e.g., I found reference to this for a thinkpad) may toggle multiple things, which could cause peripheral effects.  These effects may or may not matter to you, depending on what they are.

**e** Though it shouldn't be necessary, repeat **c** and **d** a couple of times to make sure that it flips back and forth and that nothing else seems to be happening.

**f** With the setting disabled, suspend and/or hibernate your computer, testing to see whether the setting did in fact disable resuming when opening the lid.  And also that you can come back out of suspend/hibernate without any problems.

**Step 2**.  Making the change permanent.
Only do this if all worked well above!  For this step, I'm assuming you are still root; however, you can do all of this as a regular user by appending "sudo" in front of all commands.

**a** Execute ```
gedit /etc/init.d/lid
``` in a terminal; you can use any other editor instead of gedit (nano, mousepad, kate, whatever) if you like.  Although "lid" should be safe, it is possible there is a file called that in /etc/init.d/, so if you do NOT see a blank file, close it and choose a name other than "lid" and substitute your name in **c** below.

**b** Copy the following into your new file.```

#!/bin/sh
RETVAL=0

case $1 in
  start)
    echo "Toggling lid wake-up switch..."
    echo " LID" > /proc/acpi/wakeup
    ;;
  stop)
    echo "Use start to toggle lid wake-up switch"
    ;;
  status)
    echo "Displaying lid wakeup status..."
    cat /proc/acpi/wakeup
    ;;
  *)
    echo "Usage: lid {start|stop|status}"
    echo "Start will toggle the switch"
    echo "Stop is just a placeholder"
    echo "Status displays the status of all possible wakeup events (including lid)"
    RETVAL=1
esac

exit

```

**c** In a terminal, type```
update-rc.d lid defaults 99 01
``` which will spit out some text about copying links.

That's it!  Now whenever you reboot, the necessary command will be issued to turn off the lid response.  I can't promise that future kernels won't break this solution, and if the default setting in the kernel is flipped (i.e., becomes disabled instead of enabled), the init.d script will have the effect of re-enabling the lid feature.

If you need to remove the lid script, for whatever reason, execute (as root/sudo)```
rm /etc/init.d/lid
update-rc.d lid remove
```in a terminal.

---

### Post by reacocard on 2008-05-13
> **tweedledee said:**
> I realize that this question is 18 months old, but no matter how hard I looked for the answer, it took me a while, and Google kept this question near the top of most search results.  So, having found the answer, I'll post an answer here in the event it is useful to others.

<snip>

Nice find! I've since solved the problem a different way (physically disabling the lid switch), but if I ever have this problem again I know how now. Thanks!

---

### Post by makito on 2008-07-17
It's been a while, but I can't get this to work. I can toggle the state of LID in /proc/acpi/wakeup but it has no effect. My laptop still resumes on opening the lid. Is there anything else that would effect this?

uname -r
2.6.24-19-generic

---

### Post by rosanna84 on 2008-07-17
Hi all, here are some popular website that may help you convert flv to 3gp or to other video formats, just have a try&#65281;&#65281;
cucusoft youtube mate[FLV to 3GP](http://www.flv-converter.com/flv-to-3gp.htm)
ultra flv converter [FLV to 3GP](http://www.flvto3gp.net/convert-flv-to-3gp.html)
cucusoft youtube mate: [FLV to 3GP](http://www.flvconverter.biz/flv-to-3gp.html)
aimersoft video converter[FLV to 3GP](http://www.flvtomp3.net/flv-to-3gp.html)
[FLV to 3GP Mac](http://www.flvconverterformac.com/FLV-to-3GP-for-Mac-Os-x.html) iksysoft video converter for mac

If you're a Mac user, you can use this [FLV to 3GP Mac](http://www.flvconverterformac.com/FLV-to-3GP-for-Mac-Os-x.html) converter.

---

### Post by tweedledee on 2008-07-18
> **makito said:**
> It's been a while, but I can't get this to work. I can toggle the state of LID in /proc/acpi/wakeup but it has no effect. My laptop still resumes on opening the lid. Is there anything else that would effect this?

uname -r
2.6.24-19-generic

If there is a BIOS setting, that would override anything set in the kernel.  It's also possible that the suspend/hibernate scripts are setting this value, overriding any of your changes.  I don't immediately recall where the script settings are (/etc/acpi?) as I'm currently running Debian and it uses a different suspend/hibernate system, but you should be able to turn them up in a general forum search.  I've also found that using "single user mode" (or 
"recovery", I think Ubuntu calls it) for testing is quite helpful to isolate this issue, although it requires manually sending the computer into suspend and hibernate using the /proc system.  I found a useful webpage a while back on troubleshooting suspend/hibernate that way, but can't recall exactly what it was.  A little googling should turn it up, though - you're looking for something that explains how to manually set the triggers in /proc to manipulate the power state the computer is in.  Beyond that, you're outside my experience.

---

### Post by makito on 2008-07-18
My BIOS is phoenix, there are no power management settings. lshw says I have a Clevo M5x0N motherboard, though I can't find any information on google about that mother board. Just a page on hardware4linux that says it is mostly supported.
   Ubuntu now uses pm-utils to suspend/hibernate. I greped through all the scripts but nothing writes to /proc/acpi/wakeup or has the string "wakeup" in them at all. Attached are the output of a couple of commands that might help someone more knowledgeable than me. The only thing I can see is that dmesg gives lots of:
ACPI Exception (thermal-0471): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
This is worrying, though possibly unrelated to my problem.

 In my wanderings in search of a solution (can one wander without moving from the couch?) I noticed that /proc/acpi/wakeup is deprecated (though supposedly still used) but I cannot find anything in my /sys/devices folder that corresponds to my lid switch. Everything in there is gibberish to me and there is no pci* line in /proc/apci/wakeup next to the lid switch.

Note: The reason I need to disable the lid switch is that my laptop will not suspend after being woken up by the lid switch. It works just fine as long as I don't close the lid, but once I close the lid and wake the computer up by opening it it hangs with black screen (no backlight) on suspend. I am more interested in disabling the lid switch however as I don't really want my laptop resuming on opening the lid.

Note on uploaded files. all files are after suspend and resume with lid switch. wakeup is my /proc/acpi/wakeup file. This file does not change after suspend. I had to change the extension on dmesg and lshal to .doc because the forum would not allow text files larger than 19.5 KB. They aren't that big < 100KB, but someone please tell me if this is not cool on this forum.

May thy Wandering be with greater fruit than mine

---

### Post by tweedledee on 2008-07-19
> **makito said:**
> Note: The reason I need to disable the lid switch is that my laptop will not suspend after being woken up by the lid switch. It works just fine as long as I don't close the lid, but once I close the lid and wake the computer up by opening it it hangs with black screen (no backlight) on suspend. I am more interested in disabling the lid switch however as I don't really want my laptop resuming on opening the lid.

To deal with the improper resume issue, you may want to look into "post_video" as a solution in the suspend/hibernation scripts; playing with that often appears to help recover from a blank screen, assuming that the computer fully resumed (e.g., the keyboard works); I've had several computers with blank screen issues where it didn't help, but generally the entire resume seems to have stalled at some point; in all cases, I've found changing the video driver and/or settings were necessary to resolve the problem, and the solutions were different for the same computer under Ubuntu 8.04 and Debian testing.

Regarding the /sys vs. /proc issue, you may have some success using this page as a starting point, if you haven't seen it (in one form or another):
[http://groups.google.com/group/fa.linux.kernel/msg/b3ca53d8e041c94a](http://groups.google.com/group/fa.linux.kernel/msg/b3ca53d8e041c94a)

I'm not clear if the suggested /sys approach was implemented; on my system, I see various "wakeup" *files* under /sys/devices/pci0000/, but the specification calls for *directories*.  It also appears that there may be a difference between i386 and AMD64, although I'm using the lid trick as described above on both types of systems.

Although it's non-optimal, you may also have success by changing the sleep state from S3 to S1 or S2 (one isn't used, but I forget which); you'll have more power drain during sleep, but whatever's allowing the lid trigger may be specific to S3.  With Ubuntu 8.04, I noticed that the default hibernation state was changed from S5 to S4, which influenced the lid state parameter on my systems.

---

### Post by makito on 2008-07-19
The keyboard does not work after failed suspend/resume. At least attempting to switch terminals, login, and issue a sudo shutdown -r now and typing my password has not done anything. 
My video card is the intel 945GM, I tried switching from the i810 driver to the intel experimental modesetting driver but it didn't change anything. I think the problem is something else though, because after I resume from a suspend with the lid switch, the next time I try to suspend it appears to suspend and then immediately try to wakeup, and then hangs. I ran a loop that echoed dmesg to a file. The last line in dmesg was 

Syncing filesystems ... done.

This line normally comes just before the pm system freezes userspace processes. I didn't see anything blatantly wrong, but then again, it would have to be pretty obvious for me to catch it.

Yes, I saw that page and a whole bunch of copies of it. I guess the linux kernel mailing lists is copied all over the place, but it doesn't really help. I understand that /proc/acpi/wakeup is being deprecated and the new one is /sys/devices.../wakeup, but wakeup is disabled in /sys/devices.../wakeup for the lid switch. writing enabled or disabled to that file results in an invalid argument error. This means that wakeup is not supported on that device according to a post (I don't remember where I read it). 

I can't write standby (S1 sleep state) to /sys/power/state, just mem (S3) works. S2 sleep state is not used and is generally a synonym for S3.

I am running an intel core 2 duo processor, though I hope processor architecture does not change the config file locations.

I just filed a bug report, [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/250018](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/250018), just about the /proc/acpi/wakeup issue, not the machine hanging on suspend. Let me know if there is anything more I should include in that report. 

P.S. I appear to be first in google for the search "ubuntu /proc/acpi/wakeup"! Pretty impressive for a bug report, eh?

---

### Post by tweedledee on 2008-07-19
> **makito said:**
> I just filed a bug report

From the sounds of it, you've attained about the same level of understanding of the issues involved as I have, so my final suggestion would have been to file a bug report (though even that's a bit hit-or-miss - Launchpad has been drowning in bug reports for the last few months).  At this point, all I can say is good luck, and please share if you find a solution, since this will likely affect all my computers once the /proc interface is actually removed.

A final note on your log files and analyze resume issues - my experience has been that some of the log entires for the suspend/hibernate process aren't written until after resuming, with some random frequency, so troubleshooting resume problems is fairly difficult using those alone.  It's possible to get lucky, but it's definitely a bit cryptic.  You can try posting a separate bug  on that issue, but they tend to be ignored unless you can pinpoint the problem yourself.  Your best bet may be to try to find a similar report already filed for similar hardware and see if anything is suggested that helps.

---

### Post by makito on 2008-07-20
well, everything works (including my old suspend problems) if i run
sudo /etc/acpi/sleep.sh force
instead of using pm-utils (default for gnome GUI)

So know I just have to find out how to tell gnome not to suspend with pm-utils, but use the old /etc/acpi scripts.

---

