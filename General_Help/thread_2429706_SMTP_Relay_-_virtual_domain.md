---
title: "SMTP Relay - virtual domain"
date: 2019-10-22
forum: General Help
---

### Post by kamilkrk on 2019-10-22
Hello for the first time


He started with a difficult topic right away from me.


I need help configuring SMTP Relay to work like the SMTP_Relay.JPG schema.
I mean exactly that it would be possible to configure SMTP Relay in such a way that depending on what e-mail address will get the message redirected to the appropriate mail server and account. However, I take into account that if you can't do the rule on the email address only on the domain then you will have to do it.
Additionally, for one of the mechanisms it needs authorization.
This is a strange case because the program tells you to enter the login and password for the SMTP service so that you can save the settings, but unfortunately it does not work with the O365 service, therefore in this case it also needs SMTP Relay.
Mechanism description:
1. A message is sent to SMTP Relay from mail address @ domain1.com. SMTP Relay recognizes the email address @ domain1.com and knows that it should route this message to the GMAIL mail server at 123 @ gmail.com.
2. A message is sent to SMTP Relay from the address mail1 @ domain2.com. Authorization to SMTP Relay is done via login and password and is sent on port 587/465. SMTP Relay recognizes the address mail1 @ domain2.com and knows that it is to forward this message to the O365 mail server to the address mail1 @ ourdomain.com.
3. A message is sent to SMTP Relay from mail2 @ domain2.com. SMTP Relay recognizes the address mail2 @ domain2.com and knows that it is to forward this message to the GMAIL mail server to address 456 @ gmail.com.
4. A message is sent to SMTP Relay from mail address @ domain3.com. SMTP Relay recognizes the email address @ domain3.com and knows that it is to forward this message to the O365 mail server to the address mail2 @ outdomain.com.
5. A message is sent to SMTP Relay from the address @ domain4.com. SMTP Relay recognizes the mail address @ domain4.com and knows that it is to forward this message to the O365 mail server to mail2 @ outdomain.com.

[IMG]https://ibb.co/Q7g1ZMK[/IMG]
[IMG]https://ibb.co/Q7g1ZMK[/IMG]

In each of the above cases, SMTP Relay is authorized with accounts (O365, GMAIL) by login and password and the appropriate port.


I tried solving the virtual domain but unfortunately it didn't work for some reason.


Has anyone tried to extend SMTP Relay to the above requirements and is it even possible?


Please help.

---

### Post by SeijiSensei on 2019-10-22
In sendmail, I'd do this with a mailertable that relays messages based on their destination domains.  I'm sure there's a way to do this in Postfix as well, but I don't use that enough to know.  In sendmail, you build a simple database with entries like this:
```

example.com      relay:[10.10.10,10]
example2.com     relay:[10.20.20.20]

```
You then run the makemap command to turn these entries into a db-style database.  Mail addressed to example.com will be forwarded to 10.10.10.10, and mail for example2.com is relayed via 10.20.20.20. All other mail is sent using MX records.

---

### Post by TheFu on 2019-10-22
I think the OP is confusing server-to-server SMTP on port 25 with client-to-server SMTP on port 465 or 587.
server-to-server SMTP doesn't require authentication.
client-to-server SMTP usually does require authentication.

In postfix, there is a **transport** file which handles any specific relay server to be used for specific domains. The format is identical to the sendmail as shown by SeijiSensei above. Using postmap to build a DB file isn't usually needed. The text file is sufficient, but the main.cf file should have a reference to the specific transport file. Mine has this:
```
transport_maps = hash:/etc/postfix/transport_custom hash:/etc/postfix/transport
```
The transport manpage has many more details, like using the **postmap** tool.
```
       relay_transport (default: relay:)
              This  is  the default for remote delivery to domains listed with
              relay_domains. In order of decreasing  precedence,  the  nexthop
              destination   is   taken   from  relay_transport,  sender_depen-
              dent_relayhost_maps, relayhost, or from the recipient domain.

```

If only 1 relay server is used, then there is a setting in the main.cf file, here's mine: 
```
relayhost = 172.22.22.45
```

Direct client connections to remote servers use the 465/tcp or 587/tcp settings with authentication.

