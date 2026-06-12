---
title: "USB where are they really?"
date: 2006-12-29
forum: General Help
---

### Post by gobuntu on 2006-12-29
Friends,

New in UBUNTU, so far all is OK, have questions on USB drives, both hard-disk and flash-sticks, as follows:

USB Drives appear well on Desktop when plugged, and vanish when removed, and clicking opens them, and can play mp3's from them fine.

Something is funny, though. 

Clicking on the icon at the desktop of a USB stick, or usb harddisk, Properties, one finds Location: on the desktop, and Type: folder.

However, clicking on the top bar Places, Desktop, the File Browser opens the Desktop folder and neither the USB flashdrive nor the USB hard-disk appears there. Other items that I have placed on the Desktop such as links to webpages DO appear correctly. ONLY the USB drives do not show.

So, where are the drives actually, so I can access their contents from the command console?

The fact that the drives are mounted automatically to the Desktop, so it appears, does not seem to be quite true. So, what's the story?

If one can access them by clicking on the desktop, that means they are automounted, doesn't it? Now, if they are mounted, how to access them via commands?

If one needs to mount them, how is it to be done?

Thanks!

---

### Post by d3v1ant_0n3 on 2006-12-29
I don't know if this is exactly what you mean, but my USB thumbdrive mounts in /media/LEXAR MEDIA . This is just where it's always automounted to.

---

### Post by teaker1s on 2006-12-29
gnome(ubuntu) right click on desktop panel,click add to panel,disk mounter and add.


make sure you eject removable drives before removing or you can corrupt them:mrgreen:

---

### Post by gobuntu on 2006-12-29
Thanks!

They are indeed mounted automatically at /media subdirectory directly, no further subfolder.

That's quite clear now. 

However, am dumb on why clicking at the icon that appears on the Desktop tells me it is located on the Desktop, and that it is a folder? Obviously it is analogous to a windows short-cut icon. Whatever it is that one clicks-on on the desktop, it still is an item, but no such item shows when the Desktop is opened by the File Browser that is accessed from the Places option on the top bar.

I am very impressed and grateful by the almost instantaneous replies of you all. I am a little slow here in getting back, though, was verifying your replies.

Also, am using the EJECT option on the desktop icon before pulling the usb drives out.

Am moving on again, but would like to clear my grasp on the questions I do ask for help concerning the dektop icons for the usb drives.

Thanks again.

---

### Post by gobuntu on 2006-12-29
What I also want to say, is that the Properties information when one clicks the USB drives icons, nowhere tells one that the drive is mounted at /media subdirectory.

Now, subdirectories are now officially called folders?

(I did have some old-time brief encounter with Linux in which EVERYTHING was a file, including printers and drives).

Thanks.

---

