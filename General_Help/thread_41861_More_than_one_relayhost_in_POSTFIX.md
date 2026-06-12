---
title: "More than one relayhost in POSTFIX"
date: 2005-06-15
forum: General Help
---

### Post by ragu on 2005-06-15
Hi,

i've spent several hours trying to set up postfix mailserver for my system. Since Ubuntu comes with postfix, i desided i would make that server work, instead of installing a different system. Untill now i've used Evolution, but would like to switch to a mbox system, using fetchmail for my POP3 accounts.

Now, sending mail has been the major problem. Since my Ubuntu PC isn't online all the time, i find it a good thing to let my ISP smtp server take care of the mail delivering. Thats why i did the relayhost thing. My ISP wants the 'correct' FROM email address, and thats why i found out that 'sender_canonical_maps' must be set up.

But here's the problem: My local network is used by another user (my girlfriend) and she has a different ISP with a different emailaddress.

Anybody knows how to set up two relayhosts?

Below goes my setup files:
#
# /etc/postfix/main.cf
#
myhostname = client.home
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = client.home, localhost
mynetworks = 10.0.0.3
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
disable_dns_lookups = yes
relayhost = [mail.isp.nu]
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_always_send_ehlo = yes
smtp_sasl_security_options = noanonymous
transport_maps = hash:/etc/postfix/transport
sender_canonical_maps = hash:/etc/postfix/sender-canonical

#
# /etc/postfix/transport
# This file is probably not nesesary, it was a wild guess and it didn't make it work
#
client.home		smtp:
.client.home		smtp:
smtp.client.home	local:
localhost.client.home  local:

#
# /etc/postfix/sender-canonical
#
@client.home		[email]rasmus@isp.nu[/email]

#
# /etc/postfix/sasl_passwd
#
SECRET

Anyone got an idea?

I've seen an example on the net where:

relayhost = [mail.isp1.nu] [mail.isp2.nu]

but i cant see how this would affect the sender-canonical file.

Please help.

/rasmus

---

### Post by GrumpySmurf on 2005-06-15
Why can't you set up your mail client to send to a different SMTP server?  I don't use Evolution, but I'm pretty sure it supports that. 

If you want to pursue the postfix method, [http://www.postfix.org](http://www.postfix.org) is the definitive source for postfix documentation.  However, I believe that additional relayhost entries tell postfix to use another host if the first is down.  I'm pretty sure you'd need to set up a map telling postfix that email from your girlfriends computer goes to one server and email from your computer goes to the other.

---

### Post by ragu on 2005-06-15
I know that Evolution supports smtp, and i've used that program so far. 

I was just thinking that since Ubuntu comes with postfix, i might as well learn how to set it up. I always try to run Ubuntu as 'clean' as possible. I don't know much about postfix yet but i imagine that there are several features in that system which might become handy along the way.

I also just found a small program which COULD solve my problem called msmtp. This program simply forward the outgoing email to a smtp account defined in the users home. It pretty much solves my problems except that i like to use Ubuntu as it is intead of installing software that are uncertified.

And thanks for the reply. The solution probably lies in [www.postfix.org](www.postfix.org).

/rasmus

---

### Post by blacksheep on 2005-07-22
[QUOTE=ragu]
But here's the problem: My local network is used by another user (my girlfriend) and she has a different ISP with a different emailaddress.
[/QUOTE]

I've a similar problem: i want to set up two different users which use freemail accounts as relays with postfix. Therefore it's necessary that each user connects to the mail sever with his/her own username / password.

I 'googled' a bit on the internet. The result: it's possible but NOT recommended and there are some restrictions.

To get this working you have to set the parameter "sender_based_routing = yes" in the main.cf file. But be aware: the man pages recommend not to use this parameters and it's also not officially documentated.

After that you can set up a "transport" map for each ISP. Additionally you have to setup up the smtp authentication for each user.

Here a link to a post from the origin developer of postfix: [http://www.archive-two.com/new-2590181-2887.html](http://www.archive-two.com/new-2590181-2887.html)

---

