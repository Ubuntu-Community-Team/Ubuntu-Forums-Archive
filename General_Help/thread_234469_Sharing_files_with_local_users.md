---
title: "Sharing files with local users"
date: 2006-08-11
forum: General Help
---

### Post by ericsp on 2006-08-11
I just bought a Maxtor 3200 USB as external HD and managed to get it running with ext3. All users on this PC can now execute/view the files, but not delete/modify them. Since we plan to put pictures from the camera on it and want to be able to all modify them with the GIMP, I was wondering whether it would be possible that all files stored on this HD automatically get a 777 (or 767) without having to change that manually. Any help would be really appreciated.

Eric

---

### Post by tseliot on 2006-08-12
moved to a more appropriate section

---

### Post by leeyee on 2006-08-12
I'm not sure if you want to change the access mode of the whole HD? If so, try this:
```

chmod -R 777 /DirectoryName/YouWant/

```
where parameter -R means you can change access mode of files/sub-folders in the folder recursively.For more details:
```

man chmod

```

---

### Post by ericsp on 2006-08-12
Yes I know about the chmod command, but thought that that one has to be issued verytime new files have been added, right? Or when I make folders etc 777, all files stored in there will have the same mod?

---

### Post by ifokkema on 2006-08-12
I know there is an easy way to set a group ID default for new files on a certain directory, but that's only going to get you half-way.
I think ext3 doesn't have an umask option in the /etc/fstab file, or else you could've used that.

It's not the best way, but possibly change everybody's umask to make sure the new files are group writable, then set the sticky bit on the groupid on the external drive, so that new files & directories have the same group settings as the parent dir. That should fix it for you.

---

