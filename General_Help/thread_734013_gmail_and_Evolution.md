---
title: "gmail and Evolution"
date: 2008-03-24
forum: General Help
---

### Post by jd8001 on 2008-03-24
Hey,
     I think my problem with evolution extends beyond the program itself. I can't get either evolution or kmail to work. I've tried just about everything and am beginning to wonder if I'm behind some firewall or something (I'm afraid also that I don't know the technical term). Somebody mentioned the possibility of a server being blacklisted? Anyway.. I'm beginning to really show my ignorance on this topic so I'll shutup and see if anyone can help me.



JD

---

### Post by munkyeetr on 2008-03-24
First of all, we need a bit more information about your problem...

What are you trying to do? (I assume you are trying to set up evolution to access your gmail account, but I don't know)
What errors are you getting, if any?

Have you tried searching for answers in other threads? In the search box type "evolution gmail" and see if other people have solved the issue already.

Have you set up your gmail account to allow POP access? That needs to be done prior to setting up a client like evolution.

---

### Post by forrestcupp on 2008-03-24
> **munkyeetr said:**
> 
Have you set up your gmail account to allow POP access? That needs to be done prior to setting up a client like evolution.

That is your problem.  Use your web browser to log in to your gmail account and go to your settings and set it for POP access.  Then if you have your POP and SMTP settings right in Evolution, you won't have any trouble.

But if you're open to a different program, Thunderbird has an automatic setup for gmail accounts.  You still need to have gmail set up for POP, though.

---

### Post by munkyeetr on 2008-03-24
> **forrestcupp said:**
> That is your problem.  Use your web browser to log in to your gmail account and go to your settings and set it for POP access.  Then if you have your POP and SMTP settings right in Evolution, you won't have any trouble.

But if you're open to a different program, Thunderbird has an automatic setup for gmail accounts.  You still need to have gmail set up for POP, though.

I am reasonably sure that will be the issue also, but I want to help people get in the habit of describing their problem as clearly as possible and search the forums before posting. :wink:

---

### Post by Kevbert on 2008-03-24
Settings to access Gmail.
In Evolution go to Edit - Preferences.
In Preferences (Mail Accounts) check that the Gmail account is ticked and the Protocol is pop.  If not add a tick and continue checking settings...
Select the Gmail account so it is highlighted and click on Edit.
Under the Identity tab check the email address is your full address e.g. [email]jon.doe@googlemail.com[/email] (or [email]jon.doe@gmail.com[/email]).
Under the Receiving tab - 
Server Type POP
Server pop.gmail.com  
Username your full email address (jon.doe@googlemail.com)  
Security SSL encryption  
Authentication Password  (tick remember password)
Sending email tab -
Server type SMTP
Server Configuration smtp.gmail.com (tick server requires authentication)
Security SSL encryption  
Authentication Plain  
Username your full email address (jon.doe@googlemail.com) (tick remember password)
Click on OK then Close.

---

### Post by jd8001 on 2008-03-24
POP is enabled and yes I have searched the forums and have found nothing pertaining to my problem. Just a bunch of how to's showing me how to set up a gmail pop or imap receiver. typically the error message I get is that it cannot connect to the server. Any thoughts?

---

### Post by fragos on 2008-03-24
Gmail doesn't use the standard POP and SMTP port #'s.  Look at [http://mail.google.com/support/bin/answer.py?answer=78799](http://mail.google.com/support/bin/answer.py?answer=78799)

---

### Post by Kevbert on 2008-03-25
In Account Editor, Receiving (and Sending) Email, Authentication Type, try clicking on 'Check for supported types.  If this works some of the listed authentication types will have a line through them and it means you can connect to the servers.
If you need to set the ports, you can do this under Server Configuration.  For Pop, receiving email this is pop.gmail.com:995 and for sending smtp.gmail.com:465

---

### Post by simonsmith06 on 2008-03-25
you also have to configure your gmail account 'under settings when your logged in the web version to allow pop and smtp'.

simon

---

