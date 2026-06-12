---
title: "System Timer"
date: 2007-12-16
forum: General Help
---

### Post by Conspirator45 on 2007-12-16
I am going away on holidays soon. I wish to leave my computer on to download some things. Is it possible to set my computer to shut down after the downloads are finished? I am using to download the files via BT. I would be happy to change to another client to do this. If thats not possible can I just set a timer to turn off my computer after a week? Thanks in advance.

---

### Post by Conspirator45 on 2007-12-18
so...nobody can be of any help?

---

### Post by Conspirator45 on 2007-12-18
=(

---

### Post by sstusick on 2007-12-18
I am sure there is a way to accomplish this... have you tried searching the forum?

---

### Post by Conspirator45 on 2007-12-19
I have found a way to do it. With cron. Now if anyone could help me with the editing and what i need to put in...

---

### Post by FuturePilot on 2007-12-19
> **Conspirator45 said:**
> I have found a way to do it. With cron. Now if anyone could help me with the editing and what i need to put in...

I think Gnome Schedule can help with this. Gnome Schedule is a GUI front end to Cron.
```
sudo apt-get install gnome-schedule
```
;)

---

### Post by Conspirator45 on 2007-12-19
Thanks for the prompt help.

---

### Post by ~LoKe on 2007-12-19
Bah, no need for so many extra programs.

```
sudo su && sleep 1209600 && halt
```
Or more elegantly...
```
sudo su && sleep 14d && halt
```

---

