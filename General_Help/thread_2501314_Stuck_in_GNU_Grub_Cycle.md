---
title: "Stuck in GNU Grub Cycle"
date: 2024-10-01
forum: General Help
---

### Post by pbabs on 2024-10-01
Hello, I recently dual booted my Windows laptop with Ubuntu and got it working, but when I signed back into windows I had a bad image error for chrome and so I tried fixing that. When I tried to boot Ubuntu again I got stuck in this GNU Grub message and I can't boot Ubuntu again. So I put the boot USB back in and hit Try Ubuntu so that I could install the boot repair. I did that and now I have the diagnostic information from the boot repair but I haven't actually run the repair. I wanted to post the diagnostic information on this forum to see what I should do.

---

### Post by pbabs on 2024-10-01
Here is the link to the diagnostic information: [https://paste.ubuntu.com/p/ywcqzW2mXt/](https://paste.ubuntu.com/p/ywcqzW2mXt/)

---

### Post by oldfred on 2024-10-01
Did you install Ubuntu with UEFI Secure Boot on? 
You now have Secure boot on, and Ubuntu should work if installed with it on.

Report shows p5 as Linux but does not open/mount that partition. Is it corrupt needing e2fsck which might be from an abnormal shutdown or encrypted and you have not mounted the LVM & encrypted volume so report could see it?

Once working:
But HP requires you to change boot order in UEFI settings, not UEFI one time boot menu.
HP - <kbd>escape</kbd>  + <kbd>F9</kbd> for UEFI boot menu, <kbd>F10</kbd> for UEFI/bios settings
Screenshot of HP's UEFI settings change of boot order
[https://ubuntuforums.org/showthread.php?t=2490924&page=2](https://ubuntuforums.org/showthread.php?t=2490924&page=2)
[https://www.phoronix.com/news/HP-BIOSCFG-For-Linux-6.6](https://www.phoronix.com/news/HP-BIOSCFG-For-Linux-6.6)

Also Windows update may also update UEFI firmware resetting to defaults, or fast boot on, secure boot on, Intel RST/RAID. If you had to change any of those to boot Ubuntu, you may need to redo them.
Windows updates may also update Windows settings turning Windows fast startup back on. That sets hibernation flag locking NTFS partitions.

You should always be able to directly boot both Windows & Ubuntu from UEFI one time boot menu.

---

### Post by yancek on 2024-10-01
> I signed back into windows I had a bad image error for chrome  

I don't know how a problem with a web browser like Chrome on windows would affect booting another OS?  Here's where keeping notes when you are making changes comes into play and can be very helpful.

Also, it would be useful if you indicated specifically what this GNU Grub message was as Grub outputs a variety of different messages.

Try the suggestions by oldfred in the post above and make sure you set Ubuntu to first boot in the BIOS.  Tapping the F10 key on boot should get you the BIOS Settings, arrow over to the Boot Options tab and down to the OS Boot Manager and hit enter which should show the entries if you have both windows and Ubuntu.   On the right of that page it explains using the F5 or F6 keys to move entries, the F5 key on a highlighted entry will move it down while the F6 key will move it up (unless it is already at the top).

---

### Post by lilyrogwes on 2024-10-11
Before running the boot repair, it&#8217;s a good idea to share the diagnostic information here; it can help others identify the problem.

---

