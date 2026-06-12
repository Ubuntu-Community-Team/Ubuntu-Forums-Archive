---
title: "Evolution IMAP filter will not set label"
date: 2008-05-07
forum: General Help
---

### Post by @)--',------- on 2008-05-07
I have Evolution set up with Gmail via IMAP, however when I set a message filter on incoming mail to first set a label of "To Do", and then move to an IMAP folder it will not set the label.

I would like it to sort my mail, and set labels according to filters. My normal work process is to set the labels depending on the type of work order so I can see if I have done the task or not.  When I right click on a message and set its label "by hand" it changes the color and sets a label. I can then change its label when the task is completed. In Thunderbird, this was brain dead easy and worked without issue.

In Evolution Mail it will not set the label, will not change the color, and is not persistent when I set the label by  hand (tomorrow when I log in and sync with gmail, all hand set labels will not show up).

What am I doing wrong?

---

### Post by @)--',------- on 2008-05-13
No one is familiar with Evolution Mail and Gmail?

---

### Post by oscarjd74 on 2008-07-28
I have the same problem.

I'm using Evolution 2.22.3.1 on Ubuntu 8.04

I have several pop3 accounts and set up message filters to, among other things, automatically set labels on incoming messages. It doesn't work. Other filter action are taken (set status, move to folder, play sound etc.) but the message label remains unset.

I have reported a bug at:
[http://bugs.launchpad.net/ubuntu/+source/evolution/+bug/252503](http://bugs.launchpad.net/ubuntu/+source/evolution/+bug/252503)

Oscar

---

### Post by oscarjd74 on 2008-07-30
Based on the response I got from the bug report it seems that this problem arises if in the filter actions you first move the message to another folder and then set the label. At least in my case changing the order of the filter actions such that the label is set before the message is moved solved the problem. Hope this helps in your case too.

Oscar

---

