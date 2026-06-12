---
title: "Windows Shared Drives"
date: 2006-07-10
forum: General Help
---

### Post by BrokenKingpin on 2006-07-10
Ok I just got a new 160 GB external USB HD. I have a laptop running WinXP and a desktop running Ubuntu. I need both computers to be able to read and write to it. The drive is formatted as NTFS. Right now I have it plugged into my laptop and have it shared. From Ubuntu I can access this going to the gnome panel and going through the network services and going to windows network and so on; I think it is using SMB, which will allow me to read and write to the shared drive. But I don't know how to access it through the command line; I think I would actually have to mount it. So how do I go about having this drive automatically mounted at start up, and I am assuming I would have to reformat the drive to fat32 so I can write to it? Or is there a package that would allow me to be able to write to NTFS. Also would I be able to connect the drive to the Ubuntu box and access it through Windows? Any input would be great, thanks guys.

---

### Post by scxtt on 2006-07-10
i'd format it fat32, then plug it into ubuntu and share it via samba -- then you can access it via XP as well ...

smbfs will allow you to mount a samba share ... something akin to:
[indent]mount -t smbfs //$box_name/$share_name /media/$shared_folder[/indent]

---

### Post by BrokenKingpin on 2006-07-10
Where can I get Samba for windows, and will it be a GUI tool? And will it be able to automaticly mount the drive on startup?

---

### Post by scxtt on 2006-07-10
samba is a windows 'thing' -- you don't have to install anything ... just make sure the 2 boxes are on the same 'workgroup' ... you'll be able to mount it by "map network drive" w/in XP - there's also a "reconnect @ logon" option ...

---

### Post by BrokenKingpin on 2006-07-11
Sorry for all the questions, how can I change the workgroup on my Ubuntu box, and what would be the network path to that machine through windows? Thanks for all your help Scxtt.

EDIT: Ok I got the workgroup changed. I just need to figure out how to properly share folders so I can access them through windows

---

### Post by BrokenKingpin on 2006-07-11
OK I can see my Ubuntu computer in windows under windows in my Workgroup. I shared a folder in Ubuntu, but when I click on the Ubuntu computer in Linux it asks for a user name and password. How do I properly share files on the Ubuntu computer so I can have access to them in windows?

---

### Post by scxtt on 2006-07-11
on the ubuntu box, type **smbpasswd -a $USER** -- this will setup a samba password for your user account on the ubuntu box ... this should allow you to enter your username and the new samba password in XP to login to the share ...

---

### Post by BrokenKingpin on 2006-07-11
Is there a way to disable the password thing totally, or have windows automatically log in with the mapped network drive? Thanks again for your help.

---

### Post by scxtt on 2006-07-11
there is, but i don't remember what it is off the top of my head -- doing some research on on smb.conf should shed some light on that subject for you ...

---

### Post by BrokenKingpin on 2006-07-11
Yea I was looking into it a bit last night, I have a smb.conf in my bin and sbin folders, which one do I modify?

---

### Post by scxtt on 2006-07-11
neither as far as i know - should be */etc/samba/smb.conf* ... and you'll have to restart samba after any changes to the config file ...

---

