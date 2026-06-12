---
title: "Is there a Samba guide for a NOOB (or a Multi-Idioto, to be more correct!)"
date: 2017-10-18
forum: General Help
---

### Post by Malmberg on 2017-10-18
Hi All,
I do know that there is a load of "How to get Samba working", here and elsewhere, and trust me - I have tried a lot of ways!
But I’m just too stupid, or maybe too old :-) !!!!
 
So I do hope that one of you can point me in the right direction!!
What I want to do is maybe not rocket science - so here we go:

A:
I have a Ubuntu 16.04 PC in our basement - with 3 hard drives, maybe more to come, this should act as a kind of Server  :-).
One system drive, and one 500 GB drive I would use as backup for the rest of the households PC (read/write) - this drive should be accessible for all PCs in the household, and a3 TB drive for "evaluation files" - these files should be accessible for all other PCs in the household (maybe just Read)!

B:
I have a Desktop Ubuntu 16.04 PC in my "office", used for mails, docu's and so on, you know - normal "home office work"! - I would like to back up important files to A, the one in basement.

C:
Then we have 3 LibreELEC/Kodi players, only used for "Infotainment",these players should have access to files on A - the 3 TB drive!

D:
Then Junior on 1. floor has a Windows 10 PC. It would be great if he (or I) could take backup for his important files, on A's backup drive!

I do NOT worry about security - at all! No password is needed for any "clients"!!

Is this doable?

BTW: English is not my native language (nor second) - so excuses for the gibberish!!!!!!!!!

Cheers - and thanks!


(To Admin - if this has been covered before, then feel free to  delete this - I would just be happy if you would give me a hint of where  to see the light! :-)

---

### Post by ian-weisser on 2017-10-18
> **Malmberg said:**
> I have tried a lot of ways!

You have not told us what you tried.
And, more importantly, you have not told us if you cleaned up after unsuccessful attempts.

Dreck left over after unsuccessful attempts may interfere with future attempts.

---

### Post by Malmberg on 2017-10-18
Ahhr - my bad!
I am looking for a "fresh start"!
Delete Samba - reinstall - and start all over again!!

---

### Post by ubname on 2017-10-18
It's very easy to share folders in Unbuntu with win just right click on the folder you want to share
and set up the share options it's really a couple of clicks ...

---

### Post by Malmberg on 2017-10-18
> **ubname said:**
> It's very easy to share folders in Unbuntu with win just right click on the folder you want to share
and set up the share options it's really a couple of clicks ...

It seems like that!
I have a attached drive on my "A" PC, where I have created a folder called "Backup", been though the "Local Network Share". 
But when I try to open this folder from another PC, I do get a "Access denied" message!

---

### Post by ubname on 2017-10-18
Have you enabled "guests" for the folder, try with a folder in the system drive first
to grasp how it works (not sure you can do it with an NTFS, probably your usb drive is
formatted as NTFS so you'll have possibly to change that to use external USB disk)

---

### Post by Morbius1 on 2017-10-18
Why not post the output of this command if you created the share from your file manager:
```
net usershare info --long
```

---

### Post by Malmberg on 2017-10-18
> **ubname said:**
> Have you enabled "guests" for the folder, try with a folder in the system drive first
to grasp how it works (not sure you can do it with an NTFS, probably your usb drive is
formatted as NTFS so you'll have possibly to change that to use external USB disk)

I sure have enabled Guest!
And, I cant use FAT32 - due to the limit in file size :-)

---

### Post by ubname on 2017-10-18
of course, use ext4 not fat try with a folder in your home first

---

### Post by mastablasta on 2017-10-19
make sure the windows users are in the same workgroup.

alternatively you can use sFTP (along with WinSCP or Filezilla) for server file access.

---

### Post by sudodus on 2017-10-19
> **mastablasta said:**
> make sure the windows users are in the same workgroup.

alternatively you can use sFTP (along with WinSCP or Filezilla) for server file access.

I think it is a good idea to use ssh / sftp for file transfer. Make a linux computer an SSH server by installing openssh-server. 

See [this recent answer at AskUbuntu](https://askubuntu.com/questions/966229/why-am-i-unable-to-create-a-shared-folder/966245#966245)

---

### Post by HermanAB on 2017-10-19
Hmm, for a home server setup, Samba could be too much effort to set up and maintain.  I gave up with Samba more than a decade ago - just too much hassle.

The simplest file server system is anonymous FTP.  Windows supports that natively.  So if you set up an anonymous FTP server then you don't have to do much, just connect with the Windows file browser.

See this page to get some ideas:
[http://www.aeronetworks.ca/2017/02/simple-file-server.html](http://www.aeronetworks.ca/2017/02/simple-file-server.html)

---

### Post by Malmberg on 2017-10-19
> **Morbius1 said:**
> Why not post the output of this command if you created the share from your file manager:
```
net usershare info --long
```

Ok - here we go:

[HTML]sbm@TheMatrixMini:~$ net usershare info
[Hentet]
path=/home/sbm/Hentet
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Billeder]
path=/home/sbm/Billeder
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Movies]
path=/mnt/usb-ST2000DL_003-9VT166_222269D14C6E-0:0-part1
comment=
usershare_acl=Everyone:F,
guest_ok=y

[BackUps]
path=/media/sbm/BackUp/BackUps
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Offentligt]
path=/home/sbm/Offentligt
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Dokumenter]
path=/home/sbm/Dokumenter
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Musik]
path=/home/sbm/Musik
comment=
usershare_acl=Everyone:F,
guest_ok=y

[/HTML]

Thanks!

---

### Post by Morbius1 on 2017-10-19
> I have a attached drive on my "A" PC, where I have created a folder called "Backup", been though the "Local Network Share". 
But when I try to open this folder from another PC, I do get a "Access denied" message!                 
> [BackUps] 
path=/media/sbm/BackUp/BackUps
comment=
usershare_acl=Everyone:F,
guest_ok=y
Edit /etc/samba/smb.conf and add a line under the workgroup = WORKGROUP line:
```
force user = sbm
```
Then restart samba:
```
sudo service smbd restart
```

This wasn't a samba issue. It was a Linux permissions issue. When the system sets up /media/sbm it places an access control list ( acl ) on that folder that prevents everyone except sbm accessing anything under it.

---

### Post by Malmberg on 2017-10-19
> **Morbius1 said:**
> Edit /etc/samba/smb.conf and add a line under the workgroup = WORKGROUP line:
```
force user = sbm
```
Then restart samba:
```
sudo service smbd restart
```

This wasn't a samba issue. It was a Linux permissions issue. When the system sets up /media/sbm it places an access control list ( acl ) on that folder that prevents everyone except sbm accessing anything under it.

Great - Thanks!

If/when I add the line to the Samba file - can "All" our PCs access the various files/drives??
(That's what I want :-)

Cheers

---

### Post by Morbius1 on 2017-10-19
The "force user" line is being placed in the [global] section of smb.conf so it will affect all of your shares. If sbm can access the folder being shared locally the guest user on the client machine will as well.

---

### Post by Malmberg on 2017-10-19
> **Morbius1 said:**
> The "force user" line is being placed in the [global] section of smb.conf so it will affect all of your shares. If sbm can access the folder being shared locally the guest user on the client machine will as well.

It seems like this did the trick :-)

Thanks!!

---

