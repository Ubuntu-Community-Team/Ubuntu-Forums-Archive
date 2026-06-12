---
title: "Custom desktop file/application runs root command. How to prompt user for PW in GUI?"
date: 2016-02-10
forum: General Help
---

### Post by Roasted on 2016-02-10
Hello friends. So I'm trying to find a way to make interfacing with samba shares less frustrating in KDE land. While KDE can interface with samba shares, it's quite broken, as you cannot stream videos over the LAN nor can you (at times) edit Libre Office documents without some headaches, such as permissions getting automatically changed to nobody:nogroup, etc etc etc. (There's a six year old bug about this with no hope in sight...)

My hopes was to leverage the command line, but in an easier to use more straight forward fashion. KDE does not utilize gvfs, and I'm finding gvfs is quite a gem since it works by mounting the samba share to a local directory on your computer. This allows applications to operate with files on the network as if they were on your own computer. Brilliant. That's how I ended up here, in KDE land, wondering how I can make things a bit more straight forward (but by using the terminal).

The command I want to run is:

sudo mount -o username=jason //NAS/share /media/NAS

This mounts my NAS share to /media/NAS on my laptop. And you know something? It works great! But as I said, I wanted it to be more straight forward. So I set up a desktop file and tied it to an icon. This allows me to pin an application in my taskbar as a shortcut. In theory, I click, it runs, thereby executing the above command, and boom = it's mounted and things function.

The catch is... the mount command requires root. But I'm not sure how I can get the custom "Samba Share" application/desktop file to call for a graphical prompt to allow me to type in my root password to my laptop so I can thereby issue the mount command. Does anybody have any idea how I could leverage that? 

Thanks for any and all insight!

---

### Post by Tadaen_Sylvermane on 2016-02-10
You should enter the samba share into your /etc/fstab file with the user option. Then users can mount it. For my nfs shares I have a script run at login that mounts everything. this is a sample line from my /etc/fstab
```

# server iso share
192.168.1.240:/spinner/iso      /data/iso       nfs     noauto,user     0       0

```

---

### Post by Roasted on 2016-02-10
> **Tadaen_Sylvermane said:**
> You should enter the samba share into your /etc/fstab file with the user option. Then users can mount it. For my nfs shares I have a script run at login that mounts everything. this is a sample line from my /etc/fstab
```

# server iso share
192.168.1.240:/spinner/iso      /data/iso       nfs     noauto,user     0       0

```

Hi there. Thanks for your suggestion. I had given some thought about going the fstab route, but the thing is I want something a bit more modular and "on demand" feeling. My laptop won't always be at home on the same network as my NAS. It may be elsewhere. Likewise, if I'm out, close lid, come home, and open lid, I'd have to either mount it manually or reboot my laptop for fstab to kick in and remount the share.

I'm basically after gvfs-like functionality, as in a local mount point but I want it to be as easy to use and straight forward as possible. I'm hooked on it being as one-click as possible in the event that my wife takes an interest in KDE, because once I mention command line that'll kill KDE entirely for her, yet we need that gvfs-like functionality to fly (which as I mentioned, has been lacking in the KDE camp for quite a number of years). 

In short, fstab is a great solution, but it's not an optimal solution for this case. :( If I can just get the prompt to fire up requesting password, that'd be better yet. OR, if there's a way to mount a samba share to a folder within the user's home directory but it not require root, that'd also be great. (mount via CLI requires root, otherwise that'd be an idea)

EDIT - So, simple solution that I somehow entirely overlooked. In the desktop file, terminal=true, and it prompts a terminal. Perfect! This is great.

....but a new problem. The mount intercepts the permissions on the NAS. Since the bulk of the users/groups don't exist on my laptop (as they are on the NAS itself), the permissions come across all wonky, identified by the UID/GID's. Is there a way to mount a samba share via terminal on Ubuntu and make it "act" like my actual user I'm authenticating as?

---

### Post by SeijiSensei on 2016-02-10
Have you tried simply opening an SMB URL in Dolphin?  You can type smb://server/share into the address bar in Dolphin. You'll be prompted for the username and password and can tell KDE to save it.  I believe you can make a launcher for this and attach it to a desktop icon.

