---
title: "KEEPASSX was installed - please help - security compromised?"
date: 2013-03-23
forum: General Help
---

### Post by Broad_ripple on 2013-03-23
Hi, definite newbie as to security and looking for some help.

A good friend of mine is kind of a guru with Ubuntu. He has helped me set up my system so that I can remotely access it from work using remmina remote desktop client. We did this about a month ago.

Today I find that there is an app on the system called keepassx (which I did not install). Research shows that it is a password manager and records all web sites requiring username along with the password. When I launched the app it required a password to get in but it used none of the passwords I usually use. Going into the Ubuntu software center, I found that I could uninstall the app and did so.

Okay, is there anyway I can find out when keepassx was actually installed even though I have removed it (it could have been out there longer than I know)? As you cam imagine, most all the sites I visit and log into have been accessed overtime and now I fear that all my usernames/passwords have been compromised. Also, even though its been removed, can I find out when the last time it was accessed? Is there some terminal command that will show me this information (a history command of some kind for apps used)?

All my financial and email accounts may now compromised. Do I need to worry?

Please help.

Broad_ripple

---

### Post by keithb on 2013-03-23
KeePassX is just a password manager program. You would use it as a database for usernames and passwords of different web sites. Not sure how it could get installed with your knowledge though.

---

### Post by Broad_ripple on 2013-03-23
Hi keithb,

The friend had full access to the computer for an hour or so while he was setting up the remote software and testing. I believe keepassx could have been installed then. I know I did not install it. I understand that it is a database for passwords but it can be set up to capture all usernames and their password automatically.

---

### Post by deadflowr on 2013-03-23
Did your friend install anything?

It's possible that keepassx is part of a package they installed?

It is in the repos. (at least for raring it is)

---

### Post by stinkeye on 2013-03-23
Keepassx is just a password store and manager.
It doesn't record websites you visit or passwords you use.
You have to manually add them.

When you run Keepassx it gives a password dialogue to open a database of passwords you have created.
If you haven't created any password databases click cancel and Keepassx will continue loading 
where you can create a password protected database of your passwords.
Keepassx stores your passwords as an encrypted .kdb file.

Unless your friend knows all your passwords, he's just installed Keepassx for
you to create your own password database.

---

### Post by Broad_ripple on 2013-03-23
Hi stinkeye,

Thanks for your input. Just what I needed to know. Thanks again.

---

