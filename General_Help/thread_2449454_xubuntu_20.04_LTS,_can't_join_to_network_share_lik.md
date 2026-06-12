---
title: "xubuntu 20.04 LTS, can't join to network share like i used to"
date: 2020-08-26
forum: General Help
---

### Post by cdoublejj on 2020-08-26
this or something very similar worked to mount my network share. i can't get it to work. i'm loosing my mind!!!

> //192.168.1.8/ProRaid /media/user/ProRaid cifs username=<administrator>,password=<passwordhere>,uid=1000,gid=1000,iocharset=utf8,sec=ntlm,users 0 0

it tries to work but, errors and says the directory does not exist when i try to open up the mounted folder.

---

### Post by TheFu on 2020-08-27
What s the client machine and what is the server machine running?
Samba defaults have changed, which could be the issue.

A quick thing to try is removing the _sec=ntlm_ option.  For better security, putting the userid and password nto a credentials file would be better too.

If the client and server are linux/unix, using nfs is recommended.

---

### Post by cdoublejj on 2020-08-27
putting them in creds file is over my head/skill set. this is one of  those cases where ther GUI fails you have to use CLI which really sucks.

windows server 2019 is hosting the file share, client is xubuntu 20.04 LTS


i got a new error after remving netsec,

[COLOR=unset][img]https://i.imgur.com/A71KARZ.png[/img][IMG]https://imgur.com/a/LaYZ2AD[/IMG][/COLOR]

---

### Post by TheFu on 2020-08-27
I don't have the skill to help. Haven't touched any Windows newer than Win7, but there are other threads in these forums.

Want to access a Windows Share from Linux? In short, seems that  Win10 disables NetBIOS and using a manual CIFS is necessary.
Morbius1's instructions:
[https://ubuntuforums.org/showthread.php?t=2435292&p=13925468#post13925468](https://ubuntuforums.org/showthread.php?t=2435292&p=13925468#post13925468)

From the mount.cifs manpage:
```
credentials=filename|cred=filename
       specifies  a  file  that contains a username and/or password and
       optionally the name of the workgroup. The format of the file is:

          username=value
          password=value
          domain=value

       This is preferred over having passwords in plaintext in a shared
       file,  such  as  /etc/fstab . Be sure to protect any credentials
       file properly.
```
Since I don't have any Windows-Domain, I've never used that in the credentials= file.
```
username=thefu
password=my-LEET-password$@$992343%6

```
Anything after the first '=' character. Don't have spaces. I don't know how those are handled.  Whatever the file is names, set the permissions to 600 root:root and place into a protected directory to other users can't view it.

---

### Post by cdoublejj on 2020-09-10
you can do with the username and password in the fstab file for simplcitiy if you choose.

i'm having the same problem with ubuntu server 20.04 LTS and unraid and neither are windows

---

### Post by TheFu on 2020-09-10
For connecting non-Windows storage, I use NFS. It always works, is usually faster, and honors Unix permissions across all systems.
[https://ubuntu.com/server/docs/service-nfs](https://ubuntu.com/server/docs/service-nfs)

The mount in the fstab for the client is pretty easy too.
```
istar:/TV   /TV  nfs    proto=tcp,intr,rw,async  0 2
```

The only trick is that the uid/gid for any files/directories on the storage should be the same for all clients. See the uid/gid by using the 'id' command.

I'd only use CIFS/Samba when Windows was involved.

---

### Post by cdoublejj on 2020-09-11
> **TheFu said:**
> For connecting non-Windows storage, I use NFS. It always works, is usually faster, and honors Unix permissions across all systems.
[https://ubuntu.com/server/docs/service-nfs](https://ubuntu.com/server/docs/service-nfs)

The mount in the fstab for the client is pretty easy too.
```
istar:/TV   /TV  nfs    proto=tcp,intr,rw,async  0 2
```

The only trick is that the uid/gid for any files/directories on the storage should be the same for all clients. See the uid/gid by using the 'id' command.

I'd only use CIFS/Samba when Windows was involved.

i'm not sure i understand the wording there. i'm simply trying to mount my unraid to my VM hosting an nextcloud SNAP. what if the nextcloud runs on a user level different than the user account? what about the file permissions nextclud might apply to the files? or would they only be applied as the user nextcloud runs under?

Agreed but, NFS is old and it's broken on unraid, limetech's answer is to use SMB.  [URL="https://forums.unraid.net/bug-reports/prereleases/680-rc3remote-nfs-shares-disappearingdying-randomly-r676/?do=findComment&comment=6388"]https://forums.unraid.net/bug-reports/prereleases/680-rc3remote-nfs-shares-disappearingdying-randomly-r676/?do=findComment&comment=6388


[/URL]

---