---

### Post by Roasted on 2016-02-10
> **SeijiSensei said:**
> Have you tried simply opening an SMB URL in Dolphin?  You can type smb://server/share into the address bar in Dolphin. You'll be prompted for the username and password and can tell KDE to save it.  I believe you can make a launcher for this and attach it to a desktop icon.

I have. The catch is that functionality you described is where the issue lies, as Dolphin will utilize KIO for the Samba functionality (in comparison this same process in a Gnome-esque environment will leverage gvfs here). It's with KIO that is the root problem when it comes to being able to do (what I'd argue is common) tasks, such as clicking a video on a file server and it working, or clicking on a Libre Office document on a file server and being able to edit it, save it, and it not act strangely.

I didn't have access to my KDE system tonight however I tinkered with this idea on my regular Ubuntu system and I believe I got somewhere. I created a basic desktop file, attached an icon to it, and put in the exec line the (what I feel is) cumbersome mount command to effectively mount the share. It reads below:

```
[Desktop Entry]
Version=1.0
Name=Samba Share
GenericName=Samba Share
Comment=Samba Share
**Exec=sudo mount -t cifs -o username=jason,uid=1000,gid=1000,file_mode=0700,dir_mode=0600,forceuid,forcegid //192.168.1.20/vault /media/jason/NAS**
Icon=/usr/share/icons/sambashare.png
Type=Application
Terminal=true
Categories=Network;

```

Most of that Exec= line I'm not familiar enough with to simply write out of memory, however through some digging around online this seemed to be the ticket. The basic jist I got out of it was it's mounting the cifs share as me (jason) with my uid/gid of my "jason" user on my laptop (for any future Googlers reading this, 'id username' in terminal outputs the uid/gid), and the rest of the command, from what I've read, is some seemingly "sane defaults" for interacting with samba shares in a gvfs-like manner -- as in, permissions appear to line up properly, etc etc.

This gives me an entry in my launcher that I can click, a terminal opens (notice the desktop file says Terminal=true), it asks for root password (expected behavior since mount requires root, hence 'sudo' in the Exec= mount line), I type root password, it asks for samba password for user jason, I type it, and the terminal disappears. Boom the share is mounted and I can access it in the file manager.

The real kicker will be if this works on my KDE rig when I get back to it. Given this is mounting via terminal, I would suspect it would certainly fly, as it removes all of the extra "stuff" involved (KIO, gvfs, etc) and works entirely based on the command issued to mount the share.

Fun facts I observed: (Server is on gigabit network, 4x3TB in RAID6 via mdadm, laptop is wireless N600 with SSD)
gvfs speed with 1GB ISO file copying from server to laptop: 12.5 MB/s average
manual terminal mount as described above with 1GB ISO file copying from server to laptop: 22 MB/s average

Fancy that. Based on this speed premise alone it makes me a little more inclined to be more accepting of this extra legwork to get the share to mount exactly as I'd see fit.

Downside 1: This would almost require a dedicated .desktop file for each samba share in question. Not a big deal, but worth noting.
Downside 2: Should I want to unmount the share in question, it would require I (via terminal) sudo umount it. Not thinking that matters at all in my scenario, though.

Upside 1: Speed. Speed. Speed.
Upside 2: I thought I recall shutdown/reboots hanging in the past with a root-mounted network share still mounted. This is no longer the case, at least on Ubuntu 15.10 (will try others then).
Upside 3: A desktop file is all but a few kilobytes. Easy to back up -- makes for an easy deployment should I ever get a new laptop. Copy desktop file (and its corresponding icon, of course) to the appropriate directories I'm back in business.

At any rate, I'll see how this goes in KDE land soon. Thanks for everybody's input!

---

### Post by SeijiSensei on 2016-02-11
Is the server running Windows or Linux?  If the latter, then you should be using NFS, not CIFS.  My home office server has both NFS and Samba running to share files with both Linux and Windows clients.  Using NFS I have none of the problems you describe concerning either video or LibreOffice documents.  I mount the NFS shares at boot from /etc/fstab on Linux clients.  With CIFS, I found video software like mplayer wanted to first make a local copy of the file before playing it.  With NFS that doesn't happen.

