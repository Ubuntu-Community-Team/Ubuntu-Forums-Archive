---
title: "how to mount my NAS"
date: 2024-01-10
forum: General Help
---

### Post by hmiersch on 2024-01-10
hello.  i want to auto-mount a folder on my NAS (a synology DS423+ with 4 2TB HDs, in case that matters) when i boot my system. for that purpose i have the following line in my fstab:  192.168.1.8:/volume1/data /mnt/data nfs x-systemd-automount 0 0  the problem is that it doesn't work, and when i try to mount it manually (sudo mount -a) i get an error telling me that the mount point does not exist. so what can i do about this?  do i have to add a folder to /mnt? if so, how do i change the permissions for /mnt so i can create a folder inside it? and if not, how do i get that folder on the NAS mounts so i can access it? is there something i have to do on he NAS to make it work? and why does the forum ignore my blank lines and put everything in one giant line?

---

### Post by ActionParsnip on 2024-01-10
You need to make the point point
```

sudo mkdir -p [COLOR=#E8E6E3]/mnt/data

```[/COLOR]

---

### Post by SeijiSensei on 2024-01-10
More specifically, 
```
sudo mkdir /mnt/data
```
since that appears to be where you want the device mounted.

---

### Post by hmiersch on 2024-01-10
> **SeijiSensei said:**
> More specifically,  ```
sudo mkdir /mnt/data
```  hm, for some reason that wasn't necessary, because /data already appeared in /mnt. weird.  >  since that appears to be where you want the device mounted.  is there another place where the NAS folder should be mounted? me, i don't really care where it is mounted as long as i can access it just like any other external HD. IOW, it should appear as an icon on the desktop or in the left column of the files window. but the only way i can access it is by clicking on "other locations", then "DS423". the problem with that is that it is SMB which i don't want. i want NFS because of the restrictions of SMB.

---

### Post by SeijiSensei on 2024-01-10
The next possiblity is that the server is exporting a share whose name is not "/volume1/data". Perhaps it's exporting just "volume1"? If so, you must mount that. The data subdirectory will be available automatically.

If that doesn't work you'll need to run mount manually with the verbose option enabled to find the problem.
```
sudo mount -vvv 192.168.1.8:/volume1/data /mnt/data
```
You should see where the problem lies in the debugging output.

NFS3 vs NFS4 can also be an issue; you'll probably see it in the verbose output if it's a problem.

I assume you've already run
```
sudo apt install nfs-common
```

---

### Post by TheFu on 2024-01-10
```
showmount -e 192.168.1.8    # to see available nfs mounts at that IP.
```

> hm, for some reason that wasn't necessary, because /data already appeared in /mnt. weird. 

This is confusing.  /mnt is in the root directory.  /data as written above is also in the root directory. You probably mean /mnt/data.  Any path that begins with a '/' is an absolute path.  If you want a relative path and want to denote a directory, I find it is best to use a trailing slash, like data/.  Make sense?

Whenever posting terminal stuff - text config files, always use forum code tags.

```
 192.168.1.8:/volume1/data /mnt/data nfs x-systemd-automount 0 0
```
Doesn't look right.  BTW, the systemd automount option doesn't work all that well. Best to avoid using it.  Try this:
```
192.168.1.8:/volume1/data      /mnt/data      nfs      defaults     0     0
```
I've assumed what you posted already was valid, but we don't know that for certain.  1 space or 20, doesn't matter (no tabs, ever). I like to line up all the columns in my /etc/fstab so it is clear which field is being used.

For automatic, sometimes-available, storage, like NFS, I prefer to use **autofs**.  Actually, I use it for USB connected storage too.

---

### Post by hmiersch on 2024-01-12
> **SeijiSensei said:**
> 
```
sudo mount -vvv 192.168.1.8:/volume1/data /mnt/data
```

doing that gives me the following output: 
```

mount.nfs: timeout set for Fri Jan 12 11:05:32 2024
mount.nfs: trying text-based options 'vers=4.2,addr=192.168.1.8,clientaddr=192.168.1.64'
mount.nfs: mount(2): Protocol not supported
mount.nfs: trying text-based options 'vers=4,minorversion=1,addr=192.168.1.8,clientaddr=192.168.1.64'
mount.nfs: mount(2): Device or resource busy

```

> 
I assume you've already run
```
sudo apt install nfs-common
```
i entered that line and it told me that nfs-common is already installed and up-to-date.

and in case it matters, ```

showmount -e 192.168.1.8
```
 gives me 
```
Export list for 192.168.1.8:
/volume1/data        192.168.1.1/24
/volume1/Media files 192.168.1.64
/volume1/Backups     192.168.1.64
```

---

### Post by TheFu on 2024-01-12
```
mount.nfs: mount(2): Device or resource busy
```

