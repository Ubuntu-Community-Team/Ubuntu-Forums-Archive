---
title: "Problem on installing with terminal in 12.04"
date: 2013-04-17
forum: General Help
---

### Post by tc101 on 2013-04-17
I have not used the terminal since installing 12.04.  

I don't know why terminal opens to 
tom@tom-OptiPlex-755:~$

I don't use terminal much, but as I remember it used to just open to tom

I just tried to install ruby and got the message below

> 
tom@tom-OptiPlex-755:~$ apt-get install ruby1.9.1
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
tom@tom-OptiPlex-755:~$ 


---

### Post by ibjsb4 on 2013-04-17
You forgot sudo

sudo apt-get install ruby1.9.1

---

### Post by slickymaster on 2013-04-17
> **tc101 said:**
> ...
I don't know why terminal opens to 
tom@tom-OptiPlex-755:~$

I don't use terminal much, but as I remember it used to just open to tom
...

Before the '**@**' it's your username, the name that is used for your user menu, your home folder, and behind the scenes. After the '**@**' it's name your computer uses, for terminals and networks.
These values/attributes were defined by you at Ubuntu installation time.

---

### Post by Impavidus on 2013-04-18
That is to say, your user name and the computer's name have you defined (wait, is it proper english to use object – verb – subject as a marked word order? I mean non-default, but adding stress to the object.). The format of the prompt is the default and has been the default since ancient times in computer history. You can change it, it's somewhere in your bash configuration.

---

