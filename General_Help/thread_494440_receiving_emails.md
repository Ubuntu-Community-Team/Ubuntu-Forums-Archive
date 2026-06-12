---
title: "receiving emails"
date: 2007-07-06
forum: General Help
---

### Post by neil10 on 2007-07-06
can send out mail but cant receive any  won' accept my password double checked password seems ok   help

---

### Post by defishguy on 2007-07-06
Are you trying to use POP3 with gmail?

---

### Post by neil10 on 2007-07-06
pop3 yes for incoming

---

### Post by yorkie on 2007-07-06
server =pop whatever your internet ie pop.ntlworld.com
 try  pop3  ie pop3.ntlworld.com

---

### Post by neil10 on 2007-07-06
i use pop3  followewd by myu provider

---

### Post by HermanAB on 2007-07-06
You can debug SMTP and POP3 email by hand using telnet.  Here are the common commands:

SMTP, port 25

    [localhost:~] matt% telnet mail.domain.com smtp
    Trying 64.224.19.12...
    Connected to mail.zone.com.
    Escape character is '^]'.
    220 mail.zone.net ESMTP
    ehlo
    250-mail.zone.net
    250-AUTH LOGIN PLAIN
    250-AUTH=LOGIN PLAIN
    250-PIPELINING
    250-STARTTLS
    250 8BITMIME
    mail from: <user@domain.com>
    250 ok
    rcpt to: <user@domain.com>
    250 ok
    data
    354 go ahead
    Subject: foo
    .
    250 ok 1016471746 qp 9246


POP3, port 110

    telnet pop.domain.com pop3
    +OK Hello there.
    user [email]user@domain.net[/email]
    +OK Password required.
    pass secret
    +OK
    list
    1 1586
    2 13304
    3 795
    .
    dele 2
    +OK
    quit
    Connection closed by foreign host.


IMAP, port 143

    telnet imap.example.com imap
    Escape character is '^]'.
    * OK Courier-IMAP ready. Copyright 1998-2002 Double Precision, Inc. See
COPYING for distribution information.
    . login [email]user@example.com[/email] secret
    . OK LOGIN Ok.
    A0001 CAPABILITY
    * CAPABILITY IMAP4rev1 CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT
THREAD=REFERENCES SORT QUOTA
    . logout
    * BYE Courier-IMAP server shutting down
    . OK LOGOUT completed


Here is a session where I verified a user password. I made a mistake in there, so you can see what happened:

[herman@mercury herman]$ telnet mail.aeronetworks.ca 110
Trying 66.98.130.68...
Connected to mail.aeronetworks.ca (66.98.130.68).
Escape character is '^]'.
+OK POP3 svr35 [cppop 19.0] at [66.98.130.68]
user [email]alice@aeronetworks.ca[/email]
+OK Need a password
w0nd3rland
-ERR Command not implemented
pass w0nd3rlan
+OK You have 0 messages totaling 0 octets from
/home/mail/aeronetworks.ca/alice/inbox (full load)
quit
+OK Bye!
Connection closed by foreign host.
[herman@mercury herman]$

---

### Post by neil10 on 2007-07-06
pop3 .nsw.exemail.com.au is what i used on  wiondows

---

### Post by yorkie on 2007-07-07
just a thought saw your last message
pop3 .nsw.exemail.com.au
noticed space after pop3 should be no space maybe a typo error but have you done the same in your details

---

### Post by HermanAB on 2007-07-07
You can monitor the communication between your mail client and the server using tcpdump like this "tcpdump -i eth0 port 110 -A -s 256":

Here is a capture:

