---
title: "Stuck on the boot screen"
date: 2015-12-09
forum: General Help
---

### Post by CybaCowboy on 2015-12-09
When I start-up my  laptop, my BIOS loads fine and I even get the opportunity to  (successfully) enter my encryption key (the disk is encrypted, as per  the option in the “normal” Ubuntu installation procedure)...

But that's it - Ubuntu gets "stuck" with the message:
```
The disk drive for /dev/mapper/ubuntu--vg-swap_1 is not ready yet  or not present.
Continue to wait, or press S to skip mounting or M for  manual recovery.
```

Pressing "S" displays:
```
The disk drive for /dev/mapper/cryptswap1 is not ready yet or not present.
Continue to wait, or press S to skip mounting or M for manual  recovery.
```

Pressing "S" a second time just causes the little  "loading" dots to fill-up (i.e. so that they're colored), and then my  laptop just sits there...

This laptop has been dead for a while, I've been using the kid's desktop  for most of this year, so I can't really remember whether I made any  drastic changes or not - though at most, I would have installed some  updates (not that this information *really* helps, without knowing what was *actually* installed!). I do recall however, that my laptop failed immediately after rebooting...

Thus far, I have followed the instructions someone suggested on Reddit [here]("https://www.reddit.com/r/Ubuntu/comments/3v9024/ubuntu_freezes_after_decryption_screen_xpost_from/cxlh8dc") and I have an Ask Ubuntu post [here]("https://askubuntu.com/questions/681381/stuck-on-the-boot-screen"), though neither contains any information not yet posted here.

Any ideas on what the problem *might* be, and how I can fix it? I'm  on leave from work for christmas, so I have an entire month to stuff  around and get this issue fixed...

This has been posted on [Ask Ubuntu]("https://askubuntu.com/questions/681381/stuck-on-the-boot-screen"), [Reddit]("https://www.reddit.com/r/ubuntuhelpdesk/comments/3v8zi5/ubuntu_freezes_after_decryption_screen_xpost_from/") (they closed the original Reddit above), Ubuntu Forums and [LinuxQuestions]("http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/stuck-on-the-boot-screen-4175561024/").

---

### Post by dragonfly41 on 2015-12-09
I have no experience with encrypted drives .. it is tough enough recovering data from an unencrypted drive when it fails.

However being curious (and in case I have to encrypt in future and recover) I found this post which might be relevant ..

[https://alvinabad.wordpress.com/2012/09/22/how-to-recover-a-luks-encrypted-disk/](https://alvinabad.wordpress.com/2012/09/22/how-to-recover-a-luks-encrypted-disk/)

---

### Post by CybaCowboy on 2015-12-10
That helped, a *lot*... And I was able to get through the guide with relative ease, using a "live" DVD.

Though I am now stuck at a seemingly *trivial* step - the part that says (step 7a):
>  That’s it. You can now view your data in /tmp/disk.

Okay, *all* of the Terminal commands worked fine (though it was a lengthy, *tedious* process)... But *how* do I "view" my data in /tmp/disk?

* Worse-case scenario*, I have an external storage drive here and I'd like to browse the storage drive in Nautilus/folder view, to work out *what* data I want to copy and thus save (not all of the data on my laptop needs to be saved)... *Best-case scenario*, I would like to "fix" the boot issue (*removing the encryption permanently, if necessary*), so that I copy the data over to the external storage drive "the normal way" (i.e. *without* the use of a "live" DVD and this lengthy process).

Lastly, I want to identify what the problem *is/was* - did something just get corrupted, or is my aging (laptop) storage drive *finally* on its way out?

---

### Post by dragonfly41 on 2015-12-10
I can't offer much more advice since as I wrote I don't use LUKS.
But if you have progressed to step 7a or 7b .. my guess is that from your Live CD you can use terminal command to inspect contents of mounted /tmp/disk

i.e. open Ctrl+Alt+F1 and

cd /tmp/disk
ls

What response do you see?

Perhaps someone else can step in with more advice?

Regarding identifying the root cause of the problem and testing the ageing laptop drive I would research smartctl for monitoring health of drives.

But the best insurance policy is frequent backup.  
 Look at LuckyBackup as one tool.   grsync as a GUI for rsync.   There are many approaches for backups.

Also research testdisk as a disk forensic tool for (future) data recovery in case of a crash.

[COLOR=#b22222][later edit][/COLOR]

You have progressed beyond ..

"Device /dev/sda1 [COLOR=#333333]is not a valid LUKS device".[/COLOR]
  
So now you can revisit this thread ..

[https://www.reddit.com/r/Ubuntu/comments/3v9024/ubuntu_freezes_after_decryption_screen_xpost_from/cxlh8dc](https://www.reddit.com/r/Ubuntu/comments/3v9024/ubuntu_freezes_after_decryption_screen_xpost_from/cxlh8dc)

one writer suggests ...

[COLOR=#333333]"Then, find /etc/fstab on the [encrypted/decrypted] drive, remove any lines with [/COLOR]/dev/mapper/ubuntu--vg-swap_1[COLOR=#333333]and unmount and reboot"[/COLOR].

But first .. **back up** the existing /etc/fstab or you may not be able to boot up again without restoring it.

---

### Post by CybaCowboy on 2015-12-12
> **dragonfly41 said:**
> [COLOR=#b22222][later edit][/COLOR]

You have progressed beyond ..

"Device /dev/sda1 [COLOR=#333333]is not a valid LUKS device".[/COLOR]
  
So now you can revisit this thread ..

[https://www.reddit.com/r/Ubuntu/comments/3v9024/ubuntu_freezes_after_decryption_screen_xpost_from/cxlh8dc](https://www.reddit.com/r/Ubuntu/comments/3v9024/ubuntu_freezes_after_decryption_screen_xpost_from/cxlh8dc)

one writer suggests ...

[COLOR=#333333]"Then, find /etc/fstab on the [encrypted/decrypted] drive, remove any lines with [/COLOR]/dev/mapper/ubuntu--vg-swap_1[COLOR=#333333]and unmount and reboot"[/COLOR].

But first .. **back up** the existing /etc/fstab or you may not be able to boot up again without restoring it.

Okay, I have no idea what you *or* that thread are telling me to do here... I *think* you are both telling me to remove a line of code ("/dev/mapper/ubuntu--vg-swap_1"), but I'm not sure *how* to do this.

By the way, I can sort-of mount my laptop's storage drive when using a "live" DVD - when I login/launch the "test Ubuntu" part of the "live" DVD, it's (my laptop's storage drive) *already* shown on the Launcher, seemingly *already* mounted, just like any other storage drive (e.g. a "thumb" drive or external storage drive)... Once I click it and enter my decryption password (that I would *normally* use prior to the login screen of Ubuntu), I can even browse the storage drive, just like I would any other folder!

Unfortunately, when I try to open /home/gregoryopera, I am told (in a pop-up dialog box):
   ```
This location could not be displayed.

 You do not have the permissions necessary to view the contents of &#8220;gregoryopera&#8221;.
```

This is good, right?

If I am not mistaken, this means that all I need to do is somehow open this (Nautilus) folder as *root* (once I can copy the contents of/home/gregory/whatever that matter, I intent to wipe the laptop and/or "clean" install without encryption)... So *how* do I do that?

---

### Post by dragonfly41 on 2015-12-12
It appears that you now have a decrypted file system to work with in recovering files.
So yes .. that is *good*.

You are quite correct that you may need root permissions to access files.

From within your Live DVD try launching Nautilus (in root mode) from command line using

gksu nautilus

and then try to access your file system in the mounted drive you are trying to recover.

Don't forget to recover any hidden files which might be important.

To remove (or comment out) the line of code in /etc/fstab ...
Just to clarify .. editing this file is only necessary if you try to reboot the (decrypted) system. If you can use LiveUSB or LiveCD then it is not necessary to edit /etc/fstab.

The /etc/fstab file contains boot instructions for mounting various partitions (including swap which might still be encrypted).
easiest approach is to comment out that line by prefixing with character #
then save the file before rebooting.

Incidentally Nautilus is fine and is the Ubuntu recommended tool .. but I tend to use Krusader for file system management. It is like Total Commander in the Windows world.
There are other Ubuntu file system management tools to try such as Thunar.

On the matter of clean start after files recovery you can use GParted (in your Live DVD) to reformat (Ext4) your previously encrypted partitions.
If reinstalling you might consider installing separate partitions for "/", "/home" and "swap".   But you can just install in a single partition.

You already have a Live DVD containing your Ubuntu installer. 
After recovery just boot up and use "Install Ubuntu" instead of "Try Ubuntu".
There are many threads on that subject in this forum.

---

### Post by CybaCowboy on 2015-12-13
So    	 	 	 	here's what I did...* Login with the “Try Ubuntu” option.

 * There is an storage drive icon shown on the Launcher, with padlock in lower-right corner of this icon; the storage drive is named “500GB Encrypted”.
 I enabled Universe repository via Settings, and installed gksu via Terminal.

 * Open drive via the Launcher, then typed the decryption password.
 * The name on the Launcher changes to 483GB Volume.
 * I open Terminal and enter "gksu nautilus". 
* Files (Nautilus) opens.
  * An error message appears:
```
Oops! Something went wrong.
 Unable to create a required folder. Please create the following folder, or set permissions such that it can be created:
 /root/.config/nautilus

```* I click "OK".
* I click the storage drive – now named “b5fa5bf5-ed69-48b9-8abd-757cdcc95ac6” in Files (Nautilus).
 * I navigate to /Home/gregoryopera.
 * There are just two icons are shown therein: "Access-Your-Private-Data.desktop" and "ReadMe.txt". 
 * ReadMe.txt says (inside):
```
THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA. 
  
 From the graphical desktop, click on: 
  "Access Your Private Data" 
  
 or 
  
 From the command line, run: 
  ecryptfs-mount-private

```* Clicking “Access-Your-Private-Data.desktop” causes a Terminal window to flash on-screen and then disappear just as quickly. 
* Entering the Terminal command above shows: ```
ERROR: Encrypted private directory is not setup properly
```

---

### Post by oldfred on 2015-12-13
Did it say it unencrypted your partition with the passphase.
Then you may have corruption and need to run fsck to repair partition.
You need to do all the same steps.

I do not know know encryption, but this is for standard partitions
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

While these discuss resizing, they should have the same mount instructions for an encrypted partition as you did above.
Just before resize then run the fsck. And of course skip any instructions on resizing.


 Resizing your encrypted file system can not be done directly as of yet with Gparted as Gparted sees the encrypted partitions as unformatted space.
How to: Mount & Resize an Encrypted Partition (LUKS) also mount
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
sudo apt-get update && sudo apt-get install lvm2 cryptsetup
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)
df -h
sudo blkid
sudo fdisk -l
sudo pvdisplay
sudo lvdisplay
mount
sudo vgscan --mknodes
sudo vgchange -ay
sudo e2fsck -f /dev/mapper/XXXXX-root
where XXX is your mapper for your root.

---

