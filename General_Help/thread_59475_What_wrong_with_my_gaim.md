---
title: "What wrong with my gaim???"
date: 2005-08-24
forum: General Help
---

### Post by fei on 2005-08-24
I have been using ubuntu for days. It's great. But there is one problem: I can't use gaim to log into MSN, ICQ. I didn't change any setting related to gaim and my network works fine. Can someone give me any clue what's wrong?

Thanks!

Fei

---

### Post by ubuntme on 2005-08-24
Can you give anymore info?

Like what does gaim do?  How for do you get? Do you have your accounts set up in gaim? any error messages?

Are you behind a proxy?

---

### Post by fei on 2005-08-24
I'm using my computer at home with ADSL connection. There is no proxy, or any firewall stuff. It'a direct connection. I can use other Internet applicaitons without problem.

I've added my msn and icq acount succefully. When I clicked the "sing on" button, it took a long time to connecting,  and when the connection window showed "connection established, cookie sent" and then poped up a error message (using my icq account) saying  "XXX has been diconnected " where xxx is my icq number. That's all I got. I have no idea what is the problem. 

I just  tried the web icq, the connection failed as well. It seems the icq server is not responding.

I can use amsn to log into msn, but not with gaim. It showed me a window saying I used either a wrong user name or a wrong password. BUT, they are all correct. No diea why.

---

### Post by heywire on 2005-08-24
I too am having troubles connecting to MSN today using GAIM.  I was able to connect fine yesterday.  I had upgraded to GAIM 1.50, so I thought it had somehow broken MSN support.  I guess it must be something on M$'s part.

---

### Post by m0ther on 2005-08-31
hello all, first post
[been a happy ubuntu user for a few weeks now, largely due to this forum]

ANYWAY just solved my MSN issue (i couldn't connect via gaim v1.5) and thought it may help others. i changed the logon server from 

**messenger.hotmail.com** 
to 
**65.54.239.140**

and it now works fine.

hope that helps others :)

peace,

---

### Post by Elrohir on 2005-08-31
always thought that the server was 207.46.37.125... funny world... good to know though...

MSN servers have been up and fine... upgraded to GAIM 1.5.0 with no problems...

as for ICQ protocol, can't say much...

---

### Post by TristanMike on 2005-10-02
[QUOTE=Elrohir]always thought that the server was 207.46.37.125... funny world... good to know though...

MSN servers have been up and fine... upgraded to GAIM 1.5.0 with no problems...

as for ICQ protocol, can't say much...[/QUOTE]That address worked for me, but not the other one, thanx for the alternative.

EDIT: Maybe not, did for a couple minutes. Too bad.....:(

---

### Post by avc on 2005-10-23
Both my MSN Messenger and AIM accounts don't work unless I use IPs instead of the default messenger.hotmail.com and login.oscar.aol.com. You can find out the IPs using nslookup or ping. I tried disabling ipv6 (by editing /etc/modules.d/aliases and removing ipv6.ko) to no avail. What's going on?

---

### Post by xkiddiegrinders on 2005-12-22
Im having the same problem that avc is having...

I started off not being able to use anything that connects to the net, I fixed firefox though...Everything else is not working

EDIT: I got gaim to work. Using the IP was the trick, now I just need to get Azureus to run...

---

