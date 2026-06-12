---
title: "Edited Fstab and now Ubuntu will not boot"
date: 2013-11-04
forum: General Help
---

### Post by aideds on 2013-11-04
As the title implies, I edited the fstab of my computer and now Ubuntu will not boot. I created a backup of my Fstab file prior to editing and when I placed that in the fstab folder, Ubuntu still does not boot.

Currently, my fstab reads as this:

```

#/dev/sda5
UUID=320ab1f7-a4a8-41c6-ba20-7f73bdd263e4 / ext4 errors=remount-ro 0 1
#/dev/sda6
UUID=66d4e3ec-efe9-4f77-9f49-8c776973b737 none swap sw 0 0
```

I'm not really sure what I did wrong so I would really appreciate any help. :?

---

### Post by TheFu on 2013-11-04
Please run **boot-info** and post the results.  See my signature for links.

---

### Post by aideds on 2013-11-04
> **TheFu said:**
> Please run **boot-info** and post the results.  See my signature for links.

Here's the [link to the boot-info]("http://paste.ubuntu.com/6362010/").

---

### Post by TheFu on 2013-11-04
Well, the fstab does NOT appear to be the issue. Perhaps you did something else too?
According to the boot-info, running **boot-repair** should fix something.

If that refuses to boot after the repair, comment out the swap line and try to boot again.

---

### Post by aideds on 2013-11-04
> **TheFu said:**
> Well, the fstab does NOT appear to be the issue. Perhaps you did something else too?
According to the boot-info, running **boot-repair** should fix something.

If that refuses to boot after the repair, comment out the swap line and try to boot again.

I didn't do anything except edit the fstab. I ran boot-repair but I still cannot boot successfully. Uh oh.

What swap line are you referring to?

---

### Post by ian-weisser on 2013-11-04
When you boot, please describe *exactly* what happens. In detail.

Do you see the BIOS or boot-setup prompt?
Do you see the grub prompt or timeout?
What does the screen show?
What text do you see?
When the boot fails, is there text? Image? Color? How do you know the boot has failed?

---

### Post by aideds on 2013-11-04
> **ian-weisser said:**
> When you boot, please describe *exactly* what happens. In detail.

Do you see the BIOS or boot-setup prompt?
Do you see the grub prompt or timeout?
What does the screen show?
What text do you see?
When the boot fails, is there text? Image? Color? How do you know the boot has failed?

I see the BIOS prompt.
I see the grub prompt.
After it timeouts, it is a black screen with a blinking cursor in the top left. It stays on the screen for about five seconds.
After the boot fails, it displays:
```
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.
root@hostname:~#
```

That's how I know the boot has failed.

---

### Post by ian-weisser on 2013-11-05
(Withdrawn)  TheFu's response is more complete and concise than mine!

---

### Post by TheFu on 2013-11-05
> **aideds said:**
> I didn't do anything except edit the fstab. I ran boot-repair but I still cannot boot successfully. Uh oh.

What swap line are you referring to?

The swap line in the fstab, but it appears you need to manually update/install grub into the sda MBR. The exact steps are hard to explain, but the overall idea is simple.
[LIST=1]
[*]Boot off a liveCD or into rescue-mode
[*]mount the root-partition somewhere - under /mnt is a good place
[*]run chroot so that the mount for /boot and / and /etc are now seen as / inside the liveCD environment
[*]run grub-install /dev/sda
[/LIST]
The boot-repair tool should be able to do these things, but I have seen it get confused when the liveCD environment orders mounted drives in odd ways. That happened here last month on a new server. Had to manually use grub-install.

---

### Post by jamesisin on 2013-11-05
Why are we having this user attempt to reinstall Grub rather than trying to fix the fstab?  Wouldn't it be best advised to first check the information in the fstab for accuracy?

I would log into the LiveCD and run blkid to make absolutely certain that the UUID's listed in the fstab are identical to what is shown in blkid.

I might also attempt to revert the fstab (if that information is available).

---

### Post by oldfred on 2013-11-05
+1 on jamesisin suggestion

Bootinfo report should show fstab. It should see the file in line 52 with the boot files, and then output the fstab further down, but I do not see it. Did it get renamed to .backup or something and not get restored or restored to correct location.

---

### Post by TheFu on 2013-11-05
Why?

Perhaps I missed something, but I did copy/paste the blkid from the boot-info output and matched it with the fstab he posted.  Seemed correct to me.

