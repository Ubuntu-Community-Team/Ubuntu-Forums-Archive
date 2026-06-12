---
title: "share from ubuntu to ubuntu"
date: 2008-05-15
forum: General Help
---

### Post by smmalis on 2008-05-15
I am trying to share files over the network from one Ubuntu machine to the other.  They are on the same network and see each other, but the individual shared folders don't appear.  Any ideas?

---

### Post by bodhi.zazen on 2008-05-15
Did you install samba ? or nfs ?

---

### Post by smmalis on 2008-05-15
Both comps have samba installed.

---

### Post by bodhi.zazen on 2008-05-15
Not sure.

You can try a few things. Open the samba config file :

```
gksu gedit /etc/samba/smb.conf
```

Scroll down to the shares section.

Make sure you have a line :

```
browseable = yes
```

in each share.

Re-start the samba server :

```
sudo /etc/init.d/samba restart
```

---

### Post by smmalis on 2008-05-15
It seems that the nautilus panel doesn't actually do anything, as there was no entry listed for the folders I was trying to share.  I manually added entries and now everything works.

---

### Post by Xiong Chiamiov on 2008-05-15
For sharing between unix-like systems, it's really much better to [use NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo").

---

### Post by bodhi.zazen on 2008-05-15
To add a share via gui :

right click on a directory in your home (do not do this with your home folder)

select share from the drop down menu.

You must have permission to r or rw the directory if you want to share it r or rw respectively.

HTH

---

### Post by smmalis on 2008-05-15
> **bodhi.zazen said:**
> right click on a directory in your home (do not do this with your home folder)

select share from the drop down menu.

You must have permission to r or rw the directory if you want to share it r or rw respectively.

That's exactly what I did, but nothing happened.  I'll try NFS, but I want Samba to work because there are some windows comps on the network as well. I'm okay with editing smb.conf every so often.

---

### Post by bodhi.zazen on 2008-05-15
Hmm ... sharing is working out of the box here ....

At any rate ...

You can mount NFS shares on Windows if you like. I am a big fan of NFS but feel Samba is more secure and has some advantages (as well as disadvantages, primarily speed).

If security is an issue, take a look at sshfs

There are a number of tutorials on sshfs :

[http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html](http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html)

[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

---

