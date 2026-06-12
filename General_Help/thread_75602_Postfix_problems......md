---
title: "Postfix problems....."
date: 2005-10-13
forum: General Help
---

### Post by Zensunni on 2005-10-13
I didn't know where to put this, was it okay that I posted here?

Anyways, I'm brand new at postfix so I might have missed something obvious.

Because I'm new, I used webmin to handle the postfix settings. I used mozilla thunderbird as an email client on a windows PC that's on the same lan as my server.

my domain is "thehiddengrotto.com" and my server name is "zensuni"

When I put "zensunni" into the outgoing and incoming mail server settings, I can click "get mail" without any errors. I can also send mail to my own account and see it in the account on webmin.

However, I can't seem to receive any mail from my email account when I hit "get mail". I look at my ubuntu system and it's there, but it won't transfer to an email client. What's worse is that when I put "zensunni.thehiddengrotto.com" into the incoming/outgoing settings (making the fetch command go over the internet, instead of just on the LAN), I get an error, "failed to connect to server "zensunni.thehiddengrotto.com" when I go to "get mail" and a similar error when I try to send.

So there's two things I need to be able to do:
1. Be able to access my server from the internet
2. Be able to get my email from my ubuntu machine.

I've tried opening all the router ports, so it's not a router problem.

Any help would be awesome. I'm going to post my config settings

---

### Post by Zensunni on 2005-10-13
Main.cf:
-----------------------------------------------------------------------------------------------------
# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = zensunni
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = thehiddengrotto.com
mydestination = thehiddengrotto.com, localhost.localdomain, localhost.localdomain, localhost
mynetworks = 127.0.0.0/8
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
mydomain = thehiddengrotto.com
append_at_myorigin = no
allow_percent_hack = no
unknown_local_recipient_reject_code = 450
-----------------------------------------------------------------------------------------------------------------
If you want to see any other config files, let me know.

---

### Post by bmichel on 2005-10-14
By the way if somebody knows how to start postfix at boot load.

it should be a parameter in /etc/default/postfix but I can't find which one...

Thanks

---

### Post by aran384 on 2005-10-14
is the problem that postfix wont start at boot up after updating from hoary ???

---

### Post by Zensunni on 2005-10-14
I know that if you load webmin, it will ask you if you want postfix to start at boot. 

Otherwise, you'll have to configure your init.d files manually (fun fun). You'll have to go into the rc.d folders, located in "/etc". You'll see folder rc1.d to rc6.d. The numbers represent the runlevels. Ubuntu runs at a default runlevel of 3, airgo, you would have to make changes to the rc3.d folder. All you need to do is create a link file in rc3.d that links to the shell script executable of postfix. These shells are located in "/etc/init.d".

Hey, you could prolly help me too. You seem to know postfix a little better than me... :P

---

### Post by bmichel on 2005-10-16
[QUOTE=bmichel]By the way if somebody knows how to start postfix at boot load.

it should be a parameter in /etc/default/postfix but I can't find which one...

Thanks[/QUOTE]
I've found some solution.

Go to Administration > Services and check postfix to have it launched at boot load.

$ cat /etc/default/postfix
SYNC_CHROOT="n"

---

### Post by flyingbrass on 2005-10-16
Instead of altering files by hand, use update-rc.d.  Check the man for more info on usage. To add postfix:

sudo update-rc.d postfix defaults

That will start it in runlevels 2,3,4,5 and stop it in 0,1 and 6.


If you want to stop it from loading:

sudo update-rc.d -f postfix remove

This only works for services with entries in /etc/init.d.  Postfix should already be set to run if you installed using a deb.

---

