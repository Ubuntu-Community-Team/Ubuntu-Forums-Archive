---
title: "XMMS and SMB"
date: 2005-03-19
forum: General Help
---

### Post by orion_114 on 2005-03-19
I have a machine that I want to turn into a media center. The problem is that it has a really small hard drive so I am running a share on my windows machine where I put all my music.  I just can't seem to add the entire directory into XMMS. How can I find the SMB share from the file system ? I thought it would be in \mnt but it aint? I tried adding the directory via the add url and using the string smb://user@192.168.0.1/Music/ but it also didn't work.

I managed to get the "music player" to find my smb share and add the files, but frankly the interface sucks! I also took a look at the VLC player but once again the interface is what lets the program down. Has anyone got any ideas on what I could use ?

The other issue that I have is that video plays really slowly and jumpily on my machine. I have a 400 Mhz machine with 128 MB of RAM. Is it purely hardware related or is there a tweak for Totem to get it playing more efficiently. I think I am using the gstreamer codecs.

---

### Post by akshoslaa on 2005-03-20
[QUOTE=orion_114]I have a machine that I want to turn into a media center. The problem is that it has a really small hard drive so I am running a share on my windows machine where I put all my music.  I just can't seem to add the entire directory into XMMS. How can I find the SMB share from the file system ? I thought it would be in \mnt but it aint? I tried adding the directory via the add url and using the string smb://user@192.168.0.1/Music/ but it also didn't work.

I managed to get the "music player" to find my smb share and add the files, but frankly the interface sucks! I also took a look at the VLC player but once again the interface is what lets the program down. Has anyone got any ideas on what I could use ?

The other issue that I have is that video plays really slowly and jumpily on my machine. I have a 400 Mhz machine with 128 MB of RAM. Is it purely hardware related or is there a tweak for Totem to get it playing more efficiently. I think I am using the gstreamer codecs.[/QUOTE]
 just did this teh other day :P

it would seem that linux doesn't deal with network paths quite as easilly as those of us coming over from windows-land have come to expect...

My solution? Mount the windows share, then all works well :P (I'm running Hoary on a 166, with 96megs of ram for this purpose (not bothering with video though :P))

smbmount //computername/sharename /mount/to/location/ -o username=guest%,fmask=644,dmask=755,uid=1000,gid=100, debug=0,workgroup=mshome

This is the command line I use (you'll need to install smbfs to get smbmount)
as it's connecting to windows shares, the username by default is guest, and there's no password (from memory the syntax with a password is username=guest%password=password ) but you might want to look that up...
I stick that in a shellscript, and run it when I want to acces the network (there's actually several drives mounted this way on my system)
It probably possible to have it automount on startup, but I'm not sure how... I didn't look into that. Still new to linux (but loving Ubuntu)

then from xmms, add->dir browse to where you mounted the share, hit ok and your off...
I recommend saving the playlist though... building it is timeconsuming (on my systems at least)

to unmount use:
smbumount /mount/to/location/

(I've noticed sometimes it gets stuck with a file open or something and wont unmount... remounting, then unmounting seems to do the trick though)

hope that helps :P
O)-c

---

### Post by orion_114 on 2005-03-21
Thank you so much for the help !!!!
It is working like a dream !!!!!! :D

---

### Post by akshoslaa on 2005-03-22
[QUOTE=orion_114]Thank you so much for the help !!!!
It is working like a dream !!!!!! :D[/QUOTE]
 No probs :P

I did notice last night though that the previously saved playlist wouldn't work... all the tracks were pointed to the right place, and the drives were mounted (triple checked) but it just wouldn't play them (shuffling all over the place)

re-adding the directory to a fresh playlist worked though... just something to keep an eye out for :P
O)-c

---

