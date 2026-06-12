---
title: "/etc/resolve conf is missing or cant be read.."
date: 2007-07-26
forum: General Help
---

### Post by djsoss on 2007-07-26
I'm very new to linux and I am trying to set up Kutunbu 6.06 for dial up but I keep getting this /etc/resolve conf is missing or can't be read message and it's fustrating me. I use the terminal and did a sudo pppconfig to set up my dialer but when I go to internet kppp dialer, it erroer out. what do I have to do to fix this problem?

---

### Post by tbroderick on 2007-07-27
Is /etc/resolv.conf there? Is it empty?

---

### Post by kevinlyfellow on 2007-07-27
Does /etc/ppp/resolv.conf exist?  If it does, try symlinking it to /etc/resolv.conf

```
sudo mv /etc/resolv.conf /etc/resolv.conf.bak
sudo ln -s /etc/ppp/resolv.conf /etc/resolv.conf
```

---

### Post by Bartender on 2007-07-27
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

---

### Post by djsoss on 2007-07-27
Keep in mind that I don't know very much about Unix or Linux commands, I come from a Microsoft world. I don't know if it's there but I will go ahead and try those terminal commands and see if they fix the problem. Thanks guys.:)

---

### Post by Bartender on 2007-07-28
djsoss -
I tried to write that so that someone new to Linux would be able to follow it.  I know nothing makes sense the first couple of times you go into terminal but take heart, go slowly, and you should be fine.  Tell me if there's some part that just didn't make any sense.  As the originator I can go back and edit the post.

---

### Post by djsoss on 2007-07-28
well I finaly made the error go away by using the terminal comand " sudo touch /etc/resolv.conf ". Now when I open the kppp internet dialer the error doesn't show up any more but I still can get the darn thing to dial out! the kppp dialer comes up just fine and seems like it's going to work but then when I hit connect, it just hangs there. It just says modem read & then it says initializing modem and it just stays there. I opened the log box and all it says is ATZ ATZ ATZ and some weired characters like []|v0 or something like that. Also the dialer box keeps saying script timed out. :confused: Please help.

---

