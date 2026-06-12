---
title: "Weird behavior from e-mail &amp; browsers - can't open user profile directory..."
date: 2016-05-27
forum: General Help
---

### Post by dkolars on 2016-05-27
Not sure if this is Xubuntu problem, e-mail programs problem, or browser problem.

Runnint Xubuntu 14.04 64bit.
Have both Evolution and Thunderbird for e-mail
Use mainly Opera, sometimes Chrome browsers

1)  IF I have Opera open, and click on a web link in an e-mail in Evolution, I get the message:
Can't open user profile directory, because you lack sufficient privileges. You might want to contact the administrator of this machine.

Seriously?  I'm the only user!  I have read/write permissions on everything that I can assign that to!!

But, if I have Opera closed, and click that link or any other, Opera opens, loads my previously open tabs (as I have it set to do that) AND the new link.  
BUT, it won't open any further links from Evolution e-mails unless I close Opera again.


2)  IF I have Opera open, and click said link in Thunderbird, the system (?) wants to know which browser I want to use.  I choose Opera, and off we go.  Then, it works just fine, and I can open links all day long.  

I have Opera set as my default browser, but Xubuntu can't seem to remember that, as I get asked that way too often.

So, dunno what the problem is...  I was using Thunderbird for email, but it decided to start disappearing e-mails from the Inbox.  I had tried Evolution a while back, and was glad to discover that all the e-mails are there, as I can not find them anywhere related to Tbird.  Searched/read web help for over an hour...  As an aside, I miss Eudora!!

So, any idea what is causing this problem?  It's super frustrating!  TIA

DK

---

### Post by Omar_Jair on 2016-05-27
Have you tried to run it under sudo command? or maybe you can re-give yourself administrator rights from the ubuntu account settings.:-\"

---

### Post by dkolars on 2016-05-27
Well, it appears to be solved?  I went to System - User/Groups and checked my name in the "adm' and 'root' groups, and then it worked...  When I updated from 32 bit to 64 bit, I must not have reset them, or thought that the settings would be automatic...  at any rate, all better now.  Thanks.

---

### Post by DuckHook on 2016-05-27
> **Omar_Jair said:**
> Have you tried to run it under sudo command?Though the OP solved his/her own problem, it is important to note for others who happen upon this thread that a browser must ***never*** be run using *sudo*, unless one is researching how quickly one can get owned and even then, only doing so inside a fully sandboxed virtual machine.

---

