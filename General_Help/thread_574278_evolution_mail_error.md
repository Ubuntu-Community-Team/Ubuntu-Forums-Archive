---
title: "evolution mail error"
date: 2007-10-12
forum: General Help
---

### Post by d_iane1954 on 2007-10-12
error while fetching mail could not connect to server 127.0.0.1connection refused!

any help with this would be appreciated!! thanks in advance.

---

### Post by thomasaaron on 2007-10-12
When posting questions, it is always helpful to give as much pertinent information as possible.

The error is saying that either you do not have evolution configured correctly or your email server doesn't permit mail to be checked by an external client (although that is probably not the case).

There are a number of things that you might have wrong: username, password, port, smtp or pop address, etc...

You might want to let us know who you're trying to connect to and what settings you are currently using. You can find these in Edit > Preferences. Then hit the Mail tab.

Best,
Tom

---

### Post by d_iane1954 on 2007-10-13
> **thomasaaron said:**
> When posting questions, it is always helpful to give as much pertinent information as possible.

The error is saying that either you do not have evolution configured correctly or your email server doesn't permit mail to be checked by an external client (although that is probably not the case).

There are a number of things that you might have wrong: username, password, port, smtp or pop address, etc...

You might want to let us know who you're trying to connect to and what settings you are currently using. You can find these in Edit > Preferences. Then hit the Mail tab.

Best,
Tom

error while fetching mail

failed to read a valid greeting from pop server 127.0.0.1


can anyone please help!thanks in advance i would really like to use evolution for my account at hotmail....

---

### Post by d_iane1954 on 2007-10-13
> **d_iane1954 said:**
> error while fetching mail

failed to read a valid greeting from pop server 127.0.0.1


can anyone please help!thanks in advance i would really like to use evolution for my account at hotmail....

followed this how to it worked right up to when i wanted to read or send mail:[http://www.ubuntugeek.com/send-and-receive-your-hotmail-messages-through-evolution.html](http://www.ubuntugeek.com/send-and-receive-your-hotmail-messages-through-evolution.html)

everything went fine entered the info as described recieved all proper readouts from commands entered but still no mail or cannot send mail in evolution recieve the above error message1 can anyone help.thanks in advance.

---

### Post by pionium on 2007-10-20
Hi, this is cryptic and here is a shot in the dark of a try to help =P

I just had trouble recieving mail after upgrading 7.04 to 7.10. It turns out the upgrade reset /etc/inetd.conf (I was probably warned, but I didn't pay attention). The pop3 line was disabled so I just removed the tag.

Make sure your /etc/inetd.conf looks something like this:
(use: sudo gedit  /etc/inetd.conf to edit)
```

pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd -r

```

I hope this helps, but I suspect that it won't if you have followed the howto you referred to.

regards

---

### Post by aardvaark on 2008-02-06
I hope you might review this post even though you posted back in October.  I am a complete noob to linux, but I was able to find the answer to my problem from this post:  
 .  I had to reinstall this command in the terminal: sudo apt-get install inetutils-inetd .Once I reinstalled it I am now able to receive and send hotmail.  Hope you see this and it helps.:)

---

