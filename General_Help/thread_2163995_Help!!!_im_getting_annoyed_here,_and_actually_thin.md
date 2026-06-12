---
title: "Help!!! im getting annoyed here, and actually thinking of re-installing windows"
date: 2013-07-20
forum: General Help
---

### Post by 7hr08ik on 2013-07-20
Ive got another thread about my main issue, but i wanted to start this one, to try and get answers to 2 questions

1. In shell script how to get the "if" command to figure out what /dev/ the OS drive is on. (i.e. if the OS drive is on sda then do this, but if not, do this)

2. How to stop the rest of the dammed hard drives from changing /dev/ positions everytime the computer starts up!!!! I have a script to mount o few truecrypt HDDs i have. But everytime i restart the PC, they are allocated to totally different /dev/ points. For exsample, one of my drives contains backups. My script has is set to mount sdd1 (the backups drive) to /dev/backups but when i restart it was mounting the music drive to that point, or it might be another drive......not good for my links, and librarys, and automated background programs.

---

### Post by DeathByDenim on 2013-07-20
For your first question, you can use something like this:
```
OSDRIVE=`mount|grep "on / "|cut -d' ' -f1`
```
That will set the variable OSDRIVE to "/dev/sda1". You can then use that in if-statements if you like.

For the second part of your question, you could look into udev rules. They allow you to assign permanent names to your drives based on the serial number for example. See for example [http://reactivated.net/writing_udev_rules.html#sysfsmatch](http://reactivated.net/writing_udev_rules.html#sysfsmatch)
I don't really understand why your drive names keep switching around though. Weird.

---

### Post by 7hr08ik on 2013-07-20
Its coz i have only 4 SATAs on my mobo, but 6 total HDDs. So i have a PCI extention card for the 2 other drives. Problem is sometimes they mount at /dev/sda /dev/sdb other times they are /dev/sdc /dev/sdef they randmly change, and that makes all the others change about.

I`ll take a look at the udev though, if i can force all the drives to be on the same /dev/ everytime, then most of my problems are gone :P

---

### Post by DeathByDenim on 2013-07-20
Actually, another thought occurred to me. You can simply use the UUID's to mount the desired hard disk. It's what Ubuntu uses by default in /etc/fstab anyway. See here for an more details: [http://centoscert.com/content/how-mount-drive-uuid](http://centoscert.com/content/how-mount-drive-uuid)
You should be able to manually mount partitions using the UUID with the -U parameter for mount. See the man pages for that.

---

### Post by 7hr08ik on 2013-07-20
Tried that already, wont work with truecrypt as i have fully encrypted the drives. If i run blkid with the drive UN-mounted, i only get a response for the OS drive. So the drives need to be mounted for the UUID to be gained....this is why i have been having the problems....I like the look of the udev custom rules, just need to figure out what the hell im doing....

With that i should be able to allocate the 5 encrypted drives, to specified /dev/sd** and then i can use my script to mount each /dev/sd** to my specified mount point, and keep all of my librarys, and links working.

---