---

### Post by Roasted on 2016-02-11
Oh my, isn't that just glorious. Mounting via terminal in KDE/Plasma worked great! Another thing I noticed. Above I mentioned the speed differences between gvfs and mounting via terminal... I did the same thing just now with KIO vs mounting via terminal, and the results were similar. If I mount via terminal (which again, is using that custom desktop file I made since that's what it's doing in the background) it is significantly faster than KIO as well... to the tune of about 2.5 times faster.

So, this is pretty awesome. I can interface with my NAS on KDE without any frustrations, such as Libre Office documents being saved and KDE auto-uploading them with permissions nobody:nogroup, or Dolphin hard locking because it cannot stream a video that I just opened from the NAS share. And it's faster than both KIO and GVFS (giving me some justification for using this method over GVFS on my non-KDE systems anyway). Very nice.

My only question remaining is the above exec command in the desktop file I largely pulled from an example that I tailored to my specifications. One section I'm not sure about is the file_mode and dir_mode part. I removed them for kicks and ran the command but I didn't see anything change...? I also didn't see any mention of them in the man page for mount, though I did find some references online -- however very dated responses.

Can anybody tell me what the point of file_mode and dir_mode is? I ran the same command both with *and* without file_mode and dir_mode and I saw no change in the permissions of the mounted share. As far as I can tell, the command:

sudo mount -t cifs -o username=jason,uid=1000,gid=1000,forceuid,forcegid //192.168.1.20/vault /media/jason/NAS

is simply mounting "vault" on my NAS to /media/jason/NAS via the user "jason" while utilizing uid 1000 and gid 1000, which of course is the uid/gid of "jason" on my laptop. This is seemingly similar behavior to gvfs, since if I mount via gvfs and run ls -l, I can see it mounted the share with me as the owner/group.

So really, that's my last question. Does file_dir + dir_mode matter?

---

### Post by Roasted on 2016-02-11
> **SeijiSensei said:**
> Is the server running Windows or Linux?  If the latter, then you should be using NFS, not CIFS.  My home office server has both NFS and Samba running to share files with both Linux and Windows clients.  Using NFS I have none of the problems you describe concerning either video or LibreOffice documents.  I mount the NFS shares at boot from /etc/fstab on Linux clients.  With CIFS, I found video software like mplayer wanted to first make a local copy of the file before playing it.  With NFS that doesn't happen.

Hi there - sorry I missed your response when I posted earlier. The server is running Linux (Ubuntu Server 14.04). I did give thought about running NFS, but correct me if I'm wrong -- my understanding with NFS is the UID/GID of the user on the client system (laptop) must match the UID/GID of the user on the server (NAS). With that being the case, I'm not really interested in using NFS, because I don't want to have to fumble with UID/GID's of the users on both ends just to make things work. I'd much rather use Samba where I can just authenticate as a user and boom, things work fine. If I'm incorrect with this and NFS is not that specific, I may look into it again, but user based authentication has its benefits.

In reference to the video/Libre Office thing, I wouldn't expect you to see that via NFS, and likewise I didn't run into it at all with the CIFS/samba shares mounted via terminal. This is entirely because of the way KIO interfaces with the file shares. It's been a long standing bug in KDE land for nearly 6 years, but with no solution in sight and, frankly, I was tired of this being the very last thing in KDE land that was preventing me from using it, I ended up here with the "click on custom application = boom share mounted" idea.

---

### Post by SeijiSensei on 2016-02-11
You can solve the user ID problem by using the right permissions on the share.  You can either make the share have 777/666 permissions, or put all the users in a group and give the group full rights.

Another option is to map all requests to a specific UID/GID:  [http://ubuntuforums.org/showthread.php?t=1103198&p=6939701&viewfull=1#post6939701](http://ubuntuforums.org/showthread.php?t=1103198&p=6939701&viewfull=1#post6939701)

You can also use idmapd, but I have no experience with that.

---

