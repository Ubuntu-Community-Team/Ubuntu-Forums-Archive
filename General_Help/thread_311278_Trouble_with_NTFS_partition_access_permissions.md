---
title: "Trouble with NTFS partition access permissions"
date: 2006-12-02
forum: General Help
---

### Post by kenquad on 2006-12-02
Hi all:

I have an NTFS partition on the same system with Ubuntu - /dev/hda1.  I can mount it with sudo mount /dev/hda1 /windows (where /windows is the mount point, naturally), and I can view its contents with sudo ls /windows, but my normal user cannot even view the contents of the drive: I get permission denied, even if I mount it to a location inside my user's home directory.  I put an entry in /etc/fstab to have the same effect, restarted - no effect.

Incidentally, when I go to "places" and try to access the media graphically, it give me "device is not removable, unable to pmount" or something to that effect, whatever that means.

As you can see, I'm quite confused.  Any help would be appreciated.

Kenquad:confused:

---

### Post by nixclusive on 2006-12-02
```
mount /dev/hda1 /windows -o nls=utf8,gid=46,ro
```

this should help.

/etc/fstab entry:

```
/dev/hda1       /windows     ntfs    defaults,nls=utf8,umask=007,gid=46,ro   0       1
```

after editing /etc/fstab, issue the command: ```
mount -a
```

---

### Post by strabes on 2006-12-02
also check out [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows)

---

### Post by kenquad on 2006-12-02
Thanks, people.  Could I trouble you for a rundown of those parameters and what they do?  Thanks!!!:)

---

