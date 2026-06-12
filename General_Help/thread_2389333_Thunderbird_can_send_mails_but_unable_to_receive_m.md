---
title: "Thunderbird can send mails but unable to receive mails"
date: 2018-04-15
forum: General Help
---

### Post by satimis on 2018-04-15
Hi all,

Thunderbird can send mails but unable to receive mails.

This Thunderbird has not been run for sometimes.  Previously it can receive mails download on webmail server.  Just discovered that it can't download mails but can send mails.

Unfortunately I couldn't find the file for setting this Thunderbird on my database.  Please advise how to fix the problem.

Thanks in advance.

Regards
satimis

---

### Post by deadflowr on 2018-04-15
firewall enabled?
If so, what are the current settings?

Is something like this helpful:
[https://ubuntuforums.org/showthread.php?t=1925615]("https://ubuntuforums.org/showthread.php?t=1925615")

---

### Post by satimis on 2018-04-15
> **deadflowr said:**
> firewall enabled?
If so, what are the current settings?
- snip -
Hi,

Thanks for your advice and link.

Whether you meant "Account Setting" ?

Something strange happened on Thunderbird here;
If creating a duplication account it allows
(example: [email]aaa@exampl.com[/email])
The new aaa@example account can download all mails of this account on webmail but without the mails retained on its old account

I can't explain why?

Edit
===
The Thunderbird was installed on an Ubuntu VM of Oracle VirtualBox

Cloned a new Ubuntu VM and started Thunderbird.  Created all emails accounts of the webmail.  All mails can be download to the respective email accounts without problem, only missing following folders on each email account:
Bulk mail
Sent items
etc.

Regards
satimis

---

### Post by rsteinmetz70112 on 2018-04-16
What type of mail server do you have (IMAP POP3 or something else)?
Are you sending email through the same server you receive it from?
When you attempt to get email what happens?
You say previously you could send email and "receive mails download on webmail server", usually that means you are getting your email through a web browser not Thunderbird.

---

### Post by satimis on 2018-04-16
> **rsteinmetz70112 said:**
> What type of mail server do you have (IMAP POP3 or something else)?
Are you sending email through the same server you receive it from?
When you attempt to get email what happens?
You say previously you could send email and "receive mails download on webmail server", usually that means you are getting your email through a web browser not Thunderbird.
Hi,

The old Thunderbird has not been run for long time.  The OS was upgraded from Ubuntu 14.04 to 16.04

Following is the comparison of settings of the old and new  Thunderbirds

```
Old Thunderbird
===============
Incoming
Server Settings
Server Type: IMAP Mail Server
Server Name: mail.example.com
Port: 143  Default 143

Security Settings
Connection security [STARTTLS]
Authentication method [Normal password]

Outgoing Server (SMTP)
[aaa@example.com - mail.example.com (D....)


New Thurnderbird
================
Server Settings
Incoming
Server Type: POP Mail Server
Server Name: pop.secureserver.net 
Port: 995  Default 995

Security Settings
Connection security [SSL/TLS]
Authentication method [Normal password]

Outgoing Server (SMTP)
[Your WildWest domain-smtpout.securese....]

```

Thanks

Edit:
Just tested the "send function" of the new Thunderbird.  It worked without problem but no "sent copy" left on webmail account

The webmail is SquirrelMail

Regards
satimis

---

### Post by rsteinmetz70112 on 2018-04-16
The two configurations for receiving and sending mail are different. The outgoing setting you posted can't be correct for a working outgoing server example.com is not a functioning domain.
Have you tried changing the setup of the "Old" not working Thunderbird to match the "New" working one?
What is the address of the squirrelmail server? Do you need to set Thunderbird to send it a bcc: ?

---

### Post by satimis on 2018-04-16
> **rsteinmetz70112 said:**
> The two configurations for receiving and sending mail are different. The outgoing setting you posted can't be correct for a working outgoing server example.com is not a functioning domain.
Have you tried changing the setup of the "Old" not working Thunderbird to match the "New" working one?
Made following changes:-

Incoming
Server Name: mail.satimis.com
change to: pop.secureserver.net

Port: 143
change to: 995

Security Settings
Connection security [STARTTLS]
change to: [SSL/TLS]

-> OK

Server Settings```

Your User Name has been updated. You may also need to update your Email Address and/or User Name associated with this account.
```

-> OK

(Please refers to Screenshot_Add_Security_Exception.png attached)

-> Confirm Security Exception
```

Enter your password for pop.secureserver.net on mail.satimis.com:

```
for downloading mails on webmail.  But I couldn't find a password to satisfy it.

> 
What is the address of the squirrelmail server? Do you need to set Thunderbird to send it a bcc: ?
Address
[https://godaddy.com/](https://godaddy.com/)..........

and NO

Still I couldn't resolve that I haven't made any change to Thunderbird.  It worked seamlessly before update, upgrade and dist-upgrade.  It has not been run for long time and I just discovered this problem.

Edit:
===
Actually I don't need this Thunderbird.  I have a new Thunderbird on another VM working without problem.  What I need is to preserve the old mails on this Thunderbird.

Besides it allows me creating duplicated user accounts on this problematic Thunderbird.  The duplicated user accounts work without problem downloading mails on webmail server.  Maybe after moving those old emails to the duplicated user accounts I can delete the old user accounts.  What is your comment?  Thanks

Or leave it without doing anything to correct it and just retaining the old mails here?

Regards
satimis

---

### Post by rsteinmetz70112 on 2018-04-16
```

Enter your password for pop.secureserver.net on mail.satimis.com:

```

Regards
satimis[/QUOTE]

YOU can probably get the administrator of the mailserver to reset the pawword or you can check the password manager on Old Thunderbird to see if it was saved.

---

### Post by satimis on 2018-04-16
> **rsteinmetz70112 said:**
> ```

Enter your password for pop.secureserver.net on mail.satimis.com:

Regards
satimis
```

YOU can probably get the administrator of the mailserver to reset the pawword or you can check the password manager on Old Thunderbird to see if it was saved.

Sorry, I'm administrator.  I couldn't recall its password nor I can recall such an account nor I could find it on the database.  Just login Godaddy cPanel.  On Email I can't find such an account.

On first time starting the Old Thunderbird it asked for the password of mail.satimis.com but I'm allowed creating new user account.

Tried creating a duplicated user account.  It worked without problem and after its creation mails on its webmail were download automatically without asking for the password of mail.satimis.com

Strange !!!

Tried moving old mails on inbox of the old user account to its duplicated user account's inbox it asked for the password mail.satimis.com.  I supposed that if reverting back to the old settings I can move the old mails.

I think all old users accounts are corrupted and can't be used.  What is the cause, unknown to me?

Regards
satimis

---

### Post by rsteinmetz70112 on 2018-04-17
You own the domain and server pop.secureserver.net ? If so you have the authority to reset any password and view any account. All you have to do is login as a root or go su with ethe root password or sudo as a sudo user.

---

### Post by satimis on 2018-04-17
> **rsteinmetz70112 said:**
> You own the domain and server pop.secureserver.net ? If so you have the authority to reset any password and view any account. All you have to do is login as a root or go su with ethe root password or sudo as a sudo user.
Sorry, I can't resolve.  I'm owner of the the domain

pop.secureserver.net is Godday server.  I have password to sign in their cPanel.  But that password can't work here, on Thunderbird.

I have the root password and on Terminal I can run;```

satimis@ub1404dkpc1a_03:~&#10219; su -
Password: 
root@ub1404dkpc1a_03:~# 

```

But that root password can't work here, on Thunderbird, to download mails,  Also I have passwords of users' account but none of them can work here.

Regards
satimis

---

