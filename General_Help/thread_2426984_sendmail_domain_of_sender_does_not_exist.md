---
title: "sendmail domain of sender does not exist"
date: 2019-09-16
forum: General Help
---

### Post by ReneVeerman on 2019-09-16
hi.

i'm having difficulty getting sendmail to work :(

here's some output :

```
root@albatross:~# echo "Subject: t" | sendmail -v [email]seductiveapps@gmail.com[/email]
[email]seductiveapps@gmail.com[/email]... Connecting to [127.0.0.1] via relay...
220 albatross. ESMTP Sendmail 8.15.2/8.15.2/Debian-10; Mon, 16 Sep 2019 19:26:51 +0200; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
>>> EHLO albatross.
250-albatross. Hello localhost [127.0.0.1], pleased to meet you
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
>>> MAIL From:<rene@albatross> SIZE=11 AUTH=rene@albatross.
250 2.1.0 <rene@albatross>... Sender ok
>>> RCPT To:<seductiveapps@gmail.com>
>>> DATA
553 5.1.8 <seductiveapps@gmail.com>... Domain of sender address rene@albatross does not exist
503 5.0.0 Need RCPT (recipient)
>>> RSET
250 2.0.0 Reset state
>>> RSET
250 2.0.0 Reset state
rene... Using cached ESMTP connection to [127.0.0.1] via relay...
>>> MAIL From:<> SIZE=1035
250 2.1.0 <>... Sender ok
>>> RCPT To:<rene@albatross>
>>> DATA
250 2.1.5 <rene@albatross>... Recipient ok
354 Enter mail, end with "." on a line by itself
>>> .
050 <rene@albatross>... Connecting to local...
050 <rene@albatross>... Sent
250 2.0.0 x8GHQpSb006121 Message accepted for delivery
rene... Sent (x8GHQpSb006121 Message accepted for delivery)
Closing connection to [127.0.0.1]
>>> QUIT
221 2.0.0 albatross. closing connection
```


i couldn't find anything that fixes this situation on ubuntu via a google search, so i made this thread.

---

### Post by TheFu on 2019-09-16
A few background questions, first.
Do you own a domain name?
Did you setup DNS for the domain?
Did you setup an MX record for the email server on the domain?
Did you setup an SFP text record?
Is your email server on a commercial network or is it residential?
Do you plan to email just 1 account on gmail or every where in the world?

gmail won't accept email from unknown, unverified, domains.
```
Domain of sender address rene@albatross does not exist
```
says something is missing.

---

### Post by lisati on 2019-09-16
Is "albatross" is the name of one of the devices on your local network? If so, other email providers (e.g. gmail) are unlikely to know what to do with it, they'll be expecting something like *albatross*[dot]*something-more*.

---

### Post by ReneVeerman on 2019-09-17
i run websites for myself and other people, both on https and plain http, from behind an ADSL line.

for simplicity's sake, i'll state that i need to get two domains working; said.by (http) and nicer.app (https)

for both domains i have DNS set up with an MX record that points like everything else in the DNS setup to my outside IP of my ADSL line.

at the ADSL modem, i have port forwarding ('permit access' in my modem) enabled to send traffic to a single machine.

on that machine, i will probably need to run something like haproxy to get couchdb working,
but i think that's excess information for this thread..

i did not set up an SFP text record yet.
how would i do this?

and i need to be able to email anyone in the world from PHP and unix commandline.

also, 'albatross' is the internal name of the machine in question. nicer.app and said.by are it's external names.

---

### Post by SeijiSensei on 2019-09-17
You need to be sending from a machine with a "fully-qualified domain name" like albatross.example.com.  An unqualified name like just albatross will not work.

---

### Post by TheFu on 2019-09-17
I'll await the answers to my other questions.
Thank you.

---

### Post by ReneVeerman on 2019-09-17
> **SeijiSensei said:**
> You need to be sending from a machine with a "fully-qualified domain name" like albatross.example.com.  An unqualified name like just albatross will not work.

ok, ehm, would i specify that in /etc/hosts?

---

### Post by ReneVeerman on 2019-09-17
> **TheFu said:**
> I'll await the answers to my other questions.
Thank you.

i think i did that earlier in this thread :)

