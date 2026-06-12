---
title: "Evolution on MS Exchange server 2003"
date: 2005-09-06
forum: General Help
---

### Post by fonva on 2005-09-06
Hi

I have this problem. I'm a newbie on Linux. I've been trying to make Evolution receive/send mail and read the Directory, but I can't get it to connect properly to the Exchange server. Does someone has ideas on this issue?

Thanks

---

### Post by evilghost on 2005-09-06
I don't believe Evolution supports MAPI, so you'll need to have IMAP enabled on the Exchange 2003 server and connect using that method.

Someone correct me if I am wrong.

---

### Post by nuke on 2005-09-08
Do you have 2 issues?  

(1) connect to MS Exchange server and (2) connect Evolution to Exchange mail server?

---

### Post by fonva on 2005-09-09
I've worked a little on this. I'm connected to my server (log in, use internet, see others PC's). My problem is with the mail.

Recently i get to receive/send e-mail. Now the thing that I have to do is to connect with the adresses directory.

I've tried to download the latest version of the ximian connector but i can't find it. Can someone help? Do you think this may be the solution

thx

---

### Post by iimess on 2005-09-09
[QUOTE=][/QUOTE]
 I have a similar problem. I thought Evolution only supports WebDAV but not MAPI and it requires an OWA to connect, which our Exchange server doesn't provide...

---

### Post by yyagol on 2005-09-10
I can get to my [COLOR=Red]OWA[/COLOR] server and even see all my directorys
but when i try to look inside the dir for email i get nothing
can that be that my [COLOR=Red]OWA[/COLOR] server is blocking me from seeing
the messages ? or [COLOR=Red]Evolution[/COLOR] problem ?

---

### Post by KenLazlo on 2005-09-13
[QUOTE=fonva]I've worked a little on this. I'm connected to my server (log in, use internet, see others PC's). My problem is with the mail.

Recently i get to receive/send e-mail. Now the thing that I have to do is to connect with the adresses directory.

I've tried to download the latest version of the ximian connector but i can't find it. Can someone help? Do you think this may be the solution

thx[/QUOTE]

ximian-connector is obsolet.

Install package evolution-exchange. It's a Evolution plugin for MS Exchange. 
Then create a new account in Evolution.

Your Exchange Server needs OWA (Outlook Web Access) enabled.

---

