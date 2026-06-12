---
title: "[Ubuntu] Newest update &quot;broke&quot; everything"
date: 2017-05-03
forum: General Help
---

### Post by Myst1234 on 2017-05-03
Hi all,

I sat down at my computer this morning to start work. As it's done many times before, the software updater popped up and I clicked install. Once it was done updating, it asked to restart the computer. Since I've been using Linux distros (Ubuntu for over half the time) I've never really thought twice about these updates since I've never seen anything go wrong. Well, to my surprise, once the computer restarted, all of my settings were reverted to some default, my wireless mouse is not working and wi-fi is off. 

I'm semi-familiar with keyboard shortcuts so I've navigated around a little to inspect things, but nothing appears out of place. I tried restarting the network manager, I checked the wireless dongle was being detected, and everything appears correct, but it is obviously not based on the above issues.

Question(s) is, what happened? How can I fix this?  

Thanks in advance

P.s. I'm writing this from my phone (no WiFi on the comp) so I may not be able to provide code snippets.

---

### Post by oldfred on 2017-05-03
Do you have a separate /home partition?
It could be it could not load the /home partition, and created a new default /home.
If that is the case run fsck on /home partition.

If you can boot using recovery mode to a terminal. Make sure partition not mounted.
But better to use your live installer.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Edit:
Also have you tried booting with the older kernel?

---

### Post by Myst1234 on 2017-05-03
When I set this computer up I didn't partition anything aside from what the install does on its own. I also tried hardwiring Ethernet cable and it still would not pick up internet.

I'm going to check partition now in recovery mode

---

### Post by ian-weisser on 2017-05-03
Please post your /var/log/apt/term.log entry for the update in question.
If that machine cannot access the network, please post a clear photo of the log entry.

Oldfred's advice to try an older kernel is excellent. Clears up a lot of situations like these easily.

---

### Post by Myst1234 on 2017-05-03
> **ian-weisser said:**
> Please post your /var/log/apt/term.log entry for the update in question.
If that machine cannot access the network, please post a clear photo of the log entry.

Oldfred's advice to try an older kernel is excellent. Clears up a lot of situations like these easily.

How would I try an old kernel? Also, I can't connect to the internet wifi or Ethernet so wouldn't I need to in order to use an old version?

And how should I get to the read out of the log to post a pic?

---

### Post by Myst1234 on 2017-05-03
I just noticed the filesystem, and it looks like it is booting from fat32. That should not be booted correct? 

The other two are ext4 and linux-swap(v1).

---

### Post by ajgreeny on 2017-05-03
Are you using 16.04?

There was an update of kernel yesterday which has caused many headaches for users as the update did not originally pull in the usual header packages and linux-image-extra which is needed for drivers for many wifi and graphic cards.
A bug was posted at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687623](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1687623) though the problem now appears to be solved simply by updating again.

If this is your situation you can get to the grub menu to choose a different kernel by holding Shift at boot, or repeatedly stabbing at Esc if machine uses UEFI.

PS: That fat32 partition is possibly the EFI partition made automatically when installing to a UEFI machine; do not do anything to that but try the earlier kernel and then updating again.

---

### Post by Myst1234 on 2017-05-03
Thank you everyone for your help. It's been a trying morning but it looks like selecting a previous kernel did the trick.

@ajgreeny - so you're saying updating again from this old kernel should work? Or should I stick with the 4.4.0-75 (-77 is the new one) for a while?

---

### Post by deadflowr on 2017-05-03
Update again.
The completed kernel package should get fully installed this time around for the -77 kernel version.

---

### Post by Myst1234 on 2017-05-03
Thanks again everyone. Everything is back to normal and system is updated.

---

