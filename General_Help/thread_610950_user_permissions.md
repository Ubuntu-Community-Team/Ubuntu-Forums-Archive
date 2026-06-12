---
title: "user permissions?"
date: 2007-11-12
forum: General Help
---

### Post by jgeeting on 2007-11-12
I goofed up and took away my user permissions, and of course now I can't log in. Is there a way to get my user permissions back as root though the command line? Is it part of FSTAB?

---

### Post by taurus on 2007-11-12
I am a little confused.  You can't log in with your regular account or you can't log in as root?  Did you change permissions of your $HOME directory?

---

### Post by jgeeting on 2007-11-12
I think that is what I did, I kept getting message about sharing my home directory on my network. I highlighted the home folder, right clicked, permmisions tab, and left the top item alone but set the second two, I'm thinking one was "group" and the second item was "others" both to" list files only"... 

I guess I could run the live cd to give you a better description of what I did... I took a shot at fstab a while back and I thought the home directory was listed there?

---

### Post by taurus on 2007-11-12
Boot into recovery mode from GRUB menu and post the output of the output of this command from a prompt.

```
ls -la /home
```
What is your login name because you might need to change it back so you can log into your $HOME directory.

---

### Post by jgeeting on 2007-11-12
ls -la /home

total 12
drwxr-xr-x root root 4096 nov 2 13:16 .
drwxr-xr-x root root 4096 nov 2 12:54 ..
drw-rw-rw joe joe 4096 nov 2 13:06 joe

sorry had to hand write - dual boot laptop

---

### Post by taurus on 2007-11-12
Boot into recovery mode from GRUB menu and run

```
chmod -R 755 /home/joe
chmod 644 /home/joe/.dmrc
ls -la /home
```

Now, you should be able to log into your $HOME, /home/joe, with no problem.

---

### Post by jgeeting on 2007-11-12
problem solved - thank you for your help... 

I'll change the header...

---

