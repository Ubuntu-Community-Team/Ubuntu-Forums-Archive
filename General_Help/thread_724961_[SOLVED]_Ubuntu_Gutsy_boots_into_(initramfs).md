---
title: "[SOLVED] Ubuntu Gutsy boots into (initramfs)"
date: 2008-03-15
forum: General Help
---

### Post by Marcolin on 2008-03-15
Hello,
My laptop (HP dv 6000) started booting into BusyBox v1.1.3 (initramfs). I tried searching the internet and forums last night but I can't find any useful information.

Other people with this problem have reported the following error:
'/bin/sh: Can't access tty; job control turned off'
but I am not getting this. My laptop just goes straight to the (initramfs) prompt.

Here are some other differences I've noticed:
1> Some have reported that this is caused by my hard drive mount being lost. Mine is not lost, I can still browse my entire hard drive, including all personal files.
2> Some have reported that a tweak to fstab is the cause. I've never heard of fstab before I started looking into this issue last night. I have never tweaked that file.
3> Some recommend using a live CD to fix. I cannot boot into a live CD either. It does the exact same thing.

I installed Ubuntu last week and have had minimal problems. I was last using my laptop on battery power yesterday at school. I was downloading updates but noticed that my battery power was getting dangerously low. I canceled the downloads and tried to shut the system down. However, the shutdown button was not working. It wasn't frozen, it just wouldn't do anything. (I then clicked on the FireFox shortcut and that worked...not sure what the problem was). I was then down to 1% battery life. So, I hit Ctrl-Alt-F2 and typed "shutdown now" but it said the shutdown command wasn't found. ??? Then, my battery died. My class was then over so I didn't have a chance to look into it until I got home. When I booted, it went straight to initramfs.

I thought it was related to the fact that it didn't shut down correctly. But I am at a complete loss. Any help would be greatly appreciated.

---

### Post by JRoush on 2008-03-15
I'm trying to boot from a Live CD and having exactly the same problem (I think).  The kernel loads fine, and I get the ubuntu loading screen, followed by a BusyBox shell.  There are no errors or faults reported, just the (initramfs) prompt, which I have little idea how to use.  The same thing happens when I try to check the disk for faults.
  My system currently has XP installed - which is how I'm writing this - on the one and only hard drive, and perhaps that has something to do with it.  In any case I'd be interested in a solution, or better yet, an explanation.

-- Edit -- I did some further reading, and it seems this is the default behavior if something goes very wrong during the boot process.  I removed the "quiet" parameter from the command to start ubuntu on the Live CD menu, and saw that in my case the loading craps out while "mounting the root file system."  So I think if you get dumped to the busybox prompt without any obvious error messages it means you have to start looking harder for the error messages.

---

### Post by Marcolin on 2008-03-15
I deleted 'quiet' and 'splash' from the boot command and was able to see the following error:
Target Filesystem doesn't have /sbin/init
That sounds bad. However, I am finding a lot of posts that show possible solutions for this error. I will post my results here shortly.


I was able to boot via Live CD and mount my file system. I looked in the sbin directory and sure enough, there is no init. 
This post states a possible fix ->[http://ubuntuforums.org/showthread.php?t=466603&highlight=Target+filesystem+doesn't+have+%2Fsbin%2Finit](http://ubuntuforums.org/showthread.php?t=466603&highlight=Target+filesystem+doesn't+have+%2Fsbin%2Finit)
This post states to back up my personal files and reinstall ->[http://ubuntuforums.org/showthread.php?t=398487&highlight=Target+filesystem+doesn%27t+have+%2Fsbin%2Finit](http://ubuntuforums.org/showthread.php?t=398487&highlight=Target+filesystem+doesn%27t+have+%2Fsbin%2Finit)

I compared the sbin directory on the Live CD to the sbin directory on my mounted drive....  Looks like I am missing 20 files. Would it work to just replace them?

EDIT:
Well, looks like I am up and running now. I booted using the live CD and copied the contents of the /sbin directory to my mounted hard drive /sbin directory, skipping files that were already there. I rebooted and all is well now. If I run into other issues that I think may have been caused by this, I will repost.

---

### Post by DS_USER_997 on 2008-03-16
I also have this error- could you give a simple guide on what to do as I am new to ubuntu

---

### Post by DS_USER_997 on 2008-03-16
ok - i have removed quit and splash - now what?

oh yeah i cant boot normally as my grub is broke

---

### Post by Marcolin on 2008-03-16
First of all, from what i have read, booting into BusyBox with the initramfs prompt can have multiple causes. The purpose of removing "quiet" and "splash" is to see what error you are getting. You will have to scan the post script fairly quickly but the line you will be interested in will be towards the end.

For me, I saw "Target Filesystem doesn't have /sbin/init" before a bunch of lines about usb hardware.

To use my fix, make sure you DO NOT have the line "/bin/sh: can't acces tty; job control turned off". If you do, you have a different problem.

Also, it appears that my problem was originally caused by an improper shutdown. If you haven't had an improper shutdown, your problem may be something else.

Final note, I dont know that this is a good fix. I dont know of any side effects this will cause. If someone knows any more info on this, please inform me (us). Here it goes:

> Boot using a Live CD
> Open a terminal and type the following lines
>>sudo mount -t ext3 -o rw /dev/hda1 /mnt
>>sudo chroot /mnt

This will mount your harddrive to the Live session and make you the root user in that mount.

At this point, I opened up the /sbin directory in Nautilus (it is acutally /mnt/sbin) and found that I was missing the "init" file which is why my system wasn't booting. 

> I then typed this into the terminal to change permissions to add "write" access to the /sbin directory
>>sudo chmod a+w sbin

Then, I opened up a second Nautilus window and browsed to /sbin while the other was at /mnt/sbin. I then copied all files from /sbin to /mnt/sbin and told it to skip existing files. This replaced my init file and about 20 others. 

Then I clicked on restart/reboot, removed the CD when it ejected, and everything booted up fine. I have not seen any side effects yet but I will be sure to post here if I do find a negative effect.

Again, if anyone knows this to be dangerous, please let me know. I too am new to Linux but I am trying to learn.

EDIT: It has now been two days and I haven't noticed any side effects.

---

### Post by dolphinsonar on 2008-03-26
I noticed your original post says that you could not boot from the live CD and the latest one says to solve the issue, that we should boot from the live CD.  I am still not able to boot from the live CD, when I restart the system recognizes the CD (I hear a noise and the green light on the cd drive blinks) but it goes directly into BusyBox from there, not ever giving access to the live CD.  Did you post a fix to this or did I miss it?  Much appreciated.

---

### Post by dolphinsonar on 2008-03-26
Hi,

I just figured out that I was using a bad Live CD, so it is a false alarm.

---

