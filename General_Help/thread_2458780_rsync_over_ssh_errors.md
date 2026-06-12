---
title: "rsync over ssh errors"
date: 2021-03-03
forum: General Help
---

### Post by raccoonstrait on 2021-03-03
Hello Everyone:

I am trying to set up rsync over ssh from my Xubuntu 20.04.2 system to a Raspberry Pi OS system (new install and updated). The ssh works fine. I have done rsync on the Pi, and know that that works. I tried to get rsync over SMB to work, but while it seemed to work, the results were not satisfactory. So now I am trying rsync over ssh. The drives are mounted via FSTAB to /home/public/user/DRIVES/ on both systems. These are multi terabyte external drives mounted via USB. Here is what I get.

```

rsync -rogvP --delete --ignore-existing --size-only --partial -s /home/public/users/MyDrive01/ pi@IPAddress:/home/public/users/5TBMyDrive01-BU
pi@IPAddress's password: 
sending incremental file list
rsync: change_dir "/home/public/users/MyDrive01" failed: No such file or directory (2)


sent 24 bytes  received 12 bytes  2.88 bytes/sec
total size is 0  speedup is 0.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1207) [sender=3.1.3]

```

I have tried a number of options sets. I have also tried a number of rsync configurations, following different recommendations from various websites after searching for the error statements. I have even added the source drives (the ones rsync seems to be complaining about) to my path. No joy.

Is this merely a syntax error, or am I missing something completely?

Thanks

Raccoon Strait

---

### Post by HermanAB on 2021-03-04
Well, the error message is very explicit!
At the exact point in time when rsync runs, the source directory is not accessible.

---

### Post by raccoonstrait on 2021-03-04
Thanks for the response HermanAB, 

That's the thing though. The source directory is part of a Samba NAS and has no trouble serving that function. The source directory is accessible to file managers, and even remote machines over SMB. I even exited ssh and changed the current directory to the root of the source in Bash and then tried ssh and rsync again. That error message was captured when the current directory was the source directory that rsync is telling me it can't access. And this went on for several hours as I searched for possible answers.

I suppose I should add that if I move the target drive to the source machine, rsync runs without issue.

Why would that be?

Raccoon Strait

---

### Post by HermanAB on 2021-03-04
So you are running rsync over ssh over samba?  Layer it three deep is just looking for trouble.  If you remove either samba or ssh, then it will probably work much better.

---

### Post by raccoonstrait on 2021-03-04
Well, I had tried that, rsync over Samba, from the target system, and I got a lot of errors. Just now, I tried again from the source system. Rsync had issues with retaining permissions and there were a number of files that reported 'permission denied (13)'. All the devices have had chown nobody:nogroup both with and without the -R as well as chmod 777, again both with and without the -R. Some of the permission denied files are new, but many that have been overwritten recently are not denied. I was hoping the ssh method would alleviate that issue.This is similar behavior that took place when running rsync over SMB from the target system. It doesn't seem right, and that is why I tried to do it using ssh. 

If you note the ssh/rsync  command I used in my original post, there is no SMB mentioned, which to me means the Samba was removed from the equation. Or is that fact that samba is running at all the problem?

When running rsync strictly over SMB the path looks like this:

```

rsync: recv_generator: failed to stat "/run/user/1000/gvfs/smb-share:server=raspberrypi.local,share=public/5TBMydrive01-BU/Programs/series/season/filename": Permission denied (13)

```

smb is definitely involved there.

So, I am back to my original issue, I think.

Thanks

Raccoon Strait

---

### Post by TheFu on 2021-03-04
rsync over SMB?  That's confusing.
How about "rsync to an SMB mount"?
Just mount the SMB/CIFS to the machine where the files are located and use rsync. That works. I use it a few times a week.

Oh ... and don't use a GUI to mount samba/CIFS storage.  Setup the CIFS mount in the /etc/fstab or by using autofs if you want this to work.

**gvfs won't work.**  That's the problem.

---

### Post by raccoonstrait on 2021-03-04
Thanks for your input TheFu

Here is how all of these drives are mounted via fstab, on both systems. I did have a statement at the end x-gvfs-show which I have now removed, could that have been the problem? I was already using auto for the fs, the drives are all ext4.

```

LABEL=5TBMydrive01 /home/public/users/5TBMydrive01 auto rw,nofail,noatime 0 2

```

Is this the correct mounting?

Raccoon Strait

---

### Post by TheFu on 2021-03-04
If you type 
```
df -Th
```
Does all the storage involved show up?  Both the source and the target?  If not, no, that is not correct.

I've never used "auto" for the file system type. The actual type is very important. Other options maybe needed, but i cannot tell.

---

### Post by raccoonstrait on 2021-03-04
No, only the local drives show up using df.

I have just tried to rsync using the path shown in Thunar for the remote drive, no help as it doesn't seem to like the smb// and removing the smb didn't help either.

I am going to try to change all the mounts from auto to ext4 and see if that helps.

Raccoon Strait

---

### Post by HermanAB on 2021-03-04
If df doesn't show the mounted file system, then it is not mounted.

