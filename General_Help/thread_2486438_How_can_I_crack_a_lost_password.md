---
title: "How can I crack a lost password"
date: 2023-04-30
forum: General Help
---

### Post by Gnusboy on 2023-04-30
Hi all. It's been a minute.
I've been off the forum for awhile, but I need some help fixing a new-ish rig.
I had a fatal crash with my previous Ubuntu 18.04 system. Long story short, I had to switch to an old Win XP machine without the ability to go back to Ubuntu.
I finally bought an old, but Linux compatible system. It's good enough for now, but here's the rub - 
The guy I bought it from had pieced it together and loaded Ubuntu 22.04. It runs good, but I can't install any new programs or tweak the existing stuff. 
I can't get past authentication and can't update anything.
When I picked it up, my friend said he could not remember if there was a password on it, but didn't think so. Apparently, it does and he can't remember the password.

I tried anything I thought might work, but that just ain't doing it and I can't get through authentication. The pgp & gpg keyrings are empty files, and the others are locked.
I am still not confidant under the hood, so if anyone has an idea to fix it, I'd really appreciate the help.

Thanks.

---

### Post by tea for one on 2023-04-30
Download your preferred Ubuntu flavour 22.04 iso.
Make a bootable USB.
Install with your own password.
Your PC is now under your complete control.

---

### Post by MAFoElffen on 2023-05-01
+1 with Tea For One.

Then you have a PC that is a clean install. No extra files left over from the old user. Install the programs you want. All is known to you. No surpises later, in how someone else did something.

***
Operating System security is "physical". Meaning that anyone who has the physical security of a computer can get into it. (Unless you setup disk or partition encryption.)

Hint. Grub2 boot menu > Advanced Options > Rescue Mode > Enable Networking (mounts filesystem) > Root prompt... At root prompt, reset password for the known User.

---

### Post by Gnusboy on 2023-05-01
> **tea for one said:**
> Download your preferred Ubuntu flavour 22.04 iso.
Make a bootable USB.
Install with your own password.
Your PC is now under your complete control.
---------------------------------------------------------------------------
Thanks, Y'all

But Ubuntu 22.04 is already installed - (by seller)

Do I still make bootable USB, and install it with a new password? (probably yes?)

And ... is it still necessary to install 20.04 before I can install 22.04?  (Ubuntu 18.04 - 20.04 - 22.04) over write existing data unless I make a separate partition ? 

I appreciate your help with this.. THX

---

### Post by deadflowr on 2023-05-01
> And ... is it still necessary to install 20.04 before I can install 22.04?
What? No, 
Just grab the flavor of choice (as suggested already) for 22.04 and create a quick bootable media for it and do a clean install of 22.04.

Unless you have some oddball setting that requires 20.04 to be installed first in order to rectify it before installing 22.04,
there shouldn't be any need to install 20.04.

---

### Post by Tadaen_Sylvermane on 2023-05-01
If you want to use what's already installed (I wouldn't) then you can use the same live usb installer to chroot in and change the password yourself. Another option. Not a good one. Do a clean install that you can trust.

---

### Post by Gnusboy on 2023-05-01
OK got it. 
When I first started using Ubuntu, to upgrade you had to go version by version to install a new version. Or so I recall it. 
Why is it that I can remember this, but not how to do stuff I need to know today.
Word to the wise - don't get old. Or, alternatively, do get old, but learn the phrase "doddering old fool." You might hear it a lot. :shock:

---

### Post by Gnusboy on 2023-06-19
Hi Deadflowr
I get what you're saying, but when do the clean install does that wipe the hard drive?
Or I can  do a full sys backup and go from there?

---

### Post by Gnusboy on 2023-06-19
This is weird
I just got the response on cracking my password on the "general help"and asked a related question from Deadflowr. 
Then I went to check something and when I came back after a couple of minutes, the 6 answers that were previously posted
were not there. All I saw was the question I'd asked without those earlier responses.
What gives?

---

### Post by yancek on 2023-06-19
> When I first started using Ubuntu, to upgrade you had to go version by version to install a new version. Or so I recall it.  

You need to go version to upgrade from one release to another unless you are upgrading from one LTS to another.  LTS versions are those released in April of even numbered years.  That is not the same as doing regular updates or installing software. 

> I get what you're saying, but when do the clean install does that wipe the hard drive? 

If you do a clean install you will have options.  The installer will likely see the currently installed 22.04 and ask if you want to overwrite it or if you want to install it on another partition.  If yo want to keep the old one, you need to use the Manual (Something Else) option so you can tell the installer what you want.  Another option is to install to the same partition on which the old 22.04 is but do NOT format that partition or other partitions such as /home if they exist.

---

### Post by Gnusboy on 2023-12-10
Hey all,

I'm trying to reset my password on 22.04. I followed the instructions to get to the recovery boot 
But ... instead of the usual root prompt to reset, there's a "to be filled by O-E-M"
[mount -o rw, remount] 
is not accepted
[ls/ home] 
[password username] is not accepted
etc.

I was going to try to use GRUB, but it looked like it might wipe out my files. (I'm pretty sure it would not do that - but "pretty sure" doesn't work for me.)
I tried everything I could find about it, but there was nothing about the OEM thing. And I can't get past it. 
 I know what OEM is - but this is a secondhand build from a friend who can't remember setting a password or admin authorization.
I have an external 1 TB drive connected by USB - It's got plenty of room, but unless I'm doing Ubuntu clean install, I'm not comfortable making a new partition on it with existing important files.
I HAVE to get this system working properly. I'm currently running old versions of everything and without the admin password nothing will install.

Some ideas would be appreciated. Thank you

---

### Post by ajgreeny on 2023-12-10
On first run of an OEM installed system you would, or should, have been asked to create a user and a password.
Did that happen?

---

### Post by HermanAB on 2023-12-10
Reinstalling only takes about 30 minutes.  You prolly wasted more time on it already! &#128514;

---

### Post by TheFu on 2023-12-10
> **HermanAB said:**
> Reinstalling only takes about 30 minutes.  You prolly wasted more time on it already! &#128514;

+1.  

There's no practical way to crack a password for login to any Unix/Linux system.  

The solution is to either perform a fresh install or to use some non-beginner-friendly methods to overwrite the old password with a new one.  

Based on the difficulties you've shown in these forums, both in this thread and others, I agree that for you, the best, easiest, answer is to start with wiping the system and doing a fresh install or 22.04.  

The wipe will happen during the install - just choose "use entire drive".

A fresh install takes 12 - 20 minutes, so the time you've already wasted in this thread is beyond the time for a fix/solution that would result in an install that you KNOW isn't pre-hacked.

---

### Post by MAFoElffen on 2023-12-10
+1 -- It's a "new-to-you" computer system. There is no reason why you should balk at starting out with a new & fresh OS, instead of with someone else's hand-me-down installation.

---

### Post by Gnusboy on 2023-12-10
Did you see my reply? It's not showing on my screen

---

### Post by Gnusboy on 2023-12-10
Thanks, TheFu. You have helped me a lot through the years and I appreciate it.
Is 22.04 current or should I get a newer flavor?

---

### Post by MAFoElffen on 2023-12-10
@Gnusboy -- Yes, I saw your posts.

Ubuntu 22.04.3 Is the latest LTS version ([https://releases.ubuntu.com/jammy/](https://releases.ubuntu.com/jammy/)). The next LTS release is at the end of April.

Download the iso. Create a bootable Installer LiveUSB. Ubuntu's "Startup Disk Creator" can do that for you, using that downloaded ISO file. Install. If you need help with that, we can talk you through that.

---

