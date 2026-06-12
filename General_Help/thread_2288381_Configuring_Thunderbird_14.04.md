---
title: "Configuring Thunderbird 14.04"
date: 2015-07-26
forum: General Help
---

### Post by coljohnhannibalsmith on 2015-07-26
Hello,

I'm in the process of trying to set up Thunderbird in 14.04, for my Gmail account, with POP3: but I can't locate where to put all of the mail settings.
Gmail has instructions for Thunderbird; but they were not complete.

Here are the settings for gmail:

Mail servers:

Incomming: pop.gmail.com
Use SSL, Port 995

Outgoing: smtp.gmail.com
Use TLS or SSL

Use Authentication: Yes
Port For TLS/StartTLS: 587
Port For SSL: 465
Server Timeouts: 5 min

Alternative SMTP Ports: 465 or 587.

Thanks, Hannibal

---

### Post by ajgreeny on 2015-07-27
The last time I did this with TB I did not need to add any of those details manually.

Simply enter your email address when asked, your password if you want TB to remember it, chose either pop3 or imap, and the software makes all the configurations needed for gmail with no further user input.

---

### Post by gdesilva on 2015-07-27
As ajgreeny has pointed out TB automatically sets up the account when you provide your email address. I am using TB in 14.04. Of course, there is an option to manually configure if one wants to but if your mail provider is gmail this is unnecessary.

---

### Post by coljohnhannibalsmith on 2015-07-27
Whenever I launch TB I get the following Alert:

[COLOR=#ff0000]*"Unable to locate mail spool file."*[/COLOR]

Also, I was never asked for a password and could not find a place to enter it.

Thanks, Hannibal

---

### Post by howefield on 2015-07-27
> **coljohnhannibalsmith said:**
> Whenever I launch TB I get the following Alert:

[COLOR=#ff0000]*"Unable to locate mail spool file."*[/COLOR]

Also, I was never asked for a password and could not find a place to enter it.

Thanks, Hannibal

You might find the start of a solution here.. [http://forums.mozillazine.org/viewtopic.php?f=28&t=2672939](http://forums.mozillazine.org/viewtopic.php?f=28&t=2672939)

---

### Post by coljohnhannibalsmith on 2015-07-27
My original Home Account was created in TB the first time I used Firefox Hello, which is a web conferencing app in Firefox.
This account was created for a Movemail server automatically.  I created a new account from scratch and Gmail worked perfectly with it;
however, it took me forever to find the location of this feature.  First, I had to drill down to Write > Edit > Account Settings.
In other words I had to compose an email to get to this setting; the task bar at the top of TB does not have this option.  Finally all
the way at the bottom left of the Account Settings window lies the option for Account Actions.  This let me create a new account
which worked; however, I had to remove the original account to get the error message to go away.  Now, I have to create a new
Firefox Hello account.  I hope I don't get that message again.

Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-07-27
Update,

Firefox Hello appears to be working correctly with the new account.

Hannibal

---