[herman@odin ~]$ su -
Password:
[root@odin ~]# tcpdump -i eth0 port 110 -A -s 256
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 256 bytes
22:08:10.537158 IP odin.aeronetworks.ca.49173 > venus.propagation.net.pop3: S 1762138478:1762138478(0) win 5840 <mss 1460,sackOK,timestamp 745874891 0,nop,wscale 7>
E..<<.@.@......
@.. ...ni..n.........m.........
,u%.........
22:08:10.602107 IP venus.propagation.net.pop3 > odin.aeronetworks.ca.49173: S 169395637:169395637(0) ack 1762138479 win 5840 <mss 1460>
E..,..@.9.;D@.. ...
.n..
...i..o`...g.........
22:08:10.602162 IP odin.aeronetworks.ca.49173 > venus.propagation.net.pop3: . ack 1 win 5840
E..(<.@.@......
@.. ...ni..o
...P.......
22:08:10.672614 IP venus.propagation.net.pop3 > odin.aeronetworks.ca.49173: P 1:64(63) ack 1 win 5840
E..g..@.9.'-@.. ...
.n..
...i..oP...)
..+OK Qpopper (version 4.0.5) at ns.aeronetworks.ca starting.

22:08:10.672665 IP odin.aeronetworks.ca.49173 > venus.propagation.net.pop3: . ack 64 win 5840
E..(<.@.@......
@.. ...ni..o
...P....s..
22:08:10.674028 IP odin.aeronetworks.ca.49173 > venus.propagation.net.pop3: P 1:14(13) ack 64 win 5840
E..5<.@.@......
@.. ...ni..o
...P...yo..USER herman

22:08:10.737847 IP venus.propagation.net.pop3 > odin.aeronetworks.ca.49173: . ack 14 win 5840
E..(..@.9.'k@.. ...
.n..
...i..|P....f........
22:08:10.738509 IP venus.propagation.net.pop3 > odin.aeronetworks.ca.49173: P 64:99(35) ack 14 win 5840
E..K..@.9.'G@.. ...
.n..
...i..|P...<r..+OK Password required for herman.

22:08:10.738731 IP odin.aeronetworks.ca.49173 > venus.propagation.net.pop3: P 14:27(13) ack 99 win 5840
E..5<.@.@......
@.. ...ni..|
...P....q..PASS MYPASSWORDWASHERE

22:08:10.805614 IP venus.propagation.net.pop3 > odin.aeronetworks.ca.49173: P 99:165(66) ack 27 win 5840
E..j..@.9.''@.. ...
.n..
...i...P...]...+OK herman has 89 visible messages (0 hidden) in 1062394 octets.

22:08:10.809216 IP odin.aeronetworks.ca.49173 > venus.propagation.net.pop3: P 27:33(6) ack 165 win 5840
E...<.@.@......
@.. ...ni...
..ZP....>..LIST

22:08:10.873591 IP venus.propagation.net.pop3 > odin.aeronetworks.ca.49173: P 165:207(42) ack 33 win 5840
E..R..@.9.'>@.. ...
.n..
..Zi...P...o@..+OK 89 visible messages (1062394 octets)

22:08:10.915002 IP odin.aeronetworks.ca.49173 > venus.propagation.net.pop3: . ack 207 win 5840
E..(<.@.@......
@.. ...ni...
...P...~...
22:08:10.981958 IP venus.propagation.net.pop3 > odin.aeronetworks.ca.49173: P 207:1029(822) ack 33 win 5840
E..^..@.9.$1@.. ...
.n..
...i...P...6n..1 2119
2 4229
3 2119
4 4511
5 9938
6 3482
7 20523
8 1807
9 2016
10 15065
11 9172
12 2862
13 5578
14 3457
15 3301
16 4293
17 2496
18 1403
19 3421
20 2253
21 2251
22 12265
23 4530
2
22:08:10.982014 IP odin.aeronetworks.ca.49173 > venus.propagation.net.pop3: . ack 1029 win 7398
E..(<.@.@......
@.. ...ni...
...P...ux..
22:08:11.037400 IP odin.aeronetworks.ca.49173 > venus.propagation.net.pop3: P 33:39(6) ack 1029 win 7398
E...<.@.@......
@.. ...ni...
...P.......UIDL

---

### Post by neil10 on 2007-07-07
just a typo ther  still no luck with password    Its always something simple

---

### Post by defishguy on 2007-07-07
Gmail requires SSL encryption for POP3 and SMTP.  If the encryption isn't selected then it will act exactly like a password or user name failure.

Make sure that SSL encryption is set for both protocols and give it another try.

Good luck, I hope that this works for you.

---

### Post by lisati on 2007-07-08
I think GMAIL also requires you to enable POP access from its options page. You'll need to sign into their webmail page to change the settings.

---

### Post by neil10 on 2007-07-08
thks for the reply but what you are sying is past my understanding. This is my first go  at ubuntu

---

### Post by neil10 on 2007-07-08
thks for that         where would i find the encryption       thks

---

### Post by r0ck80y on 2007-07-08
That depends on which client you are using (kmail, thunderbird, evolution etc). I use kmail...so for me the settings would be in "Settings -->configure kmail ----> Account tab (where i select the email service provider) --> and in there theres a "Security" tab where the encryption options are made. So just check your menu options ans search for something like "preferences" or "configure" etc just like you do in windows.

---

### Post by neil10 on 2007-07-08
yep evolution is mine I'll  look  thks

---

### Post by neil10 on 2007-07-08
It actually says ERR Authentication failed

---

### Post by neil10 on 2007-07-08
Ha d a thought went into my providers site where it says creat a account i see outlook express and microsoft outlook  would this be something that could be the problem, would it need something else

---

