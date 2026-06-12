---
title: "Bash script for rtmpsuck"
date: 2013-07-09
forum: General Help
---

### Post by iebo on 2013-07-09
hello , i need someone help :confused:  me  to make this commands into script that run in terminal please


1.cd to shared folder for example "rtmpsuckfolder"

2.sudo iptables -t nat -A OUTPUT -p tcp --dport 1935 -m owner  \! --uid-owner other-account-on-pc  -j REDIRECT 

3.sudo su other-account-on-pc  // after this i will be asked for password then redirected to this path   niceguy@niceguy-laptop:/home/niceguy$ 

finally 

4.rtmpsuck 

:)

---

### Post by Cheesehead on 2013-07-11
The script should probably be run as root (using sudo), not by your user.
Using 'sudo' and passwords in a script is a good indicator that it shouldn't be run as a user.

Shouldn't you undo the iptables nat rule upon completion?

---

### Post by greenbag2 on 2014-06-19
> **Cheesehead said:**
> Shouldn't you undo the iptables nat rule upon completion?

I've been using rtmpdump/rtmpsuck for 2 years now... and still haven't figured this out... I keep having to reboot just to access the internet after the terminal's closed. :P

Any idea on a command that would reverse that?

I realise this post is a year old... but it's all I culd find googling... :(

---

### Post by oldos2er on 2014-06-19
Hi greenbag2, please start a new thread for your question, where you'll be much more likely to receive help.. You can link back to this thread if you wish.

---

