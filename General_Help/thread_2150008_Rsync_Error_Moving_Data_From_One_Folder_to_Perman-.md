---
title: "Rsync Error Moving Data From One Folder to Perman-mount Network Drive"
date: 2013-05-30
forum: General Help
---

### Post by Sanityisboring on 2013-05-30
Hello all!
Like the title states, I'm using rsync to copy data sitting in /home/neaspec/data to a perma-mounted network drive (through /etc/fstab) sitting on /home/neaspec/Network_Drive/NEASNOM Data

Rsync copied and ran test .txt files fine; I could even use gnome-schedule to make the backup recurrent and there were never any issues. However, the first time I used real data my rsync spat back this wonderful batch of errors at me:[B]
[FONT=arial]rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)[/FONT]
[FONT=arial]rsync: connection unexpectedly closed (50 bytes received so far) [sender][/FONT]
[FONT=arial]rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.8][/FONT]
[FONT=arial]Rsync process exit status: 12

[/FONT][/B][FONT=arial]My rsync command:
```
rsync -r -t -x -v --progress -s /home/neaspec/data/ /home/neaspec/Network_Drive/NEASNOM Data
```

Running with/without sudo privileges didn't create any difference in the error, or the number of files copied.

My /etc/fstab/ mounting code:
```
//128.239.10.150/groups/infrared /home/neaspec/Network_Drive cifs uid=neaspec,credentials=/home/neaspec/.smbcredentials,rw,iocharset=utf8,sec-ntlm 0 0
```

I would appreciate any help, and I'll supply any more information I didn't include in a future post.

Because I've seen this be the first question for a lot of posts like these, here is the result from running
```
df -h
```
[/FONT]```
[FONT=arial]neaspec@nea26:~$ df -h[/FONT]
[FONT=arial]Filesystem            Size  Used Avail Use% Mounted on[/FONT]
[FONT=arial]/dev/sda1              30G  3.3G   25G  12% /[/FONT]
[FONT=arial]udev                  2.0G  4.0K  2.0G   1% /dev[/FONT]
[FONT=arial]tmpfs                 798M  832K  797M   1% /run[/FONT]
[FONT=arial]none                  5.0M     0  5.0M   0% /run/lock[/FONT]
[FONT=arial]none                  2.0G  148K  2.0G   1% /run/shm[/FONT]
[FONT=arial]/dev/sda3             427G   26G  381G   7% /home[/FONT]
[FONT=arial]//[/FONT][128.239.10.150/groups/infrared]("http://128.239.10.150/groups/infrared")
[FONT=arial]                       28T  2.9T   25T  11% /home/neaspec/Network_Drive[/FONT]
```[FONT=arial]


EDIT: Following up. After test-copying and moving singular files, I have discovered something is making rsync have meltdowns when it copies...non .txt files. I would receive the same error codes for .ascii and .dump files. 

[/FONT]```
    rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
    rsync: close failed on "/home/neaspec/Network_Drive/NEASNOM 
    Data/2012-11-07_10-58-44_trace/.2012-11-07_10-58-44_trace.screenshot.png.KwHs1g": Input/output 
        error (5)
    rsync error: error in file IO (code 11) at receiver.c(752) [receiver=3.0.8]
    rsync: connection unexpectedly closed (89 bytes received so far) [sender]
    rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.8]
    Rsync process exit status: 12
```

---

### Post by redmk2 on 2013-05-30
```
//128.239.10.150/groups/infrared
```

This does not appear to be a proper remote address to be used in fstab.  I assume this is a CIFS mount as you have stated that in the fstab line.  If so the proper usage is: ```
 //IP_address/share_name
```

  No directories are to be used.  Were you advised to use this form by someone at W & M.

---

### Post by Sanityisboring on 2013-05-30
I was not advised this direction, I just assumed it was the proper way to mount something with a slightly more complicated directory. I thought I had to specify the directory I was routing to on the server, instead of just the group share. It's funny that you say that, because with the way I currently have it mounted rsync can copy simple text files to the network share.

So I would change the fstab to:
```
//128.239.10.150/infrared
```

Just trying to be clear, total noob at this.

