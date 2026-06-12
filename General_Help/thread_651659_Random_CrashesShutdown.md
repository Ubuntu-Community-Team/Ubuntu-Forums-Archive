---
title: "Random Crashes/Shutdown"
date: 2007-12-27
forum: General Help
---

### Post by jlh on 2007-12-27
I'm running Gutsy on a Thinkpad T30, 1GB memory.  The laptop is nearly five years old, but it has been very stable and reliable.

Recently, however, I've experienced random crashes.  They occur not when I'm actively using the computer, but rather when I'm away, and the computer should have gone into a screensaver or power management state.

The crash shuts down the machine.  When I reboot, frequently the boot will go into the shell and ask me to log in.  I've found, sometimes, that I can get back to a normal boot by Control-Alt-Backspace, without logging in at the shell.  (Troubleshooting from the shell is beyond my expertise.)  If I don't to something - like C-A-B or shutdown manually - a screen appears telling me that GDM will be dis-abled.

Sometimes, after the crash, the computer boots to what should be the desktop, but hangs there.  Then, I have to manually shut down and reboot.

I've found that, after a crash, if I have real difficulty, I can boot into the recovery state. or use the the installation CD to load the kernel.  These two approaches get me to the desktop, but sometimes my wireless card is not recognized.  I shut down normally and re-boot, which then usually proceeds normally.

I cannot detect any pattern.  Sometimes the computer will be up over-night, with no problem.  When I shut down normally, the next boot proceeds normally as well.  

Reading logs, I am afraid, is also beyond my skill set.

Thanks.

---

### Post by gilf on 2007-12-27
Sounds like a power management problem.

You can test this by turning off ACPI and or APM as a boot option, to temporarily disable power management. One or the other may still work.

Also you should upgrade your system BIOS from the Thinkpad site to the latest version. Many older power schemes had bugs in the BIOS.

---

### Post by jlh on 2007-12-27
Thanks.  But you are already beyond my skill level.

1.  Where do I turn off ACPI or APM?  Is that a bios setting or Ubuntu?  What happens if I do one or the other?

2.  I haven't updated the bios in a while.  Can I do that running Gutsy, or do I have to use the Windows side of my machine?  (The latter is not a happy prospect.)

---

### Post by gilf on 2007-12-27
In answer to 1, you can do that as an option when you first start to boot up into Ubuntu.

When you boot up, the program that launches you into Ubuntu (or Winows, as a choice)  is called Grub. You can interrupt Grub at the stage where it is asking you which OS you want, and then tell it not to use ACPI (the newer power management scheme) or APM (the older and more bug prone power management scheme).

Disabling in turn each type of power management may help with crashes. It can have some side effects besides giving you less options when battery power is low, ets. One of them may be causing problems with sound. There are workarounds for both power management and sound problems. However the main reason for doing this temporarily is just to see whether power management is causing your crashes. In other words, it's a temporary test.

Grub options entered as a command line while booting are not permanent, and a reboot will restore ACPI and APM.

Command prompts in GRUB do not affect your BIOS.

APM and ACPI DO depend on your BIOS -- and that is why updating it can fix power problems.

In question 2, you generally update BIOS  in an older thinkpad through a floppy disk in DOS mode. Instructions will be located on the Thinkpad website for your model. Usually you first have to download a file to put on the floppy -- and that can be done in either OS.

Be sure to follow the instructions on the Thinkpad Website.


To understand more about Boot Options in Grub, look this up in Community documents.

You can also read a thread about ACPI and APM boot options here:

[http://ubuntuforums.org/showthread.php?t=347507&page=2](http://ubuntuforums.org/showthread.php?t=347507&page=2)

---

### Post by jlh on 2007-12-29
I see this is going to exceed my confidence level.

I'll try to turn off acpi when I boot up tomorrow.  I confess, however, that I've never tried to do anything at that point in the boot process.

 Is the idea that, then I leave the machine alone, and see if it crashes?

Thanks.

---

### Post by jlh on 2007-12-29
Ok.  I shut down a few minutes ago, but that was abnormal.  I got a text screen message to the effect that I was shutting down, which I would not expect to see.

I rebooted, and added acpi=off as you suggested. I then continued the boot, which proceeded normally into my desktop.

At this point, I am going to leave the machine on for the night.  I'll let you know if it crashes while I sleep.

---

### Post by jlh on 2007-12-29
No crash yet.  The computer has been up since my last post.  I've not rebooted.  I will leave the machine up and running.  I have other things to do for much of the afternoon.

---

### Post by gilf on 2007-12-29
Well, I hope it works out for you.

As I mentioned before, there is good news and bad news if turning off ACPI stops the crashes.

The good news is that you pretty much know where the problem lies. 

The bad news is that you've turned off advanced power management, and you may want its features -- sleep mode, battery level reporting, screen saving, and other things may or may not be affected. If you find that something doesn't work that you want, the possible solutions are limited.

The best would be that updating the BIOS solves your crash problem, and you can boot with ACPI on.

Workaround solutions may be possible for features you want, if you have to run with ACPI off.

I had an older Thinkpad that had to run with both ACPI and APM off. I was able to install a small Linux battery monitoring application to replace the missing APM function.

That's about all I can suggest. Hope things work out for you. Maybe someone else can suggest a better cure..

---

### Post by jlh on 2007-12-29
I'm going to leave the computer up for maybe another day, and see whether there is any crash.  I take it that, by editing /boot/grub/menu.lst, I can boot with acpi off regularly.

Power management is low priority for me.  I run this laptop at home on power 98% of the time.  Very little on-battery usage.  At this point, I don't see a screen saver effect - it still launches.  

Thanks for the suggestions, and links.

---

### Post by gilf on 2007-12-29
To make permanent changes, here are the directions copied and pasted from the community docs:

> Once you know you need to boot with a special option on your installed system, you'll have to edit the file /boot/grub/menu.lst to make the boot option permanent.

To to this please do the following:

sudo nano /boot/grub/menu.lst

Add the option to the line that starts with "# kopt=". Then run

sudo update-grub

to have the menu entries updated. 

Nano is a small terminal editor. If you are not familiar with its operation and commands, you may want to substitute the following for the first command above:

gksudo gedit   /boot/grub/menu.lst

that will give you a graphical editor called gedit-- which is more intuitive in operation and may feel more familiar.

The instructions above gloss over slightly the fact that not only do you need to make the changes, but you need to save the file and leave the editor before running the command sudo update-grub in a terminal.

the community documents where all this appears is located here:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

good luck!

---

### Post by jlh on 2007-12-30
good to know about the update-grub command.  I could have missed that.

Thanks again.

---

### Post by jlh on 2007-12-30
I'm a little confused.  I did the edit to /boot/grub/menu.lst.  I saved and updated.  But I do not see what I added in the file if I re-open it.

Is that right?

---

### Post by gilf on 2007-12-30
You should see the changes.

Here are some possible causes:

1.) You may have forgotten to save the file after you edited it

2.) You may have saved it under a different filename or in a different directory. This can happen if you first save a backup copy with another name and then forget to reopen the original file to edit it.

3.) You may not be looking in the right place in the file you edited. There are several similar looking sections in menu.lst for different OS booting choices. Be sure that you actually edited the right line in the file -- or that you are looking for your edits in the right boot line this second time around.

4.) You may have tried to look at the wrong file for your edits -- opening a backup file instead of the original -- this can happen particularly if you browse to a file to view it, rather than using the terminal command line. In browsing, sometimes you don't notice an extension or variation on a files name, and open the wrong one.

5.) Some sensitive files are automatically restored to their former state after an edit if there is a mechanism for this. I don't remember if /boot/grub/menu.lst has this kind of mechanism. But I believe the community doc would have given the procedure for making the change permanent, if so. Also can't remember if sudo update-grub did something like this.

