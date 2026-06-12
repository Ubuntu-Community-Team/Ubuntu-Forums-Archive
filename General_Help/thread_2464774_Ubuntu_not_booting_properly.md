---
title: "Ubuntu not booting properly"
date: 2021-07-11
forum: General Help
---

### Post by fedepop on 2021-07-11
Hi, I'm a new graphic user of Ubuntu, and use it for graphics designs, now I have this issue since I was watching a movie from my folders and the system get freeze, the past month.
I was watching the forum about my problem  and try everything, but nothing.
I have Ubuntu with encrypted hard drive in a mother 
Gigabyte GA Am1m s2h.

Error:
Free initramfs and switch to another root FS:
Cheroot to new_inti. Pod must be 1. New_root must be a mountpoint.

Any help will be appreciated.

---

### Post by videoclocknet on 2021-07-12
Hi!

For me it seems that the error message is a bit changed, maybe some spell mistake?

Could you check the error message is as follows?
```

Free initramfs and switch to another root fs:
chroot to NEW_ROOT, delete all in /, move NEW_ROOT to /,
execute NEW_INIT. PID must be 1. NEW_ROOT must be a mountpoint

```
Is that the error message?
&#8203;

---

### Post by TheFu on 2021-07-12
The general answer for any Linux problems is: 

