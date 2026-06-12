---
title: "Cannot run Skype"
date: 2019-05-23
forum: General Help
---

### Post by emcquinn8 on 2019-05-23
I am unable to launch Skype from the Ubuntu software center. Running ubuntu 18.10.

I get an error message: "Unable to download updates from 'extensions.gnome.org':......cannot resolve hostname.

How do I get skype to run for me?

---

### Post by dino99 on 2019-05-23
which extension is it ? Maybe the source does not not exist for 18.10

---

### Post by emcquinn8 on 2019-05-23
> **dino99 said:**
> which extension is it ? Maybe the source does not not exist for 18.10


*/*/*/source/*shell-extensions/*

---

### Post by dwhitifled on 2019-05-23
Can you run skype from the command line as a test?

If you can't, I don't know what we'll see, but we might see something interesting if you run 'strace skype' from the command line. 

If you can run Skype from the command line, that tells us it is not a problem with Skype.

Are you able to launch other applications from the software center?

---

### Post by emcquinn8 on 2019-05-24
> **dwhitifled said:**
> Can you run skype from the command line as a test?

If you can't, I don't know what we'll see, but we might see something interesting if you run 'strace skype' from the command line. 

If you can run Skype from the command line, that tells us it is not a problem with Skype.

Are you able to launch other applications from the software center?

When I entered 'strace skype' in the terminal, skype did not open. I got a long amount of code from terminal, but skype did not open.

I am able to launch rhythmbox from the software centre, as well as terminal.

---

### Post by emcquinn8 on 2019-05-27
It's ok. I found skype and it is running fine now.

---

