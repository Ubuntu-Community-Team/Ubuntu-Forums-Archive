---
title: "[Problem] Conky's imap_unseen on Gmail."
date: 2008-04-23
forum: General Help
---

### Post by sanus|art on 2008-04-23
Does anyone was able to successfully run ${imap_unseen ...} in conky  to fetch mail count from Gmail?

Thanks.

---

### Post by londonali1010 on 2009-03-04
I haven't managed to get it to work with my Conky either :(  And I've not seen anyone who's managed to do it...Anyone?  Anyone?

I'm trying to use imap_unseen or imap_messages with GMail.

---

### Post by jezster on 2009-03-13
I also have major problems with Conky in this regard - I'm going to have a hunt about and see if it would be better to script an imap checker and have Conky provide that to the screen.

---

### Post by dfmalh on 2009-04-08
Hi all, 

Have anybody come up with a solution? It would be much simpler to use imap_* to check how many unread emails here are in my inbox.

---

### Post by VCoolio on 2009-04-08
You can use kaivalagi's script to provide email info. Not only unread messages possible, but also who sent it and what it's about. Check [here]("http://www.kaivalagi.com/node/8").

---

### Post by spcgh0st on 2009-09-03
Ok... I finally could use $imap_unseen w/Gmail. Here's how:

**1. Install Stunnel** (as says in Conky's FAQs)

Here's my stunnel.conf (from /etc/stunnel/stunnel.conf)

```

; Protocol version (all, SSLv2, SSLv3, TLSv1)
sslVersion = SSLv3

; Some security enhancements for UNIX systems - comment them out on Win32
chroot = /var/lib/stunnel4/
setuid = stunnel4
setgid = stunnel4
; PID is created inside chroot jail
pid = /stunnel4.pid

; Some performance tunings
socket = l:TCP_NODELAY=1
socket = r:TCP_NODELAY=1
;compression = rle

; Some debugging stuff useful for troubleshooting
debug = 7
output = /var/log/stunnel4/stunnel.log

; Use it for client mode
client = yes

; Service-level configuration

[gmail]
accept = localhost:993
connect = imap.gmail.com:993

```
(I'm using IMAP Gmail server. To use POP3, change port to 995 and mail server to pop.gmail.com [and of course, use Conky's $pop3_unseen])

**2. Start stunnel** (or restart) * See PS at the end of this entry

On Debian
```
sudo invoke-rc.d stunnel4 start
```On Ubuntu (probably, I am not sure)
```
sudo /etc/init.d/stunnel4 start
```**3. Modify your Conky config file** (probably ~/.conkyrc)

Insert

```

imap localhost username password -p 993
TEXT
${imap_unseen}

```If something goes wrong, look at the stunnel's log file at /var/log/stunnel4/stunnel4.log

I hope it works for u people! :)

PS.: there's a problem with the init script in Debian and Ubuntu which is solved by changing the value of the variable ENABLED from 0 to 1 in /etc/default/stunnel4 . Once done, the init script functions ok, and stunnels loads at startup. See this link,

[https://bugs.launchpad.net/ubuntu/+source/stunnel4/+bug/137472](https://bugs.launchpad.net/ubuntu/+source/stunnel4/+bug/137472)

---

