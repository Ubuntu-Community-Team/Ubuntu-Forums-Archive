---
title: "step by step guide"
date: 2007-01-25
forum: General Help
---

### Post by insanitywetrust on 2007-01-25
hello
decided to try setting up a server on partition to run alongside win xp on dell pc
is there a website with step by step setup instructions?
kind of in middle of setup process and would like some sort of help instructions
thanks
brian (no brain today, it left in search of something i cannot remembr now)

---

### Post by meng on 2007-01-25
[www.psychocats.net/ubuntu/installing](www.psychocats.net/ubuntu/installing)

---

### Post by insanitywetrust on 2007-01-25
thanks, luckily i have the second computer... but alas, all the other info is on the server comp and cannot access the link supplied... i do remember the name...  hope this works

[crossin fingers and hitting wood]

---

### Post by insanitywetrust on 2007-01-28
hi there, ok, back and forth i go.... this time i will stick with this ubuntu...

so, the command line reads, 

loki44@alpha:~$ 

and well, now what? does anyone have a website i can look using this win xp computer and then find out what to do, i have seen some tutorials, but, i have not been able to figure how to install any, as i have yet to see a tutorial that shows that....

might be one of the experienced users can remember what helped them as then i can further help someone else in the future...

---

### Post by iamhugeinjapan on 2007-01-28
What do you want to use Ubuntu Server for?  We can point you in the right directions if we know that.

---

### Post by etank on 2007-01-28
insanitywetrust the Ubuntu server install does not install a GUI. This is because it is common to not run the GUI on a server to save CPU and Mem for serving web pages or storing data in a database. If you need a GUI you can run:
```
sudo aptitude install ubuntu-desktop
```
to get a Gnome interface or:
```
sudo aptitude install kubuntu-desktop
```
to get a KDE interface.
I hope that helps some.

---

### Post by insanitywetrust on 2007-01-28
hmm, the basic and most important objective is to get server going so i can host my own sites currently being hosted elsewhere and to start some radio player, as currently going with my sites now... as i use the two towers here, it would be ideal to have the current xp tower as is, and the new 'linux' tower as the server, accessible from the xp tower as far as the typical cpanel or similar interface as i do now with the sites i have... and then if needed can run the needed linux commands as i learn them.....

will take into consideration the linux desktop but for now, the server is where i would like to go with this

---

