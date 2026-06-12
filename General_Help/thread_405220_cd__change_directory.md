---
title: "cd ? change directory"
date: 2007-04-09
forum: General Help
---

### Post by fseigert on 2007-04-09
Hi,
i opend with Edgy 6.10 a terminal. I don´t know how i can go from desktop menu to base file system. Tried with cd \ but i don´t work. Doing sudo -s also don´t work with cd. Wanting to change a file to allow to write. 
Can somebody help me?
Frank

---

### Post by finferflu on 2007-04-09
You should use / instead of \, I think that's your problem ;)

---

### Post by Falcorian on 2007-04-09
> **finferflu said:**
> You should use / instead of \, I think that's your problem ;)

That's probably it.

In the Linux terminal, directories are separated by / so:

```
/home/fseigert
``` 
or 
```
/media/ipod
```
or similar.

The \ is an escape character, and tells the terminal to not treat the next character as it normally would. For example (a bad one...) & puts a process in the background, but maybe you want to list files that contain & (I'm not sure that's legal, but will assume it is), you'd do something like:

```
ls *\&*
```

You also use \ when you have spaces in a file name to escape the spaces, and tell the terminal that you mean a space in the filename, and not a new entry.

---

### Post by Kizilbas on 2007-04-09
If you want to go to root then:


cd /root

---

### Post by maheshjagadeesan on 2007-04-09
> **fseigert said:**
> Hi,
i opend with Edgy 6.10 a terminal. I don´t know how i can go from desktop menu to base file system. Tried with cd \ but i don´t work. Doing sudo -s also don´t work with cd. Wanting to change a file to allow to write. 
Can somebody help me?
Frank

a. Use / instead of \, as the others have mentioned
b. If you own the file whose permission you want to change, then you really don't have to sudo, all you have to do is 
```
chmod +w <filename> 
```
In case the file is somebody else's, then you might have to do 
```
sudo chmod o+w <filename>
```

HTH.

---

### Post by fseigert on 2007-04-09
Hi!
Thanks to all!
Yes it was the mistake with the / \. I was very in doubt with me for that reason.
And sudo chmod 777 goes ok. 
Frank

---

