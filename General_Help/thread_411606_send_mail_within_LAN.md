---
title: "send mail within LAN"
date: 2007-04-17
forum: General Help
---

### Post by jmvidalvia on 2007-04-17
I'm trying to set postfix to send messages within my LAN: from one laptop to another. 
¿can anybody help me?
Thanks!

---

### Post by kidders on 2007-04-17
Hi there,

That's a slightly odd request, which would probably require two Postfix installs ... one on each laptop. For most purposes, storing all mail at a single location is most desirable.

Could you describe what you want to achieve? Perhaps you are trying to find a way of moving large amounts of email between two delivery systems?

---

### Post by jmvidalvia on 2007-04-17
Hello, 

Just installed my first ubuntu-server at home: got ssh, nfs, squid, dansguard and apache, all working....Feel so happy that I want to go ahead: now is time to start with mail!
I exactly don't know what I want (bad start, I know).

1st, what seems more simple, to get messages from the server to my laptop, every time something happens. Have to decide this events: copy completed, somebody tried to login, etc.

2nd, already posted here, I would like to have a backup of my gmail. The e-mail client should download all messages and leave them in the gmail server, so I don't notice anything. I've been told about mutt, but had no time to work on it yet.

Perhaps my real question is ¿what interesting things can I do with an e-mail server? Does it make any sense to spend time trying to learn? 
Many thanks!

---

### Post by kidders on 2007-04-17
Hey again,

> **jmvidalvia said:**
> Just installed my first ubuntu-server at home: got ssh, nfs, squid, dansguard and apache, all working.That's an impressive list!

> **jmvidalvia said:**
> Perhaps my real question is ¿what interesting things can I do with an e-mail server? Does it make any sense to spend time trying to learn?Mail servers are certainly worth learning about. :-) Since you don't have any particular configuration in mind, I would suggest something like the following...

_**Postfix**_
Installing Postfix makes you a mail gateway. Normally, an organisation will only have one of these, which stores mailboxes for its users, and handles the delivery of incoming & outgoing messages. So, if you want your system to notify you when certain things happen, you could configure it to deliver messages to jmvidalvia@yourdomain. Properly configured, your Postfix will recognise the local address, and drop the messages in your personal mailbox.

_**Fetchmail**_
Fetchmail can be configured to download email from other SMTP servers, and deliver them to a local address, using your Postfix installation. That would allow you to collect all your email together from multiple sources (eg Gmail, Yahoo, etc.), and access it from a single location. One advantage in doing this is the ability to apply your own filtering, set up spam/virus protection, pass emails through local applications (eg rebooting your PC by sending "Reboot" to your Gmail account, or something like that), and other advanced behaviour.

_**IMAP**_
Once you've got message delivery sorted out, you will need a way to read your messages. I use Courier-IMAP-SSL for this ... but you can use whatever you want. IMAP allows you to store your mail in one place, but still get access to it from multiple locations.

_**Outgoing mail delivery**_
That's quite a thorny topic, that I probably shouldn't go into until I have a clearer idea of what you plan on doing. It's something worth thinking about though.


So, I suppose the point is that because email systems are designed to be highly scalable, server applications tend to be very compartmentalised. Before you can decide what you need to install, or how you want to configure it, you need to have a pretty clear idea of what you'd like to achieve.

---

### Post by jmvidalvia on 2007-04-17
Great help!
It was very difficult for me to understand this "all together": I will follow your advises!
Thanks you very much!

---

### Post by kidders on 2007-04-17
No problem. :-) Post back if you have any trouble!

---

### Post by jmvidalvia on 2007-04-18
Hi, back again.
I am following the nice guide you can find [here]("https://help.ubuntu.com/community/PostfixBasicSetupHowto#").

I already installed Postfix: it works
I made this telnet test:

```
jm@jm:/etc/postfix$ telnet jm 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 localhost ESMTP Postfix (Ubuntu)

```
In the guide, they get this:

```
Trying 127.0.0.1...
Connected to mail.fossedu.org.
Escape character is '^]'.
220 localhost.localdomain ESMTP Postfix (Ubuntu)

```


My 1st question is: **how is mail.fossedu.org assigned to 127.0.0.1?**

My /etc/hosts looks like:

```
127.0.0.1 localhost jm
127.0.1.1 jm
192.168.1.132 server

```

My 2nd question is also related with domains:
After installing IMAP and POP3, the guide does this test:

```
telnet mail.yourdomain.com 25
```

and my question: **is yourdomain.com suposed to be a public domain?** Is it just a local name? what about passwords? I tryied with my real domain but It didn't work: It would have been a miracle, as  my MX are re-directed to Gmail-hosted...

