---
title: "mail/domain name conifguration"
date: 2007-06-07
forum: General Help
---

### Post by jfang on 2007-06-07
I am running Ubuntu 6.10 as a web development test server and I would like to send emails via my PHP program.  

I was able to get it to work before, but ever since I changed from Comcast Cable Internet to AT&T DSL, I haven't been able to get it to work.

I've recently installed Postfix and replaced Sendmail in a desparate attempt to get sending email to work, but no success.

All I want is for my PHP program to send emails out.  I am not looking to set up a full mailserver to receive email.  

Also, this is behind a Linksys router (WRT54GL)

Thanks in advance.

---

### Post by bugler on 2007-06-07
It's been along time, but don't you have to setup smtp to coordinate with your isp.  Check your ISP's mail ports.  They may be blocking outgoing ports that sendmail or postfix is using.  Get back with us.

Edit:  You may have to login to their smtp server using your isp account to send mail.

Bugler

---

### Post by richmarchman66 on 2007-06-07
I would have to agree with Bugler here.

After switching to brighthouse...I had to send all mail through smtp.tampbay-rr.com where with verizon I could just send out.  After a little googling I find a few people listing asmtp.attglobal.net ... but that probably differs on location.

Good luck

---

### Post by jfang on 2007-06-07
Thanks for the quick reply bugler and richmarchman66.  After doing some more research I did find that AT&T DSL is blocking port 25 to fight spam.  

[http://helpme.att.net/article.php?item=4640]("http://helpme.att.net/article.php?item=4640")

In the process of trying to get sending email to work, I think I may have screwed up my hostname/domain name setting.  Can some one point me to the instructions on how to set up my hostname/domain name and postfix configuration correctly via the command line?

---

