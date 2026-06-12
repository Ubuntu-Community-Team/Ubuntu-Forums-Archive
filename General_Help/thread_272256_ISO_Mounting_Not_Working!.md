---
title: "ISO Mounting Not Working!"
date: 2006-10-05
forum: General Help
---

### Post by taekwondodogoof on 2006-10-05
Hi, I'm trying to mount an ISO, I've tried using this in terminal
```
jared@MeinKampf:~$ sudo mkdir /media/iso
mkdir: cannot create directory `/media/iso': File exists
jared@MeinKampf:~$ sudo modprobe loop
jared@MeinKampf:~$ sudo mount file.iso /media/iso/ -t iso9660 -o loop
file.iso: No such file or directory
jared@MeinKampf:~$

```

I've moved the iso to the media/iso folder, and I've renamed it file.iso! What can I do?

---

### Post by K.Mandla on 2006-10-05
Hmm. I think the directory might need to be empty to mount it. I would keep file.iso out of the /media/iso directory, or move it to your home directory. 

Then I think the -t and -o options come before the source and mountpoint parts of the command. Try *cd ~* and then *sudo mount -t iso9660 -o loop ~/file.iso /media/iso*, if you put file.iso in your home folder. 

I think that might help. See if it does.

---

### Post by IcemanV9 on 2006-10-06
Here's [***[COLOR="Orange"]wiki[/COLOR]***]("https://help.ubuntu.com/community/MountIso?highlight=%28iso%29%7C%28mount%29") on mounting iso.

---