---

### Post by TheFu on 2019-09-17
> **ReneVeerman said:**
> i think i did that earlier in this thread :)

Appears to me that 4 of the questions aren't answered. If you don't understand a question, that isn't a good sign.  Ask and I'll try to explain.
In short, if you aren't on a business internet connection with static IPs, didn't buy a domain name and didn't buy a DNS provider to setup A, C NAME and MX records, then you won't be sending any email that will be accepted over the internet.

---

### Post by SeijiSensei on 2019-09-17
> **ReneVeerman said:**
> ok, ehm, would i specify that in /etc/hosts?

> >>> MAIL From:<rene@albatross> SIZE=11 AUTH=rene@albatross.
250 2.1.0 <rene@albatross>... Sender ok
>>> RCPT To:<seductiveapps@gmail.com>
>>> DATA
553 5.1.8 <seductiveapps@gmail.com>... Domain of sender address rene@albatross does not exist


rene@albatross is a valid email address, but not one that would work outside a local network.  For that you need a fully-qualified name with a domain part included as well.

In a telnet session to a remote mail server, you need to use "MAIL FROM: [email]rene@albatross.example.com[/email]".  You need control a valid domain and use it when composing a message.  Alternatively you could use [email]rene@example.com[/email]. How to do this depends on how your mail server is configured.  Also, if you want to receive email at one of these addresses, your mail server needs to know it is responsible for handling mail addressed to @albatross.example.com or just @example.com.  You need to specify both forms if you are intending to use both.  See the "mydestination" directive in Postfix or the local-host-names file in sendmail.

If you're using a client like Thunderbird, you would need to specify it in the configuration for your account.

Have you registered a domain?  If not, none of this will work.

/etc/hosts has nothing to do with this.

---

### Post by ReneVeerman on 2019-09-19
> **TheFu said:**
> Appears to me that 4 of the questions aren't answered. If you don't understand a question, that isn't a good sign.  Ask and I'll try to explain.
In short, if you aren't on a business internet connection with static IPs, didn't buy a domain name and didn't buy a DNS provider to setup A, C NAME and MX records, then you won't be sending any email that will be accepted over the internet.

i have a static IP address, 2 domain names (nicer.app and said.by) registered at 2 domain registrars, and DNS for both domains set to my static (permanent) IP address provided by my internet provider. and i do have a single MX record set up for both domains.

---

### Post by ReneVeerman on 2019-09-19
> **SeijiSensei said:**
> rene@albatross is a valid email address, but not one that would work outside a local network.  For that you need a fully-qualified name with a domain part included as well.

In a telnet session to a remote mail server, you need to use "MAIL FROM: [EMAIL="rene@albatross.example.com"]rene@albatross.example.com[/EMAIL]".  You need control a valid domain and use it when composing a message.  Alternatively you could use [EMAIL="rene@example.com"]rene@example.com[/EMAIL]. How to do this depends on how your mail server is configured.  Also, if you want to receive email at one of these addresses, your mail server needs to know it is responsible for handling mail addressed to @albatross.example.com or just @example.com.  You need to specify both forms if you are intending to use both.  See the "mydestination" directive in Postfix or the local-host-names file in sendmail.

If you're using a client like Thunderbird, you would need to specify it in the configuration for your account.

Have you registered a domain?  If not, none of this will work.

/etc/hosts has nothing to do with this.

