---
title: "File Locked After Crash"
date: 2017-11-12
forum: General Help
---

### Post by HDTimeshifter on 2017-11-12
My system (cursor) froze up on me and after several minutes I pressed the reboot button and it simply shut down instead of rebooting. So I restarted, (and after clearing bad inodes), 2 files (a LibreOffice Writer and Calc) files went through recovery process, but I still can' open the Writer file. It says it is locked and I tried to open a read-only version as well as copy and save as a new filename. I then deleted the original file and renamed the new file to the old filename, but it still says it's locked. I even tried deleting it and copying from my backup drive, and it still gives me the locked message. What is going on and how do I fix it? The error message is below:

```
Document file 'CDs.odt' is locked for editing by:

Unknown User

Open document read-only or open a copy of the document for editing.
```

When I open it read-only mode or a copy and try to overwrite it from Writer, I get the below error:
```
Error saving the document Untitled1:
Object not accessible.
The object cannot be accessed
due to insufficient user rights.
```

I tried running fsck, but it says
```
/dev/sda1 is mounted.

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.
```

I can't unmount /dev/sda1 in the disks utility (probably because it is my boot drive/partition. Is there a way to set it up to run fsck at next boot?

I rebooted and still have same problem, even after copy the file on my backup drive to another name, renaming back, and copying back to my main drive.[https://linuxconfig.org/how-to-force-fsck-to-check-filesystem-after-system-reboot-on-linux](https://linuxconfig.org/how-to-force-fsck-to-check-filesystem-after-system-reboot-on-linux)

I Googled and found this to force fsck on next boot (going to give it a try now):
```
The simplest way to force fsck filesystem check on a root partition eg. /dev/sda1 is to create an empty file called forcefsck in the partition's root directory.
# touch /forcefsck
```

Well, that was worthless. No fsck ran.

Well, I forced it run fsck on every boot as the link below describes. Hopefully I'll be able to set it back to not run on every boot. fsck didn't find any major errors (.3% non-contiguous files is all). **[COLOR="#FF0000"]But I still have a locked file that I can't do anything with![/COLOR]**
[https://linuxconfig.org/how-to-force-fsck-to-check-filesystem-after-system-reboot-on-linux]("https://linuxconfig.org/how-to-force-fsck-to-check-filesystem-after-system-reboot-on-linux")

Ok, Bueller never responded and I decided to Google "Linux Document file is locked for editing" and found this. I turned on show hidden files and found the locked file and deleted it. 2 hours wasted on my Sunday afternoon and now it's dark and I didn't get any yard work (or the leaky kitchen faucet repaired) as a result...
[https://askubuntu.com/questions/183024/why-libreoffice-keeps-saying-the-document-is-locked-for-editing]("https://askubuntu.com/questions/183024/why-libreoffice-keeps-saying-the-document-is-locked-for-editing")

---

