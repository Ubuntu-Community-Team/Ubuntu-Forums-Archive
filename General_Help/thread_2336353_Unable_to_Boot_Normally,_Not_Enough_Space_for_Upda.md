---
title: "Unable to Boot Normally, Not Enough Space for Updates, Unable to Make Space"
date: 2016-09-07
forum: General Help
---

### Post by jakeclarkphoto on 2016-09-07
Hi everyone, 

I'm running Lubuntu 14.04 and had been doing so for several months without issue, but my computer is no longer able to start normally, and I think it stems from an incomplete update caused by a lack of space to store said update. 

When I use recovery mode to boot and try to run the software updater, I get a message that says "Not enough free space," as I have at times in the past. I've previously used a terminal command to resolve my recurring lack of space issues (caused by undeleted old kernels, it seemed), but that solution is no longer working for me. And while I managed to install Ubuntu Tweak, it doesn't seem to be removing those old kernels. 

I'm able to boot the system only by using recovery mode and fiddling around (I really have only the most basic understanding of how to use Ubuntu). When I try to boot normally, I get several lines of text that culminate with:

"[ end kernel panic - - not syncing: VFS: unable to mount root fs on unknown--block (0,0)"

I'd attached some photos of some of the screens I've encountered throughout my travails to this post, but of course they were too large to attach (because how could anything ever be that simple?). If anyone has any tips, I'd love to hear them. This whole old kernel business is pretty demoralizing - trying to learn how to use Ubuntu only to have it self-destruct on me.

---

### Post by jakeclarkphoto on 2016-09-07
Ok, here are a few photos of screens I come across while trying to fix things. The last photo shows the terminal command that used to clear up my old kernel issues, but now just results in the output that you see in the photo to its left.

---

### Post by ian-weisser on 2016-09-07
Do you want to work hard to repair your current system, which may take a few days on-and-off?
Or are you interested in simply doing a backup-and-reinstall, which will take most of an afternoon?

On an LVM/encrypted system, it's really important to do proper maintenance on the /boot partition.
If we help you fix the problem (or reinstall14.04), the problem will promptly recur with your current habits.

FYI - That issue was fixed in Ubuntu 16.04.

---

### Post by jakeclarkphoto on 2016-09-07
If the old kernel issue has been fixed in 16.04 then I may just go ahead and install it and start over from scratch, frustrating as it is - I really had my system set up just how I liked it. I figured that with a long-term release I could just set it up and leave it, provided that I didn't ever develop any needs beyond its capabilities. 

What is it about my habits that led my Lubuntu set-up's implosion?

---

### Post by Impavidus on 2016-09-07
[s]What has been fixed in 16.04 (I think) is that the installer now makes the /boot partition large enough by default.[/s] (See below.) Your problematic habit is that you don't uninstall old kernels right after installing a new one, despite having a small /boot partition. So you should either change that habit and uninstall old kernels, or make the /boot partition bigger, which works best if you do a fresh install.

To see if we can clean this up easely, run these two commands and post the output (copy-paste into a forum post, in [noparse]```
code tags
```[/noparse]).
```
uname -r
dpkg -l | grep -E 'linux-(headers|image)'
```From one of your pictures, I get the impression that you have 14.04 with the vivid kernel, support wherefore ended last month. But in that case you can move on to the 4.4 kernel without reinstalling and keep the rest of your system at 14.04, if you wish. But if you want the latest LTS release, just do a fresh install of 16.04.

---

### Post by ian-weisser on 2016-09-07
> **jakeclarkphoto said:**
> What is it about my habits that led my Lubuntu set-up's implosion?

LVM (including encryption) cannot boot natively. So Ubuntu needs a small unencrypted/non-LVM partition to read the kernel and initramfs image in order to boot. This tiny /boot partition works great...until a few kernel updates fill the partition. Then you begin to get apt and dpkg 'out-of-space' errors until you simply uninstall the old, obsolete kernel packages.

There are two interrelated issues (not bugs):
1) Apt does not autoremove old kernels in 14.04 by default. That's deliberate - if a bad kernel upgrade hits, you *need* a working older kernel.
2) Apt remembers it's queue of unimplemented actions, runs each in order, and aborts the entire queue when one action fails. This is changing in 16.10.

The upshot of these issues is that tiny /boot fills with old kernels that are not getting removed. Your habit in 14.04 with LVM/Encryption must be to clean them out. This can be trivial - simply enable the 'autoremove' option in unattended-upgrades (included in the default install), and you will never encounter the problem. Or simply run 'apt-get autoremove' every month. Once /boot is full, however, 'autoremove' won't work anymore due to that second issue (prior actions abort the queue due to out-of-space, so autoremove doesn't run), and you must clean out the kernels using dpkg (NEVER use 'rm'. That makes things worse).

Once the developers were made aware of the problem (by people in this forum!), they solved the problem in two days. In 16.04, an additional feature in unattended-upgrades (that *is* enabled by default) specifically cleans out old kernel packages daily, keeping only the current and one older kernel. The fix is unlikely to be backported to 14.04, which already has a trivial fix.

---

