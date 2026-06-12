---
title: "Shared network drives."
date: 2006-11-24
forum: General Help
---

### Post by Roasted on 2006-11-24
Not really sure how to do this in linux. I have a spare hard drive on the shelf and my brother's windows OS took a crap and it's completely hosed. Can't even boot to safe mode or anything. His computer, the way it's designed, is only capable of having one drive. I'd rather not reflash the bios and all that so I figured I'd add another drive in my computer, share it over the network, and allow him to dump music and pictures onto it to back them up.

Do I even need linux installed on the shared drive? And regardless of whether I do or not, how would I go about sharing it? Would windows machines be able to see the drive?

---

### Post by psyeye on 2006-11-24
To share some folder, use

  System -> Administration -> Shared Folders

Use "Windows networks (SMB)" for the "share through" option and you should be set. If the share does not show up at the Windows machine, try the IP, like so: \\xxx.yyy.zzz.www

hth
psyeye

---

### Post by Roasted on 2006-11-26
What else do I do? Do I adjust anything in "General Windows Sharing Settings" or let that alone? Also, when I set this up, I went upstairs and put my IP in. It wants a username and password. I figured it was my linux name and PW but it wasn't. What would it be?

Also - this is an entire drive I want to share. Do I just put the folder on the drive, and just let the drive go? Should it be formatted? All I did was use gparted to delete what partitions are on it. Would that suffice? I need Windows XP/2000 machines + Ubuntu Linux machines to read/write from this drive.

---

### Post by Roasted on 2006-12-01
:confused:

---

### Post by Mike'sHardLinux on 2006-12-01
You will want to add users to Samba. One way to do this is in the terminal, type: sudo smbpasswd -a username

Of course, you'll need to enter your password for sudo. Then, it will ask for the new samba user's password. Once you do that, you should be able to use that username and password from your win boxes.

There are other ways to set up Samba to share, but this is probably the easiest. You could also manually edit the smb.conf file.

As far as sharing the drive...
1) partition the drive
2) format the drive (I suggest using EXT3 filesystem)
3) mount the drive (you need to set up fstab to always mount the drive when you boot up)
4) when you mount a drive in Linux, it is basically a folder in the filesystem. You can just share that folder, and then you will be sharing the whole drive.

There may be other steps with Samba. For some reason, it seems like I had to install another package to get it working :-k . Check to make sure samba and samba-common are both installed and that should be enough. You may need to open some ports in your firewall, too. (Maybe Ubuntu automagically does this when you share a folder via smb?? seems like it did for me)


Hope this helps.

---

### Post by [bigmac] on 2006-12-01
I don't know if it is necessary, but I recommend sharing with samba to windows machines, and with NFS to linux machines. It's possible to share the same folder with both methods, and from linux clients you can mount your shared drive like it was a floppy or cdrom. That's the way I've got my fileserver running.

First of all i assume you've formatted the shared drive on your host with, say, EXT3 filesystem, and edited the fstab so the drive is accessible on your host machine. I also recommend having a dedicated machine as fileserver, so you dont hose it so easily by day to day use, but its ok if its not possible for you.

I recommend reading some howto's. Try searching or maybe these will do:

Samba:
[http://www.ubuntuforums.org/showthread.php?t=202605&highlight=smb+share+howto](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=smb+share+howto)

NFS:
[http://www.ubuntuforums.org/showthread.php?t=249889&highlight=nfs+share+howto](http://www.ubuntuforums.org/showthread.php?t=249889&highlight=nfs+share+howto)

Read through them before starting out. I only did a quick search but at a glance they look like good howtos. Again NFS may not be necessary, but it works very well for me.

---

### Post by Roasted on 2006-12-01
This drive will be shared by one linux machine and three windows machines. Will formatting it using the EXT3 file system alter anything? All we need to put on the drive is pictures, music, etc, just for backup. Will the windows machines have trouble writing to an operating-system-less drive formatted with EXT3? That's where I'm getting a bit confused...

I guess in reality, if need be, I wouldn't need to use the linux machine for backup, because I have two hard drives in my system with an rsync backup script that I often run. So really, I won't even use this drive. However I decided to put it in my computer because I knew I had the bigger power supply and figured it'd work out the best. 

But I really, REALLY want to share this drive through linux, with the ability of the windows machines to read/write/explore/etc.

---

### Post by [bigmac] on 2006-12-01
The clients will be able to write to the network shared drive, yes. They don't care what filesystem is on because it's only the host that sees the physical drive. The host shares the drive with samba, and then the client will be able to see it as a network drive.

If your host is linux, then use EXT3 or similar, and share it with samba if all clients are windows.

---

### Post by Roasted on 2006-12-02
I just thought I could right click, share drive, click a few more things, and bam the drive is usable to all clients. Silly me.

I'll wait till I have more time to tinker with this.

---

### Post by Wangsta on 2006-12-02
yeah, I tried to set up a Windows-Ubuntu network too.
it didn't take long before I gave up.

I have a Windows desktop, a Mac desktop, and a Linux laptop. Trying to get these guys to cooperate is beyond me.

---

### Post by Roasted on 2006-12-03
Yeah. I just thought that like... when I share the drive, it's just an open ended drive accessible to anybody who can tap into the network I have in the house. *shrugs*

I do have a windows 2000 partition on here. Maybe I should just share it through there? It just aggrivates me, I wanted to do it in linux. ](*,)

---

### Post by nix4me on 2006-12-03
So do it.  Its easy.  There was a very easy howto already posted on how to do it.

Share the folder from the system->admin menu and then just edit the smb.conf file.  If you don't want user logins, just change te security to share from user.

Its really very easy.

nix4me

---

### Post by Roasted on 2006-12-25
"So do it. It's easy"

Even the simplest thing can be incredibly difficult if you have no idea what to do. Right now? Yeah... no idea what to do. The few things I have done that were recommended to me, yeah, didn't work.

Not getting anywhere here...

---

### Post by Roasted on 2007-01-02
Anymore input before I give in and wait until next term where I have an actual linux class?

---

### Post by Roasted on 2007-01-07
So I followed the directions for SAMBA to install it. So far I was on a roll. Then I had to go to a windows machine to enable WINS. But the windows machine we're working with is windows 2000, and there's no advanced tab in the tcp/ip properties to enable wins. Now what?

This is incredibly aggrivating. ALL I want is to share a 200 gig drive on the network with 3 other computers. It's so ungodly easy to do at school, yet when you try to do it with linux I find that very few people can help. ](*,)

Also, if this thing doesn't work, how can I reverse everything I changed with samba so far. Like how can I revert my settings and get rid of what I did so far?

---

### Post by Roasted on 2007-01-15
All right. I'm trying here once again... I've read many how-to's and even spoke to a cousin of mine who has used linux for years. I can't seem to find anything to help me out.

In fact, I don't even know how to start where my issues are at, so I want to start over.

So, let's begin with this. My spare drive that I want to share to the network is a 200 gig drive (189gb). However, when I go to 'computer' the drive is listed to only have 129.5gb. Why? Also, must this drive be formatted with a certain file system? Right now 100% of the space is unallocated. I was unsure if I should format it due to the fact I want windows and linux machines to read/write files (pictures, music, music videos, etc) off of this drive.

Help. ](*,)

---

