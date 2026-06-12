---
title: "Replacement for microsoft mail"
date: 2005-04-24
forum: General Help
---

### Post by crazybill on 2005-04-24
On our network, I presently use two email servers. To communicate with the world, I am using sendmail on a freeBSD machine (a service which I may transfer to Ubuntu Linux.)

For our LAN (with private IP addresses and firewalled from the world), we have been using microsoft mail. The reason for using this simple -- but non-secure email program -- is well, basically because it has been there since 1995 and staff is use to it. Also, when experimenting with sendmail, test users got confused between emailing the world and emailing staff. Microsoft mail has a postoffice list that clients can choose from and staff likes it. As administrator of our netwok, I dislike it and want to get rid of all Windows servers.

My question is this: does anyone know of an email server that runs on Ubuntu Linux 5.04 that is similar to microsoft mail.. in that it is not POP3/SMTP (so staff can keep straight LAN emal from world email) and that it has a postoffice list that clients can choose from, rather than typing in names.  [I can not count the number of times staff complained that sendmail was not working correctly when they were actually typing incorrect email addresses.]

Thanks for any suggestions that you can give.

---

### Post by Vache on 2005-04-24
[QUOTE=crazybill]On our network, I presently use two email servers. To communicate with the world, I am using sendmail on a freeBSD machine (a service which I may transfer to Ubuntu Linux.)

For our LAN (with private IP addresses and firewalled from the world), we have been using microsoft mail. The reason for using this simple -- but non-secure email program -- is well, basically because it has been there since 1995 and staff is use to it. Also, when experimenting with sendmail, test users got confused between emailing the world and emailing staff. Microsoft mail has a postoffice list that clients can choose from and staff likes it. As administrator of our netwok, I dislike it and want to get rid of all Windows servers.

My question is this: does anyone know of an email server that runs on Ubuntu Linux 5.04 that is similar to microsoft mail.. in that it is not POP3/SMTP (so staff can keep straight LAN emal from world email) and that it has a postoffice list that clients can choose from, rather than typing in names.  [I can not count the number of times staff complained that sendmail was not working correctly when they were actually typing incorrect email addresses.]

Thanks for any suggestions that you can give.[/QUOTE]
 Bill - Your post is almost identical to what I was going to post a few days ago.

My office also uses MSMail for internal mail - why? Because it's been in use since 1997 :), and POP3 for external mail. I have looked into OpenExchange as a replacement for both (Currently, our ISP is doing the external mail, and I'd like to take that job over). Anyone have any suggestions?

---

### Post by crazybill on 2005-04-27
Does anyone out there have any suggestions?

---

### Post by chollis888 on 2006-05-24
hey guys founds this link in another thread, and I planned on trying this at home on test system tonight. 
 
[Here]("http://flurdy.com/docs/postfix/")
 
not sure if it will help, but hey who knows?

---

