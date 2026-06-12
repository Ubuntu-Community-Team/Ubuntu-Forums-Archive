---
title: "playing remote mp3s over samba share"
date: 2005-07-21
forum: General Help
---

### Post by egnaro on 2005-07-21
I keep my music on a windows XP system, and I would like to be able to play music directly over from its hard drive via a share. I can access the files fine by going to smb://computername in nautilus but if I try to play a song via xmms  or even mplayer nothing happens. Any clues as to whats going on or why it wont play. I copied a song over and it plays fine locally.

---

### Post by souki on 2005-07-21
I think you cannot do it this way.
You have to mount the windows shared folder or use a mp3 streamer on the xp box

---

### Post by gil-galad on 2005-07-22
I think totem might stream it.

---

### Post by SepheeBear on 2005-07-22
Totem can access files using the "smb://<share>" paths. I think rhythmbox can do this also. IIRC this has everything to do with the app you are using being gnome-vfs aware. I think of it as a 'soft' mount where gnome-vfs handles communication with the share and the app communicates only with gnome-vfs. xmms and AFAIK beep-media-player cant access files on samba shares this way. For those to work you'd have to mount the share somewhere so that xmms thinks its accessing a file on a regular local harddrive. 

To do that, you need to have the smbfs package installed, if its not already and use the command: 
```
sudo mkdir /media/<somename> && sudo mount -t smbfs //<IP-ADDRESS>/<share> /media/<somename> -o uid=1000 -o username=user -o password=pass
```
That'll make it show up in the Gnome menu under "Places". You can also use /etc/fstab to mount it this way as well.
/etc/fstab:
```
//IP-ADDRESS/share /media/share smbfs noauto,user,uid=1000,credentials=/ etc/samba/pass/share,rw 0 0
```
I use a separate credentials file to define the username and password that is readable by root and users in a special "samba" group that I created. Check `man mount.smbfs` for more info.

---

### Post by buster on 2005-08-05
If anyone is still interested  ;-) you can use Totem to do this easily by opening Totem and then your share on the Windows machine, side by side, and using drag and drop to put a folder from your Window's music files to the middle of Totem. It will probably start right away.

---

### Post by satbunny on 2006-09-01
I have been doing this with RhythmBox for a few days and it keeps crashing after a few hours left alone. I suspect that the smb link just isn't quite secure/stable enough for the programme. I am going to do a proper mount using fstab and test that.

---

### Post by satbunny on 2006-09-01
I have tried a full mount using fstab and RB still crashes after an hour or so. Maybe it's actually a faulty mp3 file or something?

---

