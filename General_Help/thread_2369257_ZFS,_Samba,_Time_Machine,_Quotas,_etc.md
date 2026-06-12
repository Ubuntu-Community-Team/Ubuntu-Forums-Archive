---
title: "ZFS, Samba, Time Machine, Quotas, etc"
date: 2017-08-20
forum: General Help
---

### Post by rnctx on 2017-08-20
I'm surely very bleeding edge with all of this but hey, it's fun to tinker...

I had a FreeBSD NAS for many years specifically for ZFS, but due to FreeBSD (finally) starting to slip in terms of modern goodies (particularly a Dropbox client) I chose to undertake a migration of my data to Linux.

Good news:  ZFS on Ubuntu 16.04 for the past few weeks has been very stable, I have no issues at all.  The migration was a little tedious but once I got grub to work everything was fine.  I was able to migrate the pool from BSD to ZFS-on-Linux successfully.

Now to some more nitty-gritty.  I have OSX machines at home, and I want to use the NAS for time machine backups of course. I also want to eliminate netatalk because, well, netatalk.  Via the patch [here]("https://bugzilla.samba.org/show_bug.cgi?id=12380"), Samba seems to work fine for this purpose. I built Samba from 4.7.x sources with that time machine patch and my OSX machines see the Time Machine share I set up and my desktop is backing up to it now.

The only hurdle left is quotas and I'm not sure what's supported on that front, I'm hoping someone can tell me.  As of now, I have dataset/home as a dataset within my pool, because all of the data I migrated from BSD were in user home folders.  I have set up my time machine user with a typical /home/timemachineuser folder and mapped the unix user to my OSX username via a Samba user map.  The problem is quotas.  I defined a user quota on the ZFS dataset for timemachineuser but Samba doesn't seem to pick that up, on my OSX machine I see a 10 TB disk with 3.6 TB available after giving the user I logged in as a 1 TB limit.  I have no doubt that ZFS will properly enforce that quota but if OSX doesn't see it, I suspect bad things will happen. OSX does not have client-side limitations for time machine backups, it assumes that the server enforces a quota on each user and adjusts its backup rotation to match space available on the remote volume.

What does Samba support on Linux in this capacity?  Since Time Machine support in Samba is quite new (not even merged into stable releases yet), I don't expect to see a lot of features there, but I was hoping that by now Samba would support a good bit of the underlying ZFS features on Linux.  Although userquotas seems to not be one of them if my OSX desktop's time machine config is any indication...

Anyone else done this?

---

### Post by TheFu on 2017-08-21
Uh ... doesn't ZFS have a native CIFS implementation?  Why bother with Samba?

I don't know anything about Time Machine, but seems like NFS would be a better solution, since it supports native Unix file system features - ownership, groups, permissions, ACLs, xattrs, etc.

Samba is the lowest of all network file sharing protocols today.  Always prefer NFS over it.

---

### Post by rnctx on 2017-08-21
I haven't done it personally, but from initial reading up, it seems that while the OSX time machine client may work over NFS, it's not trivial to set up.  Up until recent releases of OSX Apple was foolishly trying to push AFP by only allowing time machine to work over that protocol, but as of a couple of versions ago they (Apple) have abandoned it in favor of SMB, so Samba is the most obvious solution to using the OSX-included time machine client seamlessly.

Answering my own question a bit in case anyone else stumbles on this: I could not find any documentation on ZFS userquotas being supported by Samba in any way.  However, it is trivial to simply create new datasets with quotas in ZFS, so I did that and the OSX client sees the quota that way.  I simply moved the existing files for my time machine user, made a dataset/home/timemachine dataset with a 1TB quota, and then moved the files back into that new dataset.  Now the client on OSX sees the remote file system as being 1TB in total capacity.

