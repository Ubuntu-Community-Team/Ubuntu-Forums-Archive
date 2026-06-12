---
title: "email stuck in outbox"
date: 2008-05-07
forum: General Help
---

### Post by underdog512 on 2008-05-07
I am running the evolution email client on ubuntu 7.10.  My wife tried to use evolution to send an email with an attachment that is way to big. Now that email is stuck in the outbox.  I tried just deleting it but all that does is put a line through the email address. upon restart of evolution and the computer all together, emails are still stuck in the outbox.  

any ideas on how remove these from the outbox?

---

### Post by bmac on 2008-05-07
Have you tried expunging the folder?
left click on outbox
On toolbar select folder/expunge
select expunge.

Hope this helps...

---

### Post by underdog512 on 2008-05-09
> **bmac said:**
> Have you tried expunging the folder?
left click on outbox
On toolbar select folder/expunge
select expunge.

Hope this helps...


the only thing I have when I right-click is flush outbox. I did that and they are still stuck in the outbox.

---

### Post by bmac on 2008-05-09
I'm believe you can open your file manager and show hidden files (look under view).
evolution/mail/local/outbox
Locate the folder called "Evolution" in your home directory
Open Evolution folder then locate the "mail folder" and open it.
Locate "local" folder and open it.
Locate "Outbox" text file and double click on it.

This will open your text editor with the contents of you outbox.
select "edit" in the toolbar and "select all" then delete and save.
Close the text editor and check your evolution outbox.

Hope this helps...

---

### Post by Sam Lars on 2008-06-07
I was using Evolution about six month ago and I ran into the same issue.  Just recently I changed back, but today, as soon as I change to the mail section, Evolution freezes.  Every time I open it, it complains about not closing properly.  I removed all things related to it and then reinstalled it, and got the same behavior.  I've really not been impressed with Evolution.

---

### Post by bmac on 2008-06-07
Why not use Thunderbird from Mozilla or an alternative e-mail application? That's what I love about Ubuntu "try anything, pick what you like and what works for you", at no charge... Gotta Love It....

---

