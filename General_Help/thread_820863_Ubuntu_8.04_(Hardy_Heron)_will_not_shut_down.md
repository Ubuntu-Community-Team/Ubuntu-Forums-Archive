---
title: "Ubuntu 8.04 (Hardy Heron) will not shut down"
date: 2008-06-06
forum: General Help
---

### Post by zipcodeman on 2008-06-06
So I Just did a fresh install of hardy heron with Wubi (Under Windows Vista), and after I updated (I think) the exit menu has no Shut Down or Restart buttons.

When I use Sudo Shutdown now, it will start by displaying an array of colorful bars across the screen. then it goes black and switches between showing Vertical white lines, and strobing what looks like the console (it's hard to tell)

the only way to shut down at that point is to hold the power button, and then at restart Ubuntu treats it as a crash.

I have tried other forums with no luck. any help would be appreciated.

---

### Post by Dan Hinojosa on 2008-06-06
I get the same thing.  I noticed that I get crashes everytime Firefox 3 Beta 5 crashes.  I can run the other apps, but the menu freezes.

---

### Post by ago on 2008-06-06
did that occur after the update only?
what is the output of 

cat /proc/cmdline

?

---

### Post by Dan Hinojosa on 2008-06-07
root=UUID=b3bbc3f0-7bd9-4eb3-b4c0-3b74a01ceba6 ro quiet splash

---

### Post by zipcodeman on 2008-06-07
> **ago said:**
> did that occur after the update only?
As far as i can tell, i did an update right after install so i can't be sure

root=UUID=3EFA764D75A175BE loop=/ubuntu/disks/root.disk ro quiet splash

---

### Post by ago on 2008-06-09
zipcodeman, looks like you installed on a fat partition, you have to boot with the kernel 16 (press esc at boot) a fix should be provided soon.

---

### Post by ago on 2008-06-09
Dan Hinojosa do you have any log? 

Like /var/log/syslog

---

### Post by Lpyo87 on 2008-06-09
I have the same problem, I'm new in any linux platform, and the shutdown/logout/hibernate menu doesn't appear at all in fact when I click on the exit button on the xfce menu it does nothing but if I click on the exit icon on the bar, I exit the Xfce panel. btw the output of cat /proc/cmdline is:
root=UUID=0ec85888-03eb-43b2-83be-cb5457c76024 ro quiet splash

---

### Post by ago on 2008-06-10
> **Lpyo87 said:**
> btw the output of cat /proc/cmdline is:
root=UUID=0ec85888-03eb-43b2-83be-cb5457c76024 ro quiet splash

There should be more to it unless you are on a real partition

---

### Post by zipcodeman on 2008-06-10
> **ago said:**
> zipcodeman, looks like you installed on a fat partition, you have to boot with the kernel 16 (press esc at boot) a fix should be provided soon.
Thanks ago I'll try that, but it should be on an NTFS Partition, or at least thats what it tells me at startup

---

### Post by zipcodeman on 2008-06-12
Booting into Kernel 16 didn't fix it, it just  created issues with Gnome

---

### Post by dksau on 2008-06-13
I have one computer that Hardy Heron won't shut down and one that works right.  This is from a fresh install but I think it happened after and update.  Its been a while so I can't remember for sure.  I thought it would be cured with another update. The computer that Hardy Heron does shut down is an AMD processor.  The one that doesn't shut down is an Intell 3.3 gig. I do show a message during boot that the BIOS fails the date test.  There is a post on the board from someone who claims to have found a solution but its for xubuntu and I get a no such command message when I attempt his remedy.

---

### Post by torgrot on 2008-06-17
My install initially would restart, but after the .18 update it will no longer restart.  It goes through the bar zipping back and forth until there are no segments lit and it just hangs there.  I need to use the power button to shut it down and restart it.  Now the curious thing is if I choose shutdown it shuts down.  I am currently running kernel 2.6.24-19

torgrot

---

### Post by ago on 2008-06-17
Can you shutdown/reboot normally if you boot with the 18 or 17 kernel (press esc at boot)?

---

### Post by ChameleonDave on 2008-06-17
Argh.  Why do people insist of trying to install Linux onto Windows partitions?

People, FAT is evil and NTFS is eviller still.  Use Ext3 or ReiserFS for your root partition, and Ext3 or FAT for data partitions that need to be read by Linux and Windows.

Edit: Ah, I didn't know about the whole Wubi thing.  I got here from a general search.

---

### Post by garg on 2008-06-17
Isn't that the whole point of Wubi? You can't expect a beginner using Vista to start using Ext3 or ReiserFS. :)

---