Once mounted, the remote filesystem directory works the same as a local filesystem directory, so then you don't need a smb:// anymore.

The upper layer tool can't work if the lower network layer is broken.

---

### Post by raccoonstrait on 2021-03-04
OK guys, I think I see some light in this tunnel. Mounting the remote drive to a local directory is the key (one I had not heard of before). And, when done it does show up in thd df -TH. 

For those who are interested this seems to work, but prepare the local directory first.

```

sudo sshfs -o allow_other pi@IPAddress:/home/public/users/5TBMydrive01-BU /home/username/Backup-Temp/

```

Even though I did not get the original issue solved, I did get a working solution.

Thank you guys.

Raccoon Strait

---

### Post by TheFu on 2021-03-04
sshfs is really slow. Best to be used for temporary stuff or over the internet.  
Either use nfs or cifs when on the same LAN. Both will be 2-4x faster than using sshfs.

---

### Post by raccoonstrait on 2021-03-06
Thanks TheFu,

It took a while to configure the cifs mount, but I finally got it.

The drives are all mounted on /home/public/users/Drivename, on both systems but the remote drives have -BU appended to their name.
The local directories were created in advance.
All files/directories are owned by nobody:nogroup which is what the number 65534 represents.
All the files have been treated with sudo chmod 777
I tried to  mount //IPAddress/5TBMyDrive but that failed, I needed to include the /public/, as seen below

Here is the fstab command that worked

```

//192.168.11.115/public/5TBSeagate01-BU/  /home/raccoon/Backup-Temp-01 cifs rw,guest,noperm,_netdev,credentials=/etc/samba/.cifscreds,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=65534,gid=65534,nofail 0 0

```

All the options were gleaned from various websites in trying to get this to work. Some of them may not be necessary.

These drives now mount at reboot or with sudo mount -a.

Thanks again

Raccoon Strait

---

### Post by TheFu on 2021-03-06
Good job on getting something working. With so many moving parts, this can be confusing.

You might find my post here: [https://ubuntuforums.org/showthread.php?t=2457754&p=14024193#post14024193](https://ubuntuforums.org/showthread.php?t=2457754&p=14024193#post14024193) with explanation to be helpful.

[LIST]
[*]chmod doesn't work with cifs mounted storage.  If you want chmod to work, use NFS.  NFS is preferred for a number of reasons. One of those is that native owners, groups, permissions, ACLs and often xattrs are supported, unlike the back-o-da-bus CIFS.
[*]Mounting storage under an existing HOME is a poor choice for a number of reasons.  You can trust me now or learn those reasons when it happens to you.
[*]Almost always, setting permissions to 777 is a terrible idea.  I think it is in this situation too. It makes for non-secure situation and provides anyone who can claim to be the client able to delete all the files.  That's always a bad idea.
[*]uid=65534,gid=65534 are useless. No need to specify either, if you use 777. If you have just 1 userid, set that (the name or the numeric id can be used).  If you have multiple userids that you want to provide access, use that after you put all the client-side users into a shared group together. Use the 'id' command to get numbers.
[*]guest doesn't mean the same thing on the client site as it does in Windows. I doubt you want that - if you do, then you shouldn't need any credentials=.
[/LIST]

That's probably enough. Ignore whatever you like.

---

### Post by raccoonstrait on 2021-03-06
Advise taken. Local directories moved to /mnt/Backup-Temp-01, and etc.

The fstab now looks like this:

```

//IPAddress/public/5TBMydrive01-BU  /mnt/Backup-Temp-01 cifs rw,noperm,_netdev,credentials=/etc/samba/.cifscreds,iocharset=utf8,uid=1000,gid=1000,nofail 0 0

```

Thanks for the feedback.

Raccoon Strait

---

### Post by TheFu on 2021-03-06
I'm guessing there's no convincing you to use NFS?  I had to ask. ;)

---

### Post by raccoonstrait on 2021-03-06
I loves me a challenge, so I have tried NSF, and was mostly successful.

I can mount the remote drives manually using:

```

sudo mount 192.168.11.115:/home/public/users/5TBMydrive01-BU /mnt/Backup-Temp-01 && sudo mount 192.168.11.115:/home/public/users/5TBMydrive02-BU /mnt/Backup-Temp-02 && sudo mount 192.168.11.115:/home/public/users/5TBMydrive03-BU /mnt/Backup-Temp-03 && sudo mount 192.168.11.115:/home/public/users/BU-Hosts-BU /mnt/Backup-Temp-Hosts

```

But when I try to get fstab to do the same thing with sudo mount -a  it times out. Here is the latest code tried in fstab though there were several other sets of options at various points.

```

192.168.11.115:/5TBSeagate01-BU  /mnt/Backup-Temp-01 nfs auto,_netdev,proto=tcp,async 0 0

```

I will replicate whatever works here to the other shares and uncomment them.

It is a standard domain WORKGROUP and I found a thread where a similar issue was being discussed, but did not find any resolutions, (that person made some change to systemd timeouts, but I have no earthly idea how to go about that).

