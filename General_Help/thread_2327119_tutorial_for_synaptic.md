---
title: "tutorial for synaptic"
date: 2016-06-07
forum: General Help
---

### Post by Joe_Zien on 2016-06-07
I can't install synaptic on ubuntu 16.04.
Downloaded synaptic.deb and couldn't install with
# dpkg -i synaptic nor with #apt-get install synaptic.
Is there a tutorrial to install synaptic.

jozien

---

### Post by vasa1 on 2016-06-07
*sudo apt-get install synaptic*?

Run that as a normal user. No need of becoming root as implied by the "#" signs in your post.

---

### Post by Bucky Ball on 2016-06-07
Best to check in the official repositories (Software Centre or Gnome Software, depending on release) before going for third-party .deb files before installing software. You'll find hundreds of things there and the safest and easiest way to go. Good luck. :)

---

### Post by lisati on 2016-06-08
If you're following someone else's instructions, you won't normally need to include the *#* or *$* that at the start of a command line. If you're running as a normal user, try:
```
sudo apt-get install synaptic
```

---

### Post by coldraven on 2016-06-08
Tutorial is here, a slightly old version is pictured but it works the same as the latest one.
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

