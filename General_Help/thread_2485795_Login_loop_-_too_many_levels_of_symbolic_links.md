---
title: "Login loop - too many levels of symbolic links"
date: 2023-04-10
forum: General Help
---

### Post by maj0rt0m on 2023-04-10
Hi everyone,

please excuse the short post, I am slightly stressed and have to write from my phone.
After I tried to install youtube-dl into my binaries yesterday, I can't start my Ubuntu Desktop environment anymore. Trying to do so from the GUI just resets the login screen and when I switch to the terminal it works but throws following error:

sh: 1: /usr/bin/env: too many levels of symbolic links

Here is the full terminal output:

Ubuntu 22.10 gibbosuspc tty3

gibbosuspc login: [name]
Password: 
sh: 1: /usr/bin/env: too many levels of symbolic links
Last login: Monday...


And the command which I ran before the problem occured:

sudo cp /usr/local/bin/youtube-dl /usr/bin/env

I appreciate any help and am glad to provide more info!

Best
Carroll

---

### Post by maj0rt0m on 2023-04-10
Uff, only now I realized how much I messed up.

I did overwrite env. Okay, I'll try to fix it and if successful post how I did it.

---

### Post by dragonfly41 on 2023-04-10
After you reverse and restore env 

to install youtube-dl run

pip3 install --upgrade youtube-dl

Taken from this discussion


[https://askubuntu.com/questions/1253678/how-to-set-environment-variable-for-the-updated-youtube-dl-installed-from-pip3](https://askubuntu.com/questions/1253678/how-to-set-environment-variable-for-the-updated-youtube-dl-installed-from-pip3)

I have just followed the workflow suggested.

---

### Post by maj0rt0m on 2023-04-10
I reinstalled coreutils, this fixed it.
Sorry for bothering (:

---

### Post by maj0rt0m on 2023-04-10
Thanks, I will now also use pip!

---

### Post by JmM4RCGXwJJUCt on 2024-01-05
@maj0rt0m, can you please describe how you went about fixing this? I've got the same problem, I think.

---

### Post by MAFoElffen on 2024-01-06
@djackson33 -- Since this is an old thread, which the OP looks like he just registered for this issue and never stayed... I would suggest that openning a new thread might get yo uhelp easier and faster.

Please described exactly what you did and the error your are getting.

---

