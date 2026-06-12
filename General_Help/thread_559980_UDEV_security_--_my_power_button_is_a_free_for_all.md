---
title: "UDEV security -- my power button is a free for all!"
date: 2007-09-25
forum: General Help
---

### Post by nfox on 2007-09-25
Hi, thanks for help... I installed gizmodo and want to make my XBOX controller work as a mouse/keyboard. Their site makes registering devices under a user "input" pretty easy. Problem is that when I 
#:     ls -al /dev/input/

it shows that "input" owns the devices and I'm a part of that group. Great.
But running gizmodo shows:

    Standard - Power Button (FF) [/dev/input/event5]
    Standard - Power Button (CM) [/dev/input/event6]
    Standard - Sleep Button (CM) [/dev/input/event7]

I don't like these buttons being open to anyone but root since the previous command (ls -al /dev/input) shows:

crw-rw----  1 root input   13,  69 2007-09-25 20:37 event5
crw-rw----  1 root input   13,  70 2007-09-25 20:37 event6
crw-rw----  1 root input   13,  71 2007-09-25 20:37 event7

My question is how do I restore those buttons to keep a hacker from bringing down my box??

---

### Post by nfox on 2008-01-17
I've noticed that nobody is answering this question.....

I assume that I need to edit the group's permissions to a comfortable level. I don't know how to do this because the group needs root access to get the device. 

So.............

---

