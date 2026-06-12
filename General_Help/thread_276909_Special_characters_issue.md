---
title: "Special characters issue"
date: 2006-10-13
forum: General Help
---

### Post by ww2 on 2006-10-13
I have Ubuntu configured to mount two NTFS network drives from a Windows machine ("computername"), using the following code in /etc/fstab:

```
//computername/WINDOWSC  /media/WINDOWSC smbfs ro,**iocharset=utf8**,credentials=/home/username/.smbpassword 0 0
//computername/WINDOWSD  /media/WINDOWSD smbfs ro,**iocharset=utf8**,credentials=/home/username/.smbpassword 0 0
```

I've tried diverse parameters, like "nls=utf8" and "iocharset=iso8859-1,codepage=850" instead of what's in bold, always restarting the system after changing fstab. *Still, when browsing the network drive via Nautilus, I see "?" marks in file names that contain special characters.* The problem manifests itself in the terminal too, although in a different way: "Casa das Máquinas", for instance, is displayed as "Casa\ das\ M\240quinas". I suppose the problematic filenames are encoded as latin1 (same as iso8859-1).

I think Samba is the culprit: this is a dual-boot setup (Windows XP + Ubuntu) and when mounting the local Windows NTFS drive with
```
/dev/hdb1 	/media/WINDOWSlocal ntfs ro,nls=utf8,uid=1000,umask=0277 0 0
```
I can see special characters normally.

Two more things that may be relevant:

[LIST]
[*]If I open the files with problematic names in Rhythmbox, for instance, it is able to play and display them correctly (no "?" marks).
[*]If I browse the files through "Network Servers", instead of mounting the drive, special characters are shown normally.
[/LIST]

I've searched the forums and found that this is a common problem. Wasn't able to find a solution though. Any help will be appreciated.

---

### Post by ww2 on 2006-10-13
Should I have posted this elsewhere? :(

---

### Post by ww2 on 2006-10-13
Ok, after a bit more searching I've found the solution:

[http://www.ubuntuforums.org/showpost.php?p=169045&postcount=2](http://www.ubuntuforums.org/showpost.php?p=169045&postcount=2)

Looks like sbmfs was the source of the problem indeed. Changing to cifs does the trick. So, in my case, the final command lines are:

```
//computername/WINDOWSC  /media/WINDOWSC **cifs** ro,iocharset=utf8,credentials=/home/username/.smbpassword 0 0
```
```
//computername/WINDOWSD  /media/WINDOWSD **cifs** ro,iocharset=utf8,credentials=/home/username/.smbpassword 0 0
```

For me this works perfectly. Hope it helps the ones bound to struggle over this in the future. I know I did.

---

