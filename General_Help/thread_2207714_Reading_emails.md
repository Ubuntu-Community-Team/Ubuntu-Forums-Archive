---
title: "Reading emails"
date: 2014-02-24
forum: General Help
---

### Post by jason_b2 on 2014-02-24
I am sure this has been posted many times but as they all say I couldn't find it. I would like to set up a linux box to download mail from various providers (ISP (easy), Gmail and Hotmail (not sure)) and store it on the linux box. I then want to be able to read it from various over PCs/tablets on the local network. I think I have worked out the first part which is use fetchmail, sounds easy enough. Now for the fun part, is it just an easy process of pointing Outlook to the mail location for the various users? I would like to think Android on the Samsung Galaxy Tab will be just as simple but knowing my luck it won't be. 

Thanks in advance.

---

### Post by SeijiSensei on 2014-02-24
No, you need to be running an SMTP server like Postfix and an IMAP/POP server like dovecot.  When fetchmail retrieves your messages, it will hand them to Postfix for delivery.  Fetchmail will split up a mailbox where the To: addresses are different and ask Postfix to deliver them to the matching local users.  This works well when organizations have all the mail for a domain delivered to a single mailbox.

Your email client will then connect to dovecot to display the messages in your mailbox using, preferably, IMAP. 

Here's a good place to start: [https://help.ubuntu.com/12.04/serverguide/email-services.html](https://help.ubuntu.com/12.04/serverguide/email-services.html)

One other question to ask yourself:  What about outgoing mail?  Will people read mail locally but send mail out through their other providers like GMail?

---

### Post by jason_b2 on 2014-02-24
Thanks for the info. Obviously I have a bit more reading to do. I will do a bit of brain frying tonight.

As far as sending emails....oooppssss wife won't like not being able to send emails. Currently we use our ISP, Gmail and Hotmail so will have to consider how to do that as well.

---

### Post by jason_b2 on 2014-02-27
Ok. Been reading a bit but still a bit confused. If I do basically what you have suggested will I have access to all my emails from all machines on the network? Or will the first one to log on to an account have those emails sent to that PC only and be deleted from the server?

---

