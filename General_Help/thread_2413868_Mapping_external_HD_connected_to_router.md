---
title: "Mapping external HD connected to router"
date: 2019-03-03
forum: General Help
---

### Post by cAlpha on 2019-03-03
I'm trying make the contents of an external HD accessible to users on my wireless network.  

I've adjusted router settings and am able to access contents of the connected HD via the Ubuntu file explorer by hitting Ctrl + L and entering the following:
```
smb://192.168.0.1/
```

I can see the drive and drill down to access its contents.  

I'd like to mount this drive, ideally automatically at startup.  

I've created a mount point using 
```
sudo mkdir /media/chris
```

And then tried to assign my network drive to the mount point as such
```
sudo mount -t "smb://192.168.0.1/volume(sda2)" /media/chris
```

Which gives the error
```
mount: /media/chris: can't find in /etc/fstab.
```

It isn't clear to me why my mount point needs to be included in the fstab flie when I'm doing this explicitly.  


I'd ultimately like to set this up to mount automatically at startup.  How do I set that up given my current set up?

---

### Post by TheFu on 2019-03-03
My I suggest reconsideration in using a WAN router to share storage unless the intent is to share the files with the entire world.  Pretty much every WAN router with this capability has had multiple security failures leading to unintended sharing.

The correct format of the mount command isn't what you have there. Using non-standard characters in the mount is asking for trouble. Also, trying to mount to /media/{userid}/ breaks other automatic mounts.  Best to mount elsewhere - either deeper or somewhere outside /media/ completely.
Here is the script that I use to mount CIFS storage:
```
#!/bin/sh
USERID="thefu"
MNT_PNT=/Data/mybook

if [ ! -e $MNT_PNT ] ; then
     mkdir $MNT_PNT
     chown $USERID:$USERID $MNT_PNT
fi
 mount -t cifs //192.168.34.8/mybook $MNT_PNT  -o rw,uid=$USERID
```
Run the script with **sudo**. If login credentials are needed to access the storage, you'd want to use the credentials= option. From the mount.cifs manpage:```

       credentials=filename
           specifies a file that contains a username and/or password and optionally the name of the workgroup. The
           format of the file is:

                         username=value
                         password=value
                         domain=value

           This is preferred over having passwords in plaintext in a shared file, such as /etc/fstab. Be sure to
           protect any credentials file properly.

```

The format of cifs mounts in the fstab is different still.  CIFS/SMB is meant to be userid -to- server mounts, not server to server. The same options are used, just within the fstab format.  [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently) has more details than you can probably stand.  ```

