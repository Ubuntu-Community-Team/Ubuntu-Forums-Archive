---
title: "changed owner permissions in nautilus, now unable to access files"
date: 2014-07-23
forum: General Help
---

### Post by fidelandche on 2014-07-23
Hi all,

I have made a big mistake and yes I know, I should have been a lot more careful when changing anything in nautilus. 

OK so here is my problem, I have a Ipod that I only have read access to and I wanted to change the permissions to read and write ( I have no access to a Mac), so I went into nautilus and right clicked in a white space in the Ipod file. The next thing I did was to change the owner name from "me" to my user name, I did that and then I went to select "create and delete files" and missed the drop down box when I clicked and at this point, nautilus closed!! Now when I use this ```
gksudo nautilus
```a security box appears and I put in my sudo password and then nothing. However when I enter this ```
sudo nautilus
```, nautilus will open.

The next part, is when I right click in the Ipod folder and open properties - permissions, the dialogue box opens and when I try to change the owner name back, I get the error shown and this is what is going on in Konsole;

[PHP]millieandandy@millieandandy-N150P-N210P-N220P:~$sudo nautilus[sudo] password formillieandandy: 


(nautilus:3130):Gtk-WARNING **: Failed to register client:GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The nameorg.gnome.SessionManager was not provided by any .service files


(nautilus:3130):Gdk-CRITICAL **: gdk_device_ungrab: assertion 'GDK_IS_DEVICE(device)' failed


(nautilus:3130):Gtk-CRITICAL **: gtk_device_grab_remove: assertion 'GDK_IS_DEVICE(device)' failed


(nautilus:3130):Gdk-CRITICAL **: gdk_device_ungrab: assertion 'GDK_IS_DEVICE(device)' failed


(nautilus:3130):Gtk-CRITICAL **: gtk_device_grab_remove: assertion 'GDK_IS_DEVICE(device)' failed
**
ERROR:nautilus-properties-window.c:1839:schedule_owner_change_timeout:assertion failed: (NAUTILUS_IS_FILE (file))
millieandandy@millieandandy-N150P-N210P-N220P:~$ [/PHP]


So how do I reverse these changes, I have very stupidly made.

Many humble regards

Andy

---

### Post by TheFu on 2014-07-23
Running **any** GUI program with sudo can leave file permissions below your home, ~/, incorrect.  
I don't have an ipod (won't buy hardware that is so very proprietary like that), but access to the device should be controlled through the device file owner, group and permissions.  If you can find that device and post the current permissions (ls -al), then someone else may be able to help you correct them.

In the meantime, perhaps running through a file/directory permissions tutorial would be good?  
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

