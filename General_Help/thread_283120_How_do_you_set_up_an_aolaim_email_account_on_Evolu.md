---
title: "How do you set up an aol/aim email account on Evolution?"
date: 2006-10-23
forum: General Help
---

### Post by iammeagain on 2006-10-23
I don't have any idea where to start like what kind of server or any of that stuff that is asks for. Everything i have tried hasn't worked and i don't seem to find anything helpful online. Any help would be much appreciated. Thanx in Advanced.

---

### Post by IcemanV9 on 2006-10-23
I found information on using 3rd party app to send/receive AOL email from AOL.COM help section. Here's the instruction ...

=================================================

**E-mail Application Setup Basics**

Setting up access to the AOL or AIM Mail servers is relatively simple, and the settings are similar for most e-mail applications. The basic information that you need is as follows:

Your e-mail address is [email]screenname@aol.com[/email] or [email]screenname@aim.com[/email]. Be sure to include the @aol.com or @aim.com suffix.
The Incoming mail (IMAP) server address is: imap.aol.com or imap.aim.com.
The Outgoing mail (SMTP) server address is: smtp.aol.com or smtp.aim.com, port: 587.
Your user name is your AOL or AIM screen name.
Your password is your AOL® or AIM® password.

=================================================

That's it. Enjoy using Evolution to send/receive AOL email. :)

---

### Post by iammeagain on 2006-10-25
thanx just the stuff i needed, i was putting a couple things wrong. I almost had it right.

---

### Post by Larry Roll on 2006-11-27
I tried setting up Evolution to my AOL E-mail account, and it's not working.  I obviously got the server names wrong.  How do I get back into the setup wizard to fix it?  Please send replies to my E-mail account, [email]yodoc@aol.com[/email].

---

### Post by Larry Roll on 2006-12-09
I have set up Evolution using the following paramaters:

Incoming mail:  imap.aol.com

Outgoing mail:  smtp.aol.com

I included my full e-mail account address, [email]yodoc@aol.com[/email].

I can send e-mail, but am not receiving anything at all.  Does this Evolution thing actually work with AOL e-mail accounts, or am I just kidding myself?  I can get my e-mail from aol.com on my browser, but it's a very basic mail client and doesn't have the same "Outlook" like features of Evolution.

Anyone have any ideas?  I be clueless here!

---

### Post by glendavee on 2006-12-22
I have the opposite problem. I can receive aol email, but not send. My original settings were
Receiving  imap.aol.com
Sending smtp.aol.com

Following error messages re port 587, I've now changed to 
Sending   smtp.aol.com;port: 587

Still can't send. Get a server not found message.
Is there any way I should be inputting my aol password in the Evolution email setup process?

---

### Post by glendavee on 2006-12-22
Re last post - got it sorted.
Sending should be   stmp.aol.com:587
"Server requires authentication" should be checked in preferences, and "login" selected as authentication type.
You are then asked for password first time you send.
Works for me.

---

### Post by iammeagain on 2007-03-10
> **Larry Roll said:**
> I tried setting up Evolution to my AOL E-mail account, and it's not working.  I obviously got the server names wrong.  How do I get back into the setup wizard to fix it?  Please send replies to my E-mail account, [email]yodoc@aol.com[/email].

lols i was going to send you an email through evolution on the settings i have but nvm because i can't get it to work either.

---

### Post by kingkab55 on 2007-03-12
Hi I just joined.
I am having a very similar problem like **glendavee**

"I have the opposite problem. I can receive aol email, but not send. My original settings were
Receiving imap.aol.com
Sending smtp.aol.com"

Following error messages Error while performing operation.

Host lookup failed: stmp.aol.com: Name or service not known

I have Sending be stmp.aol.com:587
"Server requires authentication" is checked in preferences, and "login" selected as authentication type.

I've left everything els set as default.
If some one would please help.
Reply With Quote

---

### Post by bently on 2007-03-28
stmp.aol.com:587

should be - smtp.aol.com:587

Dyslexia runs rampant in my life too!

---

### Post by xmas1888 on 2007-04-18
You also need to make sure that SSL is turned on, as it wouldn't work for me unless it was. 

The problem I have is that Evolution doesn't recognize the Trash folder that is already in the account as the main trash, so it creates a new one. This trash folder that it creates doesn't actually exist as when I log in via the web the stuff that had been put into the evolution designated trash doesn't appear anywhere in the account, not as a duplicate trash folder and not in the regular trash folder, making it impossible to see stuff that evolution puts in its trash from anywhere else but evolution. Is there a way to tell evolution to put stuff in the trash folder that is on the server rather than it's own custom one?

---

