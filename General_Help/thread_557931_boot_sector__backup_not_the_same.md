---
title: "boot sector / backup not the same"
date: 2007-09-23
forum: General Help
---

### Post by DaveRowell on 2007-09-23
Sorry for the long post.
After 30 boots the file system check program is run.  Apparently one of my sectors has a discrepancy between the active and backup information.  But I don't know which it is.
I took a picture of the screen and got this on-screen display:
	* Activating swap ...
	* Checking root file syatem ...
	fsck 1.40-WIP (14-Nov-2006)
	/dev/hda3: clean, *---more stuff--- [my / partition]*

	* Assembling MD array mdarrays...
	* Setting up LVM Volume Groups...
	* Starting Enterprise Volume Managemant System...
	* Checking file systems...
	fsck 1.40-WIP (14-Nov-2006)
	dosfsck 2.11, 12 Mar 2005, FAT32, LFN
	There are differences between boot sector and its backup.
	Differences: (offset:original/backup)
	  2B:3f/ff, 29:00/46, 30:00/93, 31:00/0b
	  Not automatically fixing this.
	/dev/mapper/hda7: *---more stuff--- [a partition to share files with Win XP]*
	open /dev/sda1:No such file or directory  *[pen drive installed at updat?!]*
	dosfsck 2.11, 12 Mar 2005, FAT32, LFN
	/dev/????/hda6 has been mounted 30 times without being checked, check forced.
	/dev/????/hda6: |====== and here I took the pix * [my /home partition]*

The message doesn't seem to indicate which partition it is checking but I'd guess the one I'm using for for Win XP&Ubuntu files.  This situation existed before I upgraded to 7.04.  Here's fdisk's listing of partitions and notes on my usage:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
  Device Boot      Start         End      Blocks   Id  System       [used for]
/dev/hda1               1         617     4664488+   b  W95 FAT32   [Compaq's recovery junk]
/dev/hda2   *         618        5372    35947800    7  HPFS/NTFS   [Windoze XP]
/dev/hda3   *        5373        7269    14341320   83  Linux       [/]
/dev/hda4            7270       20673   101334240    f  W95 Ext'd (LBA)
/dev/hda5            7270        7404     1020568+  82  Linux swap / Solaris   [/swap]
/dev/hda6            7405       12844    41126368+  83  Linux       [/home]
/dev/hda7           12845       20673    59187208+   b  W95 FAT32   [storage shared Win & Linux]

Since everything boots and runs OK I'd guess that the back-up should be replaced with the current content.  How would I go about doing that?  How do I find which partition has the problem so I fix the right one?

---

### Post by JKyleOKC on 2007-09-23
I had the same sort of problem this past week after installing Xubuntu on the last of my six systems; the other five had all installed with no error messages.

For starters, the partition that has the error is your hda7; it's listed after the error message rather than before.

To cure it, run "sudo dosfsck -V <the device>" which will run the check individually on the device you specify, in interactive mode. When it detects the discrepancy you'll get the message followed by a menu with three choices: copy original to backup, copy backup to original, or ignore. I chose to copy original to backup. The program then continued to check, and after finishing the first check did a second verification pass. These two passes will take some time, so be patient.

Hope this helps! Incidentally I got the idea from another older post here that dealt with a slightly different error message from the disk check...

---

### Post by DaveRowell on 2007-09-25
THANKS!  Yes it helped or would have - 
Earlier, with much trepidation, I tried dosfsck without any options - first on hda6 then hda7 finding that you're right - it was hda7 - then (gleaned from yet another topic) sudo dosfsck -ar /dev/hda7 gave me a choice window where I elected to copy the original over the back-up.  All seems to be well now.
Again Thanks - Dave R

---

