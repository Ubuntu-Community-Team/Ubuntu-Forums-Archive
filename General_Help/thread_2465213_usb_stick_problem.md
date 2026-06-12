---
title: "usb stick problem"
date: 2021-07-25
forum: General Help
---

### Post by m3t3ors on 2021-07-25
im using ubuntu  20.04.20
i use it for my business and save everything to usb to transfer it to my windows machine when i get home. i used it about an hour ago and everything was good. ive just plugged it into my ubuntu laptop and although ubuntu can open the usb stick i cant paste to it. it doesn't high light paste.

any help appreciated

---

### Post by Skaperen on 2021-07-25
i wonder if the file system is affecting that.  get an unused stick and format it *ext4* and try that (*_but not on windows_*).  how do you normally put files on it from Linux?

i only use Linux (lately, only *buntu).  so i put *ext4* on mine.  but i only put stuff on by mount and *rsync* or *cp* or *">"* redirect.

---

### Post by Impavidus on 2021-07-26
If you use the usb drive to transfer files between Ubuntu and Windows, there isn't much choice for the filesystem. Use ntfs or fat32.

If Ubuntu can't write to the usb drive, there are several possibilities. Maybe it was mounted in such a way that the file manager has no permission to use it. Shouldn't happen if you use default settings and let the thing mount automatically when inserted. Or it was mounted read-only. This may happen if the device wasn't properly unmounted ("safely remove") in Windows before unplugging, or if it was accidentally unplugged (poor connection) in Ubuntu. The device may also get remounted in read-only mode whenever there's some I/O error when accessing it. Usb drives sometimes fail. A filesystem check may help (you may need Windows for that), but if the hardware is broken, it can't be fixed. Finally, it may be a problem with your file manager. Can you copy to the usb drive using command line? If not, what error message do you get?

I never repair filesystems on usb drives or sd cards. I never even remove files from them. When full, format.

---

### Post by m3t3ors on 2021-07-26
sorry i forgot to say how i sorted it. in ubuntu i went into permissions and clicked share (dont think that did anything but was set to root) added me as user of usb stick then gave all permissions. its been ok since.

---

