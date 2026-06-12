---
title: "Sudo apt-get problem"
date: 2020-04-09
forum: General Help
---

### Post by eddyarthur on 2020-04-09
Hi there,

Despite reading through threads addressing similar issues, I'm struggling to find out how to fix my problem using the sudo apt-get command on terminal. Here's what I get each time:

E: Type &#8216;sudo&#8217; is not known on line 2 in source list /etc/apt/sources.list.d/windscribe-repo.list
E: The list of sources could not be read.

Can anyone help me with this?

Thanks,

E

---

### Post by TheFu on 2020-04-09
please post the exact command and output, wrapped in code tags.

---

### Post by deadflowr on 2020-04-09
It reads as if sudo is actually in the source entry in the file /etc/apt/sources.list.d/windscribe-repo.list
(Hint: it should not be)
Post what
```
cat /etc/apt/sources.list.d/windscribe-repo.list
```
shows.

---

### Post by eddyarthur on 2020-04-11
Hi, thanks,

This is what comes up when I entered: cat /etc/apt/sources.list.d/windscribe-repo.list   - 


sudo apt-get update


First line was empty, second line had: sudo apt-get update

Thanks,

Eddy

---

### Post by speartip on 2020-04-11
There's your problem.
You cannot have anything like "sudo apt-get update" in a sources list. You need to delete the windscribe-repo.list file from the sources .list.d folder & add the repo again correctly.

---

### Post by eddyarthur on 2020-04-11
Ok thanks, although I'm afraid I don't know how to do that.

---

### Post by deadflowr on 2020-04-11
yeah, run
```
sudo rm /etc/apt/sources.list.d/windscribe-repo-list
```
then if you need the repo follow the guidance from here:
[https://windscribe.com/guides/linux]("https://windscribe.com/guides/linux")
it would seem you missed or mixed up a step at some point.

---

### Post by TheFu on 2020-04-11
> **eddyarthur said:**
> Ok thanks, although I'm afraid I don't know how to do that.

Start with 
```
sudo rm /etc/apt/sources.list.d/windscribe-repo.li*
sudo apt update
sudo apt dist-upgrade
```

if the last 2 commands work well, a reboot could be needed.

---

### Post by eddyarthur on 2020-04-11
Thanks everyone, that all really helped.

---

