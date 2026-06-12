---
title: "Email Setup Problem with Terminal"
date: 2008-01-02
forum: General Help
---

### Post by nemonic on 2008-01-02
I am trying to set up my email server, using the default email software supplied with Ubuntu 7.10.
I have entered my username and password, but I don't know which of the three protocols to use of:RDP,RDPS,VNC. Also is the Client Host name, my ISP's name.
I asked my ISP HelpDesk, but they don't sponsor Linux and the particular helpdesk officer was not familiar with Linux to help, but he did not know why i needed to input Domain.
Anyway I input what I could and thought was about right, but when I hit the Coonect button, I got an error report and no connection.
Can anybody help?

nemonic

---

### Post by elithrar on 2008-01-02
Are you trying to set up your email **account** so that you can access your emails, trying to run a mail *server* (postfix/courier) or ssh/telnet into a remote mail server?

---

### Post by nemonic on 2008-01-02
> **nemonic said:**
> I am trying to set up my email server, using the default email software supplied with Ubuntu 7.10.
I have entered my username and password, but I don't know which of the three protocols to use of:RDP,RDPS,VNC. Also is the Client Host name, my ISP's name.
I asked my ISP HelpDesk, but they don't sponsor Linux and the particular helpdesk officer was not familiar with Linux to help, but he did not know why i needed to input Domain.
Anyway I input what I could and thought was about right, but when I hit the Coonect button, I got an error report and no connection.
Can anybody help?

nemonic
Hi, I am just wanting to set up email and browser access.

nemonic

---

### Post by elithrar on 2008-01-02
You won't need to touch any of what you're going into. If your internet connection is working, then all you need to do is go to Applications > Internet > Evolution. Ask your ISP what their "POP3" (incoming) and "SMTP" (outgoing) mail server addresses are - or check the support section of their website - and if they support "SSL" on their mail servers. Once you have this information, you're good to move onto actually setting up your account. You won't need to tell them you're using Linux or Evolution or anything of that nature, by the way.

Once you're in Evolution:

[LIST]
[*]Go to Edit > Preferences.
[*]Select "Mail Accounts" and choose "Add"
[*]When the wizard appears, give the account an appropriate name. Click "Forward".
[*]Now enter the name you'd like people to see when sending an email, and also your email address. Also tick the checkbox to make this the default mail account.
[*]On this screen, choose "POP3" from the server type list. Enter in the POP3 server address provided by your ISP into the "Server" field, and your username (generally your full email address).
[*]If your ISP answered "yes" to SSL, choose Yes/SSL (whichever appears) from the "Use Secure Connection" list. If not, leave it set to "no encryption" (if you're not sure, also leave it to none).
[*]Set the "Authentication Type" to "Password" from the list and choose Forward.
[*]Untick both "Leave messages..." and "Disable support..." and choose Forward.
[*]On this screen, choose "SMTP" from the server type list. Enter in the SMTP server address provided by your ISP into the "Server" field, and your username (generally your full email address).
[*]If your ISP answered "yes" to SSL, choose Yes/SSL (whichever appears) from the "Use Secure Connection" list. If not, leave it set to "no encryption" (if you're not sure, also leave it to none).
[*]Choose "Forward" and then "Apply" to create the account.
[/LIST]

Close the Preferences box and then choose "Send/Receive" from the toolbar at the top of the application. Provided you entered in the correct details, it should work fine. 

Hope that helps.

---

### Post by nemonic on 2008-01-02
Gidday Elithrar, Thank you for your support and help. I say this before trying out your latest letter.
I will post you again after success, well I hope it is success.
I hope you are enjoying the Christmas-New Year Season. 

Nemonic

---

### Post by nemonic on 2008-01-03
Hello Elithrar, No luck; cannot send email, outbox has 5 attempts in it, none received.
Also could not operate browser. 'Server not recognised'

No mention  of SSL in Evolution, not obviously anyway

You say 'If your ISP answered "Yes" to SSL, choose ...'.
But no sign of 'SSL'.

Hope you will commet again.
nemonic

---

### Post by nemonic on 2008-01-03
Elrithrar, While waing, hoping you would write, I contacted my ISP and they have not heard of SSL.

nemonic

---

### Post by nemonic on 2008-01-05
Even if I cannot get Evolution Email going, I should be able to get Firefox picking up and opening up webpages, but cannot. I have looked at my email settings and gone over them with my ISP and we cannot see anything wrong or missing.


nemonic

---

