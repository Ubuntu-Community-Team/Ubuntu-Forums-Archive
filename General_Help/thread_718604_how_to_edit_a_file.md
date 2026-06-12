---
title: "how to edit a file"
date: 2008-03-08
forum: General Help
---

### Post by d_deniz on 2008-03-08
hello
I have a sound problem and I find a solution on this forum, I want to edit alsa-base file which is at /etc/modprobe.d/alsa-base but i cant save it, it says you dont have the permission. ok, it says in prop. root can edit the file. how can I edit a line to this file by root or by another way 
thanks
deniz

---

### Post by unutbu on 2008-03-08
```

sudo gedit /etc/modprobe.d/alsa-base

```

In general, you prefix commands with the word 'sudo' when you want superuser (root) privileges. It will ask for a password; just give your own. The first user account is always given this ability.

---

### Post by d_deniz on 2008-03-08
thank you for reply
when I wrote the code it opened a blank page
and I wrote my line there
when I wanted to save and quit, it gave the error " file not found", however the file is exactly there, do I miss something?

---

### Post by scrooge_74 on 2008-03-08
Check that you typed correctly the command, is easy to miss type

---

### Post by Fleece Flamingo on 2008-03-08
> **d_deniz said:**
> thank you for reply
when I wrote the code it opened a blank page
and I wrote my line there
when I wanted to save and quit, it gave the error " file not found", however the file is exactly there, do I miss something?Try writing the appropriate file extension and double check to see if the path is correct.

---

### Post by d_deniz on 2008-03-08
what is the extension for this alsa-base file? It is in the /etc/modeprobe.d/alsa-base. with which name should I save it?

---

### Post by gerscht on 2008-03-08
you can also just open an editor with
```
sudo gedit
```
and browse for the file if you like it more 'pointy-and-clicky' ;-)

---

### Post by Nythain on 2008-03-08
grrrrr....
sudo for command line apps
gksu for graphical apps *cough*gedit*cough
kdesu for graphical apps in kde *cough*kate*cough*

---

### Post by gerscht on 2008-03-08
> **Nythain said:**
> grrrrr....
sudo for command line apps
gksu for graphical apps *cough*gedit*cough
kdesu for graphical apps in kde *cough*kate*cough*
ups, cheers for that.

---

### Post by Nythain on 2008-03-08
hehe... more "good practice" than major trouble maker, 9 times out of 10 sudo will do the trick without harm... its just that 1 time that really sucks :)

---

