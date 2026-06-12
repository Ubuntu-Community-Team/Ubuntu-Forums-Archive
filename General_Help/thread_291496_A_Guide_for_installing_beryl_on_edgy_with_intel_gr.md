---
title: "A Guide for installing beryl on edgy with intel graphicscard?"
date: 2006-11-02
forum: General Help
---

### Post by jincast90 on 2006-11-02
Can anyone recommend me a guide for how to install beryl on edgy eft with an intel graphics card?

---

### Post by ronmarley1 on 2006-11-02
I have the Intel 855 using the 810 driver on my IBM R51 laptop and this worked for me.  Should not take more than 5 minutes (simple copy/paste from web site to terminal).
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)
Add "beryl-manager" to your start up programs to have it load at boot.  Also, there's a bug with the latest Beryl release.  Add "emerald" to your start up programs list to fix the bug.  (It's been reported to their bug tracker.)

---

### Post by jincast90 on 2006-11-02
> **ronmarley1 said:**
> I have the Intel 855 using the 810 driver on my IBM R51 laptop and this worked for me.  Should not take more than 5 minutes (simple copy/paste from web site to terminal).
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)
Add "beryl-manager" to your start up programs to have it load at boot.  Also, there's a bug with the latest Beryl release.  Add "emerald" to your start up programs list to fix the bug.  (It's been reported to their bug tracker.)

Ok I've been looking through the guide and I have been wondering what this means: Make sure to get the public key for the repository. 

Can someone tell me what I'm suppose to do when it says I have to Make sure to get the public key for the repository.

Thanks.

---

### Post by dboot on 2006-11-02
You have to request a public key to use the repository. After you add the repository to your sources.list file, ask for a public key by running the given command.

All this means is:

Add this line to to /etc/apt/sources.list:

```
deb http://ubuntu.beryl-project.org/ edgy main-edgy
```

Then run this in the terminal:

```
wget http://ubuntu.beryl-project.org/quinn.key.asc -O - | sudo apt-key add -
```

and then

```
sudo apt-get update
```

---

### Post by mike41 on 2006-11-02
> **ronmarley1 said:**
> I have the Intel 855 using the 810 driver on my IBM R51 laptop and this worked for me.  Should not take more than 5 minutes (simple copy/paste from web site to terminal).
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)
Add "beryl-manager" to your start up programs to have it load at boot.  Also, there's a bug with the latest Beryl release.  Add "emerald" to your start up programs list to fix the bug.  (It's been reported to their bug tracker.)

I added "emerald --replace" to the startup. Im not sure if only adding "emerald" will work.

---

### Post by ronmarley1 on 2006-11-02
> **mike41 said:**
> I added "emerald --replace" to the startup. Im not sure if only adding "emerald" will work.
I've read at the Beryl forums that "emerald --replace" works for some and just "emerald" works for others.  "emerald" was the first one I tried and it has worked for me.

---

