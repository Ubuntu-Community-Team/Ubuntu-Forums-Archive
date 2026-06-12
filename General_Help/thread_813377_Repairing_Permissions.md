---
title: "Repairing Permissions"
date: 2008-05-30
forum: General Help
---

### Post by 4rk3typ3 on 2008-05-30
We all know where this is headed...

Yes, while attempting to only chown my /usr/src I managed to leave out src, completely wiping my usr folder of any sort of root potential. I managed to get key things back to root (sudo, etc...), but not all the folder are set properly to the right group anymore. Is there any way, any way at all, that would allow me to repair the individual permissions?

I went into recovery console and repaired the permissions for some of the folders simply by typing:
chown -hR root:root /usr/<directory>/ 
The HAL doesn't appear to be the issue since the CD drive is working fine (played playstation games on it just before typing this), permissions must be screwy because now I cannot access any other HDDs as mount could not gain access to the files it needed (or some nonsense) due to access denied errors.

Error: org.freedesktop.DBus.Error.AccessDenied.
A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.Hal.Device.Volume" member "Mount" error name "(unset)" destination "org.freedesktop.Hal")


Reinstalling is not going to be an option in this case and as you can imagine the whole situation has got me quite annoyed. Any help would be greatly appreciated.

---

### Post by HalPomeranz on 2008-05-31
The only way I can think of to handle this is pretty ugly:

1) Get a listing of the packages installed on your system using a command like "dpkg --list | awk '{ print $2 }'"

2) Use "apt-get -d --reinstall install ..." to download the .deb files for each package.  The -d option means download the package file but don't actually do the install-- the downloaded .deb files will end up in /var/cache/apt/archives

3) Use "dpkg -c ..." to dump the contents of each .deb file.  The output will show the expected permissions/owners for the files in the package

4) Write a script that eats up the output of "dpkg -c" and resets the permissions on the corresponding system files.

Remember that you only have to care about files under /usr, and since you've already chowned most of the files back to root ownership the only files you need to pay attention to are the ones that *aren't* root-owned by default.

---

### Post by bobbwhy on 2008-06-01
Hey.. I think I have this problem.. Just wondering.. would using update to move to the next version..? lts-8 from Gutsy do the trick? 

Do I get the feeling it may be easier to reinstall everything? 
(please no)

---

### Post by HalPomeranz on 2008-06-01
> **bobbwhy said:**
> Hey.. I think I have this problem.. Just wondering.. would using update to move to the next version..? lts-8 from Gutsy do the trick?

Well the upgrade won't hit absolutely every package you have installed, so some things might still be mis-owned.

Looking at my proposed solution above, I wonder how well it would work to simply "apt-get --reinstall install" all packages on the system (notice I dropped the "-d" flag, so we'll actually be installing everything again rather than just downloading the .debs).  I'd be worried about losing customizations you made to the system.  Well, actually I'd be worried about this operation in general and wouldn't even want to attempt it unless I had a good backup of the machine.  But if your system is completely hosed up anyway, maybe it looks like a good option.

---

### Post by Keith Hedger on 2008-08-03
This wont be of help now but I have done similar things so I created a small app to record/repair permissions so checkout: [http://code.google.com/p/perms/](http://code.google.com/p/perms/) for future use.

---

