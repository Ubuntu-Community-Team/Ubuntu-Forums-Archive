---
title: "how do I change menu.lst in kubuntu?"
date: 2008-03-07
forum: General Help
---

### Post by jammeramd64 on 2008-03-07
I know how to do it in ubuntu , sudo gedit  /boot/grub/menu.lst. 
               But how do you do that in kubuntu, 
               I dual boot windows vista and linux kubuntu7.10, and want to make the default                     
               windows vista for now....
               I know you have to change the default from 0 to 4, I just don't know what program or package will do that via sudo root ?? Any help would be appreciated 
               Thanks in Advance .... jammeramd64

---

### Post by Arthur Archnix on 2008-03-07
EDIT: According to the post below, gksudo might not work and kdesu would. 

I think kate is the text editor, which would make the command:
```
gksudo kate /boot/grub/menu.lst
```If I'm wrong though just use nano,
```
sudo nano /boot/grub/menu.lst
```

---

### Post by Snakob808 on 2008-03-07
Terminal editor:

```
sudo vim /boot/grub/menu.list
```
 
or...
graphical...

```
kdesudo kate /boot/grub/menu.list
```

---

### Post by PinkFloyd102489 on 2008-03-07
Nano is much easier to use than vim. If you're going go terminal, use nano. Kate is actually the best way to go, as you can point and click.

---

### Post by jammeramd64 on 2008-03-07
Thanks all...  kdesudo kate /boot/grub/menu.lst ...did the trick, in a gui even too  kewl ..
Thanks again ALL ...... jammeramd64

---

### Post by PinkFloyd102489 on 2008-03-07
Just a note, the KDE equivalent of gksudo is kdesu.

---

