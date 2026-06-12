---
title: "Run a Script with username and password at log-in???"
date: 2013-04-15
forum: General Help
---

### Post by Zombir on 2013-04-15
Dear all,
My friend gave me a script which should be run with username and password as parameters to it. Since running this all the time as I log in is cumbersome and since there are few users of my system, I thought of asking this question. Is there any way that I could make a script run when a user logs in with the username and password the user enters as parameters? I've been searching for an answer for this problem through the internet and couldn't find it. Since many people claim that my written language is not clear enough, here's what I want to do in an example:

Say I have a user called Alex with username alex and password abc123. When Alex logs in he types in his username and password in login screen. This information should be used to automatically run a script in the terminal as  

```
$/home/my_script username:alex passwd:abc123
```

My system is 64 bit xubuntu 12.04 desktop edition.

Any suggestions will be appreciated. Thank you.

---

### Post by prodigy_ on 2013-04-15
What is this script supposed to do?

Normally you run scripts either under your own account in which case you don't need password or as root (e.g. from root's crontab or from /etc/rc.local). As root you can use **sudo -u username** construct without password.

---

### Post by Zombir on 2013-04-16
Well the script connects to a remote server (actually our geeks desktop) and retrieves files. Each one of us have an account in his desktop and each account has the same username and password as our accounts in my computer. That's why I need to run the script with username and passwords.

---

### Post by CaptainMark on 2013-04-16
If possible can you tell us how it connects to the remote server, (ssh/samba etc.) Then we might be able to help more.

---

### Post by Zombir on 2013-04-16
Well, I'm a noob actually. My geek friend is not here anymore. But his machine is a Windows machine with active directory I guess.

---

