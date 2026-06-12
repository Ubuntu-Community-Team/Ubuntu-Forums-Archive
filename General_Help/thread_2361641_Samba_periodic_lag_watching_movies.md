---
title: "Samba periodic lag watching movies"
date: 2017-05-18
forum: General Help
---

### Post by ummmcam on 2017-05-18
I run an Ubuntu 16.04.2 LTS server that I use almost exclusively for simple samba file sharing. I have 3 multi-TB hard drives with HD movie files in x264 and x265 encoding. I have noticed periodic lagging in transfer rates while watching movies. The movie will play for about 10 minutes and then will stop and the server will have a large spike in data transfer over the network. Usually the movie will fast-forward ahead and keep playing but sometimes it will cut out altogether. 

I was convinced this was an application issue or a Windows issue since my main media PC is Kodi on Windows 10 but I have been able to reproduce the same lag on OSX running both Kodi and VLC. Local files do not have the same issue. My network is gigabit cat6 through a gigabit switch. Throughput is about ~80MB/s when transferring files via samba. 

While watching the samba service with iotop I can see the data transfer rate gradually decrease until the movie pauses then there is a large spike in throughput when the movie continues. htop shows minimal CPU usage and I typically only have about 300-500mb of memory used out of the 4gb available. 

Samba version: 2:4.3.11+dfsg-0ubuntu0.16.04.6

Is there anyone else with a similar experience? Are there any known settings which may be leading to these symptoms? Any other ideas to document whats going on under the hood? I never get any error logs in syslog or the samba logs that I've noticed. 

Any help is greatly appreciated!

---

### Post by TheFu on 2017-05-19
I don't use Windows for media.  Using CIFS has been an issue for streaming for years. Lots of issues reported all over the web. I had it too, back before I switched away from using single-purpose devices that only supported CIFS (samba/smb) network storage. My network is wired GigE everywhere, though media clients are only 10/100bt.

**Use NFS** as a workaround.  NFS is faster and native for Unix systems.  Don't know what you can do for the Windows clients, I've never had good success even loading free NFS clients under Windows. Have used paid NFS clients under Windows, but that was long, long, long, ago and an expensive, pain to setup. Switched to using a Plex Server and DLNA for about 50% of my viewing. It is nice to have a central DB for media. Under Kodi, I use the PlexBMC addon to make the DLNA client less-sucky.  The OSMC (a kodi distro for raspberry pi) forums have lots of ideas about this.  Windows has DLNA clients.  Just wish there were some way to clean up the automatic DLNA menus.

There might be some samba tuning options which may help. I dunno. NFS is faster.

[http://openelec.tv/forum/76-network-filesystems/62922-nfs-vs-smb-what-do-you-use](http://openelec.tv/forum/76-network-filesystems/62922-nfs-vs-smb-what-do-you-use) OpenElec is a media-centric release.

---

### Post by SeijiSensei on 2017-05-19
I have no problems streaming video over wifi from my server using NFS.  Like TheFu, I suggest you try NFS instead.

---

### Post by ummmcam on 2017-05-19
I suppose its time to make the switch. Been thinking about it for a while but the non-nativity to Windows makes me apprehensive. Do I need a 3rd party app for Kodi to browse nfs shares on a linux server or will Kodi do this internally? I can still use samba to share the folder structure for managing the files (windows explorer) since I haven't had any issues with this aspect.

---

### Post by TheFu on 2017-05-19
You know, life really is easier if you reduce your Windows use. ;)  I'm down to about an hour a week now.  Been removing Windows from our needs for a long time now.  Don't see any viable alternative for our financial stuff, so that will be the last to go, methinks.

Never tried kodi on Windows. Don't know if kodi does the nfs-client stuff through built-ins on Windows or not.  It appears that way in the raspberry-pi OSMC/Kodi interface. I never specifically loaded NFS on it.
```
$ dpkg -l|grep nfs
ii  armv7-libnfs-osmc                    1.10.0-1                           armhf        libnfs library
ii  libnfsidmap2:armhf                   0.25-5                             armhf        NFS idmapping library
ii  nfs-common                           1:1.2.8-9                          armhf        NFS support files common to client and server
```
But it does appear to be dependent on it on the Pi.  Probably SOL on Windows. That's a guess only. I do not _know_.

---

### Post by SeijiSensei on 2017-05-19
The easiest solution is to mount the NFS shares somewhere in the file system either under /media or /mnt.  Then every application has access to them.  I mount the /home directory from my NFS server under /media to preserve my home directories on the client machines.

---

### Post by TheFu on 2017-05-19
But his Kodi is running on Windows.  Do you have a good NFS client for Windows?
For OSX, he should definitely use NFS.  Just make the uid/gid match between the systems.  The numbers - run 'id' to see them on Unix systems.  I think OSX starts at 500 and Ubuntu generally starts at 1000 for uids.

---

### Post by SeijiSensei on 2017-05-21
I'm sorry.  I thought he was running the [Linux version of Kodi]("http://kodi.wiki/view/Linux").

NFS support in Windows is pretty limited and requires using the expensive versions like Ultimate and Enterprise or a third-party add-on.  I don't know anything about them.

---

