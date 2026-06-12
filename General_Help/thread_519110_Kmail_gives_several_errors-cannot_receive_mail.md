---
title: "Kmail gives several errors-cannot receive mail"
date: 2007-08-06
forum: General Help
---

### Post by sasi on 2007-08-06
Kontact came with the new Kubuntu update today. I try to set up Kmail, but it gives me several error messages. I've been using Linux for years, I love it, but I'm still Linux illiterate. (my husband does everything for me. I just use the programs. Now he's away and I'm at a loss.) 

I followed all the instructions for set up. When I try to receive email, Kmail gives these error messages: 

1.    error while creating file /var/mail/sasi permission denied

2.  The precommand has exited with code 127. Key has expired.

It also says it could not contact the host.

This is all Greek to me. I don't know what it means. Can someone help? What am I doing wrongly? 

Thank you in advance!

---

### Post by jerrykenny on 2007-11-22
Hi Sasi   

for the first error . . . 

Possibly you havent been included in the "mail" group . . . 

Go to Prefernces, Admin, users & Groups . . . 

Look at your own account, and the group memberships you have . . .  .if theres a mail group, then make sure youre in it.

The PRECOMMAND thingy . . . look in kmail, settings,configure kmail,accounts,sending . . . . click on your account here and "modify"  there will be some tect in the PRECOMMAND box (I'm guessing STARTTLS) try deleting this, applying and OK-ing, . . . this option may be (hopefully) superfluous.

Good luck

---

