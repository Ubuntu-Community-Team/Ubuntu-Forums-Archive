---
title: "mount samba share in x-term/terminal?"
date: 2006-08-03
forum: General Help
---

### Post by eggmanpete on 2006-08-03
Well, ive recently installed fluxbox and im loving it. I would like to know how to mount windows shares using a terminal, and also where they are mounted. So if you have any guides or know how to do it, any help would be appreciated. Thanks

---

### Post by cantormath on 2006-08-03
> **eggmanpete said:**
> Well, ive recently installed fluxbox and im loving it. I would like to know how to mount windows shares using a terminal, and also where they are mounted. So if you have any guides or know how to do it, any help would be appreciated. Thanks

If you type
smbtree
it will give you a list of smb shares on that subnet, 
if you want to connect to them I think you want to use
smbclient

just look for the smbclient man.

---

### Post by eggmanpete on 2006-08-03
smbtree comes up with all network shares. 
i dont understand smbclient though, 

[SIZE="1"]also, xterm doesnt seem to have a scroll bar, how do i view more stuff above?[/SIZE]- found a solution to that: shift+page up /shift+page down

---

### Post by cantormath on 2006-08-03
Works something like this:

laptop:~$ smbtree

Password:
WORKGROUP
        \\VIRUSBACKUP
        \\G
                \\G\C$                  Default share
                \\G\ADMIN$              Remote Admin
                \\G\F
                \\G\F$                  Default share
                \\G\downloads
                \\G\print$              Printer Drivers
                \\G\SharedDocs
                \\G\D$                  Default share
                \\G\IPC$                Remote IPC
                \\G\gprinter            printer on G

laptop:~$ smbclient //G/downloads

Password:
Domain=[G] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
smb: \> help
?              altname        archive        blocksize      cancel
case_sensitive cd             chmod          chown          del
dir            du             exit           get            getfacl
hardlink       help           history        lcd            link
lowercase      ls             mask           md             mget
mkdir          more           mput           newer          open
print          prompt         put            pwd            q
queue          quit           rd             recurse        reget
rename         reput          rm             rmdir          setmode
stat           symlink        tar            tarmode        translate
volume         vuid           logon          listconnect    showconnect
!
.
.
so whats inside?

smb: \> dir
  .                                   D        0  Thu Jul 27 02:09:12 2006
  ..                                  D        0  Thu Jul 27 02:09:12 2006
  cars                                D        0  Thu Jul 27 02:09:05 2006
  music                               D        0  Thu Jul 27 02:09:12 2006
  supergamer                          D        0  Mon Apr 17 13:14:48 2006

                57231 blocks of size 1048576. 13183 blocks available

is that what you are looking for?

---

### Post by bensexson on 2006-08-03
You will want to use mount with smbfs.

---

### Post by cantormath on 2006-08-03
> **bensexson said:**
> You will want to use mount with smbfs.

Or smbfs too, didnt think of that one. 
You can add that to your fstab, correct me if Im wrong, so that it mounts on  boot up.

---

### Post by bensexson on 2006-08-03
This is the guide I used to do this: [https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28Samba%29](https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28Samba%29)

---