Can someone else review it please, since I could have missed something.

At the bottom of the boot-info, there was a comment about what a repair would do.

---

### Post by oldfred on 2013-11-05
Boot-Repair does not create a missing fstab. It may add an efi entry to an existing fstab if converting from grub-pc to grub-efi. Actually I do not think Boot-Repair even does that, but it is the grub2 install of grub-efi.

The fstab entries shown in post #1 look ok, but no fstab is shown in the correct /etc/fstab location for bootinfoscript to list it.

Run these command like I did.

fred@fred-Precise:~$ cd /etc
fred@fred-Precise:/etc$ ls fst* -l
-rw-r--r-- 1 root root 1164 Jul 19 11:00 fstab

---

### Post by aideds on 2013-11-05
> **oldfred said:**
> Boot-Repair does not create a missing fstab. It may add an efi entry to an existing fstab if converting from grub-pc to grub-efi. Actually I do not think Boot-Repair even does that, but it is the grub2 install of grub-efi.

The fstab entries shown in post #1 look ok, but no fstab is shown in the correct /etc/fstab location for bootinfoscript to list it.

Run these command like I did.

fred@fred-Precise:~$ cd /etc
fred@fred-Precise:/etc$ ls fst* -l
-rw-r--r-- 1 root root 1164 Jul 19 11:00 fstab

I don't see how the list command will solve the problem.

---

### Post by jamesisin on 2013-11-05
He's not solving the matter.  He's demonstrating whether the fstab file exists.

Alternatively you could do this:

```
ls -al /etc | grep fstab
```

---

### Post by aideds on 2013-11-05
> **jamesisin said:**
> He's not solving the matter.  He's demonstrating whether the fstab file exists.

Alternatively you could do this:

```
ls -al /etc | grep fstab
```

Okay then. It exists.

---

### Post by oldfred on 2013-11-05
And does it have correct permissions? That was part of original question.

Then post this, as it should be the same as your original list in post #1. And if all is correct as you say then it must work.

cat /etc/fstab

---

### Post by aideds on 2013-11-06
> **oldfred said:**
> And does it have correct permissions? That was part of original question.

Then post this, as it should be the same as your original list in post #1. And if all is correct as you say then it must work.

cat /etc/fstab

Yes, I have all the proper permissions. I really don't see how concatenation would help me here but I did it. It didn't fix anything. :neutral:

---

### Post by oldfred on 2013-11-06
It is not that you running it solves anything, but often having many eyes reviewing it sees something that is otherwise missed. I have looked at issues for hours and then see the problem later. Often quicker when many can review it.
If everything is then correct we move onto what else may be the issue. 
But please post both commands outputs.

---

### Post by coffeecat on 2013-11-06
> **aideds said:**
> I really don't see how concatenation would help me here but I did it. It didn't fix anything. :neutral:

Oldfred was not asking you to concatenate anything. The command cat /etc/fstab simply puts out the contents of the fstab file which needs to be seen to compare with what you posted in post #1.

---

### Post by aideds on 2013-11-06
> **oldfred said:**
> It is not that you running it solves anything, but often having many eyes reviewing it sees something that is otherwise missed. I have looked at issues for hours and then see the problem later. Often quicker when many can review it.
If everything is then correct we move onto what else may be the issue. 
But please post both commands outputs.

Okay, I understand now.

Running the commands, I get:

```
root@hostname:/# cd /etc
root@hostname:/etc# ls fst* -l
-rw-r--r-- 1 root root 524 Nov 6 07:34 fstab

```

```
root@hostname:/# cat /etc/fstab.d
```

Then it displays the contents of the fstab.

I have now discovered the root of the problem. The fstab folder was named to fstab.d for some reason. After renaming it to just fstab, the computer now boots properly. I feel dumb now.

Thanks everyone who helped me. :p

---

### Post by TheFu on 2013-11-06
We all do dumb things from time to time.  I've done a few ... er ... recently.  I'm positive I will do dumb things again.  Only been a UNIX/Linux admin since 1995.

In the meantime, please mark the thread [Solved].

---

### Post by jamesisin on 2013-11-06
Um... fstab and fstab.d are both important.  The fstab file is what you want to edit.  The other, fstab.d, is a folder.  Had you moved fstab into fstab.d?  Then, yes, you'll want to move it back up one directory.

---

