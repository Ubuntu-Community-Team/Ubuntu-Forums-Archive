---
title: "Client Pc to NFS Server"
date: 2012-11-26
forum: General Help
---

### Post by BStrizzy on 2012-11-26
Hey guys, I just exported a file directory from my sever to be shared to my personal laptop. I used the single host option and entered in my ip address and I think I did everything correct on the export side via webmin. 
The code I am using on my side via shell is   
 sudo mount 192.168.1.7: /home/bstrizzy/music  /home/bstrawt/Music

and i keep getting this 
```

Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mo
```
 and pretty much the whole help text

what is going on?:confused:

---

### Post by rnerwein on 2012-11-27
> **BStrizzy said:**
> Hey guys, I just exported a file directory from my sever to be shared to my personal laptop. I used the single host option and entered in my ip address and I think I did everything correct on the export side via webmin. 
The code I am using on my side via shell is   
 sudo mount 192.168.1.7: /home/bstrizzy/music  /home/bstrawt/Music

and i keep getting this 

```

Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mo
```
 and pretty much the whole help text

what is going on?:confused:

mount[COLOR=Red] -t nfs[/COLOR] ..........   ..........

---

### Post by BStrizzy on 2012-11-27
> **rnerwein said:**
> mount[COLOR=Red] -t nfs[/COLOR] ..........   ..........


**Mounts**

  
**Check to see if everything works**

 You should try and mount it now. The basic template you will use is: 
**sudo mount ServerIP:**/folder/already/setup/to/be/shared /home/username/folder/in/your/local/computerso for example: ****
****
**sudo mount 192.168.1.42:/home/music /home/poningru/music**


