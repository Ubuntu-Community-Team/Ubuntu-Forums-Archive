---
title: "can't add to &quot;Startup Programs&quot; in System/Preferences/Sessions"
date: 2006-11-13
forum: General Help
---

### Post by djsamsel on 2006-11-13
if i try to add anything like beryl-manager or kiba-dock by clicking Add, they appear in the list until i close and reopen the sessions, then it is gone. any suggestions?

---

### Post by edwardam on 2006-11-14
I am also having this problem. I wanted to add /usr/bin/ssh-add, but it won't save it anywhere.

---

### Post by Poison0985 on 2006-11-18
I have the same problem. It began when I did a clean install of Edgy. It didn't happen in Dapper 6.06.

---

### Post by currentshades on 2006-11-18
Same problem here....

---

### Post by aidanr on 2006-11-18
[http://www.ubuntuforums.org/showpost.php?p=1769063&postcount=5](http://www.ubuntuforums.org/showpost.php?p=1769063&postcount=5)

---

### Post by rickympl on 2006-11-20
I had the same problem, turns out that the ~/config directory was not writable by my user, dont know why though. run the following in a terminal:
 sudo chown -R username:usergroup /home/username/.config/
change username to your user, and usergroup to your group, my user and group happen to be the same. Hope this helps, it did for me. Its working fine now.

---

### Post by currentshades on 2006-11-21
Thank you so very much.  Your help is greatly appreciated!  I think this did it!  ^_^

---

### Post by ashdust on 2006-11-21
Let me add my thanks as well, as I was having this problem and changing the permissions helped.  I love Ubuntu!

---

### Post by Poison0985 on 2006-11-24
Thanks a lot! Changing the permissions worked for me too.

---

### Post by sillywilly4 on 2006-12-12
worked for me too, this forum has been better than any other reference I can find!!!

---

### Post by amoore on 2006-12-19
Worked for me too. this is a strange problem.....

---

### Post by qrm on 2006-12-19
thank you so much for the tip :)

---

