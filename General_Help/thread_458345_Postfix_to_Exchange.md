---
title: "Postfix to Exchange"
date: 2007-05-29
forum: General Help
---

### Post by lenny8088 on 2007-05-29
Got a simple intranet server running Feisty with some PHP and other scripts that collect data, package it up in excel sheets and send them off to the company thru the exchange server. All that works great.

Now I need to add an external email for a customer to get one of these reports. At first I tried hardcoding an external address in to the script but it never arrives. So I created a contact in the exchange box, set up a distribution list, added the contact to the distro list and ... same result. Everyone who is local in the distro list gets the email - but external one just "goes away".


I've looked at the Postfix wiki's - meaning I didn't read them as I didn't see my situation there - but I could have missed it. I don't need a mail server that rec's mail - just one that pipes it out to the exchange server and forgets about it.

Is it possible it's my Exchange Server?  Which if it is - do you have any ideas on how to configure it so it sends the mail out?

Help? Thoughts? 

Thanks,
-Lenny

---

### Post by Stusy on 2007-07-09
I'm in the same boat

I'm using Postfix to send emails out to an exchange server the the exchange server send out the emails. Any local users pick up the emails in the Active directory its peopel outside the domain that never get them.... I've set the ubuntu serve as a Satelight as it never going to recive mail just only ever send

I pretty sure you'll get an error about not being able to relay so you need to setup a relay client in the smtp connector.....

I'm trying to do this at the moment so I'll be able to let you know........

---

