---
title: "Slow boot"
date: 2007-02-14
forum: General Help
---

### Post by dmsn on 2007-02-14
Hey
Ubuntu edgy boot really much slower than dapper.
Can i fix so it can booter faster or something?

---

### Post by mssever on 2007-02-14
It's hard to know for sure without more specifics, but as a general rule, you should uninstall anything that you don't need that's being started at bootup.

If you want a more verbose bootsplash (like Dapper had) so you can see what's being started, hit e at the grub prompt. Then find the line for the kernel command line, and hit e again. Remove quiet from the options, hit enter then b.

---

### Post by mean6 on 2007-02-14
what command can you use to make this change permanent.
I know you can login as root and edit the menu.lst file to delete the /quiet part of the line.
But is there a command to do this from a terminal. Im very very new to linux so my knowledge is limited. but going by the threads i read you can use the sudo coomand to do heaps of "stuff". 

For a noob
What exactly do i type in from a prompt say if im already logged in and have a terminal open to change the menu.lst file.

Thanks in advance heaps

---

### Post by mssever on 2007-02-14
> **mean6 said:**
> what command can you use to make this change permanent.
I know you can login as root and edit the menu.lst file to delete the /quiet part of the line.
But is there a command to do this from a terminal. Im very very new to linux so my knowledge is limited. but going by the threads i read you can use the sudo coomand to do heaps of "stuff". 

For a noob
What exactly do i type in from a prompt say if im already logged in and have a terminal open to change the menu.lst file.

Thanks in advance heaps

sudo basically gives you root privileges for any command that you put sudo before.

To edit files from the command line, you need a text editor. nano and mcedit are probably the easiest to learn, joe is more powerful, and vi (technically vim) is professional-quality with a really steep learning curve.

So, you could do ```
sudo nano /boot/grub/menu.lst
```

Remember that every time you change menu.lst, you need to do ```
sudo update-grub
``` afterward.

---

### Post by dmsn on 2007-02-15
How can i find which programs starts when i boot without change my bootsplash?

---

### Post by mean6 on 2007-02-15
thanks heaps mssever

---

### Post by mssever on 2007-02-15
> **dmsn said:**
> How can i find which programs starts when i boot without change my bootsplash?
That isn't really easy. You can look in /etc/init.d/rc2.d, and everything with a name beginning with S runs at startup, but it isn't the complete picture. Edgy uses a new boot method in addition to the traditional one, and I don't know where its configuration files are kept. The easies thing is to do as I suggested earlier and modify your boot parameters. If you do it by means of the GRUB menu, the changes you make get reset next time you boot.

---