Sorry, I don't know what O365 is. That's completely new to me. I've never seen that domain bouncing any emails that my users send, so I guess they accept email server-to-server just fine.

---

### Post by kamilkrk on 2019-11-13
Unfortunately, I couldn't do it that way.
Below is all the configuration I've done.


```
/etc/postfix/main.cf


# default relayhost setting
relayhost = [smtp.gmail.com]:587


# sender-dependent sasl authentication
smtp_sender_dependent_authentication = yes
sender_dependent_relayhost_maps = hash:/etc/postfix/sender_relay


# smtp authentication settings
smtp_use_tls = yes
#smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_tls_security_level = encrypt
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
smtp_sasl_mechanism_filter = plain


/etc/postfix/sasl_passwd


# per-sender authentication
[email]vcenter@mydomain.local[/email]  [email]account2@gmail.com[/email]:password
[email]icinga@mydomain.local[/email]  [email]account1@gmail.com[/email]:password
[email]upc@mydomain.local[/email] [email]account2@gmail.com[/email]:password
[email]apc@mydomain.local[/email] [email]account3@gmail.com[/email]:password


# default relayhost
[smtp.gmail.com]:587 [email]account1@gmail.com[/email]:password


/etc/postfix/sender_relay


#GMAIL
[email]account1@gmail.com[/email] [smtp.gmail.com]:587
[email]account2@gmail.com[/email] [smtp.gmail.com]:587
[email]account3@gmail.com[/email] [smtp.gmail.com]:587

```

Until then, everything is working properly and I can send messages from different addresses to different gmail addresses.
Now I want to add an additional configuration under O365 and here the problem begins.
I added such lines:


```
/etc/postfix/main.cf
# Configure for O365
smtp_generic_maps = hash:/etc/postfix/generic
smtp_sasl_tls_security_options = noanonymous
smtp_always_send_ehlo = yes


/etc/postfix/sasl_passwd
[email]O365@mydomain.local[/email]  [email]accountO365@mydomain.com[/email]:password


/etc/postfix/sender_relay
[email]accountO365@mydomain.com[/email] [smtp.office365.com]:587


/etc/postfix/generic
[email]O365@mydomain.local[/email] [email]accountO365@mydomain.com[/email]

```



What combinations would I not try, I am not able to run two relayhost to gmail and O365 simultaneously.


How do I add an entry to
```
# default relayhost setting
relayhost = [smtp.gmail.com]: 587
relayhost = [smtp.office365.com]: 587
This gets the message:
postfix: warning: /etc/postfix/main.cf, line 55: overriding earlier entry: relayhost = [smtp.gmail.com]: 587

```

However, if I leave only relayhost = [smtp.gmail.com]: 587 then messages that were to go to O365 ida on gmail.


So the question is whether it can be done at all and if so what I am doing wrong.

---

### Post by kamilkrk on 2019-11-25
The final configuration where accounts for gmail and O365 work on one posftix.


```
/etc/posftix/main.cf 
# default relayhost setting
relayhost = [smtp.gmail.com]:587


# sender-dependent sasl authentication
smtp_sender_dependent_authentication = yes
sender_dependent_relayhost_maps = hash:/etc/postfix/sender_relay


# smtp authentication settings
smtp_use_tls = yes
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_tls_security_level = encrypt
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
smtp_generic_maps = hash:/etc/postfix/generic
transport_maps = hash:/etc/postfix/transport


/etc/postfix/sasl_passwd 
# default relayhost
[smtp.gmail.com]:587 [email]accountgmail@gmail.com[/email]:Password
#Gmail per-sender authentication
[email]notification@gmail.local[/email]  [email]accountgmail@gmail.com[/email]:Password
# O365 per-sender authentication
[email]AccountO365@o365.com[/email] [email]AccountO365@o365.com[/email]:Password


/etc/posftix/transport
[email]notification@gmail.local[/email]	smtp:[smtp.gmail.com]:587
[email]AccountO365@o365.com[/email] smtp:[smtp.office365.com]:587


/etc/postfix/sender relay
[email]notification@gmail.local[/email]	[smtp.gmail.com]:587
[email]AccountO365@o365.com[/email] [smtp.office365.com]:587
```

---

