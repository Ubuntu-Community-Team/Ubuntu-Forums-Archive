---
title: "Startup VPN script with password"
date: 2007-10-01
forum: General Help
---

### Post by jingdejun on 2007-10-01
Hello,

I have a SH script to start CISCO VPN Client, and it works well under Terminal window (Since sudo is used in one script line, so input of password is prompted during running)

I want to start VPN every time I login to Ubuntu, so I added this script to session startup. However, it does not work (no prompt for input password)

So, how to make auto-startup of my script?  Sorry for this newbie's question. Thanks

-Derek

---

### Post by jingdejun on 2007-10-01
BTW, authentication always failed when I input password for 'su' command, but I am sure the password is correct. Any idea?

---

### Post by bodhi.zazen on 2007-10-01
Not sure if it will help, but you might want to look at Expect : Automate interactions (will pass passwords):
	
	[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

	[http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

---

