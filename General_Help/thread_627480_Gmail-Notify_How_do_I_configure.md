---
title: "Gmail-Notify How do I configure?"
date: 2007-11-30
forum: General Help
---

### Post by rvickers on 2007-11-30
I'm running Dapper and Gmail-Notifiy. I have the icon on my panel but it doesn't turn blue when a new email arrives. I do get the pop-up notifier at the bottom of the screen. Is there a way to get the icon to turn blue like on my feisty machine? Also is there a way to configure how often it checks for new mail?
Thanks
Roy

---

### Post by ZipoTe on 2007-11-30
I used Gmail-Notify since I discovered "Checkgmail". I found this last more easy to configure so, maybe you can give try to Checkgmail.

---

### Post by hotweiss on 2007-12-01
Yes, checkgmail is so much better as you can delete messages, mark messages as read/spam without opening your browser. Use these commands to install it and remember to add it to your sessions so that it starts up when you boot your computer:

> sudo aptitude install checkgmail
wget [http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail](http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail)
sudo mv checkgmail /usr/bin/
sudo chmod +x /usr/bin/checkgmail

---

### Post by ZipoTe on 2007-12-04
doing "sudo apt-get install chekgmail" it's not enough?

---

### Post by hotweiss on 2007-12-09
> **ZipoTe said:**
> doing "sudo apt-get install chekgmail" it's not enough?

No, because when Gmail 2.0 came out they changed their interface, so you need to do it this way as far as I know.

---

### Post by Strangerdave on 2008-01-15
what would one put so that this program starts up when logging on?

is it just checkgmal? with Check Gmail as the name under sessions?

-SD-

---

### Post by tom957 on 2008-01-18
/usr/bin/checkgmail works for me in sessions/startup

---

### Post by Mark76 on 2008-02-05
I'm trying to get checkgmail to work but it keeps telling me my user name is wrong :(

---

### Post by Mark76 on 2008-02-05
cGmail seems to have solved that problem :)

---

