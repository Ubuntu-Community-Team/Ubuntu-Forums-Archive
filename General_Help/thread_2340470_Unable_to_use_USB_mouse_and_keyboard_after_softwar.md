---
title: "Unable to use USB mouse and keyboard after software update"
date: 2016-10-19
forum: General Help
---

### Post by jolew on 2016-10-19
After a recent software update and rebooting, I am unable to use my keyboard and mouse with my Intel NUC.  I have since been able to boot into 16.04.1 with a USB flash drive and am able to use the mouse/keyboard and access my file system.

My question is about best way to recover my system.  Attempting to use the install program only gives me the option of doing a side-by-side install if I want to keep my files.  Is there another better way to repair my previous installation?

---

### Post by colmax on 2016-10-19
If you have another usb port & a memstik maybe mount that filesystem & copy or backup your personal files to the second usb memstik
Could also be keyboard selection in settings ie. usa, uk,layout etc
Latest drivers are always worth a look
Cheers
[TABLE]
[TR]
[TD="width: 12%"] 
[/TD]
  			 		[/TR]
 		[TR]
 			[TD="colspan: 14"] 				 No icon 			[/TD]
 		[/TR]
 		[/TABLE]
		 		You may choose an icon for your message from this list
		 	
   			 			 				Tags:

---

### Post by jolew on 2016-10-19
Thanks for your suggestions.  I guess I'll go ahead and backup files as you suggest and do a reinstall.

---

### Post by yetimon_64 on 2016-10-19
> **jolew said:**
> ...  Attempting to use the install program only gives me the option of doing a side-by-side install **if I want to keep my files**.  Is there another better way to repair my previous installation?

Using the installer should give you a "Try Ubuntu" option as well as an "Install" option. You may need to choose the "Try Ubuntu" option to get to a working desktop, from where you can mount any filesystems on the HDD and recover your files to an external source, like a usb stick etc.

If you are getting to the "Side By Side" part of the installer it sounds like you chose the wrong option and may need to try again, initially not to do an actual install but just to load up a desktop with the "Try Ubuntu" aspect of the installer for file recovery. Once your files are recovered then you can reinstall if needed.

Did you originally install with a separate home partition ? 

If you did it is possible to reinstall the system and keep your home folder intact by choosing not to format the home partition. But if you did an automatic install originally your home folder will be a part of the root filesystem and will be lost if you overwrite it. In that case you will need to recover the files from the live boot desktop with the "Try Ubuntu" option and do a complete reinstallation once your files are saved externally. 

I personally always pre-partition my drive with gparted from the live boot desktop before running the installer then choose the "something else" option when installing. If I then subsequently need to do a reinstall I can keep the old home folder and just overwrite the system partition, hence I often don't need to do file recovery to do a reinstall of the system.

---

### Post by jolew on 2016-10-19
Yes, I've got a working desktop by booting into "Try Ubuntu".  I just tried the install option to see if I could repair my install.  Unfortunately, I did not use a separate partition, so it sounds like I am stuck backing up and reinstalling.  I guess I can now go back and fix my partition situation for the next time something like this happens. 

Thanks for your help.

---

