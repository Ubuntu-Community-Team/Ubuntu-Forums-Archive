---
title: "Tiny Problem..."
date: 2005-10-16
forum: General Help
---

### Post by Muhammad on 2005-10-16
I have two ext3 partitions, one which is 30+GB and the other is only 923MB. During Installation, I accedently mounted the Home Folder on the small partition, and I didn't notice this mistake until the installation was completed.

So my question is... Is it possible to move the home folder into the larger partition? If yes, How? If no, then I guess I'll just have to reinstall... :?

---

### Post by hassan on 2005-10-16
[QUOTE=Muhammad]I have two ext3 partitions, one which is 30+GB and the other is only 923MB. During Installation, I accedently mounted the Home Folder on the small partition, and I didn't notice this mistake until the installation was completed.

So my question is... Is it possible to move the home folder into the larger partition? If yes, How? If no, then I guess I'll just have to reinstall... :?[/QUOTE]
wat u think to change partition?   like Gparted .

---

### Post by mohaham on 2005-10-16
hope this link helps....
[http://www.ubuntuforums.org/showthread.php?t=46866](http://www.ubuntuforums.org/showthread.php?t=46866)

---

### Post by Muhammad on 2005-10-16
Hello Hassan, 

Nop I just want move the Home Folder to the Larger Partition.

Thanks for the link mohaham, I'm going check it out.

---

### Post by Muhammad on 2005-10-16
OK I found a simpler, yet non-fancy solution:

[list]```
sudo nautilus
```[/list]

[list]Move all the contents of the home folder into another one in "/"[/list]

[list]gedit /etc/fstab and change the mount from /home to /newpart for example, and don't forget mkdir the newpart in "/", followed by "sudo mount -a"[/list]

[list]**Ctrl+Alt+Backspace**[/list]

[list]**Ctrl+Alt+F7**[/list]

[list]```
sudo nautilus
```[/list]

[list]re-move the contents of the home folder into the home folder itself[/list]

Pretty Cool, huh!

---

### Post by kvidell on 2005-10-16
you could always move the contents of /home to /someplace/else then do a symlink through /home to the new user directories...
orr....
just remove the small partition from /etc/fstab so it isn't mounted anymore then create home in /...

There's probably a bunch of ways to fix this.
-Kev

---

### Post by Muhammad on 2005-10-16
Yep, I agree with you.

---

