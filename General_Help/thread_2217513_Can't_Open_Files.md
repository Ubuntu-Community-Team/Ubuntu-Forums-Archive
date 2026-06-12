---
title: "Can't Open Files"
date: 2014-04-17
forum: General Help
---

### Post by e-grieser1 on 2014-04-17
I was using 13.10 when the problem occurred, I just updated to 14.04 today to see if the problem would be corrected but alas it did not.

**BACKGROUND:**
The problem occurred when I closed my laptop before shutting down. Upon reboot my background was black, I could not open the files folder unless I was in Libreoffice, I could not change my background, and overall the system felt slower. If I attempted to open the files folder an error would occur and attempting to send a report would freeze my computer.
 
I googled around and found this thread [http://ubuntuforums.org/showthread.php?t=1531753](http://ubuntuforums.org/showthread.php?t=1531753) and followed some steps but there was no resolution. It seems to be an issue with my profile since I created a profile today and none of the above issues were a problem. If I type $sudo nautilus I get > (nautilus:5497): Gtk-WARNING **: Failed to register client: GDBus.Error: org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service filesNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing. but the file folder opens and my background appeared.

Thanks very much for any help that may come I would love to not have to reinstall ubuntu for this problem to stop.

---

### Post by ajgreeny on 2014-04-17
I don't fully understand from your description what has happened, nor what you are now seeing when you try to open these files.  More info please, and details of exactly what you are seeing.

How can you open the folders in Libreoffice? This does not make much sense, unless you mean that the Libreoffice "Open file" dialogue is the only way to see the folder contents.

By the way, you should never use the command "sudo nautilus".  For any graphical applications to open as administrator (ie with root permissions) you should always use "gksudo nautilus", and it is just possible that using sudo nautilus has made the problem worse.
For details see **RootSudo** in my signature.

I assume you can still login as your original user, but your comment "It seems to be an issue with my profile since I created a profile today and none of the above issues were a problem." is a bit confusing.  Can you run the command ```
ls -l /home/**user**
``` where **user** is your original user name if that is different from your new user/profile name.  If the new user is different from the original please tell us both names, as I am a bit suspicious of ownership of these problem files.

---

### Post by den_ on 2014-04-17
It looks like a file system corruption to me. Try booting from a live CD and run fsck.ext4 or equivalent according to your file system.

---

### Post by monkeybrain20122 on 2014-04-17
How did you 'update to 14.04'? I hope you did not do "upgrade" as obviously whatever the problem might be it would likely to carry over.

---

