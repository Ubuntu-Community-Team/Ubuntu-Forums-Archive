---
title: "Want my desktop to be usable but also act as a file server"
date: 2008-04-27
forum: General Help
---

### Post by mattgaunt on 2008-04-27
Heya everyone

I've been thinking about making my desktop PC a file server, i.e. everyone in my house can access the movie and music folders and add their stuff and i cant get any work files. I would like the movie and music file to be possible to stream on to other computers (no need to copy the file onto other computer to play) (also possibly when connected to network wirelessly rather than being plugged in). But also the last ubuntu (Gutsy Gibbon) did slow down my comp quite a bit, would the server edition be a better choice?

I admit I hav used ubuntu for around 2 years but I am still not that compitent at fixing problems.

So basically can anyone give me advice, I just figured server edition would be good choice because I had been told by friends it's very lightweight compared to desktop edition. Is the stuff im asking for possible?

ooo also would be good to get at my files over sftp or ssh for when Im uni.

---

### Post by ryanhaigh on 2008-04-27
The server editition is indeed lighter, so much so that it doesn't even install a GUI, if your not experienced and still need to use this as a desktop as well I would recommend using ubuntu and stripping it down rather than trying to build up from the server editition. If your hardware is that old you might even consider using xubuntu. As for the server samba should do everything you want and openssh-server will take care of ssh/sftp access as long as you have port forwarding setup and know the ip of your computer (or use dyndns). 

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by mattgaunt on 2008-04-29
cheers ryan ill give those and read. I might hav a play with the server edition if I have time otherwise might just do as you suggested and strip down the desktop edition.

Gaunt

---

### Post by rubicon on 2008-04-29
There are a lot of file sharing protocols, SMB is just one of them. Samba is just compatible from Windows-out-of-the-box. 

You may try WebDAV (it is based on http, and you can access your files via web-browser), NFS (unix native file sharing protocol), even FTP (which is pretty old, but reliable).

---

### Post by mattgaunt on 2008-04-29
i guess what i would like is to have it so it works with windows (vista and xp) and Mac OS X so that i can view wot ever is on my desktop like I would as if it was a folder on what ever laptop is viewing it.

Gaunt

---

### Post by carlhako on 2008-04-29
If your going to install a gui still ie.gnome/kde i wouldn't bother with the server edition IMHO. The server edition is basically ubuntu minus xorg/gnome so once you install them (apt-get install ubuntu-desktop) you have a standard ubuntu install. you could install just the gnome package which will give you just gnome no open office etc but if your using it as a desktop you will probably want these anyway?

Also i believe samba is exactly what your after, its the same as sharing a folder on a windows machine im still editing my smb.conf file manually to setup my shares.correct me if im wrong but i think its as easy as right clicking a folder select properties and there is share there somewhere that you just click on. Then jump on any windows machine type in \\pcname in explorer or try to find it through network neighborhood.Not sure how you would access on the MAC but im sure it would have no problems.

hth

Carl

---

### Post by ryanhaigh on 2008-04-29
> **carlhako said:**
> 
correct me if im wrong but i think its as easy as right clicking a folder select properties and there is share there somewhere that you just click on. Then jump on any windows machine type in \\pcname in explorer or try to find it through network neighborhood.Not sure how you would access on the MAC but im sure it would have no problems.

hth

Carl

Unfortunately its still not that easy because ubuntu (wisely in my opinion) uses user level sharing security so that unless there is some new gui to do it in hardy users still have to be added and enabled using smbpasswd.

```

sudo smbpasswd -a username
sudo smbpasswd -e username

```
Maybe we need a 'enable simple shares' somewhere that switches to share level access for those who don't want to use user/pass to connect to shares.

---

