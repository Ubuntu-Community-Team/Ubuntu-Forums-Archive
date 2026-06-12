---
title: "vino causing xfce4 log to fill hard drive"
date: 2018-06-03
forum: General Help
---

### Post by oedipusr3x on 2018-06-03
Hello,

First post here. Looking for some help on an issue here. I've been running vino-server so that I can VNC into my machine from my laptop. After about 2 days of leaving my computer running with vino active, the hard drive filled up completely. I did some searching through the files and found that a file in ~/.cache/upstart called startxfce4.log is filling up rather quickly with random IP addresses. I was able to figure out that it was vino based on some snooping, but I don't know how to prevent this from happening. Any help would be great.

-Oedipus

---

### Post by nlee2 on 2018-06-03
Check your firewall rules for port 5900. Sounds like vino-server is flooded with requests.

---

### Post by oedipusr3x on 2018-06-07
Thanks for your help! I managed to change the settings in Vino so that only internal connections could be made and the file stopped growing.

For anyone else experiencing this problem, I entered the following in a Terminal:

gsettings set org.gnome.Vino network-interface lo

---