As you see, a I am little bit confused at this point.
Thank-you for your help!

---

### Post by kidders on 2007-04-18
Hiya,

> **jmvidalvia said:**
> My 1st question is: **how is mail.fossedu.org assigned to 127.0.0.1?**Normally with DNS, although there are many other possible sources, such as LDAP, WINS, /etc/hosts.... The "hosts" line in your /etc/nsswitch.conf will tell you how your system is resolving hostnames. You can override Postfix's reported hostname in main.cf if you want ... It's not something that makes any real difference.

> **jmvidalvia said:**
> My /etc/hosts looks like:

```
127.0.0.1 localhost jm
127.0.1.1 jm
192.168.1.132 server

```According to your /etc/hosts, 127.0.0.1 resolves to "localhost" ... which you _absolutely should not_ change (just in case). Since that is the interface you telnet-ed over, Postfix correctly reported its hostname in its greeting.

> **jmvidalvia said:**
> **is yourdomain.com suposed to be a public domain?**Emmm... well... it *can* be, if you want it to be. Unless you want other mail gateways to deliver to you (which isn't the impression I got from your o/p), it certainly doesn't *have* to be though.

> **jmvidalvia said:**
> what about passwords?It's not normal practice to require authentication for SMTP mail exchange, since there would be no way for a mail delivery agent to know what it is.

The one exception would be situations where a message recipient wasn't local. If you intend to make your SMTP server externally accessible, it is *vitally* important that you configure Postfix to reject mail addressed to non-local recipients. You could then (optionally) implement authentication, that would allow legitimate users of mail clients (like Thunderbird, Evolution, etc.) to override the restriction, and send mail off-site.

I hope that helps!

---

### Post by jmvidalvia on 2007-04-18
Yes, that helps! 
Now it is my time to get it working!
Thank you very much.

---

### Post by kidders on 2007-04-18
No problem. :-) ... and good luck!

---

### Post by jmvidalvia on 2007-04-18
Still thinking about it:

If I want to do this...(from the above mentioned guide)

```
telnet mail.yourdomain.com 25
ehlo yourdomain.com
mail from: root@yourdomain.com
rcpt to: fmaster@yourdomain.com
data
etc....
```

...then I need to create my domain locally and make something to allow I supose DNS to find it im my LAN. Am I right?
I have no idea on how to do this...
Thanks again!

Added: the guide says:

```
In this setup I assume that your domain is yourdomain.com and it has a valid MX record call mail.yourdomain.com. Remember to replace yourdomain.com with your actual domain in the example codes in this howto. Also I assume that you know what an MX record is.
```

Doesn't it mean it must be a public domain?

---

### Post by kidders on 2007-04-18
For a local setup, you often don't need to worry too much about MX records, etc. Certain setups do require them though, so you would probably install **Bind**, and use it to handle all local DNS.

Having said that, for the actual SMTP commands you posted to work properly, all that is required is for Postfix to consider itself the final destination for "yourdomain.com". As you seem to be aware, MX records are only useful to services that don't already know where your SMTP server is.

(I'm not sure how well I explained that!) :-k

For something like what you describe to work properly from *outside* your local environment, you _would_ need a proper DNS service though.

**Edit:** I've just seen your additional comments. Perhaps it's time to clarify exactly what you want your mail gateway to do ... are you interested in exchanging mail with other SMTP services (ie having mail delivered to you, rather than having your server fetch it)? To put the question another way, if you were to compare your SMTP server to Gmail's one, is there anything theirs does that you *don't* want yours to do?

---

### Post by jmvidalvia on 2007-04-21
Hi again.
The more I work on it, the more confussed I get.
This is my situation:
I installed postfix, mailx, courier-pop, courier-imap and mutt
I am able to send a mail to outside accounts (gmail, or hotmail) using sendmail or mailx command, and also through mutt, the text mail client.
I am able to atacch files to mutt e-mails.
I am able to send mails througth telnet within my LAN.

Better go step by step:

1- How can I send an e-mail within my LAN, avoiding using telnet? I have "jm" machine with "jm" user, and "server" machine with "jms" user. 
2- I have a dyndns.org account. Can I use this domain to test an e-mail server?

Beware: more questions to come! :) 
Thank you very much!

---

### Post by kidders on 2007-04-21
Hey again,

If you can use telnet to send local mails, then you should be able to use *any* client to do it ... the software you send a mail with shouldn't make any difference. :confused:

