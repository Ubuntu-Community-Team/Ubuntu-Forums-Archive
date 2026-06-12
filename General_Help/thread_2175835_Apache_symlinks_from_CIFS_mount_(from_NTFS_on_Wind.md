---
title: "Apache symlinks from CIFS mount (from NTFS on Windows 7)"
date: 2013-09-21
forum: General Help
---

### Post by JohnGalt131 on 2013-09-21
I am running a webserver with some files being symlinked into my document root. These are located in /media/wdtb linked to /var/www/Media/Videos. /media/wdtb is a CIFS share from my windows machine.
```
mount.cifs -v //10.0.0.1/d /media/wdtb -o user=travis,nounix
```
These links are valid and work just fine when accessed through the file system. Permissions are 555.

When I navigate to the webserver, none of my files are visible.

I recently switched back to windows from OSX. When I was running OSX, I had the same drive (formatted HFS+) in this same configuration mounted as follows
```
mount.cifs -v //mac/wdtb /media/wdtb -o user=travisstaley,nounix,sec=ntlmssp
```
and all links worked perfectly through the webserver. I could stream my movies from my iPAd by navigating to the webserver.

After I formatted the drive NTFS and mounted the CIFS/SAMBA share via windows rather than OSX, it stopped working.

Notes:
[LIST]
[*]In general, symlinks WORK with my apache setup. This seems to affect only those mounted from Windows/NTFS
[/LIST]

I don't really understand why this wouldn't work. In both cases the links were to CIFS shares. The only differences are the OS hosting the share and the native filesystem (which shouldn't matter since both are essentially the same filesystem (cifs)).


Anyone encountered this before and/or know how to fix it?

---

