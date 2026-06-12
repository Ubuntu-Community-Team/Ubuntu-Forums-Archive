---
title: "Rsync stops and seems to do nothing"
date: 2018-04-15
forum: General Help
---

### Post by GrouchyGaijin on 2018-04-15
I am running Ubuntu 16.04 with Gnome Shell.
I have a WD Ultra Ex2 NAS

The easiest way I have found to have a script copy/move files to the NAS share is via is:
```
run/user/1000/gvfs/smb-share:server=192.168.1.100,share=<share name> 
```

**This works fine if I tar.gz a very large folder and then use pv to copy it to the above path. I use pv so that I can see the progress of the transfer.**

I would like to use rsync with the delete option instead of comprssing an entire folder then copying it. The problem is that everytime I use rsync with this:
```
rsync -avz --delete /home/<my user name>/<folder> /run/user/1000/gvfs/smb-share:server=192.168.1.100,share=<share name>/
```
All of the sub-folders are copied, so I can see the structure. Rsync indicates it is copying files then after a while it simply stops responding. When I open the destination folder, it is empty. I know that sometimes if the destination folder is open I need to navigate to another folder and back to the destination folder to see any changes. The sub-folders are still all empty. Even using ls from the terminal they appear empty.
I have also tried the above rsync command without the ```
--delete
``` flag and just ```
rsync -avzh and the path to source and destination
```

Does anyone know what could be causing this or how to fix it? The directory I want to copy is 20 GB and I have over three TB of space on the NAS left.
Since my work around actually does successfully copy the files I think the problem may be with rsync or, much more likely, my command.

---

### Post by SeijiSensei on 2018-04-16
Looks like you're trying to rsync to a windows share. NTFS doesn't offer the same filesystem primitives as *nix. If you must back up to a windows share, the only reliable method is the tarball method you used before.

If the NAS offers the option to connect via NFS, you could mount a share with that and use rsync.

---

### Post by GrouchyGaijin on 2018-04-16
Thank you for the reply. 
I checked the web interface for my NAS and indeed it is mountable via NFS.
It says Mount Point: ```
nfs://192.168.1.100/nfs/<share name>
```
When I clicked the configure box it has the host listed as *

I am not sure how I to actually use this information with rsync.
Any advice would be greatly appreciated.

GG

---

### Post by SeijiSensei on 2018-04-16
Try this:

1) Create a "mount point" on your system.  I usually place them under /media.  

```
sudo mkdir /media/nas
```

2) Next install the NFS client software

```
sudo apt install nfs-common
```

3) Now try and see if you can mount the share defined above:

```
sudo mount 192.168.1.100:/nfs/<share name> /media/nas
```

Obviously you'll have to replace <share name> with the name of the directory on the NAS that you want to export.  I presume you can configure that on the NAS.  If you have other options available to you, see if you can enable "no_root_squash".

If that works, the contents of the share will be available at /media/nas/.

There's all sorts of ways this can fail to work.  Let see what happens.

I run NFS on normal Linux platforms, so I don't know how hard or easy it is to get a commercial NAS to do what you need.

---

### Post by GrouchyGaijin on 2018-04-16
Thank you for your help. I think I found another way that seems to be working. I can use lftp with the --mirror flag to ftp the files from my laptop to the NAS.

---

