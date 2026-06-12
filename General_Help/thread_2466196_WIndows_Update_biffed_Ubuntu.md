---
title: "WIndows Update biffed Ubuntu"
date: 2021-08-22
forum: General Help
---

### Post by guy14 on 2021-08-22
Trying to help a friend who has a dual boot with Windows 10, claims both OSs co-existed weel until a recent Windows update stops Ubuntu from loading. this is what shows on his screen when choosing Ubuntu:    [https://ibb.co/SyhfJTs](https://ibb.co/SyhfJTs)

Any suggestions on fixing this problem?

---

### Post by grahammechanical on 2021-08-22
It is my understanding that a Windows update will re-activate Fast Startup. This is actually a form of hibernation and it prevents a dual boot between Windows and Ubuntu from working. Try switching off Fast Startup in the UEFI settings utility. Or, confirm that Fast Startup has been turned off so it can be eliminated as the source of the problem.

Regards

---

### Post by oldfred on 2021-08-22
UEFI has fast boot setting which assumes no system change.
With normal boot UEFI/BIOS writes hardware configuration to drive for operating system to use.
Often fast boot is so quick, that you do not have time to press any key to get into UEFI or UEI boot menu. But then a full shutdown & cold boot will have system do a one time normal boot.

Windows has fast start up which is a partial hibernation & sets hibernation flag.
Grub cannot boot a hibernated Windows nor Linux NTFS driver cannot normally mount any hibernated NTFS partitions.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by ajgreeny on 2021-08-22
Depending on what the Windows update was I think there have been cases where the partition table has been edited or even rewritten during the update and as Windows does not even see Linux filesystems, they may simply be missed out in the partition table, even though the partitions are still there on disk.

I have not really used Windows since the XP days, apart from occasional look-sees in KVM as a virtual install, so I can not really tell you more about this but you may be able to find more references to this with a search using your favourite search-engine.

My apologies for doing things this way but without Windows I will be unable to consider which, if any of these, are appropriate for your situation. However, have a look at this Google search page which I found very easily and which may help you.
[https://www.google.co.uk/search?q=windows+update+lost+linux+partitions&source=hp&ei=4XEiYZTPB4KU8gLP4qfoBQ&iflsig=AINFCbYAAAAAYSJ_8c0qxz7yRzKaTvZjGqj0YzwhedRZ&oq=windows+update+lost+linux+partitions&gs_lcp=Cgdnd3Mtd2l6EAMyCAghEBYQHRAeOgsIABCABBCxAxCDAToOCC4QgAQQsQMQxwEQowI6EQguEIAEELEDEIMBEMcBEKMCOggILhCxAxCDAToOCC4QsQMQgwEQxwEQ0QM6CwguEIAEEMcBENEDOhEILhCABBCxAxDHARCjAhCTAjoFCC4QgAQ6CAgAEIAEELEDOg4ILhCABBCxAxDHARDRAzoRCC4QgAQQsQMQgwEQxwEQrwE6CAguEIAEELEDOgUIABCABDoFCCEQoAE6BAghEBU6BAghEAo6BggAEBYQHlDJH1jekAFgmZwBaABwAHgAgAHrAYgB7RySAQYyOC40LjSYAQCgAQE&sclient=gws-wiz&ved=0ahUKEwjUw6Wx_cTyAhUCilwKHU_xCV0Q4dUDCAg&uact=5](https://www.google.co.uk/search?q=windows+update+lost+linux+partitions&source=hp&ei=4XEiYZTPB4KU8gLP4qfoBQ&iflsig=AINFCbYAAAAAYSJ_8c0qxz7yRzKaTvZjGqj0YzwhedRZ&oq=windows+update+lost+linux+partitions&gs_lcp=Cgdnd3Mtd2l6EAMyCAghEBYQHRAeOgsIABCABBCxAxCDAToOCC4QgAQQsQMQxwEQowI6EQguEIAEELEDEIMBEMcBEKMCOggILhCxAxCDAToOCC4QsQMQgwEQxwEQ0QM6CwguEIAEEMcBENEDOhEILhCABBCxAxDHARCjAhCTAjoFCC4QgAQ6CAgAEIAEELEDOg4ILhCABBCxAxDHARDRAzoRCC4QgAQQsQMQgwEQxwEQrwE6CAguEIAEELEDOgUIABCABDoFCCEQoAE6BAghEBU6BAghEAo6BggAEBYQHlDJH1jekAFgmZwBaABwAHgAgAHrAYgB7RySAQYyOC40LjSYAQCgAQE&sclient=gws-wiz&ved=0ahUKEwjUw6Wx_cTyAhUCilwKHU_xCV0Q4dUDCAg&uact=5)

---

### Post by guy14 on 2021-08-22
Fast booth was on, it's been turned off but problem remains.  I tried sudo fsck -y /dev/sdxy and I get these results : Ubuntu file system came back clean, EFI partition 406 files, 22449/65536 clusters

---

### Post by oldfred on 2021-08-22
That is just showing ESP - efi system partition which is FAT32.
Ubuntu will be in an ext4 partition. Or several.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yancek on 2021-08-22
If you have not resolved this issue, the best nest step would be to download and run boot repair with the Create Bootinfo Summary option.

Also, have you disabled hibernation by going into the Power Settings in Control Panel.  Some windows updates turn Secure Boot back on and turning it off might help.

---