To do all of this, patch the current Samba source (I'm using 4.7.x) with [the patch in this thread]("https://bugzilla.samba.org/show_bug.cgi?id=12380"), use the settings in [this gist]("https://gist.github.com/ChloeTigre/4c2022c0d1a281deedba6f7539a2e3ae") or some similar variation to advertise the Samba share on your network with avahi, and set up a user for it to use.  In my case, I set 'valid users' under the time machine Samba share to the timemachine user, specified a 'username map' in the Samba config (/etc/samba/smbusers works fine) and in smbusers specified timemachineuser = "MyOSXFirstName MyOSXLastName"

Finally, su to your timemachine user on the server, run smbpasswd, and specify the password you want.  Then you can log in to the time machine client in OSX with your OSX credentials and it should be off and running.

---

### Post by Morbius1 on 2017-08-21
Bless you for this. I was asked something similar in my part of the asylum and went down a rat hole using the samba "vfs object" of default_quota. Didn't get very far but my unfamiliarly of using that parameter and ZFS was the probable cause. I will point that user to your post. Thank You.

I do have one question. I can't seem to follow your gist link - it just never connects. Is it just an avahi samba service announcement like this:
> cat /etc/avahi/services/samba.service

<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   <name replace-wildcards="yes">SMB %h</name> ## Display Name
   <service>
       <type>_smb._tcp</type>
       <port>445</port>
   </service>
</service-group>


Or is it something more elaborate?

---

### Post by rnctx on 2017-08-21
> **Morbius1 said:**
> Bless you for this. I was asked something similar in my part of the asylum and went down a rat hole using the samba "vfs object" of default_quota. Didn't get very far but my unfamiliarly of using that parameter and ZFS was the probable cause. I will point that user to your post. Thank You.

I do have one question. I can't seem to follow your gist link - it just never connects. Is it just an avahi samba service announcement like this:

Or is it something more elaborate?

Quote from the [linked gist]("https://gist.github.com/ChloeTigre/4c2022c0d1a281deedba6f7539a2e3ae")


avahi service:

```

[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
 <name replace-wildcards="yes">%h</name>
 <service>
   <type>_adisk._tcp</type>
   <txt-record>sys=waMa=0,adVF=0x100</txt-record>
   <txt-record>dk0=adVN=Time Capsule,adVF=0x82</txt-record>
 </service>
  <service>
    <type>_smb._tcp</type>
    <port>445</port>
  </service>
</service-group>[/TD]
[/TR]
[/TABLE]


```

smb.conf:
[COLOR=#24292E][FONT=-apple-system]
[/FONT][/COLOR]```

[global]


wins support = yes
workgroup = WORKGROUP
netbios name = SAMBA
vfs objects = acl_xattr fruit
map acl inherit = yes
store dos attributes = yes
security = user
passdb backend = tdbsam
guest ok = no
read only = no


# Time Machine
durable handles = yes
kernel oplocks = no
kernel share modes = no
posix locking = no
fruit:advertise_fullsync = true
smb2 leases = yes


# Security




client ipc max protocol = default
client max protocol = default
server max protocol = SMB3


client ipc min protocol = default
client min protocol = CORE
server min protocol = SMB2




[Time Capsule]


path = /home/targetfolder
browseable = Yes
vfs objects = catia fruit streams_xattr
fruit:aapl = yes
read only = No
inherit acls = Yes

```

To mirror credentials from OSX in smb.conf:

```


[global]
username map = /etc/samba/smbusers

[Time Capsule]
valid users = timemachine

```

smbusers: 

```

timemachine = "John Public"

```

... (and then smbpasswd when logged in as timemachine to set a pass) will work for mirroring the credentials on OSX.  The share will show up in the time machine client, all the user has to do is click and log in with their OSX credentials.

However, as I mentioned, there is apparently sparse support in Samba for ZFS quota settings.  I have verified that it is **not** aware of userquotas on existing datasets, unless there is a config setting I am unaware of.  If you wish to use a quota you have to make a new dataset with a **volume** quota. You can do so by moving the data out of the target folder, deleting the target folder, and then...

```


sudo zfs create datapool/home/targetfolder
sudo zfs set quota=750G datapool/home/targetfolder
chown timemachine /home/targetfolder
chgrp timemachinegroup /home/targetfolder


```

... and then moving the data back. No need to remount or reboot, ZFS delivers on its promises of dynamic file systems ;).  The above will give you a 750 gb volume for the time machine client to use.  Adjust to taste.

Then you may uninstall netatalk and bask in the glory of it never filling your logwatch email with its unpatched, unmaintained dbus errors ever again.

---

### Post by Morbius1 on 2017-08-21
Excellent. Thank you so much.

---