Already mounted?

In post #6, the last fstab entry should work.  If rpc.d got into a strange situation, you may need to reboot. This seldom happens, perhaps once every 10 yrs.

---

### Post by SeijiSensei on 2024-01-12
I'd read the documentation for your NAS and make sure it supports NFS4. One quick test you can try is using
```
sudo mount -vvv **-o nfsvers=3** 192.168.1.8....
```

---

### Post by Morbius1 on 2024-01-13
> 192.168.1.8:/volume1/data /mnt/data nfs **[COLOR="#B22222"]x-systemd-automount[/COLOR]** 0 0
Did you mean **[COLOR="#B22222"]x-systemd.automount[/COLOR]**

---

### Post by hmiersch on 2024-01-15
>  Already mounted?   if it is already mounted, shouldn't it show up somewhere?   >  make sure it supports NFS4  as far as i can tell, my NAS supports NFS 2, 3, 4 and 4.1. > Did you mean x-systemd.automount i'll try that.

---

### Post by TheFu on 2024-01-15
> **hmiersch said:**
> if it is already mounted, shouldn't it show up somewhere? 

Depends on how it is mounted.  There are _real_ mounts and _fake_ mounts.  My delineation (not used by anyone else that I know) is whether a mount shows up in the **mtab** file or not.  The mtab file doesn't just hold real mounts, but some pseudo-device mounts too.

**Fake mounts don't show up in the mtab**. I consider those to be an abomination.  *gvfs* and *gio* almost always cause _fake mounts_.  Those are used by GUI tools, especially Gnome programs.  The fstab and using the mount command should result in real mounts.

Another method to see _real mounts_, is to use **df -Th** and filter out the pseudo-devices - mainly fake file systems like tmpfs and loop devices.

If you are expecting an icon to show in a GUI file manager, that doesn't usually happen with real mounts.  A real mount can be local or remote, but the programs on the system generally don't know where the storage is and don't care.

---

### Post by hmiersch on 2024-01-15
i just checked, it does show up in mtab. i can't post the line here because i don't know how to copy something out of nano.

---

### Post by TheFu on 2024-01-15
> **hmiersch said:**
> i just checked, it does show up in mtab. i can't post the line here because i don't know how to copy something out of nano.

Your mouse.  Select the text. the "select" process should be sufficient.
Move to the place you want to paste it. Press the middle mouse button.  This should work for any text in any program and the paste will paste into whatever active "widget" the mouse is over during the paste.  No menus.  If it takes more than 3 seconds, you are doing it wrong or running a broken DE that violated standards.

The method of selection can be click-drag-unclick or double-click or triple-click to get a specific selection, 1 word, entire line.  All three selection methods support drag to extend or reduce the selection size.

This should have been taught in the first 10 minutes of using any Unix GUI.  
Tab-completion in a shell should be taught in the 2nd 10 minutes when a terminal is used.

I couldn't imaging my workday without select-paste.  It is extremely central to how I work.

Forget all the clipboard managers. They get in the way and make something simple hard.

---

### Post by hmiersch on 2024-01-19
i tried that, and it worked. however, the line is so long that i had to copy it in pieces. here it is: ```
 192.168.1.8:/volume1/data /mnt/data nfs4 rw,relatime,vers=4.1,rsize=131072,wsize=131072,namlen=255,hard,proto=tcp,timeo=600,retrans=2,sec=sys,clientaddr=192.168.1.64,local_lock=none,addr=1 
```  the weird thing is, right after bootup, that line wasn't in /etc/mtab. it only showed up after i said  ```
 sudo mount -a 
``` does that mean that the folder is not mounted automatically at startup?

---

### Post by TheFu on 2024-01-19
The select/copy being long shouldn't matter, unless your terminal settings are screwed.  Selecting 1 character or 20 pages is possible.  Today, I selected a TV grid schedule and pasted the entire thing - probably thousands of lines - into a text file for a little processing.  Select/paste works and has since at least the early 1990s.  It uses the built-in X-buffer.

I assme that line posted was from the mtab and it is working now.  Most of those settings are defaults or negotiated between the NFS client and server. 

If you try to access the /mnt/data directory and there is stuff there, it is mounted.  

With NFS, it has to wait until after the network is up fully before any NFS mounts can happen.  In the old days, we had to specifically use the _netdev option in the fstab to prevent pre-mature mount attempts. I think that hasn't been needed in about 15 yrs.

So, if this is solved now, please use the _Thread Tools_ button and mark it so.

---

### Post by mikodo on 2024-01-19
> **hmiersch said:**
> and why does the forum ignore my blank lines and put everything in one giant line?

Late for the show. 

Many times this has happened to me also. I think probably, you need to allow "Java Scripts" on this site to be able to have line breaks.

---

