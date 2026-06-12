---
title: "[SOLVED] Live CD Accessing Hard Disk Data - Locked Permissions?"
date: 2007-11-23
forum: General Help
---

### Post by 3nigma on 2007-11-23
Hey guys,

I have a MacBook, but that (hopefully) shouldn't be related to this question.

My operating system got corrupted.  I can't boot into it.  I also have a tiny Ubuntu partition installed, which can boot totally fine (not a hardware problem).

I booted into a 7.10 Live CD, and was able to see my hard disk partitions as accessible.  I could navigate to the Ubuntu partition, and see the data there.

HERE'S THE THING:
I can also access my OS X partition, and see the data.  The problem is that some of the folders I can open just fine, while others have a tiny red circle in the top-right of the icon.  When I try to open those ones, it says that I don't have permission.

Is there a way around this?

I am trying to rescue my data before wiping the hard drive.

Thanks in advance!

---

### Post by aysiu on 2007-11-23
Try Alt-F2 ```
gksudo nautilus
```

---

### Post by 3nigma on 2007-11-23
Can you elaborate?

I haven't used Ubuntu much, and am not familiar with the details.

And what is that "Code" part with the nautilus?

Thanks very much for taking the time to help!

---

### Post by aysiu on 2007-11-23
Sure. Thanks for asking.

Alt-F2 opens up a *Run* dialogue. In Windows, it's the equivalent of Windows-R. I don't think there's a native Mac equivalent, but the closest is a Mac application called Quicksilver:
[http://en.wikipedia.org/wiki/Quicksilver_(software](http://en.wikipedia.org/wiki/Quicksilver_(software))

Basically, the *Run* dialogue allows you to run a command.

The command *gksudo nautilus* launches the file browser (in Ubuntu called Nautilus) with administrative privileges (that's the what the *gksudo* means). When you have a file browser with administrative privileges, you should have access to all the files and folders on your drive.

---

### Post by 3nigma on 2007-11-23
Okay, gotcha- thanks again.

I actually use Quicksilver on my Mac, so that is good to know about Ubuntu.  (And as a side note, I have to say that I am incredibly impressed with how nice Ubuntu is, and it's miscellaneous attention to detail.)

Anyway, I executed that command in the terminal, and it opened up a new Nautilus window with the root privileges.  However, I did not see in this new window the available option of navigating to the mounted disk drives.  I could still open and look at a normal Nautilus window, and I could access the disks, but not in the root one.

Does that make any sense?

Thanks again for all the help.  I am enjoying this tiny bit of use with Ubuntu so much, that I am even being tempted to stick around and play with it a little more long-term!

Thanks!

---

### Post by aysiu on 2007-11-23
The root file browser will default to opening to a different location (/root instead of /home/username), but you should still be able to navigate to the mounted disk drives.

Try pressing Control-L and type ```
/media
```

---

### Post by 3nigma on 2007-11-24
Hmm.

Okay, I was able to do the following:

I mounted the OS X partition, so it showed up on the desktop.

In the ROOT Nautilus, I navigated to the "Users" and then to the "Ubuntu" user (Live CD), then the Desktop.

However, the mounted "Disk" did not show up in the ROOT Nautilus, despite being able to use the normal Nautilus to navigate to it absolutely fine.

I have some very important family photos that are locked in there, and I can't get to them =(.

Thanks again so very much, I sincerely appreciate you helping me out.  This is a VERY big deal.

Thanks!

---

### Post by aysiu on 2007-11-24
The mounted disk is not really on the desktop. It just appears that way.

It's probably mounted in /media/ instead of /home/ubuntu/Desktop

To find out the mount path, type ```
df -h
``` in [the terminal](http://www.psychocats.net/ubuntu/terminal).

---

### Post by 3nigma on 2007-11-24
Thanks again for the insight, I will go and try that right now.

In the meantime, I made a post on the Apple support forums as well.  I made a more thorough list of what I have done, to help people give me a good diagnostic.  Here is the post that I made there:

> Hey dude,

Thanks again for the followup help.

I have done a million diagnostics, here is a short list:

Tried booting resetting PRAM - nothing.
Tried booting in Verbose mode, nothing
Single-user mode, nothing
Safe mode, nothing
Nothing will boot.

I have Ubuntu installed on a different partition which boots totally fine, so it's definitely not a hardware failure. Apple said this as well.

I boot into the install DVD, and run the Disk Utility FIrst Aid. It can't repair the disk, and gives me errors.

The hard drive is nearly full, so there's not 15GB free to do a Archive and Reinstall the OS.

Apple said that the OS is corrupt, and I have to recover the data and wipe and reinstall.

I tried booting in target disk mode, and the host computer can't find the target mac (I tested it with 3 different macs and the cable works and everything else works fine). Apple said this is probably due to the "headers and footers" of the partition being hard to read.

I tried DiskWarrior, and at first it DID find the disk and data, and it said IT COULD RECOVER IT. I did a hardware test and it was fine. I did the permission repair, and then it found all my data and allowed me to browse it before recovering it, but it also gave me errors. Then it said that it COULD NOT recover it. When I tried to run the recover, it said first to reboot. After rebooting, it said that it couldn't even find the Mac hard disk at all, let alone repair it.

Then after trying to boot again as normal (to the normal HDD, not CD), instead of simply staying at the permanent "boot up" screen, it goes to a gray screen with a black message that says "Please reboot your computer".

I am able to boot from an Ubuntu Live CD, and I can even see my Mac disk as accessible. I mount it and can browse SOME of the data, but other folders it says I don't have permission to access. Unfortunately, it's the locked ones that I need the data from.

I didn't put any extra locks on these folders in OS X than the other folders that I can access, so it's nothing like that.

Any ideas?

Thanks again for the help, and let me know what you think.  I will test that out, and tell me if this new information adds any help or gives you any ideas.

Thanks again!

---

### Post by 3nigma on 2007-11-24
Dude.

You have saved me.

I was able to log in as the root and access the data!  I dumped it all onto my external HD without problem.

I literally recovered 1,000+ family photos, most important of which were that of my wife and I spending our honeymoon in Mexico!

This is phenomenal, thank you again so much.  You literally have personally, individually, helped me out so very much.

Since you are ubuntu forum staff, give them my testimonial and request a pay bonus =D.

Thanks dude, I sincerely appreciate it a lot.

---

### Post by aysiu on 2007-11-24
I'm glad it worked out for you. I'd ask for a pay bonus except that we're all volunteers here...

---

### Post by 3nigma on 2007-11-25
Well PM me your PayPal, so I can gve you some money, hehe =D.  I don't have much, but I'm all for helpin' people who help me =D.

Thanks again =D

---

