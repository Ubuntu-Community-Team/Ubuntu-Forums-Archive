---
title: "Permissions - help :)"
date: 2007-04-13
forum: General Help
---

### Post by cris on 2007-04-13
I copied my backed-up data from a hdd to my home folder , but i can't see what's inside those folders , can't acces data , nothing. 
I tried to change the owner  to myself , but it still wouldn't give me full access. 
I read somewhere to use sudo nautilus , and did so , to change the permissions using the gui. But even as a root it didn't let me do that , as I wanted full acces for my user. What should I do ? 10x

---

### Post by m.musashi on 2007-04-13
How did you change the permissions?
```
sudo chown -R username:username /path
```
should chage permissions for all files in a folder. Is that how you did it?

Also, when using nautilus as root run with gksudo.
```
gksudo nautilus
```

---

### Post by cris on 2007-04-14
actually , what I did was sudo chown "user" "dir" , and that's what gave me headache. 
with the -R it worked fine .
Now , another issue : after messing around with "sudo nautilus" and trying to change the permissions using the gui , when i login , it gives me a warning , something about the permissions for my home directory , it says something about dir .dmrc being ignored , and that i shoud have 644 permissions  etc.etc. I'll try to put out the original text later. How can it be fixed ?

---

### Post by m.musashi on 2007-04-14
Hmmm, I'm not entirely sure what is going on now. It's kind of late now, but the best thing to do is not change permissions at all. The default setup is designed to work properly. If you have a file or folder you want to restrict access to then it's fine to change permissions but make sure you are only doing that in your home folder. Sometimes when you do things with sudo root takes over a file that it should not have. That is why it's best to be careful with sudo and also to use gksudo when using a GUI app as root.
```
gksudo nautilus
```

To change the read/write/execute of a file use chmod.
```
sudo chmod 644 /path
```
You can also use the -R option to change everything in a folder
```
sudo chmod -R 644 /path
```
I don't mean to beat a dead horse but be careful with these commands. You can really mess things up (trust me I know from unfortunate experience). I keep /home on its own partition and if things get too messed up I can reinstall and not lose any files or settings. Of course, if it's your /home that is messed up that doesn't work.

---

