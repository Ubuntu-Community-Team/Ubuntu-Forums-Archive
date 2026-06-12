---
title: "charset hell"
date: 2005-05-09
forum: General Help
---

### Post by qstone on 2005-05-09
Hello, I use Ubuntu Hoary at work. I'm trying to configure it to "act as a windows machine", Im mean Domain Authentication, SMB shares mounting and so on.

My main problem by now comes from UTF8. All our files are on a NAS, accessible by SMB shares. I'd like to see the correct names of the files, including (french) accents.

Filename as seen under Windows : "Modèle.doc"
Filename as seen under Gnome : "Mod?le (invalid encoding).doc"
From the console : "Mod?le.doc"

The windows file server is (supposedly) encoding in ISO-8859-15
My Ubuntu machine uses UTF8
In smb.conf, I have "dos charset=iso-8859-15", "display charset=UTF8" and "unix charset=UTF8"
There is no encoding options in /etc/fstab

Anyone knows how to configure that correctly, given the fact that I CAN'T re-encode the filenames, because it would mess up things for Windows users ?

---

### Post by qstone on 2005-05-12
Tadaaa... Auto-answer !!! 

I finally have it working, there are my parameters :
/etc/samba/smb.conf :
```
dos charset=CP850
unix charset=UTF-8
display charset=UTF-8
```
From now, you can make a first test : restart samba and try connecting with smbclient (smbclient //machine/share, enter password, then cd, dir etc. Look for files with accents or special chars !)
That **should** work fine.

Next, to have your shares correctly mounted in /etc/fstab :

/etc/fstab :
```
//server/share /mnt/mountpoint cifs iocharset=utf8,(other options) 0 0
```

Seems like the important thing is 'cifs' replacing 'smbfs' (anyone confirms?) and iocharset=utf8.
Now just finish with a 'sudo mount -a' to actually mount your shares and you're done !

---

### Post by kotodama on 2005-09-08
It seems I have the same problem with invalid encoding when I mount an SMB share. I've tried your method and it doesn't seem to work. Whether I edit the smb.conf with that font info or not, when I connect via smbclient I get valid filenames. However that does not translate to valid filenames when I mount it.

---

### Post by beastie on 2006-01-19
[QUOTE=kotodama]It seems I have the same problem with invalid encoding when I mount an SMB share. I've tried your method and it doesn't seem to work. Whether I edit the smb.conf with that font info or not, when I connect via smbclient I get valid filenames. However that does not translate to valid filenames when I mount it.[/QUOTE]

I have the exact same behavior here. Anyone has a solution for that??? I tried mounting the smb share using different codepages and iocharset, and nothing did it. Here's an example of what i tried:

```
mount -t smbfs //SomeComp/SomeShare /mnt/someshare -o iocharset=utf8,codepage=cp850
```

But all non-ASCII characters (such as é,è,ï,...) either displays as '?' when mounting without any options or as something weird like 'Ã©' when mounting with certain codepages.

Really need help here... I've been stuck with this issue for a while now!!

---

### Post by beastie on 2006-01-31
bumpity bump! any help?..

---

### Post by jmaasing on 2006-04-29
I had to experiment som but this worked for me on Ubuntu 5.10

sudo mount -tsmbfs "//<host>/<share>" /mnt/<mountpoint>/ -o username=???,password=????,uid=1000,fmask=0600,dmask=0700,codepage=cp850,iocharset=utf8

---

### Post by adamkane on 2006-05-20
Nice work!

---

### Post by qstone on 2006-05-22
Yeah, just keep in mind that smbfs is DEPRECATED, and **cifs** should be used instead. Many things are not handled with smbfs (eg. file larger than 2Gb), so you'd better avoid it !

---

### Post by castor_fou on 2006-06-06
[QUOTE=beastie]I have the exact same behavior here. Anyone has a solution for that??? I tried mounting the smb share using different codepages and iocharset, and nothing did it. Here's an example of what i tried:

```
mount -t smbfs //SomeComp/SomeShare /mnt/someshare -o iocharset=utf8,codepage=cp850
```

But all non-ASCII characters (such as é,è,ï,...) either displays as '?' when mounting without any options or as something weird like 'Ã©' when mounting with certain codepages.

Really need help here... I've been stuck with this issue for a while now!![/QUOTE]

I am in the exact same situation for ages (samba server under ubuntu, client under gentoo)
using smbclient or embedded smb protocol (smb:// in konqueror) I get correct characters
and unfortunately smb.mount using cifs is not working

---

### Post by castor_fou on 2006-06-08
Instead of
```
iocharset=utf8
```
using
```
iocharset=iso8859-1
```
does it for me
.

---

### Post by sailor.nir on 2007-11-04
OK, after some experimentation I got it to work for smbfs (cifs fails) with the codepage option. Now I have a real challenge to you gurus out there:
My foreign-language filenames are in Hebrew, and I can see the correct letters with cp862, only backwards :( Anyone know if I can also get bidirectional support as well?

---

