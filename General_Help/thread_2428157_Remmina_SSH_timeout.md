---
title: "Remmina SSH timeout"
date: 2019-09-30
forum: General Help
---

### Post by mhockett on 2019-09-30
I'm a little new to linux, but having a strange issue with Remmina 1.3.6 on Ubuntu 18.04. I'm trying to SSH to cisco switches within my network. I can SSH via terminal or Putty, but when attempting via Remmina the ssh connection times out and fails. I can however ssh to other linux boxes via remmina. Any ideas would be greatly appreciated.

---

### Post by Skaperen on 2019-09-30
the only thought that has come to mind is the suggestion to try the real ssh program in a terminal at least as a test to see what is going on.

---

### Post by #&amp;thj^% on 2019-09-30
Had a couple of Cisco devices that wouldn't work until I erased and recreated the key. Just resetting the key on them didn't make a difference.

---

### Post by mhockett on 2019-09-30
I'll try a new key on a device... but I find it weird that terminal ssh and putty ssh are both fine... remmina on the other hand times out every time

---

### Post by #&amp;thj^% on 2019-09-30
> **mhockett said:**
> but I find it weird that terminal ssh and putty ssh are both fine... remmina on the other hand times out every time

So did I but it worked for me, and that's not saying it will for you.
Just a friendly suggestion. BTW I used 2K keys.

---

### Post by mhockett on 2019-09-30
no dice.... same issue

---

### Post by Skaperen on 2019-09-30
is there a reason you need to use Remmina?

---

### Post by mhockett on 2019-10-01
It was what I found that allows me to organize the multiple connections  points. I manage a college network with around 100+ switches. In windows  I used Mremoteng which allows me to organize devices into folders based  on where they are, and store default credentials or use alternate  credentials. basically once configured it saves a ton of time looking up  switch names, logging in and such.

---

### Post by mhockett on 2019-10-07
Any other suggestions... or things to check? I would like to be able to use this software if possible for the organizational benefits...

---

### Post by #&amp;thj^% on 2019-10-07
First try editing the security options from "negotiate" to "RDP" from the advanced tab.

And Apparently this happens when the keys on the tunnel server change.
```
rm ~/.freerdp/known_hosts
```
and try again.
Good Luck

---

