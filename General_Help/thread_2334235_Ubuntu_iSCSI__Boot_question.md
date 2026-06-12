---
title: "Ubuntu iSCSI / Boot question"
date: 2016-08-17
forum: General Help
---

### Post by bmmikee on 2016-08-17
To preface, my Linux knowledge is low but I'm trying to learn by jumping in.

Version:
```
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:        16.04
Codename:       xenial
```



First off, I followed the guide located @ [https://help.ubuntu.com/lts/serverguide/iscsi-initiator.html](https://help.ubuntu.com/lts/serverguide/iscsi-initiator.html) and listed below
```

sudo apt install open-iscsi
node.startup = automatic
sudo iscsiadm -m discovery -t st -p 192.168.2.199

```

I ran the below command to connect to my LUN:
```
sudo iscsiadm --mode node --targetname iqn.2000-01.com.synology:media.a0fbbd6e84 --portal 192.168.2.199 --login
```

The disk connects with no issues, I mounted it and partitioned it to ext4.  I have had no issues with the disk / using the disk.  

My questions:
1.  What is the proper way to connect this disk on boot?  My boots seem to take a long time now and as you can see by the screenshot below, I get an error but when it does finally boot, the LUN is mounted with no issue.

2.  Is there a way to make it only connect to ONE target?  I have the target listed above but I feel like its trying to automatically connect to all targets for some reason, and it fails.

fstab file:
```
UUID=1e9fdeb1-ae68-4dad-b6af-04177e7a7e8b       /media/disk3   ext4    defaults,auto,_netdev 0 0
```

Screenshot of boot:
[IMG]http://i.imgur.com/wdVAalV.jpg[/IMG]

---

### Post by bduguid on 2016-09-25
Hi bmmikee,

Have you figured this out?

I configured a target on my Synology. The discovery shows the same target with an IPv4 and a IPv6 and treats them as different targets.  I configured a password on the Synology side, but only configured a password for the IPv4 target on the Ubuntu side. My thought was that I could specify which one I want to login into, but I haven't figured out if that key/value pair exists.

```
[COLOR=#000000][FONT=Arial]sudo iscsiadm -m node --targetname "iqn.2016-09.com.example:MyNAS:MyHost-01" --portal "192.168.1.10:3260" --op=update --name node.session.auth.authmethod --value=CHAP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo iscsiadm -m node --targetname "iqn.2016-09.com.example:MyNAS:MyHost-01" --portal "192.168.1.10:3260" --op=update --name node.session.auth.username --value=myhost[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo iscsiadm -m node --targetname "iqn.2016-09.com.example:MyNAS:MyHost-01" --portal "192.168.1.10:3260" --op=update --name node.session.auth.password --value=targetmyhost01[/FONT][/COLOR]
```

It logs in just fine to the target with the CHAP credentials, but the logs show that 120 seconds was spent waiting for a login to IPv6 and then fails.

---

### Post by bduguid on 2016-09-25
I believe I got it.

I made sure my discoverydb was empty.
[COLOR=#000000][FONT=Arial]I left[/FONT][/COLOR] [COLOR=#000000][FONT=Arial]node.startup = manual in [/FONT][/COLOR][COLOR=#000000][FONT=Arial]/etc/iscsi/iscsid.conf.

[/FONT][/COLOR]```
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]sudo iscsiadm -m node --targetname "iqn.2016-09.com.example:MyNAS:MyHost-01" --portal "192.168.1.10:3260" --op=update --name node.startup --value=automatic
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

