---
title: "Sendmail  Connection refused by [127.0.0.1]"
date: 2017-11-07
forum: General Help
---

### Post by Hadaka on 2017-11-07
Hi, from this link...
[https://clients.javapipe.com/knowledgebase/132/How-to-Test-Sendmail-From-Command-Line-on-Linux.html](https://clients.javapipe.com/knowledgebase/132/How-to-Test-Sendmail-From-Command-Line-on-Linux.html)
using the simple sendmail,the connection is refused.
hadaka:~$ which sendmail
```
/usr/sbin/sendmail
```
hadaka:~$ echo "Subject: sendmail test" | sendmail -v [email]My_Mail@yahoo.com[/email]
```
My_Mail@yahoo.com... Connecting to [127.0.0.1] via relay...
My_Mail@yahoo.com... Deferred: Connection refused by [127.0.0.1]
```
I have zero experience using the command line to send e-mail, or how to easily
correct this error. Please post the exact command and simple explanation to correct.
Or any commands you need me to post.
Thanks.

---

### Post by SeijiSensei on 2017-11-07
Sendmail needs to be running as a daemon process. How to start it depends on what version of Ubuntu you're running.  Before 16.04, you should try
```
sudo service sendmail start
```
From 16.04 onward you would use
```
sudo systemctl start sendmail.service
```

Now try entering the command "telnet localhost 25" and see if you get a banner that includes a line like "220 localhost".  If so, the server is responding.  Hold down Ctrl and hit c, then type quit at the prompt.  You'll be back to the command line.

I use the hoary "mail" program to send mail at the command prompt; it's part of the mailutils package.

```
sudo apt-get install mailutils
```

When it's done, try sending a message to yourusename@localhost like this:

```
echo test | mail -s test yourusername@localhost
```

That command sends the string "test" as an input to the mail program; the "-s test" sets the subject line.

Check to see what happens in /var/log/mail.log.  If things work correctly, your test message should reside in your inbox, /var/spool/mail/yourusername.  You can install a command-line mail reader like "alpine".  Run it from the command line as either alpine or pine.  When you get to the main menu, type "i" to see your inbox.  Your test message should appear there.

---

### Post by Hadaka on 2017-11-08
Hi, the telnet comand seems to work
sending to my yahoo.com mail account does not.

hadaka@the-beach:~$ sudo service sendmail start
 ```
* Starting Mail Transport Agent (MTA) sendmail                                                                                 [ OK ] 
```
hadaka@the-beach:~$ telnet localhost 25
```
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 the-beach.fios-router.home ESMTP Sendmail 8.14.4/8.14.4/Debian-2ubuntu2.1; Wed, 8 Nov 2017 12:01:12 -0500; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
^C
quit
Connection closed by foreign host.
```
_______________________________________
Sending this comand...
 echo "Subject: sendmail test" | sendmail -v [EMAIL="My_Mail@yahoo.com"]My_Mail@yahoo.com [COLOR=#008080]<-My Real yahoo.com I.D was sent. *EDITED for post*[/COLOR][/EMAIL]
from this link...
[https://clients.javapipe.com/knowledgebase/132/How-to-Test-Sendmail-From-Command-Line-on-Linux.html](https://clients.javapipe.com/knowledgebase/132/How-to-Test-Sendmail-From-Command-Line-on-Linux.html)
outputs...
hadaka@the-beach:~$  echo "Subject: sendmail test" | sendmail -v [EMAIL="My_Mail@yahoo.com"]My_Mail@yahoo.com[/EMAIL]
[EMAIL="My_Mail@yahoo.com"]My_Mail@yahoo.com[/EMAIL]... Connecting to [127.0.0.1] via relay...
220 the-beach.fios-router.home ESMTP Sendmail 8.14.4/8.14.4/Debian-2ubuntu2.1; Wed, 8 Nov 2017 12:04:38 -0500; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
>>> EHLO the-beach.fios-router.home
250-the-beach.fios-router.home Hello localhost [127.0.0.1], pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-EXPN
250-VERB
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-AUTH DIGEST-MD5 CRAM-MD5
250-DELIVERBY
250 HELP
>>> VERB
250 2.0.0 Verbose mode
>>> MAIL From:<hadaka@the-beach.fios-router.home> SIZE=23 AUTH=hadaka@the-beach.fios-router.home
250 2.1.0 <hadaka@the-beach.fios-router.home>... Sender ok
>>> RCPT To:<My_Mail@yahoo.com>
>>> DATA
250 2.1.5 <My_Mail@yahoo.com>... Recipient ok
354 Enter mail, end with "." on a line by itself
>>> .
this is a test
.
^CClosing connection to [127.0.0.1]
>>> QUIT
***This hangs for 5 to 10 minutes then quits.
and leaves these processes running...
hadaka@the-beach:~$ ps aux | grep -i sendmail
```
root     18337  0.0  0.1  15116  2204 ?        Ss   12:00   0:00 sendmail: MTA: accepting connections          
root     18338  0.0  0.1  15040  2712 ?        S    12:00   0:00 sendmail: MTA: ./vA8GXYPK017575 mta7.am0.yahoodns.net.: user open
root     18397  0.0  0.2  15348  3808 ?        S    12:04   0:00 sendmail: MTA: ./vA8H4c5X018397 mta6.am0.yahoodns.net.: user open
root     18474  0.0  0.1  15160  2808 ?        S    12:10   0:00 sendmail: MTA: ./vA8Ggg64017939 mta7.am0.yahoodns.net.: user open
hadaka   18521  0.0  0.0   4396   796 pts/1    S+   12:14   0:00 grep --color=auto -i sendmail
```
Perhaps the sendmail configuration is off ???
I have NO desire to send/read/write to localhost..
All seems ok when sending to telnet 25
NOT OK when sending to my yahoo.com mail
Do I need to point to port 25 ?
Thanks thus far for your help, I'm still lost.

---

### Post by SeijiSensei on 2017-11-10
You need to speak to your ISP.  If you are on a residential connection, the chances are good that you cannot send mail via SMTP to remote machines.  You can test this by running "telnet gmail-smtp-in.l.google.com 25".  Running this on my machine here times out since my provider blocks such connections.  Running the same command on my publicly-visible mail server results in an immediate reply.

---

### Post by efflandt on 2017-11-10
You likely need to configure sendmail to relay through your ISP's mail relay. That might be easy or difficult, depending upon whether that requires authentication or different port than port 25. Many MX (destination) mail servers do not accept direct mail from anything they think has a dynamic IP address due to spammers or many worms and viruses that contain their own smtp server to spread themselves. And for same reasons ISPs often block outgoing port 25 other than to their own mail relays.

For example I am on AT&T DSL (with dynamic IP) which used to use Yahoo servers (before Yahoo was acquired by Verizon) and if I tried to send mail directly to my AT&T email account, it was redirected to a Yahoo server with a name of something like nomail.yahoo.com that did not accept any mail at all. It worked going through my ISP's outgoing relay when that just required SMTP AUTH. I have not tried that since the mail relay is on a different port using SSL.

---

### Post by Hadaka on 2017-11-10
Hi, thanks SeijiSensei for taking the time to explain why it is likely not working, and for your
suggestions. Thanks also to efflandt for the additional information. This is just a simple LAN
desktop server configuration. Residential use and no router port forwarding to ssh in from outside.
What I was attempting to do is write additional code to a simple script that is used to monitor the status
of the wired and wireless connection and send an e-mail to my yahoo.com mail in the event the wireless
fails. Having zero experience with using the command line to do so, google pointed me to "sendmail'. It
appeared to be something that would be simple and easy, obviously not. Thanks again for the help, I am going
to mark this thread solved,due to my ignorance of command line email sending.

---