Any suggestions?

Thanks

Raccoon Strait

BTW, you did say or! :)

---

### Post by TheFu on 2021-03-06
192.168.11.115:/home/public/users/5TBMydrive01-BU
is not te same as 
192.168.11.115:/5TBSeagate01-BU

Is it?

the NFS server /etc/exports file needs to be setup, at least for linux nfs servers.  For a commercal NFS, you'll need to find a how-to for that model.

---

### Post by raccoonstrait on 2021-03-06
Dang, I was trying to hide the actual drive names, safety you know. The names are correct where they need to be.

The NFS Server is a Raspberry Pi running Raspberry OS and was setup using info from [ https://pimylifeup.com/raspberry-pi-nfs/]("https://pimylifeup.com/raspberry-pi-nfs/"). As I said, the drives mount manually, it is just the fstab I am having difficulty with. I just tested the rsync, for each of the partitions, and it worked (manual mount).

There is a difference between the manual mount and the fstab mount statements, the manual uses the full path, but I removed that for the fstab statement as I was getting different error messages with that, like it didn't recognize it at all. Which should it be, full path or something else? There was that issue where leaving out /public/ for the cifs setup made a difference.

Raccoon Strait

---

### Post by TheFu on 2021-03-07
> **raccoonstrait said:**
>  
There is a difference between the manual mount and the fstab mount statements, the manual uses the full path, but I removed that for the fstab statement as I was getting different error messages with that, like it didn't recognize it at all. Which should it be, full path or something else? There was that issue where leaving out /public/ for the cifs setup made a difference.

Well, the source used in the manual mount and in the fstab should be the same.  We can't just randomly remove parts and expect it to work.
The /etc/exports file controls what is shared via NFS.  

This has nothing to do with CIFS. They aren't related in any way. CIFS sharing is controlled by the smb.conf file.  You can have both or one or neither setup.  They work differently.  A few of my NFS mounts from a client system:
```
$ df -Th
Filesystem                      Type  Size  Used Avail Use% Mounted on
istar:/d/D1                     nfs4  3.5T  3.5T   44G  99% /d/D1
istar:/d/D3                     nfs4  3.6T  3.6T   15G 100% /d/D3
istar:/d/D2                     nfs4  3.6T  3.5T   29G 100% /d/D2
romulus:/Data/r2                nfs4  1.3T  1.2T   67G  95% /S
romulus:/raid/media             nfs4  1.8T  1.7T  7.7G 100% /R
romulus:/raid/media/Music       nfs4  1.8T  1.7T  7.7G 100% /M
```
In general, I prefer to have the storage mounted at exactly the same location over NFS as it is mounted on the NFS server. This limits my confusion, since I use lots of different systems. It is good to look in the same place for files.  I don't use NFS for any backup storage. That's a safety thing. Wouldn't want to accidentally delete stuff.  

Also, for some systems, the NFS mounts are read-only to protect the data.  For example, I want Music and photos available via Nextcloud, but I don't trust Nextcloud not to delete everything.  That means a read-only mount. I consider Nextcloud to be a high-risk webapp. If someone hacks into that system and decides to be mean by deleting everything - fine.  But the read-only data won't be touched as it sits on a different system.

---

### Post by raccoonstrait on 2021-03-07
OK, I found the issues. The previous error messages had to do with my using leading // for the IP address, my failure to use the : between the IP and the share name, my failure to use the full path, and a bunch of options that apparently don't fit the need. Some of these errors probably happened at the same time and changing just one of them didn't fix the problem, and of course gave me different obtuse error messages. 

The fstab statement now looks like this:

```

192.168.11.115:/home/public/users/5TBMydrive01-BU  /mnt/Backup-Temp-01 nfs auto,_netdev,proto=tcp,async 0 0

```

for all four partitions. On first reboot only three of the four mounted. I used sudo mount -a and the remaining partition mounted. I then rebooted again, and all four mounted.

Thank your for your support, and patience.

Raccoon Strait

---

### Post by TheFu on 2021-03-07
The initial issue was just how the storage was not mounted to the r-pi.  For some reason, I got the impression that the r-pi was mounting storage from a NAS device, not a directly connected USB HDD.

Rsync can be used directly from the client to the Pi directly. No need for CIFS or NFS at all.
And with an ssh config file setup so you never need to know the r-pi IP address again.  With ssh-keys, on the r-pi, the client don't need to wait for a password to be entered, should you want to automate this.

rsync behaves differently when it knows the systems are separate as compared to when the storage is all local. NFS appears to rsync like a local mount.  This can make for inefficiencies when local storage is involved.  If the files are tiny, it probably doesn't matter. With larger files, the entire file will be copied again rather than just the parts that were changed.  That's the real power with rsync.

---

### Post by raccoonstrait on 2021-03-07
Now you tell me. Rsync does remote??? It even works, automated.

Well aside from the frustration, the hair loss, time spent, and overindulgence on coffee and hard liquor (just kidding), I did learn some things.

Thanks, one more time.

Raccoon Strait

---