//servername/sharename  /media/windowsshare  cifs  guest,uid=1000,iocharset=utf8  0  0
```
The only real trick is not to have any spaces between options. In both these methods, the options cannot have spaces.

---

### Post by cAlpha on 2019-03-04
This is helpful, thanks.  

Couple follow-up questions:

(1)  Your reference to WAN has to do with me using the default IP as the connection point?  
(2)  I don't see an option to change the volume name within my router's options, and it was created by default when I set it up.  Is this something I can do at the command line or otherwise?

As to security, being that all users are within the LAN, I didn't think I'd need it (since getting access would require getting access to the router itself).  Are there good reasons to add security to the drive itself?

---

### Post by gsahli on 2019-03-04
One small question - is your username chris? You would need a mountpoint like /media/chris/smb_drive or similar. The way you were attempting will interfere with automount of external drives (like USB). TheFu was getting at this, too, but didn't ask for clarification.

---

### Post by TheFu on 2019-03-04
> **cAlpha said:**
> This is helpful, thanks.  

Couple follow-up questions:

(1)  Your reference to WAN has to do with me using the default IP as the connection point?  
No. My point was that WAN routers - the one protecting your LAN from the internet should never, ever, ever, have storage connected to them unless you want the entire world to have access to that storage.  Routers have bugs and sharing of connected storage has been a bug in almost every router made, multiple times, even have so-called "fixes."  IMHO, it is a terrible idea.  That was my point, but I was trying to be nice about it. Not blunt.  When I'm blunt, people are unhappy, usually.

> **cAlpha said:**
> 
(2)  I don't see an option to change the volume name within my router's options, and it was created by default when I set it up.  Is this something I can do at the command line or otherwise? I have no idea. I don't connect storage to WAN routers, especially after seeing all the major brands and aftermarked firmwares have security failures in that area over the years.

> **cAlpha said:**
> 
As to security, being that all users are within the LAN, I didn't think I'd need it (since getting access would require getting access to the router itself).  Are there good reasons to add security to the drive itself?

You've lost me.  Security is always important.  Via javascript, any remote server gains access to your LAN thanks to any web browser that allows javascript to run.  Javascript is a full network programming  language. This has liabilities and risks for security. I think that allowing javascript to run when visiting any remote website if foolish. 
Think about it for a second. Javascript is a scripted language that our browsers download and run.  The browsers protect against access of the javascript to the machine where it is running, but it cannot protect against any network scans, network commands or network requests towards different machines, either on the LAN or on any other network which can be accessed.  Here's an example scanner. [https://defuse.ca/in-browser-port-scanning.htm](https://defuse.ca/in-browser-port-scanning.htm) with an interface we control.  It would be trivial to have every port scanned for every address on the LAN and transmit that data anywhere over an encrypted https connection.  All the bad guys need to do is get anyone on the LAN to visit 1 webpage.

---

### Post by Morbius1 on 2019-03-04
> **cAlpha said:**
> 
And then tried to assign my network drive to the mount point as such
```
sudo mount -t "smb://192.168.0.1/volume(sda2)" /media/chris
```

Which gives the error
```
mount: /media/chris: can't find in /etc/fstab.
```

It isn't clear to me why my mount point needs to be included in the fstab flie when I'm doing this explicitly.  

You have a wee bit of work to do there.

[1] Your mount command is syntactically incorrect - you didn't specify the type of mount and there is no "smb" in the command. It should look something like this:
```
sudo mount -t cifs "//192.168.0.1/volume(sda2)" /media/chris
```
[COLOR=#0000cd]*** The assumption here is that "volume(sda2)" is actually the entity that was shared and not a folder under it.
*** And I would use another mount point ... like /media/Router

[/COLOR][COLOR=#000000][2] Converting that to an fstab entry requires some finger exercises because of the parentheses in the share name.[/COLOR][COLOR=#0000cd]

[/COLOR][COLOR=#000000]A ( is represented by a \050 in fstab.
A ) is represented by a \051 in fstab

So volume(sda2) looks like this in fstab: volume**\050**sda2[B]\051
[/B]
And the line in fstab would look something like this:
```
//192.168.0.1/volume**\**050sda2**\**051 /media/Router cifs guest,uid=1000,nounix 0 0
```

I would suggest you get the manual mount correct before adding anything to fstab.
[/COLOR]

---

### Post by TheFu on 2019-03-04
Using funny characters, anything that isn't alpha-numeric, can be problematic. As usual, Morbius1 cuts to the very important detail.

I would be surprised if using the normal escape character, \, wouldn't work inside the fstab.
```
//192.168.0.1/volume\(sda2\) /media/Router cifs guest,uid=1000,nounix 0 0
```
but I didn't test it.  I've never needed to use octal or hex encoding for mounts, ever.

Also, whether an IP address or hostname can be used comes down to whether name resolution is setup and/or working by the different clients and servers on the network.  IP addresses are always safe, assuming that the devices have a static IP. A router should.

[https://www.makeuseof.com/tag/router-security-risk-fix/](https://www.makeuseof.com/tag/router-security-risk-fix/) - from 2014, but still valid.
[https://arstechnica.com/information-technology/2018/05/hackers-infect-500000-consumer-routers-all-over-the-world-with-malware/](https://arstechnica.com/information-technology/2018/05/hackers-infect-500000-consumer-routers-all-over-the-world-with-malware/) - 2018
[https://www.tomsguide.com/us/russian-router-malware,news-27288.html](https://www.tomsguide.com/us/russian-router-malware,news-27288.html)
[https://securityaffairs.co/wordpress/63724/hacking/netgear-security-advisories.html](https://securityaffairs.co/wordpress/63724/hacking/netgear-security-advisories.html) - Netgear
[https://securityzap.com/d-link-vulnerability-allows-remote-hacking/](https://securityzap.com/d-link-vulnerability-allows-remote-hacking/)  - DLink
[https://www.networkworld.com/article/2984124/attackers-can-take-over-cisco-routers-other-routers-at-risk-too.html](https://www.networkworld.com/article/2984124/attackers-can-take-over-cisco-routers-other-routers-at-risk-too.html) - Cisco
[https://www.wordfence.com/blog/2017/04/home-routers-attacking-wordpress/](https://www.wordfence.com/blog/2017/04/home-routers-attacking-wordpress/) - home routers used to attack wordpress and others

And cheap network storage isn't better:
[https://thehackernews.com/2018/09/wd-my-cloud-nas-hacking.html](https://thehackernews.com/2018/09/wd-my-cloud-nas-hacking.html)
[https://www.csoonline.com/article/3121338/seagate-nas-hack-should-scare-us-all.html](https://www.csoonline.com/article/3121338/seagate-nas-hack-should-scare-us-all.html)

Please be very careful with networked storage that doesn't get patched weekly, constantly, like any Ubuntu system would.  There are lots and lots of risks with these speciality devices. Mitigation is the gameplan.

---

### Post by cAlpha on 2019-03-04
Thank you all. 

> **TheFu said:**
> No. My point was that WAN routers - the one protecting your LAN from the internet should never, ever, ever, have storage connected to them unless you want the entire world to have access to that storage.  Routers have bugs and sharing of connected storage has been a bug in almost every router made, multiple times, even have so-called "fixes."  IMHO, it is a terrible idea.  That was my point, but I was trying to be nice about it. Not blunt.  When I'm blunt, people are unhappy, usually.


Direct is good, that's helpful.  Sounds like my general approach is flawed then (ie, connecting external to router via USB for access by different machines).  Do you have suggestions for an approach that would be more secure, would allow for sharing data hosted on an HD across machines without requiring plugging the HD in to the respective machine then?

---

### Post by HermanAB on 2019-03-05
Howdy,

Note that the usual convention is to put static mounts under /mnt.  The /media directory is meant for automounting removable media.

Also, using special characters like "()" in a mount point, is just looking for trouble.  You should be able to get it to work like that, but why make yourself yet another thing to debug?

---

### Post by Morbius1 on 2019-03-05
Removable media hasn't been automounted under /media in years. It's now under /media/$USER

---

### Post by TheFu on 2019-03-05
[https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) and the official 43 page standard document say:
```

