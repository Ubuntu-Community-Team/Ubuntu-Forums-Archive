---
title: "Problems with internet"
date: 2006-10-18
forum: General Help
---

### Post by Jungingen on 2006-10-18
I used ubuntu for about a year without a problems, without a configuring network interfaces files. But now, i want to ask a question - what the **** is going on? I'm using external pppoe modem to connect the internet - Lucent Cellpipe 22A-GX-E. But now, from july i have a problems - default ubuntu program to connect internet pppoeconf didn't find any modem concentrators on eth0. I need to tell, that the lan card is configures on linux and working properly. The problem is that some time, then i booting linux, pppoeconf can find internet, some times not, without me changing anything. Forget to say, what on the windows anything is working properly.
A week ago i get TL-WR642G router to connect my and computer of my friend. I configured this router to dial-up automatically on startup and get to me computer, connected by first LAN port IP adress by dhcp. About two days anything was working properly, but now i can't connect to internet, i can't connect from linux to me router by adress192.168.1.1. I don't know, what's going on with    internet. One of friends tell me, that it can be a low ping of my dsl provider, but i don't know that it meens. That should i do?  I don't want to use windows, but know i'm forced to do this.  

P.S. Sorry of me english.
If you can, please wrote me 
[email]jungingen@gmail.com[/email]

---

### Post by wieman01 on 2006-10-18
Have you configured your firewall recently or install Firestarter (configuration tool for IP tables)?

---

### Post by Jungingen on 2006-10-19
No, i haven't install firestarter, because i can't connect!
 And what should i configure on my ip-tables?

---

### Post by wieman01 on 2006-10-19
If you have not configured any kind of firewall (or IP tables) then this is not the source of your problem.

---

### Post by Jungingen on 2006-10-19
So what should i do?

---

### Post by metalheart on 2006-10-19
Do you get any reply from the router using
```
ping 192.168.1.1
```

Can you connect to the router/Internet from Windows?

---

### Post by wieman01 on 2006-10-19
I have seen similar posts in here and the the common solution was to **restart/reset** the modem. Please try that & let us know how that goes.

---