I believe it is a CIFS mount? It's a network share that is formatted to also work with a windows XP and windows 7 computer. It's formatted NTFS, but when I browsed around for help setting the fstab up I saw a lot (so maybe 3 or 4 links off of google) of people using CIFS (even when linking network shares to windows and so on). Would I also want to change CIFS to NTFS in the fstab?

---

### Post by redmk2 on 2013-05-31
> **Sanityisboring said:**
> I was not advised this direction, I just assumed it was the proper way to mount something with a slightly more complicated directory. I thought I had to specify the directory I was routing to on the server, instead of just the group share. It's funny that you say that, because with the way I currently have it mounted rsync can copy simple text files to the network share.

So I would change the fstab to:
```
//128.239.10.150/infrared
```

Just trying to be clear, total noob at this.

I believe it is a CIFS mount? It's a network share that is formatted to also work with a windows XP and windows 7 computer. It's formatted NTFS, but when I browsed around for help setting the fstab up I saw a lot (so maybe 3 or 4 links off of google) of people using CIFS (even when linking network shares to windows and so on). Would I also want to change CIFS to NTFS in the fstab?

Is infrared the share name?

I'm sure this is a Windows share so cifs is correct in for fstab.  The instructions are available from the terminal using  ```
man fstab
```
The remote SMB/CIFS resource is as I said:  IP_Address/share_name.  Your problems are file system I/O errors.  This is probably due to the protocol having difficulty with your share definition.  

Mount the share correctly and go from there.

NTFS is a local file system (local to the server) and should not be a concern to you.

---

### Post by CaptainMark on 2013-05-31
According to the rsync man page the -s flag will "use blocking I/O for the remote shell" I'm no expert on rsync but have you tried the command without the -s flag, your error message some kind of I/O error.

---

### Post by Sanityisboring on 2013-05-31
Updates! I went through and man-page for rsync and dumped some useless commands and added other commands that I thought I'd like. I added the forward slashes because apparently that's how rsync knows when to read something as white space

**Rdmk2**: Infrared is the name of our share that we were allocated on the server. I have modified the fstab command to: ```
//128.239.10.150/infrared /home/neaspec/Network_Drive cifs uid=neaspec,credentials=/home/neaspec/.smbcredentials,rw,iocharset=utf8 0 0 

``` 

**CaptainMark**: I disabled the -s flag, and I'm still getting an I/O error

New rsync command:
```
sudo rsync -t -v -r --chmod=+rw --progress -e ssh --log-file=/home/neaspec/RsyncLog /home/neaspec/Desktop/New\ Folder/data /home/neaspec/Network_Drive/New\ Folder/data
```

New Error Batch (This is when I try to sync the entire filesystem)!
```
2013/05/31 17:48:17 [13205] building file list
2013/05/31 17:48:17 [13205] .d..t...... data/
2013/05/31 17:48:17 [13205] >f+++++++++ data/2012-11-06_09-41-07_camera_Opt_Mic_noZoom.png
2013/05/31 17:48:17 [13205] rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
2013/05/31 17:48:18 [13205] rsync: close failed on "/home/neaspec/Network_Drive/New Folder/data/data/.2012-11-06_09-41-07_camera_Opt_Mic_noZoom.png.IOyUAo": Input/output error (5)
2013/05/31 17:48:18 [13205] rsync: connection unexpectedly closed (51 bytes received so far) [sender]
2013/05/31 17:48:18 [13205] rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.8]
```

Error batch when targeting a singular file:
```
2013/05/31 18:01:40 [13254] building file list
2013/05/31 18:01:40 [13254] >f+++++++++ 2012-11-16_22-22-33_scan.screenshot.png
2013/05/31 18:01:40 [13254] rsync: close failed on "/home/neaspec/Network_Drive/New Folder/data/.2012-11-16_22-22-33_scan.screenshot.png.uynXMY": Input/output error (5)
2013/05/31 18:01:40 [13254] rsync error: error in file IO (code 11) at receiver.c(752) [receiver=3.0.8]
2013/05/31 18:01:40 [13254] rsync: connection unexpectedly closed (28 bytes received so far) [sender]
2013/05/31 18:01:40 [13254] rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.8]
```

I'm on the internets looking up the errors right now, but I figured updating you guys couldn't hurt

I turned super-extra-verbosity (-vvv as opposed to -v) and here is the error:
```
neaspec@nea26:~$ sudo rsync -t -vvv -r --chmod=+rw --progress -e ssh --log-file=/home/neaspec/RsyncLog /home/neaspec/Desktop/New\ Folder/data/2012-11-16_22-22-33_scan/2012-11-16_22-22-33_scan.screenshot.png /home/neaspec/Network_Drive/New\ Folder/data
[sudo] password for neaspec: 
sending incremental file list
[sender] make_file(2012-11-16_22-22-33_scan.screenshot.png,*,0)
send_file_list done
send_files starting
server_recv(2) starting pid=13618
received 1 names
recv_file_list done
get_local_name count=1 /home/neaspec/Network_Drive/New Folder/data
generator starting pid=13618
delta-transmission disabled for local transfer or --whole-file
recv_generator(2012-11-16_22-22-33_scan.screenshot.png,1)
send_files(1, /home/neaspec/Desktop/New Folder/data/2012-11-16_22-22-33_scan/2012-11-16_22-22-33_scan.screenshot.png)
send_files mapped /home/neaspec/Desktop/New Folder/data/2012-11-16_22-22-33_scan/2012-11-16_22-22-33_scan.screenshot.png of size 792420
calling match_sums /home/neaspec/Desktop/New Folder/data/2012-11-16_22-22-33_scan/2012-11-16_22-22-33_scan.screenshot.png
2012-11-16_22-22-33_scan.screenshot.png
       32768   4%    0.00kB/s    0:00:00  
