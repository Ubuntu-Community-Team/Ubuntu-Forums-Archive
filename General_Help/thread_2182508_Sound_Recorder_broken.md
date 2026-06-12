---
title: "Sound Recorder broken"
date: 2013-10-21
forum: General Help
---

### Post by arvevans on 2013-10-21
Sound Recorder asks for installation of files that apparently are not available.

[INDENT][IMG]https://docs.google.com/file/d/0B7Xo5h2IkKGqSFdRSksyTHAxZEU/edit?usp=sharing[/IMG]

arv@Workstation:~$ sudo apt-get install gsstreamer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gsstreamer
arv@Workstation:~$ 
[/INDENT]

Error message points to software that is not in the repository.

Thanks,
Arv
_._

---

### Post by Dennis N on 2013-10-21
You have a typo. It's **gstreamer**, not gsstreamer. Also, you need to add something to that to find any packages, most start with gstreamer0.10-

---