> I have a dyndns.org account. Can I use this domain to test an e-mail server?In theory you can, but as you may be aware, virtually all mail gateways will throw away messages received from IPs reserved for domestic use. Unless you take measures to cloak the true origin of mail you send, I wouldn't expect very many people to receive them. In addition, you would have to be in a position to guarantee the accessibility of your mail server at _all_ times.

As a guideline, if an external user thinks your email address is something@your-dyndns-domain.com, you're probably using the wrong mail handling strategy. Conversely, if mail reception still works with incoming connections on port 25 blocked, you're probably using the *right* strategy. You've said very little about how you're managing your mail, so I'm not sure what you're up to. :-(

Let me try to be a little clearer...

If an externally accessible MX record points mail@your-dyndns-domain.com to your IP, then mail reception should work as expected. However, depending on the nature of the connection provided by your ISP, most mail gateways your postfix tries to *transmit* to (with only a few exceptions) will consider there to be a 100% probability the message you are sending is spam. Consequently, I would not recommend using your DynDNS domain name in email, unless you are prepared to take measures to avoid this problem. In addition, should your internet connection (or anything else involved in your mail handling) go down, you will start losing incoming mail almost immediately.

A far more robust solution would be to pipe outgoing messages through existing mail gateways you have access to, such as Gmail's, perhaps. You would block all incoming connections on port 25, offer no externally accessible MX record, and use Fetchmail to collect incoming mail. Essentially, your mail server would only operate as a "proper" mail server when it is handling mail originating from _and_ destined for local users.

Does that make any sense?

> Beware: more questions to come!Yay! :-) Hehe. Keep 'em coming.

---

### Post by jmvidalvia on 2007-04-21
Many thanks!
Going for a pair of Guinness to help me understand everything..
;)
I'll be back.

---

### Post by kidders on 2007-04-21
:lolflag:


Think of it this way...[LIST=1]
[*]Block port 25 at your outermost router, so Postfix can't receive any mail from the outside world.
[*]Configure Postfix to deliver all mail it isn't the final destination for to a deliberately invalid location, so its outgoing mail queue starts to fill up.
[*]Now set Postfix up so it can handle local mail properly.
[*]Configure your POP/IMAP servers. **Do not** make them externally accessible.[/LIST]Once you've done that much, your original request is satisfied, in that you can now send internal messages, and read them from any machine on your network.

From here, there are many options. One possibility would be to teach Postfix how to send all non-local mail using your Gmail account. To an external mail recipient, your email address would appear to be @gmail.com. Your outgoing mail queue would then start to empty properly.

Another bonus would be the ability to read your mail, even when you're not at home. There are two options:[LIST]
[*]**You have a laptop that you carry around with you.** By setting up local _and_ externally visible DNS records pointing mail.your-dyndns-domain.com to the right places, and _configuring POP or IMAP to run securely_, you could get access to your mail from anywhere.
[*]**You would like to be able to use other peoples' computers.** The best option here would be webmail. Something like Horde or SquirrelMail might be worth a look. Again, these services should _always run securely_ (over HTTPS, in this case).[/LIST]How does that grab you?

The major advantages over what you might think of as the proper, conventional configuration are:
[LIST=1]
[*] You are relying on other companies' SMTP servers to stay up all the time, not your own.
[*] There will be a far higher probability of successful delivery of external mail.[/LIST]I hope that's a little clearer.

---

### Post by jmvidalvia on 2007-04-22
Hi again!
I am learning quite a lot!
I got mutt receiving and sending e-mails from my gmail account, so I can now backup everything: an important part of what I wanted is achieved.
But I still have a basic problem that I would like to understand: yesterday I posted a late  new message [here]("http://ubuntuforums.org/showthread.php?t=417616"), hopping to get help from different time-zone people. It is the same as always.
I understand now how postfix works, but need to solve e-mail sending and receiving between local IP's.
Thanks again for your help!

---

### Post by kidders on 2007-04-22
I'm confused. Why would you want to send an email between two computers on the same network? Another way of asking the question would be "Why would you want to have a domain with only one computer in it?"

To be able to send an email from someone@server to someone@laptop...
[LIST]
[*]You would have to set up two mail gatways, one of which would only have one purpose in life ... to receive mail from the other.
[*]As a result, your mail would become fragmented, rather than being stored in one place, which seems more sensible.
[*]Both computers would have to be on (and connected to each other) all the time, for mail handling to work effectively.
[*]You would have two domains, each with only one computer in it ... even though both boxes are on the same network.[/LIST]The usual purposes for the kind of configuration you're describing are replication, load balancing, and so on, where the two mail gateways are exchanging high volumes (more than 100 messages per minute) of mail.



