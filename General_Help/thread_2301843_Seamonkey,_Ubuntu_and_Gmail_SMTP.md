---
title: "Seamonkey, Ubuntu and Gmail SMTP"
date: 2015-11-05
forum: General Help
---

### Post by helmar2 on 2015-11-05
Boy....Not sure as I was overwhelmed trying to find and figure out what all is being said on the forum.

My system crashed for the last time, done with microsoft and had loaded up a older version 12.? something of Ubuntu on it.
I "used" to be able to do the line commands but to be honest, not sure of the procedure to get to it.

I have had a Gmail account for quite some time, I also like and use Seamonkey so was able to download that but having issues getting it to show up in the Dash Home ?

My Gmail account is a Pop account and I can receive mail but when I go to send it, I get password or something else is screwy.
I have gone in and changed my password right from Google Gmail so I know its working.
The problem only shows up in the Sending of mail.

I am hoping to get this worked out as I really need that working and then will progress deeper into Ubuntu.

I have gone to Google and acquired the settings for both incoming and outgoing mail servers

Maybe I should back up a bit here. I don't care for the google site mail system and choose seamonkey as my browser and mail client.
So,
SMTP Server,  smtp.gmail.com
SMTP Port, started out wiith 465 but have tried 587 and 25 port that were suggested. Closing the client and reopening each time.
SMTP User name...myusername@gmail.com
SMTP Password, I know its correct as I even went and changed it to make sure I had a good working one.
Use Authenticate, yes, SSL and of course tried the other options. 

I keep thinking this is a Google Gmail issue but after exhausting 3 hours of digging, I have done everything suggested.

I can Receive with No issues, just can't Send.  Any ideas.

---

### Post by Sweet_Baby_Jamie on 2015-11-06
If you are using Ubuntu 12.**10** then it is not supported!  Check and be sure it's 12.**04**, which is a LTS Ubuntu and well supported until next year.  I also use Seamonkey because it's so much faster and lighter than Thunderbird/Firefox, yet made by Mozilla and easy to use!

Were you prompted to enter your outgoing server password the first time you tried to send an e-mail?  If so then you were asked to input the outgoing password and if you wanted Seamonkey to remember it for future use.

Gmail defaults to IMAP, not POP3, so double-check that too.  I also use POP3 because I don't want stuff kept on another computer.  Once I send it, the only copy is on *my* computer in the Sent folder, but not preserved on the mail server.  

The outgoing server, if it's POP3, will have a different name than the incoming server.  That was my mistake when I first set up my own Seamonkey e-mail.

---

### Post by Vladlenin5000 on 2015-11-06
Please pay attention the the post above. As mentioned, the 12.xx version matters A LOT.
That said, please read the GMail help and follow their instructions to the letter.

Also, any special reason for configuring POP instead of the preferred IMAP? Most email clients can setup GMail automatically when using the IMAP protocol, the full GMail address and password are ALL you need.

---

### Post by buzzingrobot on 2015-11-06
> **helmar2 said:**
> 
My Gmail account is a Pop account and I can receive mail but when I go to send it, I get password or something else is screwy.
I have gone in and changed my password right from Google Gmail so I know its working.


This is a bit confusing, but it sounds like you updated your GMail password. 

Have a look at this.  Click through and you'll see instructions for "Other" which should fit SeaMonkey. (The server names and port numbers are always the same, regardless of client.) -- [https://support.google.com/mail/troubleshooter/1668960?hl=en](https://support.google.com/mail/troubleshooter/1668960?hl=en)

---

