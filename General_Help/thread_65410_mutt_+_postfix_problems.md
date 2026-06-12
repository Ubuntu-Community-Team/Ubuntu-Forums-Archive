---
title: "mutt + postfix problems"
date: 2005-09-13
forum: General Help
---

### Post by tom purl on 2005-09-13
I'm trying to use mutt and postfix on my Ubuntu system.  I get the following error when I send messges to some recipients:

```
<somethingbogus@uiuc.edu>: host relay8.cso.uiuc.edu[128.174.5.111] said: 553 5.1.8
    <tom@localhost.localdomain>... Domain of sender address
    tom@localhost.localdomain does not exist (in reply to MAIL FROM command)
```

My machine doesn't have a static ip or a fqdn.  I looked at the headers that I was sending in my messages and found the following:

```
Return-Path: <tom@localhost.localdomain>
```

After doing a couple hours of research, I first did the following to my .muttrc file:

```
my_hdr From: tom@tompurl.com
my_hdr Reply-To: tom@tompurl.com
```

I then made the following changes to my /etc/postfix/main.cf file:

```
myhostname = ubuntu.tompurl.com
mydomain = tompurl.com
myorigin = $mydomain
```

I even made the following change to my /etc/hosts file:

```
# 127.0.0.1     localhost.localdomain   localhost       ubuntu
127.0.0.1       ubuntu.tompurl.com      ubuntu
```

However, when I send e-mail, I'm still using the same Return-Path in my header and my mail is still getting bounced by a lot of ISP's.  

Does anyone have any idea as to what I can do?

Thanks in advance!

Tom Purl

---

### Post by banadushi on 2005-09-14
Well dude, this one is a huge hozer.  Your best option is setting the relayhost in postfix to forward all non-local mail to your ISP's mailhub.

What is happening is that the hostname of your Ubuntu box, does not match the reverse DNS entry for it.  So lots of mailservers will block it:

```

$ host ubuntu.tompurl.com
ubuntu.tompurl.com has address 69.9.180.166
$ host 69.9.180.166
166.180.9.69.in-addr.arpa is an alias for 166.164/30.180.9.69.in-addr.arpa.
166.164/30.180.9.69.in-addr.arpa domain name pointer iota.zettai.net.

```

I'd be able to tell you exactly what is going on if you post the full email that gets bounced back with all the headers and the headers of the email that is sent out.

Have a good one!

Jason

---

