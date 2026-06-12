---
title: "Change /home's partition"
date: 2015-02-13
forum: General Help
---

### Post by Paul_Cambal on 2015-02-13
Hello everyone,
I currently have installed on my laptop both elementary os and Ubuntu. I want them to use the same partition for /home, even if I have to use separate folders in that partition.
I thought it'd be rad to use

```
usermod -m -d /path/to/new/home/[COLOR=#C20CB9]**dir**[/COLOR] userNameHere
```

I dont trust workarounds of other guys doing weird things like him: [http://www.maketecheasier.com/move-home-folder-ubuntu/](http://www.maketecheasier.com/move-home-folder-ubuntu/)
The problem is, what address do I have to type in, to point to another partition? /dev/sda#/mynewuser?
Btw, I dont need any backup, I have no files yet on my brand new os.
Thank you very much :)

---

### Post by oldfred on 2015-02-13
Do not share /home, you will get conflicts.

But you can create a shared data partition, so all your data folders like Music, Documents, Video etc are shared.

       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