from ubuntu thread [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
[B]
might need to update this![/B]

---

### Post by BStrizzy on 2012-12-02
> **rnerwein said:**
> mount[COLOR=Red] -t nfs[/COLOR] ..........   ..........


this does not work help!! I am trying to mount my home music folder on ubuntu desktop to my music on my server. i keep getting the index when i use this too. i try this in both my shell on desktop and on my ssh

---

### Post by SeijiSensei on 2012-12-02
> sudo mount 192.168.1.7: /home/bstrizzy/music /home/bstrawt/Music


It appears you have a space between the colon and /home.  Remove it.

And you do not need to specify the filesystem type with -t for NFS mounts.  The mount command deduces it is an NFS mount when it encounters the "server:/share" syntax.

---

### Post by BStrizzy on 2012-12-02
> **SeijiSensei said:**
> It appears you have a space between the colon and /home.  Remove it.

And you do not need to specify the filesystem type with -t for NFS mounts.  The mount command deduces it is an NFS mount when it encounters the "server:/share" syntax.

by file system you mean?

---

### Post by rnerwein on 2012-12-02
> **BStrizzy said:**
> by file system you mean?
good morning
i just looked at your weblink and saw the "-t" option has changed from "nfs" to "nfs4".
try: mount -t nfs4 ......  ......
good luck

P.S. man pages told me: [COLOR=Red]nfs4 [/COLOR]is deprecated. -t nfs must be ok

---

### Post by SeijiSensei on 2012-12-02
> **BStrizzy said:**
> by file system you mean?

Things like ext4, ntfs, nfs, smbfs, etc., etc.  All the different types of, well, "filesystems" that Linux supports. From the manual page for mount ("man mount"):

> 
      -t, --types vfstype
The argument following the -t is used to indicate the filesystem type.   The  filesystem  types  which  are  currently  supported include: adfs,  affs,  autofs,  cifs,  coda,  coherent,  cramfs, debugfs, devpts, efs, ext, ext2, ext3, ext4, hfs, hfsplus, hpfs, iso9660, jfs, minix, msdos, ncpfs, nfs, nfs4, ntfs, proc,  qnx4, ramfs,  reiserfs,  romfs,  squashfs,  smbfs, sysv, tmpfs, ubifs, udf, ufs, umsdos, usbfs, vfat, xenix,  xfs,  xiafs.


Did removing the space fix your problem?

---

### Post by BStrizzy on 2012-12-02
> **SeijiSensei said:**
> Things like ext4, ntfs, nfs, smbfs, etc., etc.  All the different types of, well, "filesystems" that Linux supports. From the manual page for mount ("man mount"):



Did removing the space fix your problem?

it did not fix my problem, but when i added the 4 after nfs4, it seemed to work a little better.

bstrawt@panama:~$ sudo mount -t nfs4 192.168.1.7:/home/bstrizzy/music /home/bstrawt/music
mount.nfs4: mounting 192.168.1.7:/home/bstrizzy/music failed, reason given by server:
  No such file or directory

the file I am trying to link is the file on my server with a music file on my home directory, do i need to put my desktop ipaddress before the destination mount? I tried that and it still didnt work. I will copy and paste my set up via webmin.

is my ipv4 network suppose to be 192.168.1.0 or 192.168.1.1 or 192.168.1.0/8 ? maybe this is the issue? see pic attached

---

### Post by BStrizzy on 2012-12-02
> **rnerwein said:**
> good morning
i just looked at your weblink and saw the "-t" option has changed from "nfs" to "nfs4".
try: mount -t nfs4 ......  ......
good luck

P.S. man pages told me: [COLOR=Red]nfs4 [/COLOR]is deprecated. -t nfs must be ok


it did not fix my problem, but when i added the 4 after nfs4, it seemed to work a little better.

bstrawt@panama:~$ sudo mount -t nfs4 192.168.1.7:/home/bstrizzy/music /home/bstrawt/music
mount.nfs4: mounting 192.168.1.7:/home/bstrizzy/music failed, reason given by server:
  No such file or directory

the  file I am trying to link is the file on my server with a music file on  my home directory, do i need to put my desktop ipaddress before the  destination mount? I tried that and it still didnt work. I will copy and  paste my set up via webmin.

is my ipv4 network suppose to be 192.168.1.0 or 192.168.1.1 or 192.168.1.0/8 ? maybe this is the issue?

---

### Post by SeijiSensei on 2012-12-02
Post the contents of the server's /etc/exports file in [noparse]```

```[/noparse] tags.

---

### Post by BStrizzy on 2012-12-02
> **SeijiSensei said:**
> Post the contents of the server's /etc/exports file in [noparse]```

```[/noparse] tags.

bstrawt@panama:/etc$ cd /etc/exports
bash: cd: /etc/exports: No such file or directory

it says i do not have a /etc/exports, i just went down the list and couldnt find it either. have you checked the picture that I posted?

---

### Post by SeijiSensei on 2012-12-02
/etc/exports is a file, not a directory.  Display it onscreen with "more /etc/exports" or "cat /etc/exports".

---

### Post by BStrizzy on 2012-12-02
> **SeijiSensei said:**
> /etc/exports is a file, not a directory.  Display it onscreen with "more /etc/exports" or "cat /etc/exports".


bstrizzy@nova:~$ more /etc/exports
# /etc/exports: the access control list for filesystems which may be exported
#        to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subt
ree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/export    (insecure,no_subtree_check,rw,nohide,fsid=0)
/export/music    192.168.1.0/255.255.255.0(no_root_squash,rw,nohide)
bstrizzy@nova:~$ 

^ this is my server ssh

---

### Post by SeijiSensei on 2012-12-02
That says the only exported directories are /export and /export/music.  You're trying to mount a directory that isn't being shared via NFS.  You'd need to have an entry for /home/bstrizzy/music in the exports file, or perhaps export the entire /home tree,

You could mount /export/music by replacing /home/bstrizzy/music with /export/music, though I have obviously have no idea whether the files you want are in that directory.

---

### Post by BStrizzy on 2012-12-03
> **SeijiSensei said:**
> That says the only exported directories are /export and /export/music.  You're trying to mount a directory that isn't being shared via NFS.  You'd need to have an entry for /home/bstrizzy/music in the exports file, or perhaps export the entire /home tree,

You could mount /export/music by replacing /home/bstrizzy/music with /export/music, though I have obviously have no idea whether the files you want are in that directory.

ok I changed the export name /home/bstrizzy/music which is my server directory and i tried sending it to my desktop directory and did not work. 

bstrawt@panama:~$ sudo mount -t nfs4 192.168.1.7:/home/bstrizzy/music/mp3 /home/bstrawt/Music
mount.nfs4: mounting 192.168.1.7:/home/bstrizzy/music/mp3 failed, reason given by server:
  No such file or directory
bstrawt@panama:~$ 

i entered this on my desktop ssh terminal, this is the correct way to do it right?

---

### Post by SeijiSensei on 2012-12-03
You can only mount directories as they appear in /etc/exports, so remove the /mp3 at the end and try again.

However you may still run into a permissions problem if you try to mount /home/bstrizzy while logged into the client as /home/bstrawt.  You can get around some of these issues by using "no_root_squash" in the options list in /etc/exports and mounting the directory as root with sudo on the client.

Have you read this?  
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by BStrizzy on 2012-12-03
> **SeijiSensei said:**
> You can only mount directories as they appear in /etc/exports, so remove the /mp3 at the end and try again.

However you may still run into a permissions problem if you try to mount /home/bstrizzy while logged into the client as /home/bstrawt.  You can get around some of these issues by using "no_root_squash" in the options list in /etc/exports and mounting the directory as root with sudo on the client.

Have you read this?  
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

yeah i have read that, and the mp3 is at the end of the real file, it is where all my mp3s are actually located.

---

### Post by BStrizzy on 2012-12-03
> **BStrizzy said:**
> yeah i have read that, and the mp3 is at the end of the real file, it is where all my mp3s are actually located.

i have updated it to just /exports/music and deleted the mp3 part but for some reason it keeps telling me no such file or directory? I am suppose to do the code on my desktop ubuntu right?

---

### Post by borjamf on 2012-12-04
Check this:

- First, you have to bind the *real *directory on your server with the *pseudo *directory that you'll export to the client. For example:
    Directory on the server: /home/music
    Directory to export: /export/music
    Binding the directories: [I]mount bind -t /home/music /export/music

- [/I]Edit the /etc/exports file. Here is where you write the directory to share with the client.     
    ```
/export ipclient(rw,fsid=0,no_subtree_check,sync)
              /export/music ipclient(rw,no_subtree_check,sync,nohide)
    
```- Edit the /etc/fstab file and add this line, so you do not have to bind the directories every time when you reboot:
```
 /home/music /export/music   none    bind  0  0
```- Now, go to the Client, edit the /etc/default/nfs-common ([https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)).

- On the client, *mount -t nfs4 IPSERVER:/music /director*y/example/client

CHECK if you have the directory /directory/example/client created.

---

### Post by BStrizzy on 2012-12-04
> **borjamf said:**
> Check this:

- First, you have to bind the *real *directory on your server with the *pseudo *directory that you'll export to the client. For example:
    Directory on the server: /home/music
    Directory to export: /export/music
    Binding the directories: [I]mount bind -t /home/music /export/music

- [/I]Edit the /etc/exports file. Here is where you write the directory to share with the client.     
    ```
/export ipclient(rw,fsid=0,no_subtree_check,sync)
              /export/music ipclient(rw,no_subtree_check,sync,nohide)
    
```- Edit the /etc/fstab file and add this line, so you do not have to bind the directories every time when you reboot:
```
 /home/music /export/music   none    bind  0  0
```- Now, go to the Client, edit the /etc/default/nfs-common ([https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)).

- On the client, *mount -t nfs4 IPSERVER:/music /director*y/example/client

CHECK if you have the directory /directory/example/client created.

bstrizzy@nova:~$ sudo mount bind -t /home/music /export/music
mount: unknown filesystem type '/home/music'
bstrizzy@nova:~$ sudo mount bind -t /home/bstrizzy/music /export/music
mount: unknown filesystem type '/home/bstrizzy/music'

whyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy

---

### Post by LewisTM on 2012-12-04
The correct syntax is 
```
sudo mount -o bind /home/bstrizzy/music /export/music
```
/export/music must exists.

That being said, this is overly complicated for a simple setup. Just export 
**/home/bstrizzy/music *(rw,no_subtree_check,no_root_squash)**
Reload the NFS config with
```
sudo exportfs -ra
```
Then on your client, mount the share (**no need** for -t nfs4)
```
sudo mount 192.168.1.7:/home/bstrizzy/music /home/bstrawt/Music
```

To make it permanent in /etc/fstab, add this line
```
192.168.1.7:/home/bstrizzy/music /home/bstrawt/Music nfs defaults 0 0
``` 
Cheers!

---

### Post by BStrizzy on 2012-12-04
> **LewisTM said:**
> The correct syntax is 
```
sudo mount -o bind /home/bstrizzy/music /export/music
```/export/music must exists.

That being said, this is overly complicated for a simple setup. Just export 
**/home/bstrizzy/music *(rw,no_subtree_check,no_root_squash)**
Reload the NFS config with
```
sudo exportfs -ra
```Then on your client, mount the share (**no need** for -t nfs4)
```
sudo mount 192.168.1.7:/home/bstrizzy/music /home/bstrawt/Music
```To make it permanent in /etc/fstab, add this line
```
192.168.1.7:/home/bstrizzy/music /home/bstrawt/Music nfs defaults 0 0
```Cheers!

yes this does seem over complicated, but now i got the bind and i get an access denied by server error. check my attatchments. the terminal in nano is the server

---

### Post by LewisTM on 2012-12-04
I don't see any attachment.
Add **insecure** to your export options, then reload the NFS config with [FONT="Courier New"]sudo exportfs -ra[/FONT]. That usually fixes it.

---

### Post by BStrizzy on 2012-12-04
> **LewisTM said:**
> I don't see any attachment.
Add **insecure** to your export options, then reload the NFS config with [FONT=Courier New]sudo exportfs -ra[/FONT]. That usually fixes it.
  whoops =) there ya go

---

### Post by LewisTM on 2012-12-04
Try these lines in your /etc/exports
```
/export 192.168.1.0/255.255.255.0(insecure,rw,fsid=0,nohide,no_subtree_check,sync)
/export/music 192.168.1.0/255.255.255.0(insecure,rw,no_subtree_check,nohide,sync)
```

---

### Post by BStrizzy on 2012-12-04
> **LewisTM said:**
> Try these lines in your /etc/exports
```
/export 192.168.1.0/255.255.255.0(insecure,rw,fsid=0,nohide,no_subtree_check,sync)
/export/music 192.168.1.0/255.255.255.0(insecure,rw,no_subtree_check,nohide,sync)
```

same error

---

### Post by SeijiSensei on 2012-12-05
> **BStrizzy said:**
> bstrizzy@nova:~$ sudo mount bind -t /home/music /export/music
mount: unknown filesystem type '/home/music'

whyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy

Because you're not paying careful attention to the syntax people are suggesting here.  The -t parameter expects a filesystem from that long list I gave you earlier.  This has been a persistent issue in this thread.

---

### Post by rnerwein on 2012-12-05
> **BStrizzy said:**
> same error
hello
it's a long to work with nfs. therefore you will find in the attachment instructions for you.
this example works (sure) on a server running ubuntu 12.04.1 and the client is Ubuntu 10.04.
much luck

---

### Post by BStrizzy on 2012-12-15
> **rnerwein said:**
> hello
it's a long to work with nfs. therefore you will find in the attachment instructions for you.
this example works (sure) on a server running ubuntu 12.04.1 and the client is Ubuntu 10.04.
much luck


awesome man, just checked this out and its a charm. Appreciate it!

---

