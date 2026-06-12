---
title: "burning an audio cd k3b mp3s"
date: 2006-12-22
forum: General Help
---

### Post by JPMaximilian on 2006-12-22
I'm trying to burn an audio cd, I drag mp3s to a new audio cd project in k3b, and I get the error that it is an unsupported format.  What dependency do I need to download?

---

### Post by bruenig on 2006-12-22
> **JPMaximilian said:**
> I'm trying to burn an audio cd, I drag mp3s to a new audio cd project in k3b, and I get the error that it is an unsupported format.  What dependency do I need to download?

```
sudo apt-get install libk3b2-mp3
```

It is in universe so make sure you have that enabled.

---

### Post by JPMaximilian on 2006-12-22
Thank you much!

---

### Post by sween1911 on 2007-01-04
I'm having the same problem. I try that command and I get the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libk3b2-mp3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libk3b2-mp3 has no installation candidate


Does this have something to do with enabling "universe"? What is that?

---

### Post by pay on 2007-01-04
```
sudo nano /etc/apt/sources.list
``` and then add universe next to the lines that don't have it.

---

### Post by sween1911 on 2007-01-04
> **pay said:**
> ```
sudo nano /etc/apt/sources.list
``` and then add universe next to the lines that don't have it.

I spoke too soon. I found the sources file, uncommented two lines that have a comment above them that uncommenting the below two lines will allow you to install software from the universe.

I get the following:
%sudo apt-get install libk3b2-mp3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libk3b2-mp3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libk3b2-mp3 has no installation candidate

Do I need to do something for the sources file to be recognized?
 
------------------------------------
EDITED: I think I got it! Sources, updating repository, yadda yadda. I found it in my package manager! Let's see if this does the trick.....

---

### Post by pay on 2007-01-04
Yes```
sudo aptitude update
```

---

### Post by sween1911 on 2007-01-05
I'm good to go, thanks!

---

### Post by Mithrilhall on 2007-01-05
> 
and then add universe next to the lines that don't have it.

Did you mean multiverse?

---

### Post by pay on 2007-01-05
> **Mithrilhall said:**
> Did you mean multiverse?Well he asked for the universe repository, but he could add the multiverse repo aswell if he wants. I don't know which repo mp3 stuff is in so you might need to add multiverse aswell.

---

### Post by sween1911 on 2007-04-25
How can I get k3b to recognize .wav files? I try to drag and drop them in and it says "unsupported format". How do I fix that?

---

