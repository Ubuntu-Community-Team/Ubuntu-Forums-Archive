---
title: "Sudo and file management"
date: 2007-05-17
forum: General Help
---

### Post by kstella on 2007-05-17
I'm trying to install Mozilla sunbird and was following a tutorial found here:

[http://knowledge76.com/index.php/Sunbird_Installation_on_Ubuntu_Breezy](http://knowledge76.com/index.php/Sunbird_Installation_on_Ubuntu_Breezy)

However, I found that the connection kept timing out at the part where I was downloading the file into the /opt folder. Earlier, I was able to download the file I needed, but it was stored on the Desktop. So, here are my questions:

The opt folder now has a wget-log file. I opened it and saw that it hasn't stopped trying to download the sunbird file. **How do I cancel that command?** (In case you didn't follow the above link, it was sudo wget -c <the sunbird file>.)

Second, I wanted to move the sunbird file from my desktop and into my /opt folder in order to resume the tutorial from there, so I dragged and dropped. However, I get an alert that says I don't have permission to write into the opt folder. I would rather not change file permissions, etc., so** is there a way to move files using the sudo command?**

I'd appreciate your helpful replies. :)

---

### Post by teaker1s on 2007-05-17
terminal
```
 gksudo nautilus
```
be aware you are now root and can move anything-be sure you only use as required to avoid accidents

---

### Post by kstella on 2007-05-17
Before I do that, please enlighten me: what does nautilus do? :)

---

### Post by nikhilk on 2007-05-17
It is a file manager/explorer.

---

### Post by kstella on 2007-05-17
Thanks to you both. :)

Now, who can help me with my first question? What do I do about that wget-log file?

---

### Post by nikhilk on 2007-05-17
To confirm whether the wget process is still running in the background use the command
```
ps afx | grep wget
```
Post it here for reference of other users. If the output you get is something other than a single line it means wget is running and you need to kill it.

---

### Post by kstella on 2007-05-17
Thanks. But I restarted my computer about an hour ago, and the wget-log said that it had given up. So I know it's no longer running, and I can no longer post the results.

Can you tell me, for reference, how do you kill it?

---

### Post by nikhilk on 2007-05-17
The command is "kill". It requires the PID (Process ID) of the process to be killed. See man kill for details.

---