i've got my domain name, a working DNS setup, and specifying a from address like below here, doesn't work :(

```
root@albatross:~# echo -e "Content-Type: text/plain\r\nFrom: [email]do-not-reply@nicer.app[/email]\r\nSubject: Test\r\n\r\nThe body goes here" | sendmail -v -f [email]do-not-reply@nicer.app[/email] [email]seductiveapps@gmail.com[/email]
[email]seductiveapps@gmail.com[/email]... Connecting to [127.0.0.1] via relay...
220 albatross. ESMTP Sendmail 8.15.2/8.15.2/Debian-10; Thu, 19 Sep 2019 17:05:57 +0200; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
>>> EHLO albatross.
250-albatross. Hello localhost [127.0.0.1], pleased to meet you
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
>>> MAIL From:<do-not-reply@nicer.app> SIZE=88 AUTH=do-not-reply@nicer.app
250 2.1.0 <do-not-reply@nicer.app>... Sender ok
>>> RCPT To:<seductiveapps@gmail.com>
>>> DATA
553 5.1.8 <seductiveapps@gmail.com>... **Domain of sender address [email]do-not-reply@nicer.app[/email] does not exist**
503 5.0.0 Need RCPT (recipient)
>>> RSET
250 2.0.0 Reset state
>>> RSET
250 2.0.0 Reset state
[email]do-not-reply@nicer.app[/email]... Using cached ESMTP connection to [127.0.0.1] via relay...
>>> MAIL From:<> SIZE=1112
250 2.1.0 <>... Sender ok
>>> RCPT To:<do-not-reply@albatross>
>>> DATA
550 5.1.1 <do-not-reply@albatross>... User unknown
503 5.0.0 Need RCPT (recipient)
>>> RSET
250 2.0.0 Reset state
>>> RSET
250 2.0.0 Reset state
postmaster... Using cached ESMTP connection to [127.0.0.1] via relay...
>>> MAIL From:<> SIZE=2136
250 2.1.0 <>... Sender ok
>>> RCPT To:<postmaster@albatross>
>>> DATA
550 5.1.1 <postmaster@albatross>... User unknown
503 5.0.0 Need RCPT (recipient)
>>> RSET
250 2.0.0 Reset state
MAILER-DAEMON... Saved message in /var/lib/sendmail/dead.letter
Closing connection to [127.0.0.1]
>>> QUIT
221 2.0.0 albatross. closing connection
```

---

### Post by SeijiSensei on 2019-09-19
I'd try talking directly to GMail with telnet.

```

$ telnet gmail-smtp-in.l.google.com 25
Trying 64.233.185.27...
Connected to gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP y17si3039798ybm.347 - gsmtp

```
Now go through the same dialog:
```

ehlo your.server.domain.name
[replies]
mail from: do-not-reply@nicer.app
rcpt to: seductiveapps@gmail.com

```
Now what happens? "your.server.domain.name" should be the fully-qualified public name for the machine from which you are sending.  It should match the reverse-DNS entry for your IP address.  For instance, "smtp.seductiveapps.com," which is the name returned for 82.161.37.94.

It would be good to add an [SPF record]("https://support.dnsimple.com/articles/spf-record/") for your sending host to your domain records as well.

---

### Post by TheFu on 2019-09-19
If my email servers sees this:
```
EHLO albatross.
```
It will reject all email from it.  It needs to be a FQDN and passes reverse lookup tests.
If the FROM address doesn't contain a FQDN, it will be rejected too.
If the SFP record for the MX server of the FQDN says the sender's IP isn't in the list, it will be rejected.
If the connection claims to be from any of my domain names, but the IP isn't in my allowed SMTP SPF record, it will be rejected.

Spam is a huge issue. Blocking for those reasons is extremely common.

---

### Post by ReneVeerman on 2019-10-01
ok so ehm how would i change 

ehlo albatross

by

ehlo smtp.nicer.app

?

---

### Post by slickymaster on 2019-10-01
@ReneVeerman:

Please [use code tags when posting output]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") because when posted as plain text it loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.

---

### Post by SeijiSensei on 2019-10-02
Sendmail uses the fully-qualified hostname during the SMTP handshake. So you server needs to be named smtp.nicer.app. You can put an entry in /etc/hosts if you want to keep albatross as a local alias, or add a CNAME record to the DNS zone file for nicer.app.

Also the reverse-DNS entry for the machine's IP address should return smtp.nicer.app.

---

### Post by ReneVeerman on 2019-10-02
reverse DNS for my outside IP is still set to my old domain name : smtp.seductiveapps.com
i can't find any way to change it, neither at my domain registrar (godaddy.com), nor at my DNS provider (afraid.org)

i'll have a look at that hosts file now.

---

### Post by ReneVeerman on 2019-10-03
per [https://serverfault.com/questions/205271/how-to-specify-outgoing-helo-with-sendmail](https://serverfault.com/questions/205271/how-to-specify-outgoing-helo-with-sendmail) ,
i changed that /etc/mail/sendmail.mc file to include the line

define(`confDOMAIN_NAME', `smtp.seductiveapps.com')dnl
i then re-ran my mail sending command : 

echo -e "Content-Type: text/plain\r\nFrom: [email]do-not-reply@nicer.app[/email]\r\nSubject: Test\r\n\r\nThe body goes here" | sendmail -v -f [email]do-not-reply@nicer.app[/email] [email]seductiveapps@gmail.com[/email]


but that just hangs and doesn't produce any output at all anymore..

---

### Post by SeijiSensei on 2019-10-03
Editing sendmail.mc is not enough. You must use m4 to generate a new sendmail.cf like this:
```

cd /etc/mail
sudo m4 < sendmail.mc > sendmail.cf

```

As a test I installed mailutils and sendmail on my laptop and issued the command:
```
echo test | mail -s test me@mydomain.com
```
It was sent without incident to that address.  The message left my machine and was sent to the primary MX host for mydomain.com whereupon it was delivered to my account.  

The From address read [email]me@myhost.mydomain.com[/email] and carried the full name field from my entry in /etc/passwd.

Now if I try to do the same thing but send to my gmail.com address, it goes nowhere because my ISP blocks outgoing connections to port 25 on remote servers.  If I run the command "mailq" I can see the message sitting in the queue because it was blocked.  The mail server for mydomain.com is within my local network.

---

### Post by ReneVeerman on 2019-10-04
i uninstalled ssmtp and re-installed mailutils, then ran the following :

```
root@albatross:/etc/mail# echo -e "Content-Type: text/plain\r\nFrom: [email]do-not-reply@nicer.app[/email]\r\nSubject: Test\r\n\r\nThe body goes here" | sendmail -v -f [email]do-not-reply@nicer.app[/email] [email]seductiveapps@gmail.com[/email]
Mail Delivery Status Report will be mailed to <do-not-reply@nicer.app>.
root@albatross:/etc/mail# tail /var/log/mail.log
Oct  4 08:27:22 localhost postfix/smtp[405]: connect to gmail-smtp-in.l.google.com[2a00:1450:4013:c07::1b]:25: Connection timed out
Oct  4 08:27:42 localhost postfix/smtp[32585]: connect to alt1.gmail-smtp-in.l.google.com[2404:6800:4003:c04::1a]:25: Connection timed out
Oct  4 08:27:52 localhost postfix/smtp[405]: connect to gmail-smtp-in.l.google.com[74.125.143.27]:25: Connection timed out
Oct  4 08:27:53 localhost postfix/pickup[31685]: 31FB8400BB7: uid=0 from=<do-not-reply@nicer.app>
Oct  4 08:27:53 localhost postfix/cleanup[32583]: 31FB8400BB7: message-id=<20191004062753.31FB8400BB7@nicer.app>
Oct  4 08:27:53 localhost postfix/qmgr[31686]: 31FB8400BB7: from=<do-not-reply@nicer.app>, size=297, nrcpt=1 (queue active)
Oct  4 08:28:12 localhost postfix/smtp[32585]: connect to alt2.gmail-smtp-in.l.google.com[2404:6800:4008:c00::1b]:25: Connection timed out
Oct  4 08:28:12 localhost postfix/smtp[32585]: 14859400BB5: to=<seductiveapps@gmail.com>, relay=none, delay=150, delays=0.02/0.01/150/0, dsn=4.4.1, status=deferred (connect to alt2.gmail-smtp-in.l.google.com[2404:6800:4008:c00::1b]:25: Connection timed out)
Oct  4 08:28:22 localhost postfix/smtp[405]: connect to alt1.gmail-smtp-in.l.google.com[2404:6800:4003:c04::1a]:25: Connection timed out
Oct  4 08:28:23 localhost postfix/smtp[1413]: connect to gmail-smtp-in.l.google.com[2a00:1450:4013:c00::1b]:25: Connection timed out
```


i currently have no way to view mail for any address on nicer.app

i'm hoping someone here can explain to me why the gmail connection attempted above here fails to connect.
it's not like my ISP blocks outgoing ports or anything..

---

### Post by slickymaster on 2019-10-04
@ReneVeerman:

Once again, please [use code tags when posting output]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") because when posted

---

### Post by SeijiSensei on 2019-10-04
Did you try the test I posted above: [https://ubuntuforums.org/showthread.php?t=2426984&p=13890081&viewfull=1#post13890081](https://ubuntuforums.org/showthread.php?t=2426984&p=13890081&viewfull=1#post13890081)

What happened?

---

### Post by ReneVeerman on 2019-10-05
i tried your test just now, and here's the result :( 

```

root@albatross:/etc/mail# telnet gmail-smtp-in.l.google.com 25
Trying 2a00:1450:4013:c04::1a...
Trying 172.217.218.26...
telnet: Unable to connect to remote host: Connection timed out

```

i'd really love some clues as to what could be causing this.
my ISP says it isn't them.

---

### Post by SeijiSensei on 2019-10-05
They're probably not telling you the truth, or the person you spoke with isn't knowledgeable.  I assume you can ping 172.217.218.26, right?

Try the same test to 50.116.11.117, my inbound mail server. Can you connect to that?

---

### Post by ReneVeerman on 2019-10-06
i called up my ISP again, and after some tests on their end, they can't figure it out either :(

```

telnet 50.116.11.117 25 

```

didn't work (connection timed out), while traceroute and ping to the same address did.

---

### Post by SeijiSensei on 2019-10-06
Then the ISP is almost certainly blocking outbound connections to port 25. If they're not blocking those connections, someone upstream of them is doing so.

Are you running a firewall?  Could it be blocking this traffic?  If so, let's see the results of "sudo iptables -L -nv".

---

### Post by ReneVeerman on 2019-10-07
well that would suck. i suppose i should try to get sendmail to use encrypted ports? how would i do that?

```

root@albatross:/etc/mail# sudo iptables -L -nv
Chain INPUT (policy DROP 1386 packets, 234K bytes)
 pkts bytes target     prot opt in     out     source               destination         
  14M   11G ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  14M   11G ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 4104  777K ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 3108  546K ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 3108  546K ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 3108  546K ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-before-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-before-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-reject-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-track-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain OUTPUT (policy ACCEPT 191 packets, 11059 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  12M 8980M ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  12M 8980M ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 583K   37M ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 583K   37M ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 583K   37M ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 583K   37M ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-after-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-after-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    6   468 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:137
  958  228K ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:138
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:139
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:445
    3   984 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:67
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:68
   29  1391 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST


Chain ufw-after-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "


Chain ufw-after-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 2947  318K LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "


Chain ufw-after-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-after-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-before-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
    0     0 ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
1424K  207M ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
  12M   11G ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
61331 2463K ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
61331 2463K DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp spt:67 dpt:68
 227K   12M ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  608 72827 ACCEPT     udp  --  *      *       0.0.0.0/0            224.0.0.251          udp dpt:5353
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            239.255.255.250      udp dpt:1900
 226K   12M ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-before-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-before-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-before-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-before-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
1424K  207M ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
  10M 8736M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
 583K   37M ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-logging-allow (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW ALLOW] "


Chain ufw-logging-deny (2 references)
 pkts bytes target     prot opt in     out     source               destination         
 8526  348K RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID limit: avg 3/min burst 10
 4975  200K LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "


Chain ufw-not-local (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 222K   11M RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type LOCAL
 3372  172K RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type MULTICAST
  996  231K RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST
    0     0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-reject-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-reject-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-reject-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-skip-to-policy-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-skip-to-policy-input (7 references)
 pkts bytes target     prot opt in     out     source               destination         
  996  231K DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-skip-to-policy-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-track-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-track-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-track-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 271K   16M ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW
 311K   21M ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW


Chain ufw-user-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
95634 4623K ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:80
   47  2420 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:5984
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:5984
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:20
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:21
   58 45284 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            multiport dports 40000:50000
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:990
   52  2768 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:25
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:25
    0     0 ACCEPT     tcp  --  *      *       192.168.0.0/24       0.0.0.0/0            tcp dpt:80
    0     0 ACCEPT     udp  --  *      *       192.168.0.0/24       0.0.0.0/0            udp dpt:80
 126K 6220K ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:443
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:443
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:5984
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:5984
    3   132 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:5985
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:5985


Chain ufw-user-limit (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 5 LOG flags 0 level 4 prefix "[UFW LIMIT BLOCK] "
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable


Chain ufw-user-limit-accept (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           


Chain ufw-user-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-user-logging-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-user-logging-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         


Chain ufw-user-output (1 references)
 pkts bytes target     prot opt in     out     source               destination   

```

---

### Post by SeijiSensei on 2019-10-07
Wow, that's a way more complex set of rules than I'd expect.  Is this machine connected directly to the Internet, or is it behind a firewall router?  If the latter, I wouldn't bother with a local firewall at all. What if you bring down the firewall and try connecting?

---

### Post by TheFu on 2019-10-07
Is there a specific reason for using sendmail and not one of the easier-to-configure SMTP solutions like postfix?
If you are an ISP with hundreds of different domains, a case for using sendmail could be made. If you have 20 or fewer domains, postfix is much easier to configure.  I stopped using sendmail in the 1990s.  If you **need** to run sendmail, then it is probably worth buying the Sendmail book from O'Reilly.

I specifically don't support IPv6 because I wasn't comfortable with it and didn't think I knew enough to properly secure it.  A few daemons here have show they had issues with IPv6 over the years.  I've had to take specific steps with sshd, for example.  

There is little you can do if the server on the other end is rejecting your connections. I'm fairly brutal if there is spam coming from a subnet. I don't just block 1 IP, I block the entire subnet.  Last week, a subnet sent over 15,000 spam emails to one of my domains. They and all their network neighbors on the same IP are blocked. That IP resolved back to Leeds in the UK.  Every few years, I'll put in a new email gateway with upgraded software and usually don't bring the prior firewall rules over.  Usually the subnet size blocked is a /18 or /20, but every once in a while, it is a /12 or even a /8 (mainland Chinese University).

---

### Post by SeijiSensei on 2019-10-07
I don't think this is a sendmail issue, nor a problem with the remote server rejecting his connection. The telnet tests show he simply cannot connect at all which tells me someone somewhere along the line is blocking outbound port 25 connections.

---

### Post by ReneVeerman on 2019-10-08
woohoo! 

```

sudo service ufw stop

```

fixed all my problems, including the actual command line sending of emails that i was trying to get done earlier in this thread!

everyone, thanks a lot for your help.

i do wonder if stopping the ufw service permanently is a good idea.
if anyone can help me fix it's rules, i'd be much obliged :)

---

### Post by SeijiSensei on 2019-10-08
Does the machine have an interface that is directly exposed to the Internet, or is it behind a firewall router?

---

### Post by ReneVeerman on 2019-10-10
> **SeijiSensei said:**
> Does the machine have an interface that is directly exposed to the Internet, or is it behind a firewall router?

it's behind an ADSL modem which has a firewall.

---

### Post by SeijiSensei on 2019-10-10
I'm usually fine with that sort of configuration and no firewall on the machines behind the router.  If you're concerned about security, I'd buy another router. You can get a decent Ethernet router for < $100.  My home/office network runs on a [AC1200 router]("https://www.amazon.com/TP-Link-AC1200-Smart-WiFi-Router/dp/B07N1L5HX1/") behind my ISP's router.

---

### Post by TheFu on 2019-10-10
+1 for using a router that you control.  Never trust the ISP equipment.  BTW, I used to work for an ISP and worked the project to deploy patches to CPE - Customer Premise Equipment - for our 50+M customers.  Always have your own router and put theirs into bridge mode, if you can.

---

### Post by SeijiSensei on 2019-10-11
> **TheFu said:**
> Always have your own router and put theirs into bridge mode, if you can.
Mine are daisy-chained via Ethernet. What advantage would putting the ISP's router into bridge mode provide?

---

### Post by TheFu on 2019-10-11
> **SeijiSensei said:**
> Mine are daisy-chained via Ethernet. What advantage would putting the ISP's router into bridge mode provide?

Avoiding double-NAT which causes issues for some protocols (cough SIP). Direct control over subnets and firewall rules.

---

### Post by SeijiSensei on 2019-10-11
I don't use any such protocols, and I have full control over the router I maintain behind the ISP's device.  I'll stick with the daisy-chain.

---

