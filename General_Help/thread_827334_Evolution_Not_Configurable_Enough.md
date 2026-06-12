---
title: "Evolution Not Configurable Enough"
date: 2008-06-12
forum: General Help
---

### Post by Quantumstate on 2008-06-12
I run KDE, but am trying out Evolution.  But at this point it looks like I may not be able to use it because of a couple issues.  Is there any way around these?

- I have always sent and received email using SSL (sPop3, sSMTP) on ports 995 & 495.  First of all I want encryption and second I don't want 25 & 110 open for security reasons.  Well Evo does allow you to turn on SSL, but does not allow you to set the standard ports for email encryption!  What's up with that?

- Under Inbox and Sent I've set up folders for each of my email accounts. But there does not seem to be any way to associate an email account with a folder. IOW I want sent messages from a certain account to go in a folder of that name.  How do you assign a folder to an account?
 
 - I use a dark style for my desktop. (Revolution) This is all fine in Evolution except in the message body. A white HTML background has white text, and there doesn't seem to be any way to change that. Text elsewhere in my Evo window is white to contrast with the dark background, but I want a light background for the message area, the area of focus.
 
 - When I compose an HTML message there doesn't seem to be any way to set the background to a color or image?
 
 - Has anyone done a mail-merge with Evo between contacts and email? How?

---

### Post by techstop on 2008-06-12
Re: issue 2. Go to the following menu;

Edit>Preferences>Mail Accounts

Choose your account and click "Edit". Click on the "Defaults" tab. Choose your drafts and sent items folders as required.

---

### Post by Quantumstate on 2008-06-12
Ah, very good, thank you.  This takes care of Sent mail, but I guess there is no way to direct Received mail?

I've found that you can add port :465 to the server for SMTP and :995 for POP3, and I no longer get firewall messages when I try to send mail.  But the emails just do not get sent.  I suspect it's something to do with accepting the host cert, which I am never asked to do?

---

### Post by Quantumstate on 2008-06-13
Well, it's starting to look like I can't make Evo work.

---

