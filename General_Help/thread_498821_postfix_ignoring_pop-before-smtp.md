---
title: "postfix ignoring pop-before-smtp"
date: 2007-07-11
forum: General Help
---

### Post by Buggin on 2007-07-11
I've been searching the forums and google on a pop-before-smtp and postfix problem I'm having. As best as I can tell pop-before-smtp is working fine. If i run ' strings /var/lib/pop-before-smtp/hosts.db ' it prints my IP address. No matter what I do to the main.cf file in postfix I get relay access denied. I even went to the extent of adding the bd file to postfix in Webmin with no luck. 

here's the output checking the db file
sysadmin@dukka:/etc/postfix$ sudo pop-before-smtp --list
The database holds 1 IP:
        xxx.xxx.xxx.122 (xxx to hide ip)

So, like I said, to the best of my knowledge pop-before-smtp is working fine. I believe the problem lies with postfix not actually reading the db file to see if an address is ok. If I add my address to the allowed list in postfix it works fine. So I know I'm not being blocked in the middle either.

Here is the section of my main.cf that relates to pop-before-smtp
smtpd_client_restrictions = permit_mynetworks, reject_rbl_client bl.spamcop.net, check_client_access hash:/var/lib/pop-before-smtp/hosts, permit

If you need any other information feel free to ask and I'll be glad to dig it up and fork it over.

---

### Post by Buggin on 2007-07-11
also, postmap seems to be able to query the db

postmap -q xxx.xxx.xxx.122 hash:/etc/postfix/pop-before-smtp
ok


I know the file is different but it's a symbolic link to /var/lib/pop-before-smtp/hosts.db.. i figured it was worth a try

so if postmap can read the db then it's obviously in the right format (I selected BerkleyDB in p-b-s setup?!?!) and if it's in the right format and postmap can read it then why isn't postfix paying any attention to what's in the file??

Must be a misconfiguration in postfix... right???????

---

### Post by Buggin on 2007-07-11
found a workaround... and a nasty one at that

if i comment out the check_client_access line in main.cf and add hash:/etc/postfix/pop-before-smtp to mynetworks in main.cf and now it works

that is so jacked up i don't even want to talk about it but if anybody knows what's wrong please tell me so i can fix it properly

---

### Post by HermanAB on 2007-07-11
Here is an extract from my main.cf:

---
smtpd_recipient_restrictions =  permit_mynetworks,
  check_client_access hash:/etc/postfix/pop-before-smtp,
  check_sender_mx_access hash:/etc/postfix/mx_access,
  reject_unknown_sender_domain,
  reject_invalid_hostname,
  reject_unknown_recipient_domain,
  reject_unauth_destination,
  reject_rbl_client bl.spamcop.net,
  reject_rbl_client zen.spamhaus.org,
  check_sender_access hash:/etc/postfix/sender_access,
  check_policy_service unix:private/policy,
  permit

smtpd_data_restrictions = reject_unauth_pipelining,
  permit
---

Make sure that you don't have a spelling mistake in there somewhere.

Cheers,

Herman

---

### Post by HermanAB on 2007-07-11
Another thing, do edit main.cf with a proper Unix editor like vi, nano or joe.  Some of the fancy editors inject funny characters that can cause the postfix parser to barf.

I also noticed that you are using smtpd_client_restrictions, while I'm using smtpd_recipient_restrictions - I have no idea what difference that will make, or whether the two are synonyms.

---

### Post by Buggin on 2007-07-14
I usually always use vi

I've read of plenty of other with this problem.. just no solution

I actually copied the same line and pasted it in (putty) to the mynetworks and that works so i just don't get it

not goign to mess with ti for now though... got enough to deal with with an IP change from one classless to another classless froma  different subnet all together and i'm not too good with DNS

If anyone is a guru and can fix this DNS mess message a brotha

---

### Post by Mr. C. on 2007-07-15
Postfix does not re-read the file immediately.  It will reload the file at its earliest convenience.  Reload postfix manually when you are testing:

```
postfix reload
```

MrC

---

