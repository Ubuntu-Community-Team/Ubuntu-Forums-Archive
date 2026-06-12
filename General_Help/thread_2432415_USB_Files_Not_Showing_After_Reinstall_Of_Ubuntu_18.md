---
title: "USB Files Not Showing After Reinstall Of Ubuntu 18.04"
date: 2019-12-02
forum: General Help
---

### Post by ruith on 2019-12-02
Today I received a strange looking email, clearly  some scam or malware related effort. To be ultra cautious I removed and  reinstalled Ubuntu 18.04. 

So far so good..until on inserting my USB  drive (which runs fine in Windows 10 and had done so on the previous  Ubuntu OS) I'm seeing no files on that, 
only a message stating:

 'this  location could not be displayed...input/output error'.

  
I'd really appreciate a solution to this, can anyone please provide a fix? I did run sudo-apt get update after the reinstall but wonder if there's something 
missing which explains this issue
 

Thanks

---

### Post by Impavidus on 2019-12-02
Reinstalling the entire OS after every received suspicious email sounds a bit excessive.

**sudo apt-get update** (I assume that's what you meant) will just make the package manager aware of new updates. To install them, you need```
sudo apt upgrade
```Or use the GUI or any other tool you like.

The usb drive may need a filesystem check. As it works on Windows, it must have a Windows filesystem, so best to do the check on Windows. Or the usb drive may be broken. Maybe Windows has some trick to work around it for the moment. It seems unlikely this is caused by reinstalling the OS.

---

### Post by ruith on 2019-12-02
Firstly, thanks for taking timr to offer your suggestions, you misrepresent my actions in that I do not reinstall the OS "after every received suspicious email", I took this action today. Secondly while I accept 
the possibility of this likely being a Window's issue, the same USB was working perfectly on my Ubuntu 18.04 OS immediately prior to the reinstall. Which made me wonder if the problem was somehow linked to Ubuntu. Hope that clarifies matters.

---

### Post by TheFu on 2019-12-02
> **ruith said:**
> Firstly, thanks for taking timr to offer your suggestions, you misrepresent my actions in that I do not reinstall the OS "after every received suspicious email", I took this action today. Secondly while I accept 
the possibility of this likely being a Window's issue, the same USB was working perfectly on my Ubuntu 18.04 OS immediately prior to the reinstall. Which made me wonder if the problem was somehow linked to Ubuntu. Hope that clarifies matters.

It doesn't for me, but no matter.  Did you install the NTFS drivers on Ubuntu so it might be able to read the Windows-native file system?

```
$ dpkg -l |grep ntfs
ii  ntfs-3g                                     1:2015.3.14AR.1-1ubuntu0.3                    amd64        read/write NTFS driver for FUSE

```
```

sudo apt update && sudo apt upgrade  && sudo apt install ntfs-3g
``` will update, upgrade and install the ntfs driver.  If you are trying to access the drive using a GUI, there might be other dependencies needed.  I always use a real "mount" to access storage, never the GUI.  By default, the GUI tools for accessing NTFS will not use the best options for performance.  It is really too bad those are not enabled by default.

---

### Post by Impavidus on 2019-12-03
What filesystem is on that usb drive? FAT32 should work, NTFS normally too (on a default install, the driver gets installed automatically), exFAT may be a bit more problematic. But the error message you show doesn't sound like unable to mount. I/O errors normally indicate filesystem damage or broken hardware.

---

### Post by TheFu on 2019-12-03
> **Impavidus said:**
>  I/O errors normally indicate filesystem damage or broken hardware.

True.  Whenever I see I/O error on an NTFS formatted USB connected disk, I know it is time to re-format the partition.  Usually I lose a few files, but most are accessible, so it isn't a big loss.  Plus, anything important is backed up.

Might be useful to connect it to Windows and run a chkdsk or scandisk to see if the corruption can be corrected.
If that doesn't work, time to look at the SMART data for issues.

---