Check the system log files for the EXACT error message. Use google to plug in that exact error (just remove the stuff that is only for your system like the timestamp or hostname or memory address, but leave everything else in, especially the error number and program name.  Search for what other people in the world found related to that same error.  Someone will probably have a fix.  Do what the fix says.

If you know the correct time for when the problem happened, you can filter the logs for the 5 minutes around that time.  **journalctl** can do this.

Always start by checking the log files.  If you don't know what that means, google "ubuntu log files" and read that. It says where they are, how to view them, how to search them.  A log file might have 100,000 lines, but only 1-20 of those lines are interesting for the problem.

Don't have your eyes gloss over.  Actually READ the logs.  They will often say 
ERROR: X is broken.
FIX: Try {some command} to correct it.
So you should try the suggested command.  If you don't read the logs and there is a fix listed, then post those lines here, someone like me will say - "did you do what the log suggested?"

Oh ... and details matter.  Being exact matters.  Don't say "blue" when it is "cornflower blue". Be exact when possible.

---

### Post by fedepop on 2021-07-12
Free initramfs and switch to another root fs: chroot to NEH_ROOT, delete all in /, move NEW ROOT to /, execute NEW_INIT. PID must be 1. NEW ROOT must be a mountpoint.

-C DEV Reopen stdio to DEV after switch

-d CAPS Drop capabilities -n Dry run BusyBox v1.30.1 (Ubuntu 1:1.30.1-4ubuntu4) multi-call binary.

Usage: run-init [-d CAP.CAP...] [-n] [-C CONSOLE_DEV] NEW ROOT NEW_INIT [AR

Free initramfs and switch to another root fs: chroot to NEW ROOT, delete all in /, move NEH_ROOT to ,, execute NEH_INIT. PID must be 1. NEW ROOT must be a mountpoint.

-C DEV Reopen stdio to DEV after switch

-d CAPS Drop capabilities

-n Dry run

BusyBox v1.30.1 (Ubuntu 1:1.30.1-4ubuntu4) multi-call binary.

Usage: run-init [-d CAP, CAP...] [-n] [-C CONSOLE_DEV] NEW ROOT NEW_INIT [ARG

Free initramfs and switch to another root fs: chroot to NEW ROOT, delete all in /, move NEH ROOT to /, execute NEH_INIT. PID must be 1. NEH_ROOT must be a mountpoint.

-C DEV Reopen stdio to DEV after switch -d CAPS Drop capabilities -n Dry run No init found. Try passing init= bootarg.

BusyBox v1.30.1 (Ubuntu 1:1.30.1-4ubuntu4) built-in shell (ash) Enter 'help' for a list of built-in commands.

---

### Post by fedepop on 2021-07-12
I copy with Google the pic I take and I post below, what do you suggest look cool, but I not have any clue where to find the log file , yes I'm blond!! &#128514;

---

### Post by grahammechanical on 2021-07-12
I want to confirm that I am understanding the situation correctly. Ubuntu freezes. A reboot loads to a BusyBox command line and not to a Ubuntu login screen. Am I correct?

If you a dual booting Ubuntu with some other OS you should see the Grub boot menu. Do you see the Grub boot menu? If you do not see the Grub boot menu because this is not a dual boot with Ubuntu then, during the initial boot process press and hold the shift key if it is a BIOS motherboard. Otherwise, for a UEFI motherboard press (perhaps several times) the Esc key.

When the Grub menu appears select Advanced options for Ubuntu and then select a Linux kernel lower in the list. See if that loads Ubuntu. As I understand the error message Linux is not loading the initial ram file system (initramfs).

You could try selecting a Linux kernel with recovery mode. At the Recovery menu select fsck - Check all file systems. Then select resume - Resume normal boot. I have seen suggestions that running a file system check might solve the problem.

In the past when I experienced Ubuntu loading to BusyBox I simply reinstalled Ubuntu. I was too uneducated to try to fix it.

[https://busybox.net/about.html](https://busybox.net/about.html)

[https://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox](https://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox)

Regards

---

### Post by fedepop on 2021-07-12
just run Ubuntu, the PC get freeze and when I reboot , just saw in the screen initramsf file corrupted or missing, so I was trying some commands I saw in this forum with a live USB stick and I get here with the message I post here

---

### Post by TheFu on 2021-07-12
Computers running Ubuntu shouldn't freeze without some good reason.  The reasons are almost certainly in the log files.  If the system won't boot, then boot from a different kernel or use a Try Ubuntu Flash/install drive and boot from that. The Try Ubuntu environment can fix almost anything. 

Or sometimes it can be be easier to get your data off the system to backup storage and perform a fresh installation.

If I know the issue is not hardware, but configuration, I'm pretty quick to nuke it from orbit, do a new, fresh install, then restore from backups.  My rule of thumb is that 45 minutes of troubleshooting is all I'm willing to do before nuking a system.  That's because a fresh install + my settings + my data being restored so that everything on the system "feels" like it did before takes just 45 minutes, so wasting any more time is foolish, for me.

If the problem is hardware, then there will be some errors in the logs. Also, when running from a different kernel or under a "Try Ubuntu" flash disk, if there are faults, then it wasn't the config or settings. It was hardware.

---

### Post by fedepop on 2021-07-12
ok, wich part do you not understand, I'm a stupid blond!! Also my English is limited, but my heart and ass are big

---

### Post by fedepop on 2021-07-12
I need some command lines to copy and paste!

---

### Post by QIII on 2021-07-12
fedepop:

We cannot begin to help you sort this out without the information being requested.  We aren't there to look at your machine.  We weren't there when you were "trying some commands I saw in this forum" and we have no idea what those commands might have been.  We are unable to divine the state of your machine without crystal balls.  We can only help to the extent that you are able to give us information when asked.

We are uninterested in the color of your hair or the size of your derriere. There is no need to mention those things.  Please stop.

If you cannot provide the information requested, then you might need to follow TheFu's advice and re-install.  If you have little invested in the OS and no files you are worried about keeping, a clean installation would get things working again and leave you in a position where we might be able to help next time -- if you can describe what led to a future problem and what commands you issued.

---

### Post by TheFu on 2021-07-12
In post #3 above, I attempted to provide a general method for solving Linux issues faster than "reinstall", but it does take some action and searching for relevant answers.

The initramfs() stuff happens so infrequently, I see it perhaps once every 10 yrs.

We really do want to help everyone seeking help.  
Different posters have provided things to try above.  Did you try those things or not?  What happened with each?  If you ran commands, please post the exact command AND the exact output.  

This is where knowing how to save terminal commands and output to files is really useful. Then it can be saved to a flash drive and copy/pasted into these forums from another OS.  No typing.  The easy way is by having 2 windows open.
a) the terminal where commands and output happen
b) an editor that can write to a flash drive

Step 1) run the command in the terminal
Step 2) copy the command and all output into the editor, save that file to the flash drive.  Select with the mouse, paste into the editor using the middle mouse button.
Step 3) Boot whatever OS you run to login here for posting, copy/paste the file contents.  In the Advanced Editor, there's a # button. It works just like the "B" button makes whatever is selected into a bold font.  This is called "code-tags".  Wrap the command and output in "code-tags". That will make reading the output much easier for us.

Work through all the suggestions in the posts above. Try each. But be able to show us what worked and what didn't.  If you don't tell us these things, then we'll never know.

---

