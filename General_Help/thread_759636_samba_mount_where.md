---
title: "samba mount where?"
date: 2008-04-19
forum: General Help
---

### Post by svaens on 2008-04-19
Hi, 

Simple question, but i can't work it out. 

when I mount a windows drive using samba, 
eg, using the run command, and typing in smb://server/D

where is the damn thing mounted?
As in, .. a nice graphical folder pops up, 
but I want to go there via command line... but where was it mounted? 
I can't find my newly mounted windows share!!!
under mnt? nothing there of interest. 
under media ? it's not there...

---

### Post by ibuclaw on 2008-04-19
Try this.

Make a directory in media.
```
mkdir /media/**mountpoint**
```
Mount the share.
```
mount -t smbfs -o username=**yourname**,password=**yourpassword** //**win-box**/**share** /media/**mountpoint**
```
And for simplicity, create a symlink on your desktop.
```
ln -s /media/**mountpoint** ~/Desktop/**name**
```
Include all forward slashes, and change all in bold with accordance to your system.

Regards
Iain

---

### Post by svaens on 2008-04-19
hey, thanks!

---

### Post by ibuclaw on 2008-04-19
Also, I'm not sure if this will work (if the above works, then there is a probability)

You could create an fstab entry. (/etc/fstab)

```

# Samba Share
//**win-box**/**share**  /media/**mount-point**  smbfs  username=**yourname**,password=**yourpassword**,defaults  0  0

```

It's only a guestimated suggestion.

Regards
Iain

---

### Post by fjgaude on 2008-04-19
Gosh, I noranlly do most things using a GUI. When you are in Ubuntu command line I think you would have to know the IP of the virtual you are wishing to access. And from there you find the Share you have in Windows.

Something like this:

```
smbfs 192.168.45.128
```

That gets you into the virtual. I've never mounted a shared virtual drive within Ubuntu. I can go there using Nautilus and see all the Shares, read and write. And all my Ubuntu Shares can be seen in Windows.

Get the IP address in the Win run command with ipconfig /all. Then use that in Ubuntu.

Hope this is of some help.

---