The more usual approach is to think of things in terms of *people*, not computers. For instance, whether you happen to be in Germany today, or South Africa, your email address is the same ... because people send messages to _you_ (not your computer).

To be honest, I have really only been guessing about your intentions, and offering standard solutions to common situations. Perhaps you could describe what you want to achieve in a little more detail ... that way, we can be sure you get what you want!

---

### Post by jmvidalvia on 2007-04-22
Thank you very much!
I realize how confusing I have been...
Perhaps my mistake was thinkings the easiest way to learn about e-mailing was starting within my own LAN, avoiding the risks of going outside.
As you say it seems stupid to have two machines with two domains. For sure this is the point. I just wanted to send messagges from one machine to another.
Let's see an example:
I set up a cron job with a backup task. If it gets an error I wnow how to send an e-mail to my gmail account, but I wondered if it would be possible to get the messages only when logging in my LAN. Say, I arrive at home, I connect to eth1 and get: "You have an e-mail form *server*". 
Probably we have been traveling too far for a silly question like this....
I appreciate your efforts to understand me, many thanks again!

---

### Post by kidders on 2007-04-22
Hmmmm....

I'll try to describe what I've had in my mind when suggesting things to you. Hopefully, our ideas of the perfect setup aren't too far apart ... if they are, _it's my fault_, not yours!

[U][B]I - Postfix
[/B][/U]You could invent a local mail domain that provides accounts for all local users. Each user would have a single mailbox, stored on the Postfix server box. Importantly, nobody in the "real" world would be aware this mail domain exists.

Your Postfix server could receive two kinds of emails:[LIST]
[*]**Local -> Local**: These mails would be delivered normally. Postfix would drop them in the correct local mailbox.
[*]**Local -> Remote**: The sender addresses for these mails would be rewritten, and Postfix would force-feed them to a pre-defined third party SMTP server for deliver.[/LIST]The purpose here is to avoid letting anyone see your private domain name, and ensure that no-one outside your LAN ever received a mail directly from your Postfix gateway. Additionally, your gateway only receives email when _it_ wants to ... so you don't have to guarantee 99.975% uptime to avoid dropping messages!

Your Postfix would never receive messages that are either **Remote -> Remote** or **Remote -> Local**.

_**II - Fetchmail**_
Meanwhile, Fetchmail polls the third party mail server at regular intervals, looking for replies to outgoing messages. It sucks them down into your private Postfix server for local delivery.

The result is that the complicated delivery process that actually takes place is completely transparent, and appears (to you and your other users) to be perfectly simple. Also, you would never need to log into any mail server (other than your own) to read mail.

_**III - Local Messaging**_
You would now have the ability to handle ***all*** email in an effective, reliable manner ... including local messaging, as requested. Your computers could be configured to automatically transmit cron messages/etc. to your centralised local account, which would be available for reading from any computer on your network, along with all mail downloaded (by Fetchmail) from any other real-world email addresses you might have.

[U][B]IV - Variations
[/B][/U]You might not be interested in having Postfix handle remote mail at all. In that case, you would need to explicitly configure it to reject mail destined for non-local mailboxes.

Alternatively, you might decide to unify mail sorting, filtering, spam & virus protection, so that mail (whether it be from Yahoo, Gmail, Hotmail...) is all treated the same way, using a common set of rules.

You may want to read cron error messages, etc. while you're away from home. You could configure an externally accessible IMAP (or webmail) server to allow you to do this.




So.... How far is this from what you would like?

---

