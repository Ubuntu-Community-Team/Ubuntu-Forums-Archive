---
title: "Permission denied to read from a USB stick error?"
date: 2015-09-25
forum: General Help
---

### Post by wonxega on 2015-09-25
I got this Python script that reads media files from USB stick. It used to run fine, today it keeps giving me "OS Error: [Errno 13] Permission denied: media/myName/usbName'" when the script runs the command os.listdir(). os.listdir() simply checks what folders and files are in the main folder. It doesn't write anything, so why is there a permission error? I can use the USB stick just fine, open, add and delete files in it myself. I'm not very experienced with Linux, what might be the issue? Some kind of permission, etc. setting for the script file or the usb drive that somehow magically changed without me doing anything?

---

### Post by wonxega on 2015-09-26
This might give a hint: I installed the same OS on my laptop and ran the exact same script on it, no errors, no permission issues. 
Also, I just deleted every "folder" in /media/myName, plugged the drive and ran the script again. Ran fine. Why do the folders remain in media/myName after the drive is physically unplugged?
Does that give a hint?

---

### Post by efflandt on 2015-09-26
If you are repeatedly unplugging it without properly umounting it (or Safely remove) before unplugging it, that might result in a problem the next time you plug it in because Linux thinks something else is still there. Someone else had a problem when they had 2 devices with same volume name and only one or the other would mount at a time.

Before unplugging it, either right click on it in the Unity bar and "Safely remove" it, or in Nautilus (Files) hit the up arrow to the right of the device to flush and disconnect it.

---

### Post by wonxega on 2015-09-26
I'm afraid I can't do that. This is an embedded device with a media player program running on top of Ubuntu. There is no desktop, nor a monitor, keyboard and mouse.

If there is a shell command to unmount then I could modify the media player program to call that when it can't access the drive anymore.

---

### Post by sotiris2 on 2015-09-26
The shell command is ```
umount /directory
``` Directory is the directory where it is mounted. You can also use the device special file (i.e. /dev/sdx5) as argument.

---

