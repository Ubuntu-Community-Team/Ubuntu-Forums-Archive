---
title: "USB drives and LibreOffice Calc"
date: 2015-12-05
forum: General Help
---

### Post by oakridge on 2015-12-05
I have 2 Ubuntu machines, one dual boot Ubuntu 12.04 and Windows 7 and one Ubuntu 14.04 which acts as a file server.  Nowadays I never seem to need to use Windows 7.  Unfortunately the dual-boot has developed a motherboard problem which is being investigated so meanwhile I am using the file server for general work which has raised two problems:

1.  In Calc not all formulas work as they did before, I save in Microsoft formula because the other machines hear use MS7.

2. I use the 1TB USB drive for backup but the computer insists on trying to open it using VLC.

Any help will be gratefully received.

Malcolm

---

### Post by ian-weisser on 2015-12-07
Are you sure it's a *behavior* difference, like the same-named function in Excel producing a different result than in Calc. That would be a bug.
Or is it Excel or Calc misreading or misinterpreting a formula enetered using the other application? That's usually a (deliberate) issue with the .xlsx format. Try saving in a different, earlier format.

How is your USB drive formatted? Are you saying that you can't open it in any Linux file manager? Or simply that your preferred application setting is incorrect?

---

### Post by oakridge on 2015-12-08
Thank you for your reply Ian.

I have two spreadsheets that I use on regular basis originally created in MS Office.  Each has a formula which takes the date in a cell and adds 7 in order to move on one week.  This works fine in Ubuntu 12.04 but not in 14.04.

The 2TB USB drive is used for monthly backups (current bakups are done elsewehre) this has been used for some time on 12.04 but 14.04 tries to open it with VLC thinking that it is a media file.  The formatting is as it was when I bouight it, perhaps ADFS.

Malcolm

---

### Post by ian-weisser on 2015-12-08
> **oakridge said:**
> This works fine in Ubuntu 12.04 but not in 14.04.
Please file a bug against the appropriate version of the application you are using. Ubuntu is the Operating System, not the application.

> **oakridge said:**
> The formatting is as it was when I bouight it, perhaps ADFS.
See [http://superuser.com/questions/343116/how-do-i-find-out-how-my-usb-harddrive-has-been-formatted-on-linux](http://superuser.com/questions/343116/how-do-i-find-out-how-my-usb-harddrive-has-been-formatted-on-linux) for two ways to determine the actual format of your USB drive.

---

### Post by oakridge on 2015-12-11
Thank you for your reply and my apologies for my slow reply.

I will take up the LibreOffice problem directly.

The disk utility reports as follows:

New disk

2.0 TB Hard DiskWD My Passport 0827 (1012)
/dev/sdb
WD My Passport 0827 (1012)
2.0 TB (2,000,365,289,472 bytes)
Master Boot Record575836314137354E55483141
Volume:
2.0 TB (2,000,364,240,896 bytes)
/dev/sdb1
HPFS/NTFS
NTFS &#8212; Mounted at /media/oakridge/My Passport

i have deleted VLC and now when I try to open the drive I get the message

Error while copying to 'My Passprot'.
The destination is not a folder.

I get the same sort of information and response with the Seagate 2TB drive which I have been using.  

I do not understand that there is no problem using these drives with Ubuntu 12.04 or Windows 7 but Ubuntu 14.04 does not co-operate.

Malcolm

---

