---
title: "Samba Share stopped working."
date: 2022-05-24
forum: General Help
---

### Post by impwatchkeeper on 2022-05-24
Hi, I'm very new to linux. I set up a server using Ubuntu 20.04.4 LTS. I successfully set up samba shares, but when I recently tried to add some files, I have permission issues that prevented the add, when I checked, I got the following:

**drwxr-xr-x 38 nobody nogroup 4096 Jan 15 19:57**

What would have caused the "nobody nogroup" change and more importantly, how to I change it back? Since I set the server up, all I have done is regularly apply upgrades.

Regards,

Dave.

---

### Post by QIII on 2022-05-24
Please do not paste images into your posts.  It might be converted to Base64 (as yours was) and may either not be visible or it may take your post a very long time to render, which may cause browsers to time out.

Please edit your post to insert the image using the attachment tool (the paperclip), which will create an expandable thumbnail image in your post.

---

### Post by ActionParsnip on 2022-05-24
Can you post your /etc/samba/smb.conf file please. Remember to add the code tags

---

### Post by impwatchkeeper on 2022-05-24
Hi, no idea what code tags are:

[global]


workgroup = WORKGROUP
server string = Samba Server
netbios name = linuxone
security = user
map to guest = bad user
dns proxy = no
[Public]
path = /var/samba/shares/public
browsable = yes
writable = yes
guest ok = yes
read only = no
create mask = 644
[Private]
path = /var/samba/shares/dave
browsable = yes
writable = yes
valid users = dave

---

### Post by ActionParsnip on 2022-05-24
Are you sharing a folder in an NTFS file system?

---

### Post by impwatchkeeper on 2022-05-24
I access the share using Windows 10 & 11 NTFS systems.

---

### Post by ActionParsnip on 2022-05-24
That's not what I asked. Are you sharing an NTFS file system using Samba or is it a Linux based file system?

---

### Post by tea for one on 2022-05-24
> **impwatchkeeper said:**
> Hi, no idea what code tags are
Advanced Reply > #
Image attached

---

### Post by Morbius1 on 2022-05-24
I don't understand your post so I'm going to imagine a scenario where it does make sense:

You have a folder shared at /var/samba/shares/public - a somewhat unusual location - with this share definition:
> [Public]
path = /var/samba/shares/public
browsable = yes
writable = yes
guest ok = yes
read only = no
create mask = 644

The Linux permissions on the public folder are set to 777 to allow guest write access.

A smb client guest user adds a folder to that share, "map to guest = bad user" will turn that guest user to the user "nobody", and the folder will save with that user as owner.

Subsequent adds to that subfolder by any smb guest user are possible. 

What is not possible is any adds to that subfolder locally on the server or to the smb client user "dave" or any other smb client user with a defined samba password.

If "dave" is also the administrator of the samba server it would have been better to force the guest user to be dave:
> [Public]
path = /var/samba/shares/public
browsable = yes
writable = yes
guest ok = yes
read only = no
**[COLOR="#B22222"]force user = dave[/COLOR]**
create mask = 644

---

### Post by impwatchkeeper on 2022-05-24
> **Morbius1 said:**
> I don't understand your post so I'm going to imagine a scenario where it does make sense:

You have a folder shared at /var/samba/shares/public - a somewhat unusual location - with this share definition:


The Linux permissions on the public folder are set to 777 to allow guest write access.

A smb client guest user adds a folder to that share, "map to guest = bad user" will turn that guest user to the user "nobody", and the folder will save with that user as owner.

Subsequent adds to that subfolder by any smb guest user are possible. 

What is not possible is any adds to that subfolder locally on the server or to the smb client user "dave" or any other smb client user with a defined samba password.

If "dave" is also the administrator of the samba server it would have been better to force the guest user to be dave:

I had a spare server, so I added a 240gb SSD and 2 X 2tb sata drives. I loaded Ubuntu server on it. The file system is ext4 and I set up the 2 X 2tb disks as a RAID1. I then installed SAMBA, this all worked fine until yesterday, when I could not add some new films to the movies folder. I tried the "force user = dave", but it didn't change the issue I have. I can create another directory and copy the films into this, but how can I then delete the movies folder and films?

Apologies for my lack of linux knowledge, but I was pleased that I manage to get a server up and running without a GUI.

---

### Post by Morbius1 on 2022-05-24
The "force user = dave" will have no affect on the subfolder that already exists where the owner = nobody. 

It will only apply to new files and folders added to the share.

If you do in fact have a subfloder with owner = nobody you will need to change owner to dave. For example:

```
sudo chown -R dave /var/samba/shares/public/subfolder
```

---

### Post by impwatchkeeper on 2022-05-24
Hi, I get:

chown: cannot access '/var/samba/shares/public/movies': No such file or directory

---

### Post by impwatchkeeper on 2022-05-24
> **impwatchkeeper said:**
> Hi, I get:

chown: cannot access '/var/samba/shares/public/movies': No such file or directory

Tried again without the /movies and I now have read/write access to the directory. it now shows as:

drwxr-xr-x 38 dave nogroup 4096 Jan 15 19:57 Movies.

Many thanks for your assistance.

---

### Post by Morbius1 on 2022-05-24
Just as note about Linux. It's case dependent. /movies and /Movies to Linux are two different things.

---

