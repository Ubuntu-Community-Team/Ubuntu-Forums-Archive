---
title: "Help installing build-esential"
date: 2006-09-02
forum: General Help
---

### Post by Chris85r on 2006-09-02
I am a newbie to linux, and i am trying to install build-essential. This is what i get:
 
 christopher@christopher-laptop:~$ sudo apt-get update
 Password:
 Reading package lists... Done
 christopher@christopher-laptop:~$ sudo apt-get install build-essential
 Reading package lists... Done
 Building dependency tree... Done
 E: Couldn't find package build-essential
 
 
 
 PLEASE HELPME

---

### Post by Titus A Duxass on 2006-09-02
That should work, I believe the build-essential is on the CD.

Try editting /etc/apt/sources.list remove the # from each line that looks like a URL.

Do aptitude update then try installing build-essential.

---

### Post by Dinerty on 2006-09-02
Isn't build-essential in synaptic package manager mate?

---

### Post by taurus on 2006-09-02
If I am not mistaken, he already solved the problem...

---

