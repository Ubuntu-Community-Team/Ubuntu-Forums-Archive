---
title: "vmware resize &quot;hard drive&quot;?"
date: 2006-12-08
forum: General Help
---

### Post by tocleora on 2006-12-08
I got Windows 2000 working in vmware and it works and looks great, I'm so pleased! I realize this is probably a FTW for Linux overall, but I'm going to go ahead and give the props to Ubuntu since it's what I'm using! :)

My question - I was an idiot and only created a 2GB "hard disk" for it to install to.  That filled up quickly.  I added a second "hard disk" but [a] it's not showing up in windows itself and [b] I'm assuming that isn't going to resolve the problem long term as I'm sure dll's and such will still want to write to the first "hard drive".  Is there a way to make the 1st "hard drive" bigger without having to reinstall Windows 2000? Thanks in advance!

---

### Post by Psykotik on 2006-12-08
Assuming you got vmware "server" edition, "vmware-vdiskmanager" will do the trick !

---

### Post by tocleora on 2006-12-08
Well, that gets me closer, when I type in this:

```
vmware-vdiskmanager -x 6Gb "Windows 2000 Professional-000002.vmdk"
```

Which "Windows 2000 Professional-000002.vmdk" is the name I see under "Virtual Machine Settings" for "Hard Disk", I get this:

```
Failed to get geometry: The called function cannot be performed on partial chains. Please open the parent virtual disk (5).
```

Any thoughts?

---

### Post by tocleora on 2006-12-08
Oh, and I should mention I ran this in the folder:

/var/lib/vmware/Virtual Machines/Windows 2000 Professional

which is where those files are located.

---

### Post by tocleora on 2006-12-08
Nevermind, I ended up frying it by trying to use partition commander on it. :)  I'll have to reinstall anyway now... woops. Hah! :)

---

### Post by rjchute on 2008-03-09
For the purposes of others searching for the answer to this connundrum, I was able to successfully expand the disk for a Windows XP guest by using the vmware-vdiskmanager to grow the disk as above, and then using gParted LiveCD to expand the NTFS file system.

---

### Post by dcstar on 2008-03-10
> **rjchute said:**
> For the purposes of others searching for the answer to this connundrum, I was able to successfully expand the disk for a Windows XP guest by using the vmware-vdiskmanager to grow the disk as above, and then using gParted LiveCD to expand the NTFS file system.

Better to put the VM files on a higher performance filesystem than NTFS, it should run better on Reiserfs or even EXT2 - and I'd trust it more than on a non-native Linux FS.

---