### Post by jmvidalvia on 2007-04-22
Nice information: Now everything starts to be clear for me. I would like to stop in the first point:
You say (sorry, don't know how to quote)

[I]**I - Postfix**
You could invent a local mail domain that provides accounts for all local users. Each user would have a single mailbox, stored on the Postfix server box. Importantly, nobody in the "real" world would be aware this mail domain exists.[/I]

I have been trying to find out how to "invent" and set up my own local domain, without success. No idea. Is it just a matter of setting this name in the main.rc config file of postfix?
I use to make a mess with: user name, machine name and domain name. Which would be the right way to send a local email? mailx [email]usr@mail.doma[/email]inname? usr@domainname?
More questions: do all the user have to be registered in the server? I mean as a system users? till now I did't have them.. 


My second mistake: I thought I was needing two postfix (ore more) instalations: I was checking again and again the postfix folder of every computer. Now you make me understand I just need one, in the server. Probably I will have to check in the right folder/usr, but only in one machine. Yes!

Don't know how to pay you for your patiencie...
Many thanks!

PS: it's funny, I've achieved unbelievable things for linux just googling, but I couldn't go further with this issue...

---

### Post by kidders on 2007-04-22
> **jmvidalvia said:**
> Nice information: Now everything starts to be clear for me.Yay! I should stress though, that we'll do whatever _**you**_ want ... not what I want hehe.

> **jmvidalvia said:**
> I have been trying to find out how to "invent" and set up my own local domain, without success.How to do it depends on how many services you would like to make aware of your domain name. For instance, if you would like to start calling your web servers "www.mydomain.tld", or maybe start using a domain name with your DNS, the configuration would be handled differently. If you only want to use it for email, you can configure it in postfix's setup only, and leave it at that.

My approach would be to keep things simple, and create mailboxes called [EMAIL="username@mydomain.tld"]username@mydomain.tld[/EMAIL] (rather than @hostname.mydomain.tld or similar).

> **jmvidalvia said:**
> do all the user have to be registered in the server?No. Again, there are many, many ways of handling mail accounts. The *easiest* solution (but not the only one) is to create system accounts (as you suggested) on the mail server for your users. You can, if you like, create additional email addresses using aliasing ... that way, [EMAIL="jbloggs@mydomain.tld"]jbloggs@mydomain.tld[/EMAIL], [EMAIL="joe.bloggs@mydomain.tld"]joe.bloggs@mydomain.tld[/EMAIL] (sorry... I don't know your name!) and [EMAIL="jmvidalvia@mydomain.tld"]jmvidalvia@mydomain.tld[/EMAIL] could all be valid email addresses that would deliver to your account.

**Edit:** An alternative strategy (called "virtual mailboxes") allows the delivery of mail to user accounts that don't really exist. It's more complicated, but it's essential for large email services.

> **jmvidalvia said:**
> I thought I was needing two postfix (ore more) instalationsYou *can* do things that way if you like. The choice is yours. Your system would become exponentially more complex to configure & administer though, which is why I wouldn't recommend it.

> **jmvidalvia said:**
> Don't know how to pay you for your patiencie...I'm happy to help, so don't worry. :-) Just be sure to give out to me if I post something stupid or hard to understand.

**Edit:**

> **jmvidalvia said:**
> PS: it's funny, I've achieved unbelievable things for linux just googling, but I couldn't go further with this issue...Mail servers are complex creatures, but don't worry ... once you've set up two or three, it will become much easier. When I started working with them, I didn't really understand most of what was going on. :-(

---

### Post by jmvidalvia on 2007-04-23
Hi Steve,
Remember me? :) 

I decided to go step by step. Ok, I created a new system user in my server. I forget about aliases for the moment. I used my own domain within Postfix. So now when I do:

```
jmp@server:$mailx jms@casa
```

Then jms user gets an email file in server:/home/jms/Maildir/new
Same viceversa, so that seems to work
I can check that mail with mutt, for example.

**1st conclusion** (and last, by now): mail works within the same computer.

Now back to your comments. When you say:

> I - Postfix
You could invent a local mail domain that provides accounts for all local users. Each user would have a single mailbox, stored on the Postfix server box. Importantly, nobody in the "real" world would be aware this mail domain exists.

Your Postfix server could receive two kinds of emails:

    * Local -> Local: These mails would be delivered normally. Postfix would drop them in the correct local mailbox.

**1st question:** Does **Local** mean same computer or same network?(I mean, 192.168.1.0/24)

**2nd question:** If local means network, How should I send an e-mail from another computer (no my server) to a user (say, *jms* again). I supose in that case the message from any other pc should arrive to postfix and the Maildir folder in server.

**3rd and last question:** How would you read your mail strored in the local server from another computer in the network.?

Many thanks again and again!

jm


PS: I add a part of my /etc/postfix/main.cf in case it can help:

```
myhostname = server.casa
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
#myorigin = /etc/mailname
myorigin = $mydomain
mydestination = server, casa, localhost, server.casa
relayhost =
mynetworks = 127.0.0.0/8, 192.168.1.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
```

---

### Post by kidders on 2007-04-23
Hmmm... let's see what you've got...

> **jmvidalvia said:**
> Does **Local** mean same computer or same network?In that context, I meant "local" in domain terms.

> **jmvidalvia said:**
> If local means network, How should I send an e-mail from another computer?Again, the "usual" approach is to create a system that works the same way as any other mail service provider. You would configure your mail client to send outgoing mail to your SMTP server.

> **jmvidalvia said:**
> How would you read your mail strored in the local server from another computer in the network?Same story. You would configure your mail client to read mail from your IMAP server.

> **jmvidalvia said:**
> inet_interfaces = allThis has the potential to be highly dangerous. Make sure your Postfix isn't listening on any externally accessible network interfaces!

---

