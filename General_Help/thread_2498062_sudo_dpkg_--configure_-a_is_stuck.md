---
title: "sudo dpkg --configure -a is stuck"
date: 2024-05-29
forum: General Help
---

### Post by marijameme on 2024-05-29
Hello there,
I tried installing openjdk, but I got an error saying ```
dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem
```, and I run ```
sudo dpkg --configure -a
``` and it was running for about 15 hours when I noticed it was stuck. I decided to try ```
tail -f /var/log/dpkg.log
``` and it showed ```
2024-05-29 10:03:40 status half-configured context:all 2021.03.05.20220211-1
2024-05-29 10:11:15 startup packages configure
2024-05-29 10:11:15 configure context:all 2021.03.05.20220211-1 <none>

```. I killed the process and tried to configure only the file "contex:all" but the process was the same. 
What can I do to fix this?
PS I'm running Ubuntu 20.04

---

### Post by currentshaft on 2024-05-29
First try "sudo apt-get install -f"

If that fails "sudo dpkg --configure -D 999 -a" might give you more information

See "dpkg -Dh" for more debug options

---

### Post by marijameme on 2024-05-30
Thanks for the suggestion, I tried "sudo apt-get install -f" and i got  stuck again, but when I googled the last line it got stuck I found out that there is a bug that apparently expects some kind of IO operation to get it unstuck. The suggestion was to keep pressing the enter button until it gets unstuck and it worked. Here is the link to the post I read [https://askubuntu.com/questions/956006/pregenerating-context-markiv-format-this-may-take-some-time-takes-forever](https://askubuntu.com/questions/956006/pregenerating-context-markiv-format-this-may-take-some-time-takes-forever)

---

### Post by ajgreeny on 2024-05-30
Great news! 

Please now mark as SOLVED from the Thread Tools menu up-top if this really is now solved to your satisfaction. 
It is a great help to other users searching the forum.

---

