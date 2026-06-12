---
title: "[SOLVED] How to change and save fstab?"
date: 2008-06-24
forum: General Help
---

### Post by paddy1 on 2008-06-24
I have been, trying to change permissions so I can write files to a floppy drive. I have spent hours in this forum trying to get a simple answer to a simple question, and I am beginning to think I have to be a guru programmer to understand what to do. Does anyone out there speak in layman's terms?

I was given commands for the terminal window, but how can I modify /etc/fstab here. I opened the folder in file system, modified it, but it won't allow me to save.

Please, if anyone speaks in layman's terms please help before I go crazy

---

### Post by drs305 on 2008-06-24
> **paddy1 said:**
> I have been, trying to change permissions so I can write files to a floppy drive. I have spent hours in this forum trying to get a simple answer to a simple question, and I am beginning to think I have to be a guru programmer to understand what to do. Does anyone out there speak in layman's terms?

I was given commands for the terminal window, but how can I modify /etc/fstab here. I opened the folder in file system, modified it, but it won't allow me to save.

Please, if anyone speaks in layman's terms please help before I go crazy

Yes, you have to open and edit the file with (substitute your editor if you don't use gedit):
```
gksudo gedit /etc/fstab
```

When you start it will ask for your password. You can only edit and save fstab by gaining temporary administrator powers. Not every user can 'mess' with system files, so you have to get temporary permission to do so by entering your password. Opening gedit or whatever text editor you use with a 'sudo' command gives you that power. 

If you haven't used sudo/gksudo, when it asks for your password you won't see it as you type. It's a security thing. Just type your password and hit Enter and that should open the file.

---

### Post by shad0w_walker on 2008-06-24
Just run this.

```
gksu mousepad /etc/fstab
```

Edit: drs305, please note the [xubuntu] at the topic, the required editor is mousepad, not gedit (Gnomes text editor and not included with xfce) just a reminder, otherwise the commands wont work and you could spend ages trying things then release it's something so simple.

---

### Post by drs305 on 2008-06-24
> **shad0w_walker said:**
> Just run this.

```
gksu mousepad /etc/fstab
```

Edit: drs305, please note the [xubuntu] at the topic, the required editor is mousepad, not gedit (Gnomes text editor and not included with xfce) just a reminder, otherwise the commands wont work and you could spend ages trying things then release it's something so simple.

Well, that's why I added the note about text editor, but apparently I was making the change while you correctly pointed this out. One of the few things I don't like about this forum is that I can't see the type of system (xbuntu) once I start typing and sometimes I forget to look. I'll try to do better.

---

### Post by shad0w_walker on 2008-06-24
I apparently missed that note about the editor (Or as you said, posted as you were editing) and don't worry about it, it happens to the best of us. I've posted a couple of times in areas then realised I was giving advice that was for the wrong DE,etc. Atleast you noticed and fixed it. :)

---

### Post by paddy1 on 2008-06-24
I was told to go to this website, where it tells me how to change permissions for the floppy access read/write for everyone [https://help.ubuntu.com/community/Ma...ableToEveryone](https://help.ubuntu.com/community/Ma...ableToEveryone).

I am ready to give up. I did as you reccommended, and changed /etc/fstab, and saved it according to the above wbsite commands.

I still cannot save a file to a floppy, and it just seems I've been beating my head against a brick wall.](*,)

I saved an Abi word file as a microsoft doc, to the user folder. I right clicked the file to 'send to floppy'. The floppy drive started, but nothing wrote to the floppy. When I clicked on the floppy drive icon, the floppy just kept spinning until I exited the floppy0 file manager.

Exasperated, but thank you for trying.

---

### Post by drs305 on 2008-06-24
> **paddy1 said:**
> Exasperated, but thank you for trying.


We feel your pain as we have all been there at one time or another. Don't worry, the wall your head is banging on gets softer with time. ;-)

If you were trying to edit fstab and think that is the problem, post the file and we can take a look at it.

```
cat /etc/fstab
```

---

### Post by paddy1 on 2008-06-24
Thanks for all your help folks, but it seems to be a bug in xubunto. 

I refurbish older computers and donate them to those in need, usually older Athlon and Celeron computers.

This is the third machine running Xubuntu, that will not save a file to a floppy.

There is no problem with the Ubunto distro 8.04, but only xubuntu XFCE 4.

I have reported this problem, so I guess it'll be wait and see.
Thanks again, paddy1

---