/mnt is for "Temporarily mounted filesystems."
/media is for "Mount points for removable media such as CD-ROMs (appeared in FHS-2.3 in 2004). "
```

These are open to opinion. I use /mnt/ for admin purposes as a place to put storage when I'm working on it.  

I avoid doing anything manual with storage under /media/.  Automatic system mounts end up down that area and in the passed, the automatic tools would easily be confused and do odd things to manually mounted stuff in that tree.  Stuff like USB storage or LAN networked CIFS storage that is automatically mounted ends up there.

Historically, networked storage, say provided by NFS, has been mounted under /export/, but this is not in the FHS. I don't use that location anymore, though a legacy server here does have some legacy NFS storage mounted there as read-only. It provides static pages storage for a few web servers.  Seeing an attacker try to modify files on read-only NFS mounts can be entertaining.

As I've gotten older, I've decided to use /D/{something}/ for my network and USB mounts. I consider these to be temporary and use autofs to mount them on-demand and gracefully deal with failures (bad USB connections or network issues).  For simplicity and my personal sanity, I also ensure that storage shared over the network is mounted to the same location on all systems.  I like short directories that convey their purpose.

Taking the 3 minutes to scan the FHS table is well worth the time to gain a deeper understanding of Unix storage.  IMHO.

---

### Post by TheFu on 2019-03-05
> **cAlpha said:**
> Thank you all. 

Direct is good, that's helpful.  Sounds like my general approach is flawed then (ie, connecting external to router via USB for access by different machines).  Do you have suggestions for an approach that would be more secure, would allow for sharing data hosted on an HD across machines without requiring plugging the HD in to the respective machine then?

I believe using the internet router as a storage server is terrible security practice.  Many people do it, but I don't know any professional admins who do.  The IT world is full of features that shouldn't be used. 

NFS, CIFS, SFTP, SSHFS, and there are many other options, if you have replicated/redundant needs.  SFTP and SSHFS work over ssh connections and are considered secure over the internet, assuming ssh-keys are used, never passwords.  The ssh-based methods have significant overhead which makes them less desirable to use if the extra encryption isn't necessary.

For Unix to Unix storage on the same LAN, I use **NFS**. It is slightly faster than the others and provides native file/directory permissions.  OSX is Unix. Linux is Unix. BSD is Unix. Pretty much everything that isn't Windows is Unix.

For Windows to Unix storage on the same LAN, I use **CIFS**. It is the lowest common network storage option. It is really Windows-user to Unix-server protocol. It doesn't honor Unix permissions. I also use CIFS from android tablets when it is available already. If it isn't, I use sftp from Android.  I wouldn't setup CIFS for any non-Windows need.

Because USB storage isn't permanent, and physical USB connections are often flaky, I use **autofs** to manage CIFS and NFS mounts on other systems. However, if you feel the USB storage connection is solid (I've been burned) and will always be available, then using an fstab entry could make sense.

Any Linux system (well almost any), can be a CIFS or NFS server - or both.  A $35 raspberry-pi can do it, though the performance would be limited by the poor networking and slow USB2 interfaces.  Your Linux desktop can handle it easily, assuming it is wired ethernet, not wifi. If you want a good, lower-power (watts), storage server, then there are $50-$75 ARM single board computers with SATA3/USB3 and GigE network interfaces that actually provide that performance. Setting up another computer just for storage might be more than many people want.

Wifi storage servers are a bad idea. This is fact. Wifi clients are bad too, just slightly less-bad.  If the storage holds media for streaming around the house, wifi might be the easiest answer, but it isn't as solid as people think.  For years, I did wifi deployments inside a huge enterprise, over 1200 locations. Since then, I avoid wifi whenever possible.  For example, my chromebook and my new laptop do not have ethernet ports, so I added a USB3-to-GigE connector rather than trusting wifi.  A sometimes,75 Mbps vs a stable, always working, 920 Mbps; the choice is easy. I use powerline ethernet to bridge different floors.  A solid 60 Mbps is better than a "sometimes" 75 Mbps wifi.

1 other option to consider is to use an older router that has storage capabilities, but only use it inside the LAN. Don't allow it on the internet at all.
 The real issue I have with routers and USB storage connections is that a bug or poor software design easily makes that storage available to the internet.  The exact same device NOT connected to the internet doesn't have anywhere near the same security/attack risk profile.  The WAN/Internet router has a very special security job, which doesn't include storage.

IMHO.

---

### Post by Morbius1 on 2019-03-05
You people need to check the expiration date on some of your "facts"

---

### Post by cAlpha on 2019-03-05
> **Morbius1 said:**
> You people need to check the expiration date on some of your "facts"

Curious which facts are starting to stink?


> **TheFu said:**
> I believe using the internet router as a storage server is terrible security practice.  Many people do it, but I don't know any professional admins who do.  The IT world is full of features that shouldn't be used. 

NFS, CIFS, SFTP, SSHFS, and there are many other options, if you have replicated/redundant needs.  SFTP and SSHFS work over ssh connections and are considered secure over the internet, assuming ssh-keys are used, never passwords.  The ssh-based methods have significant overhead which makes them less desirable to use if the extra encryption isn't necessary.

For Unix to Unix storage on the same LAN, I use **NFS**. It is slightly faster than the others and provides native file/directory permissions.  OSX is Unix. Linux is Unix. BSD is Unix. Pretty much everything that isn't Windows is Unix.

For Windows to Unix storage on the same LAN, I use **CIFS**. It is the lowest common network storage option. It is really Windows-user to Unix-server protocol. It doesn't honor Unix permissions. I also use CIFS from android tablets when it is available already. If it isn't, I use sftp from Android.  I wouldn't setup CIFS for any non-Windows need.

Because USB storage isn't permanent, and physical USB connections are often flaky, I use **autofs** to manage CIFS and NFS mounts on other systems. However, if you feel the USB storage connection is solid (I've been burned) and will always be available, then using an fstab entry could make sense.

Any Linux system (well almost any), can be a CIFS or NFS server - or both.  A $35 raspberry-pi can do it, though the performance would be limited by the poor networking and slow USB2 interfaces.  Your Linux desktop can handle it easily, assuming it is wired ethernet, not wifi. If you want a good, lower-power (watts), storage server, then there are $50-$75 ARM single board computers with SATA3/USB3 and GigE network interfaces that actually provide that performance. Setting up another computer just for storage might be more than many people want.

Wifi storage servers are a bad idea. This is fact. Wifi clients are bad too, just slightly less-bad.  If the storage holds media for streaming around the house, wifi might be the easiest answer, but it isn't as solid as people think.  For years, I did wifi deployments inside a huge enterprise, over 1200 locations. Since then, I avoid wifi whenever possible.  For example, my chromebook and my new laptop do not have ethernet ports, so I added a USB3-to-GigE connector rather than trusting wifi.  A sometimes,75 Mbps vs a stable, always working, 920 Mbps; the choice is easy. I use powerline ethernet to bridge different floors.  A solid 60 Mbps is better than a "sometimes" 75 Mbps wifi.

1 other option to consider is to use an older router that has storage capabilities, but only use it inside the LAN. Don't allow it on the internet at all.
 The real issue I have with routers and USB storage connections is that a bug or poor software design easily makes that storage available to the internet.  The exact same device NOT connected to the internet doesn't have anywhere near the same security/attack risk profile.  The WAN/Internet router has a very special security job, which doesn't include storage.

IMHO.

Appreciate the thorough reply.  Sounds like sans connecting the HD to the server, you'd basically suggest setting up a media server internally.  One of my use cases is being able to access content both while docked and not from my main laptop.  We have a couple devices and a Plex server that I'd like to be able to read from the HD as well.  Since the router appears to offer a pretty straight forward means for doing this, it seemed like a no brainer, but I hear you on security.

---

### Post by Morbius1 on 2019-03-06
> Curious which facts are starting to stink?
I'm not going to get into a long debate over alternate facts. I was simply making a comment on this pronouncement:
> The /media directory is meant for automounting removable media
That is not true. It used to be true. But it is no longer true.

You don't have to take my word for this. Plug in a random usb stick into your machine. Does it mount to /media/XXX or does it mount to /media/your-user-name/XXX?

---

