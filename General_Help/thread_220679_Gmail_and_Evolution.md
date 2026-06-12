---
title: "Gmail and Evolution"
date: 2006-07-21
forum: General Help
---

### Post by woopud on 2006-07-21
I've been reading different articles about getting Gmail in Evolution, looks like it will work for some and not for others.  At the moment I can send and receive my hotmail in Evolution but can't get Gmail to work.  Anyone can show me their settings ?

Bert

---

### Post by T700 on 2006-07-22
Key for me:

For sending, use TSL encryption and smtp.gmail.com:587.  Password type is Plain.

For receiving, use SSL.  Authentication is Password type.

Your username is [email]xyz@gmail.com[/email], NOT xyz.

Paul

---

### Post by woopud on 2006-07-22
Tried everything, for some reason it times out when i hit send/receive
also, it never asks for a password ?

Bert

---

### Post by jongkind on 2006-07-22
I assume that you read [this link]("http://mail.google.com/support/bin/answer.py?answer=13287&topic=1555"), right?

---

### Post by woopud on 2006-07-22
Yup, and it just times out when I hit send/receive

Bert

---

### Post by jongkind on 2006-07-22
In contrast to what T700 mentioned, I use ssl (!) encripton for sending emails (smtp.gmail.com:465)

Furthermore also ssl encription for receiving emails (pop.gmail.com:995)

---

### Post by woopud on 2006-07-22
That's what I did, i'm just wondering why it don't ask for a password ?

Bert

---

### Post by jongkind on 2006-07-22
Hm, I assume that made sure that you selected an accountname in the main Evolution Preferences screen, right? 

(In Dutch: "Evolution voorkeuren", tenminste één accountnaam is ingeschakeld, password type is "plat" in E-mail versturen screen")

Otherwise it really beats me. 

**Some suggestions to elucidate this matter (steps in the following order): **

1- What you can try is to setup an account in Thunderbird to verify whether it's working with this program. If it is working in Thunderbird something weird is going on with your Evolution. You can try to reinstall it.

2- If it is also not working with Thunderbird, you can try to do the same with Windows-Thunderbird. If it is also not working there it may be time to contact your internet provider. 

3- If it works with Windows-Thunderbird you may want verify possible firewall settings in Unbuntu (do you have Firestarter installed?)

---

### Post by T700 on 2006-07-22
I've followed this thread with some interest, because I've had exactly the same issues with Gmail, from time to time.  It would work with Kmail, but not Evolution.  Evolution, but not Thunderbird.  Outlook, but not Pegasus.  Kmail on two machines, but not on the third.

My conclulsion?  Satanic forces at work.  I've taken to burning incense and sprinkling holy water on the router.  Seems to work as well and consistently as anything else I've tried.  :-)

Paul

---

### Post by Balut on 2006-07-23
I also had problems getting Gmail to work properly at first with Evolution.

Here is what worked for me:

Receiving Email Tab:
Server Type: POP
Server: pop.gmail.com
Username:  [email]username@gmail.com[/email]
Security: SSL encryption
Authentication Type: Password

Sending Email Tab:
Server Type: SMTP
Server: smtp.gmail.com
Server requires authentication checked
Security: SSL encryption
Authentication Type: PLAIN

As you can see, I didn't specify any port numbers as is usually done with setting up an email client to access your Gmail.  Hope this helps you out.

---

