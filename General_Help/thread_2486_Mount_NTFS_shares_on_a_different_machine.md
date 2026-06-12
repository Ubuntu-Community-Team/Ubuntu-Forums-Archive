---
title: "Mount NTFS shares on a different machine"
date: 2004-10-28
forum: General Help
---

### Post by svarreby on 2004-10-28
I am trying to set up my Samba (to and from a Windows XP box). The Samba server is my Ubuntu machine. I have created following folders:

/mnt/books
/mnt/mp3
/mnt/mixed

I have written the following lines in fstab:

\\\\amd\\books	/mnt/books	ntfs	users,umask=0222,ro	0	0
\\\\amd\\mp3	/mnt/mp3	ntfs	users,umask=0222,ro	0	0
\\\\amd\\mixed	/mnt/mixed	ntfs	users,umask=0222,ro	0	0

... and get the following answer:

danne@pingvin:/ $ sudo mount -a
mount: special device \\\\amd\\books does not exist
mount: special device \\\\amd\\mp3 does not exist
mount: special device \\\\amd\\mixed does not exist

Everything is set up in WinXP, shares, registry-hack, permissions ... you name it :-)

What am I doing wrong here? Is it the fstab file?

---

### Post by dasfiend on 2004-10-28
it should look more like this:

//server/sharename      /mnt/my/mount/point        smbfs   username=user,password=xxx      0               0



you can also add with username and password any other options you may want to pass such as uid,gid,fmask,dmask,ro,rw and anything else the smbfs will take (those are the only ones i've ever needed to use)

uid=XX   where xx is a user number, specifies the user number to use as the owner of all the files
gid=XX   as uid, but the group number and group owner
fmask=XXXX  where xx is a numeric file mask, this will be the default permission on all files on the mount (e.g. 600)
dmask=XXXX    as fmask but for the directories (e.g. 700)

---

### Post by triad169 on 2004-10-29
This explains what you want to do:

[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

---

