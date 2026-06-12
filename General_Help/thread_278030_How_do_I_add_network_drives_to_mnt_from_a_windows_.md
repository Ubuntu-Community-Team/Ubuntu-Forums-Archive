---
title: "How do I add network drives to /mnt from a windows Machine?"
date: 2006-10-15
forum: General Help
---

### Post by Tamed_G on 2006-10-15
Hi all,

I want to be able to play my music that I have on my Windows XP server with the 'Listen Player'. I can mount my windows shared drives on my gnome desktop but they aren't available to many media programs.

How do I make my network drives show as permanent drives (in my /mnt dir???)

I hear people talk about Samba but I'm so noobish with linux that the samba examples confuse me to the point of falling off my chair - and they all seem to be for Windows clients on Linux Servers, not the other way around?

Can anyone do a /mnt for dummies advice session for me?

](*,)

---

### Post by sitedesign on 2006-10-15
First I think you will need the smbfs package, then add the mount to your fstab so that it is done during boot, then you can check it and if it works secure it.

Here we go:

Install smbfs:
```
sudo apt-get install smbfs
```

make the mount point:
```
sudo mkdir /media/windata
```
you can change windata to what ever you like

edit your fstab:
```
sudo gedit /etc/fstab
```

add a line to bottom of the file like:
```
//servername/sharename /media/windata smbfs username=windowsuserename,password=windowspassword 0 0
```

test it works:
```
mount all
```

You should now have you mapped drive show on the desktop and in the file managers of most applications.

If you like, the mount point could even be a directory in your home folder, I use /home/pking/photos

*"I do cheat and use a linux server though"*

OK now to secure it.

Change the fstab file again:
```
sudo gedit /etc/fstab
```
and make the last line:
```
//servername/sharename /media/windata smbfs credentials=/home/myhomedirectory/.smbpasswd 0 0
```
remember to change myhomedirectory to your linux computers login name.

Now create the credentials file:
```
cd
echo username=mywindowsusername > .smbpasswd
echo password=mywindowspassword >> .smbpasswd
chmod 600 .smbpasswd
```

Now reboot your computer and see how it pans out.

If it still doesn't work try a quick search on google for "samba mount fstab".

Hope that helps.

Regards Peter King

---

### Post by Tamed_G on 2006-10-15
Thanks for this reply,

I am getting close I think, but when I get to 'mount all' I get the following error...

mount: can't find all in /etc/fstab or /etc/mtab

also in the code where you have '//servername/sharename' are these replaced by the names of the shared folders on my server?

For example, the server's name on the network MSHOME is 'file_server' and the share folder is called 'Music Archive'. So I'd put '//file_server/Music Archive....'??

Many thanks

G

---

### Post by Tamed_G on 2006-10-15
NIce - I worked it out after a little fiddling

Thanks for your help, it was just enough to get me going in the right direction.

G

---

### Post by anthro398 on 2006-10-16
I think instead of 'mount all', which I think is not a valid command, you want 'mount -a'.

---

### Post by sitedesign on 2006-10-16
oops, sorry for that, working too late again.

Glad it worked out in the end.

---

