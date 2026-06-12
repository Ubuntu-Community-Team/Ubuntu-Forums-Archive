---
title: "connect Ubuntu laptop to windows share"
date: 2012-12-16
forum: General Help
---

### Post by Robert R on 2012-12-16
Hi I have a ubuntu laptop and would like to connect it to my WD external hard drive too copy info, do backups etc... 

The HD is shared on a windows 7 machine..

Where would one start to achieve this ??

---

### Post by sahabcse on 2012-12-17
Create the test directory and mount the window share into that folder.

mkdir -p /media/test
mount -cifs //windowsserver/sharefolder /media/test

If you setup password on share folder then follow below method

Create a hidden file under root home folder. Provide the user login items
vim /root/.credentials
username=domain\my_user
password=mypassword

Follow the below command for mount the windows partition

mount -t cifs "//windowsserver/sharefolder" /mnt/windows_share -o credentials=/root/.credentials

Source: [Mount windows share folder in Linux]("http://ubuntulinux.co.in/community/index.php?threads/mount-the-windows-share-folder-with-spaces-and-domain-authentication.384/")

---

### Post by JRV on 2012-12-17
This works for me:
```

nautilus smb://WINDOWS_HOSTNAME/SHARENAME

```

---

### Post by Mark Phelps on 2012-12-17
> **Robert R said:**
> Hi I have a ubuntu laptop and would like to connect it to my WD external hard drive too copy info, do backups etc... 

The HD is shared on a windows 7 machine..

Where would one start to achieve this ??

If the external drive is a PASSPORT, and you have a password set, Linux is not going to be able to get by that password because the front-end app runs only in Windows.

---

### Post by Robert R on 2012-12-17
Tried this but got the following error, 

looking at the other options will let  you all know how it goes

---

### Post by Robert R on 2012-12-17
> **sahabcse said:**
> Create the test directory and mount the window share into that folder.

mkdir -p /media/test
mount -cifs //windowsserver/sharefolder /media/test

If you setup password on share folder then follow below method

Create a hidden file under root home folder. Provide the user login items
vim /root/.credentials
username=domain\my_user
password=mypassword

Follow the below command for mount the windows partition

mount -t cifs "//windowsserver/sharefolder" /mnt/windows_share -o credentials=/root/.credentials

Source: [Mount windows share folder in Linux]("http://ubuntulinux.co.in/community/index.php?threads/mount-the-windows-share-folder-with-spaces-and-domain-authentication.384/")
Can you explain a little more on this please? are you supposed to create a vim /root/.credentials
file and put 
"
username=domain\my_user
password=mypassword
"
in the file or are those commands to be run, srry but i am very noobie at this

---

### Post by steeldriver on 2012-12-17
My recent experience suggests you need to install the cifs-utils package in order to mount Samba (Windows) shares 

AFAIK that applies whether you mount via the command line or direct from nautilus

---

### Post by sahabcse on 2012-12-20
> **Robert R said:**
> Can you explain a little more on this please? are you supposed to create a vim /root/.credentials
file and put 
"
username=domain\my_user
password=mypassword
"
in the file or are those commands to be run, srry but i am very noobie at this

Yes we need to create a file for giving user login credentials.

---

