---
title: "synoptic menu"
date: 2008-05-01
forum: General Help
---

### Post by madsurfer on 2008-05-01
Hi

I have recently updated my Ubuntu machine to 8.4 but whilst using it my synoptic manager menu has disappeared 


Can anyone suggest a way to get it back, thanks

Adrian

---

### Post by mali2297 on 2008-05-01
> **madsurfer said:**
> Hi

I have recently updated my Ubuntu machine to 8.4 but whilst using it my synoptic manager menu has disappeared 


Can anyone suggest a way to get it back, thanks

Adrian

Does it mean that you can't do any administrative tasks? 

It might be the same problem as in [this thread]("http://ubuntuforums.org/showthread.php?t=767497"), a solution is posted at the end. Check the files **/etc/hostname** and **/etc/hosts**.

---

### Post by forrestcupp on 2008-05-01
Are you using Ubuntu with Gnome, or Kubuntu?

Try to type in a terminal
```
gksu synaptic
```and if it doesn't work, post the output.

---

### Post by madsurfer on 2008-05-01
Am using gnome! and there is no output as nothing runs!

---

### Post by mali2297 on 2008-05-01
In a terminal, run
```

sudo echo test

```
Any errors?

---

### Post by madsurfer on 2008-05-01
Ubuntu will not let me switch to root! So I cant run gksu synaptic?

what should I do next?

Adrian

---

### Post by mali2297 on 2008-05-01
So you didn't get any error message like *unable to resolve host*?

Anyhow, see if this might help:
[http://ubuntuforums.org/showthread.php?t=770801?post=#2](http://ubuntuforums.org/showthread.php?t=770801?post=#2)

---

### Post by madsurfer on 2008-05-05
> **mali2297 said:**
> In a terminal, run
```

sudo echo test

```
Any errors?
yes doinging this "Echo" produces the following, adrianr@geko80:~$ sudo echo test
sudo: unable to resolve host geko80
 I also canot switch to root anymore!
!!!
Adrian

---

### Post by madsurfer on 2008-05-05
> **madsurfer said:**
> yes doinging this "Echo" produces the following, adrianr@geko80:~$ sudo echo test
sudo: unable to resolve host geko80
 I also canot switch to root anymore!
!!!
Adrian
Hi have been away for a few days so have not replied to above post!!
Adrian!

---

### Post by madsurfer on 2008-05-05
> **madsurfer said:**
> yes doing this "Echo" produces the following, adrianr@geko80:~$ sudo echo test
sudo: unable to resolve host geko80
 I also canot switch to root anymore!
!!!
Adrian
Hi have been away for a few days so have not replied to above post!!till now
Adrian!

---