It's possible the community doc could have an error. But you might investigate the first 4 possibilities above, first.

---

### Post by jlh on 2007-12-30
I just did the editing and update again.

Here is what the file line looks like after the edit:

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e92aeb7a-b015-4d97-ad9f-fcf91c1b820f ro quiet splash acpi=off


When I do the update, here is what is returned:

:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found but preserving previous setting: splashimage=(hd0,1)/boot/grub/GNOMEroom.xpm.gz
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


If I reopen the file, here is what the line now looks like:

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e92aeb7a-b015-4d97-ad9f-fcf91c1b820f ro quiet splash

---

### Post by gilf on 2007-12-30
Hmm, what happens if you put the ACPI statement before the splash statement?

---

### Post by jlh on 2007-12-30
I don't know what happens, but it's sure not what the community development page shows:

Example: Adding the vga=771 option 

boot: /boot/vmlinuz-2.6.15-26-k7 root=/dev/hda1 ro quiet splash 

boot: /boot/vmlinuz-2.6.15-26-k7 root=/dev/hda1 ro quiet splash vga=771 

Options can be used together such as in this example: 

/boot/vmlinuz-2.6.15-26-k7 root=/dev/hda1 ro quiet splash noapic nolapic

---

### Post by gilf on 2007-12-30
okay I did a little research.

put your ACPI option in a different line.

Put it at the end of the line that starts with one # sign followed by kopt (it probably has a ro at the end and a UUID with a series of numbers and leters. Looks like  this:

# kopt ..................................................... ro


It's located further up in your file.

By the way, be sure to make a backup of menu.lst (call it menu.lst-old or something) , before changing menu.lst itself.

I'll explain what happened after I get this post off to you.

---

### Post by gilf on 2007-12-30
Looks like the community docs need a little fine tuning.

The update grub command will indeed wipe out the changes.

Actually the grub update command was unnecessary (in a way)

Making the changes without updating would have worked UNTIL you upgraded your Gutsy (or whatever you're running). Then they would have reverted back.

To make them fully permanent they should have been added to the # kopt line, not the lower boot line.
Then upgrading will not touch it.

By running the update grub command, you are making the kopt line apply the command to the boot line. the update grub command is the equivalent of what happens to menu.lst when you upgrade your system.

Hope this makes some kind of sense. If not I'll try to explain better.

---

### Post by jlh on 2007-12-30
Let me make sure I'm clear:

I see the line.  I add "acpi=off" , preceded by a space and without the quotes, to the end of that line itself, not as a new line.

Do I then do update-grub as well?

---

### Post by gilf on 2007-12-30
Okay, here's a better explanation:

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by gilf on 2007-12-30
> **jlh said:**
> Let me make sure I'm clear:

I see the line.  I add "acpi=off" , preceded by a space and without the quotes, to the end of that line itself, not as a new line.

Do I then do update-grub as well?

Yes, and Yes.

---

### Post by jlh on 2007-12-31
Thanks for all the effort.

---

### Post by gilf on 2007-12-31
You're welcome. Happy Ubuntuing!

---

### Post by jlh on 2008-01-12
I'm back.  I made the menu.lst change on a non-permanent basis to see if the problem stopped.  It seemed to for several days.  However, in the past couple days, I've experienced the same conditions that I had a couple weeks ago.  A random crash and shutdown while the computer isn't being exercised.  I've also had boot difficulties.  At the point that I should get the log-in splash screen, I'm booted into a terminal instead.  When that happens, Control-Alt-Backspace sometimes works to boot me to the splash screen.  Or, I can shut down and boot using the recovery mode.  That always seems to work.  The last time this happened, I tried sudo /etc/init.d/ at the command line and that booted me to the splash screen.

I can't figure out why things seemed fine for several days, and then I find myself experiencing the same problem.  But, this week, I have installed some updates.  None that involved the kernel, or grub.  But is it possible that just changing the system, period,has some effect?

Once I've managed to boot to the desktop, things seem fine.

---

