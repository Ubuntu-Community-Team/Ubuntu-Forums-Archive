---
title: "How do I access Network Direcotries via Terminal?"
date: 2007-06-21
forum: General Help
---

### Post by adamdawkins on 2007-06-21
Hi,

Through Places > Network > Windows Network etc I was able to access files on my Windows PC perfectly in File Browser, but how can I access these directories via terminal?

---

### Post by Persianelfster on 2007-06-21
smbclient //name of the pc on network/folder 
try that, i think thats what you meant

---

### Post by mustali on 2007-06-21
I think you are wanting to navigate to the network folder from the command line just as if it was a local directory right? In that case, you need to mount the network folder using smbfs.

I was able to access my windows Shared folder using the following:

Create a folder that you want to mount the network-folder/machine
```

cd
mkdir FOLDER
sudo mount -t smbfs -o rw,username=USERNAME,workgroup=WORKGROUP  //COMPUTER-NAME/Shared ~/FOLDER/

```

where USERNAME is the username of the remote machine, WORKGROUP is the workgroup name,

This should then ask you for a password. Enter it and you should then be able to access the remote folder from FOLDER.

Make sure you have smbfs installed. If not
```

sudo apt-get install smbfs

```

HTH

---

### Post by kinson on 2007-09-05
Hi,

Thanks for the informative post :) i've trying to setup my Ubuntu machine as a backup server, so I'd like to be able to create a crontab to backup my folders from various pc's.

One thing though, like you said, i don't think I have smbfs installed, but when I try to install it, it says 0 packages installed or updated.

```

The following NEW packages will be installed:
  smbfs 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 427kB of archives. After unpacking 995kB will be used.
Writing extended state information... Done
Get:1 http://security.ubuntu.com feisty-security/main smbfs 3.0.24-2ubuntu1.2 [427kB]
Fetched 427kB in 10s (39.9kB/s)                                                 
Selecting previously deselected package smbfs.
(Reading database ... 104920 files and directories currently installed.)
Unpacking smbfs (from .../smbfs_3.0.24-2ubuntu1.2_i386.deb) ...
Setting up smbfs (3.0.24-2ubuntu1.2) ...
kinson@oemBuntu:/$ man smbfs
No manual entry for smbfs

```

Any ideas? :(

Thanks in advance :)

Cheers,
Kinson

---

### Post by mustali on 2007-09-05
there is no manual entry for smbfs. the information is contained in the man pages for mount.

do the following and search for smbfs

```

man mount
```

HTH

---

