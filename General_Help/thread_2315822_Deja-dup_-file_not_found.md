---
title: "Deja-dup -file not found"
date: 2016-03-02
forum: General Help
---

### Post by Robbyx on 2016-03-02
The idea was to  restore the inbox of Thunderbird

**Starting the restore  ran the following in a terminal and got an immediate critical error.**

[email]robins@robins-desktop:/media/robins/audio_visual/.thunderbird/x8thazak.robin[/email]/Mail/Local Folders$ deja-dup --restore inbox

** (deja-dup:11861): CRITICAL **: deja_dup_config_location_add_volume_full: assertion 'uuid != NULL' failed

**I ignored the error and the restore box came up with the dates of the backuped up file. I chose a date but got the error message**

Could not restore ‘/media/robins/audio_visual/.thunderbird/x8thazak.robin/Mail/Local Folders/inbox’: File not found in backup

[B]The backup is on a USB HD. In the restore box I choose that location. The restore fails after the program tries to recover the file and reports file not found in backup.
I have tried two dates so far.

I have no way of knowing if the file is missing or why. I do daily backups to the USB HD.

Is this a bug? How do I eliminate the error messages and get the missing file?
[/B]

---

### Post by Robbyx on 2016-03-03
> **Robbyx said:**
> The idea was to  restore the inbox of Thunderbird

**Starting the restore  ran the following in a terminal and got an immediate critical error.**

[email]robins@robins-desktop:/media/robins/audio_visual/.thunderbird/x8thazak.robin[/email]/Mail/Local Folders$ deja-dup --restore inbox

** (deja-dup:11861): CRITICAL **: deja_dup_config_location_add_volume_full: assertion 'uuid != NULL' failed

**I ignored the error and the restore box came up with the dates of the backuped up file. I chose a date but got the error message**

Could not restore ‘/media/robins/audio_visual/.thunderbird/x8thazak.robin/Mail/Local Folders/inbox’: File not found in backup

[B]The backup is on a USB HD. In the restore box I choose that location. The restore fails after the program tries to recover the file and reports file not found in backup.
I have tried two dates so far.

I have no way of knowing if the file is missing or why. I do daily backups to the USB HD.

Is this a bug? How do I eliminate the error messages and get the missing file?
[/B]

A reply would  be great because at the moment I can not restore the file even though I suspect it has been backed up.

R

---

### Post by mastablasta on 2016-03-04
looks like the file might be corrupted. does dejadup make any file integrity check when backing up. does any of the older backups work?

---

