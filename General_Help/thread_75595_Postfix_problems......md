---
title: "Postfix problems....."
date: 2005-10-13
forum: General Help
---

### Post by Zensunni on 2005-10-13
Okay, I'm brand new at postfix so I might have missed something obvious.

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

