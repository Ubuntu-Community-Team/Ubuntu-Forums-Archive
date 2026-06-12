---
title: "apache2 installation issue"
date: 2017-10-25
forum: General Help
---

### Post by bloodinside on 2017-10-25
Hello everybody.
I am trying to install apache2 on my ubuntu15.10 but I am facing some troubles.
 When I type ''sudo apt-get install apache2'' in my terminal I got "*unable to locate* *some* [I]packages".
[/I]I've looked for a fix through the internet but what I have read did not work. 
```
sudo apt-get update
```, ```
sudo apt-get update --fix-missing
``` and ```
sudo apt-get upgrade
``` did not solve the issue (I got the "*Some index files failed to download. They have been ignored, or old ones used*" error).
I've read that it may be some repository-related issue, but I do not know where to start to fix this.

Thank you for your help.

---

### Post by mörgæs on 2017-10-25
Hi, welcome to the fora.

15.10 is out of support. That's why you get the error.

I recommend a fresh install of 16.04.3 or 17.10 (the former might give you an old version of the LAMP components). Apply all updates and reboot. 

If you want the entire LAMP stack then copy and paste the code ```
sudo apt install lamp-server^
``` to the terminal, run it and reboot again afterwards.

---