sending file_sum
false_alarms=0 hash_hits=0 matches=0
      792420 100%  181.12MB/s    0:00:00 (xfer#1, to-check=0/1)
sender finished /home/neaspec/Desktop/New Folder/data/2012-11-16_22-22-33_scan/2012-11-16_22-22-33_scan.screenshot.png
recv_files(1) starting
generate_files phase=1
recv_files(2012-11-16_22-22-33_scan.screenshot.png)
got file_sum
rsync: close failed on "/home/neaspec/Network_Drive/New Folder/data/.2012-11-16_22-22-33_scan.screenshot.png.5y0DYX": Input/output error (5)
rsync error: error in file IO (code 11) at receiver.c(752) [receiver=3.0.8]
[receiver] _exit_cleanup(code=11, file=receiver.c, line=752): about to call exit(11)
rsync: connection unexpectedly closed (28 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.8]
[sender] _exit_cleanup(code=12, file=io.c, line=601): about to call exit(12)

```

TL/DR: The folder apparently receives the file contents (if reading it right?), but seems to fail "closing" the file.

---

### Post by Sanityisboring on 2013-05-31
You guys mentioned that mounting a samba cifs network share function (in fstab) under the *//servername/sharename* methodology
This straight up doesn't work for me

In fstab, right now, I have:
```
//128.239.10.150/groups/infrared /media/Network_Drive cifs credentials=/home/neaspec/.smbcredentials,iocharset=utf8,uid=1000 0 0
```

If I were to change this to:
```
//128.239.10.150/infrared /media/Network_Drive cifs  credentials=/home/neaspec/.smbcredentials,iocharset=utf8,uid=1000 0  0
```
the drive doesn't mount after system restart.

If your wondering why directories have changed, I unmounted the drive from it's previous directory (it was in home/neaspec/Network_Drive) because I wanted to see if changing direct ownership of the drive would influence/change my errors. Now, root owns the drive (instead of neaspec) and I still get the same errors. 

Could it be /groups/infrared is my total sharename and I have to be that specific? That's how I had to set the drive up on the two windows comptuers I use and they read/write to the share fine.

If necessary, I can restore the drive to it's previous state and position

---

### Post by bab1 on 2013-05-31
> **Sanityisboring said:**
> You guys mentioned that mounting a samba cifs network share function (in fstab) under the *//servername/sharename* methodology
This straight up doesn't work for me

In fstab, right now, I have:
```
//128.239.10.150/groups/infrared /media/Network_Drive cifs credentials=/home/neaspec/.smbcredentials,iocharset=utf8,uid=1000 0 0
```

If I were to change this to:
```
//128.239.10.150/infrared /media/Network_Drive cifs  credentials=/home/neaspec/.smbcredentials,iocharset=utf8,uid=1000 0  0
```
the drive doesn't mount after system restart.
What error message do you get? What do you see in the logs (dmesg)? > 

If your wondering why directories have changed, I unmounted the drive from it's previous directory (it was in home/neaspec/Network_Drive) because I wanted to see if changing direct ownership of the drive would influence/change my errors. Now, root owns the drive (instead of neaspec) and I still get the same errors. 
We are dealing with mounting shares to mount points.  No drives at all.  You set the ownership upon mounting (e.g. uid=1000).> 

Could it be /groups/infrared is my total sharename and I have to be that specific? That's how I had to set the drive up on the two windows comptuers I use and they read/write to the share fine.
No.  A share (the SMB resource) is defined as:  //COMPUTER_NAME/SHARE_NAME (or IP address for COMPUTER_NAME).  Windows may be forgiving but Linux is not. > 

If necessary, I can restore the drive to it's previous state and position

Post the errors and then we can diagnose the problem.

---

### Post by Sanityisboring on 2013-06-03
Hey bab1, thanks for the input!

I wrote dmesg to a file, and the error that came up:
```
CIFS VFS: default security mechanism requested.  The default security mechanism will be upgraded from ntlm to ntlmv2 in kernel release 3.1
[   18.498502] CIFS VFS: cifs_mount failed w/return code = -6
[   18.534417] CIFS VFS: cifs_mount failed w/return code = -6
```

Also, does mounting the share incorrectly mean anything bad in the long run? [http://acstore.blogs.wm.edu/connecting-on-pc/](http://acstore.blogs.wm.edu/connecting-on-pc/) The IT webpage instructed me to mount the share using the full path. Since we're using the server to backup all of our data we collect in lab, I'd appreciate knowing if that my incorrect mounting will make us lose the backup.

The return code 6 implies an incorrect mount path.
Here is my current mount path though:
```
//128.239.10.150/infrared /media/Network_Drive cifs credentials=/home/neaspec/.smbcredentials,iocharset=utf8,uid=1000 0 0
```

Sorry about the response time. This computer is attached to our scanning near-field microscope and I couldn't get in to troubleshoot over the weekend.

After following the suggestion that I might be having trouble connecting the drive to the network on bootup, I included the command "noauto" in my fstab and then modified the /etc/rc.local file to mount the drive.

New fstab:
```
//128.239.10.150/infrared /media/Network_Drive cifs noauto,credentials=/home/neaspec/.smbcredentials,iocharset=utf8,uid=1000,sec=ntlm 0 0
```

/etc/rc.local contents:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

mount /media/Network_Drive

exit 0
```

Now I only get one error:
```
[   10.537712] CIFS VFS: Error connecting to socket. Aborting operation
[   10.562377] CIFS VFS: cifs_mount failed w/return code = -101
```

But this error is indicative of a problem accessing the network, right? The return code=-6 errors are gone

---

### Post by SeijiSensei on 2013-06-03
Usually I find using just "-av" as rsync parameters is sufficient for a complete snapshot.

What is the filesystem on the rsync target?  Is it ext4 or something like NTFS which doesn't understand POSIX attributes like permissions or symlinks?

---

### Post by Sanityisboring on 2013-06-03
Thanks for replying SeijiSensei

The server is ntfs formatted. Thanks for the suggestion, I'll attempt -av with rsync when this all sorts out.

Browsing around on more internet, someone had a problem with their IP address being locked out of the NAS. Could I be having something similar? I wouldn't know how to get smbclient to give me what I needed.

I removed the noauto and rc.local command and just used "_netdev" which apparently does the same thing

Errors:
```
[   14.887145] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   14.887242] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   16.410117] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   16.598666] EXT4-fs (sda3): re-mounted. Opts: commit=0
[   19.028839] CIFS VFS: cifs_mount failed w/return code = -6
[   19.068689] CIFS VFS: cifs_mount failed w/return code = -6
[   19.117498] init: plymouth-stop pre-start process (1427) terminated with status 1
[   19.363678] eth1: no IPv6 routers present
[   25.419994] eth0: no IPv6 routers present
[   37.328457] CIFS VFS: cifs_mount failed w/return code = -6
[   37.404172] CIFS VFS: cifs_mount failed w/return code = -6
```

fstab:
```
//128.239.10.150/infrared /media/Network_Drive cifs _netdev,credentials=/home/neaspec/.smbcredentials,iocharset=utf8,uid=1000,sec=ntlm 0 0
```


EDIT: Welp, I found the problem. The IT Department told us our sharename was "infrared." When I use```
smbclient -L //128.239.10.150 -U cgzoghby
``` and enter my password, the sharename that comes up is "groups." I mapped the drive successfully in fstab, changing "infrared" to "groups." I'm hunting around now, because for some weird reason the share still mounts only giving read/write permissions to the Owner (neaspec), but read-only permissions to root and other users. I also haven't attempted rsync yet, I'll update when that happens

I attempted to twek the permissions, but nothing actually changed after this command:
```
sudo chmod ugo+rwx /media/Network_Drive/infrared
``` Shouldn't this work?

---

### Post by bab1 on 2013-06-03
> **Sanityisboring said:**
> ... Welp, I found the problem. The IT Department told us our sharename was "infrared." When I use```
smbclient -L //128.239.10.150 -U cgzoghby
``` and enter my password, the sharename that comes up is "groups." I mapped the drive successfully in fstab, changing "infrared" to "groups." I'm hunting around now, because for some weird reason the share still mounts only giving read/write permissions to the Owner (neaspec), but read-only permissions to root and other users.

I attempted to twe[a]k the permissions, but nothing actually changed after this command:

```
sudo chmod ugo+rwx /media/Network_Drive/infrared
``` Shouldn't this work?
Great to hear that you got the share name figured out. That was a university induced problem that should not have happened.  You set the ownership (user and group) upon mounting the share.  Root always has rw abilities, so I don't see how you can say that.   Are you NOT neaspec? 

If you have multiple users, you need to control access with a common LINUX group (GID); say sambashare or some such. You can see all the groups using this  command```
getent groups
```... to see what groups you belong to use this```
groups
```

[COLOR="#0000FF"]Edit: You can also set the permissions at mount time too.[/COLOR]

---

### Post by Sanityisboring on 2013-06-03
bab1, I attached the picture of what the permissions for my Network_Drive looks like.
EDIT: Sorry bab1, yes I am neaspec. neaspec is the only user set up on this computer. I'm just worried the the cause for my rsync errors has something to do with permissions, which I was I just want to give everybody read/write/execture permissions. Everyone and read and execute, but only neaspec can write.

fstab:
```
//128.239.10.150/groups /media/Network_Drive cifs noperm,_netdev,credentials=/home/neaspec/.smbcredentials,iocharset=utf8,uid=1000,sec=ntlm 0 0
```

When I drag down the "group" or "others" entry to select read and write (on my Network_Dive folder; the mount point), the panel greys out for a bit. A "please wait" bar pops up (but doesn't fill), and the setting resets back to read only.

However, now that the drive mounts correctly, I have gone back to rsync. I still get the same bucket full of errors with the initial run now, but at least I know that my fstab end isn't causing problems anymore. This "bucket full of errors" consists of rsync not copying anything other than .txt files properly. My other filetypes (.png .ascii and .dump) all "copy," but they are blank. I don't blame you if you don't want to read the full error below. The lines that stick out mention "delta-transmission disabled for local transfer or --whole-file" and the fact that the file seems to "copy" (this would be consistent with it's presence on my network_drive, even if it's empty) but the "close failed on "filename" input/output error (5)"

the rsync command:
```
rsync -t -vvv -r -av --progress -e ssh --log-file=/home/neaspec/Desktop/RsyncLog /home/neaspec/Desktop/New\ Folder/data/2012-11-06_09-41-07_camera_Opt_Mic_noZoom.png /media/Network_Drive/infrared/New\ Folder/data
```

```
2013/06/03 19:35:33 [2387] cmd=ssh machine=<NULL> user=<NULL> path=/media/Network_Drive/infrared/New Folder/data
2013/06/03 19:35:33 [2387] note: iconv_open("UTF-8", "UTF-8") succeeded.
2013/06/03 19:35:33 [2387] (Client) Protocol versions: remote=30, negotiated=30
2013/06/03 19:35:33 [2387] building file list
2013/06/03 19:35:33 [2387] [sender] make_file(2012-11-06_09-41-07_camera_Opt_Mic_noZoom.png,*,0)
2013/06/03 19:35:33 [2387] [sender] flist start=1, used=1, low=0, high=0
2013/06/03 19:35:33 [2387] [sender] i=1 /home/neaspec/Desktop/New Folder/data 2012-11-06_09-41-07_camera_Opt_Mic_noZoom.png mode=0100666 len=676371 uid=1000 gid=1000 flags=5
2013/06/03 19:35:33 [2387] send_file_list done
2013/06/03 19:35:33 [2387] file list sent
2013/06/03 19:35:33 [2387] send_files starting
2013/06/03 19:35:33 [2387] server_recv(2) starting pid=2388
2013/06/03 19:35:33 [2387] received 1 names
2013/06/03 19:35:33 [2387] [Receiver] flist start=1, used=1, low=0, high=0
2013/06/03 19:35:33 [2387] [Receiver] i=1 1 2012-11-06_09-41-07_camera_Opt_Mic_noZoom.png mode=0100666 len=676371 uid=1000 gid=1000 flags=0
2013/06/03 19:35:33 [2387] recv_file_list done
2013/06/03 19:35:33 [2387] get_local_name count=1 /media/Network_Drive/infrared/New Folder/data
2013/06/03 19:35:33 [2387] generator starting pid=2388
2013/06/03 19:35:33 [2387] delta-transmission disabled for local transfer or --whole-file
2013/06/03 19:35:33 [2387] recv_generator(2012-11-06_09-41-07_camera_Opt_Mic_noZoom.png,1)
2013/06/03 19:35:33 [2387] send_files(1, /home/neaspec/Desktop/New Folder/data/2012-11-06_09-41-07_camera_Opt_Mic_noZoom.png)
2013/06/03 19:35:33 [2387] count=0 n=0 rem=0
2013/06/03 19:35:33 [2387] send_files mapped /home/neaspec/Desktop/New Folder/data/2012-11-06_09-41-07_camera_Opt_Mic_noZoom.png of size 676371
2013/06/03 19:35:33 [2387] calling match_sums /home/neaspec/Desktop/New Folder/data/2012-11-06_09-41-07_camera_Opt_Mic_noZoom.png
2013/06/03 19:35:33 [2387] sending file_sum
2013/06/03 19:35:33 [2387] false_alarms=0 hash_hits=0 matches=0
2013/06/03 19:35:33 [2387] >f..tp.g... 2012-11-06_09-41-07_camera_Opt_Mic_noZoom.png
2013/06/03 19:35:33 [2387] sender finished /home/neaspec/Desktop/New Folder/data/2012-11-06_09-41-07_camera_Opt_Mic_noZoom.png
2013/06/03 19:35:33 [2387] recv_files(1) starting
2013/06/03 19:35:33 [2387] generate_files phase=1
2013/06/03 19:35:33 [2387] recv_files(2012-11-06_09-41-07_camera_Opt_Mic_noZoom.png)
2013/06/03 19:35:33 [2387] recv mapped 2012-11-06_09-41-07_camera_Opt_Mic_noZoom.png of size 676371
2013/06/03 19:35:33 [2387] data recv 32768 at 0
2013/06/03 19:35:33 [2387] data recv 32768 at 32768
2013/06/03 19:35:33 [2387] data recv 32768 at 65536
2013/06/03 19:35:33 [2387] data recv 32768 at 98304
2013/06/03 19:35:33 [2387] data recv 32768 at 131072
2013/06/03 19:35:33 [2387] data recv 32768 at 163840
2013/06/03 19:35:33 [2387] data recv 32768 at 196608
2013/06/03 19:35:33 [2387] data recv 32768 at 229376
2013/06/03 19:35:33 [2387] data recv 32768 at 262144
2013/06/03 19:35:33 [2387] data recv 32768 at 294912
2013/06/03 19:35:33 [2387] data recv 32768 at 327680
2013/06/03 19:35:33 [2387] data recv 32768 at 360448
2013/06/03 19:35:33 [2387] data recv 32768 at 393216
2013/06/03 19:35:33 [2387] data recv 32768 at 425984
2013/06/03 19:35:33 [2387] data recv 32768 at 458752
2013/06/03 19:35:33 [2387] data recv 32768 at 491520
2013/06/03 19:35:33 [2387] data recv 32768 at 524288
2013/06/03 19:35:33 [2387] data recv 32768 at 557056
2013/06/03 19:35:33 [2387] data recv 32768 at 589824
2013/06/03 19:35:33 [2387] data recv 32768 at 622592
2013/06/03 19:35:33 [2387] data recv 21011 at 655360
2013/06/03 19:35:33 [2387] got file_sum
2013/06/03 19:35:33 [2387] rsync: close failed on "/media/Network_Drive/infrared/New Folder/data/.2012-11-06_09-41-07_camera_Opt_Mic_noZoom.png.U1YPZB": Input/output error (5)
2013/06/03 19:35:33 [2387] [receiver] _exit_cleanup(code=11, file=receiver.c, line=752): entered
2013/06/03 19:35:33 [2387] rsync error: error in file IO (code 11) at receiver.c(752) [receiver=3.0.8]
2013/06/03 19:35:33 [2387] [receiver] _exit_cleanup(code=11, file=receiver.c, line=752): about to call exit(11)
2013/06/03 19:35:33 [2387] rsync: connection unexpectedly closed (28 bytes received so far) [sender]
2013/06/03 19:35:33 [2387] [sender] _exit_cleanup(code=12, file=io.c, line=601): entered
2013/06/03 19:35:33 [2387] rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.8]
2013/06/03 19:35:33 [2387] [sender] _exit_cleanup(code=12, file=io.c, line=601): about to call exit(12)
```

I sincerely appreciate all the help guys, thanks for sticking through with this.


EDIT: So I ran```
ls -l /home/neaspec/Desktop/New\ Folder/data
```
All of the folders list "drwxrwxrwx"
THe .png's list              "-rw-rw-rw-"
As I understand, that means, somewhere, the files lost the ability to be "executed"? Which means they can't be opened, or closed. I also do not know what the "d' prefix stands for. Google doesn't seem to be hekping, I also don't exactly know the question to ask...because I do not know what "d" stands for.

---

### Post by bab1 on 2013-06-03
Out of curiosity, what do you get with this command```
ls -l /media/Network_Drive/infrared/New Folder/data/.2012-11-06_09-41-07_camera_Opt_Mic_noZoom.png.U1YPZB
```

The picture is useless to me.  I can't make out what it says.  Try using the *ls *command on that directory from the CLI.  Like this```
ls -l 
```

I just saw your edit.

> So I ran
```
ls -l /home/neaspec/Desktop/New\ Folder/data

```
All of the folders list "drwxrwxrwx"
THe .png's list "-rw-rw-rw-"
As I understand, that means, somewhere, the files lost the ability to be "executed"? Which means they can't be opened, or closed. I also do not know what the "d' prefix stands for. Google doesn't seem to be hekping, I also don't exactly know the question to ask...because I do not know what "d" stands for. 

You don't need the execute bit unless the file is a script or an app the you want to execute.  The "d" stands for directory.

---

### Post by Sanityisboring on 2013-06-04
I found it.
 
 The problem is that my linux machine will not copy files over 100 KB to  the network drive. The two windows machines that write to this network  drive will do so, regardless of file size. The linux machine can also  copy files over 100 KB to anything else, just not the network drive. I'm  assuming there is some sort of exclusion clause on the receiving end of  the server that rejects my linux machine's IP and puts  a cap on my  data trasnfer size. That's the only thing that could be going on right?
 
 I have created a 500 KB png on a windows machine, and copied that to a  thumb drive. I have moved that png onto the linux machine, and attempted  to copy the file. The same input/output error triggers. I can copy that  same png from the windows machine to the network drive fine, and then  open that png in linux. I can also back-copy from the network drive to  the linux machine, regardless of file size. 
 
 When copying the original data folder, all files below 100 KB also copy  fine (which is a couple of the .png, the .txt, and none of the  ascii/dump files)
 
 I emailed the IT guy on the server end and asked him what was up (in slightly more polite terms).

For those of you that followed this thread and provided feedback, thank you. I appreciate all your help in helping me narrow down the problem. I'm marking the thread as solved and calling it a day. Thanks again, and I hope I'm not back here anytime soon ;)

EDIT: I apparently can't mark the thread as solved, but I can tag it solved.

---

