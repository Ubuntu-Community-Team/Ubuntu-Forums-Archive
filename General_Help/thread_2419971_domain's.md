---
title: "domain's"
date: 2019-05-28
forum: General Help
---

### Post by oneleded on 2019-05-28
probably not the right place to ask questions,... just looking for a lead.. i got old e-mail problems, very old. i think a domain. will fix them. att.net, and one, bellsouth.net, just aint working anymore. it was a long time, i had them. near 2000.. i can make new accounts,.. i just want to retrieve the old, mail. maybe not much more than this year.

---

### Post by TheFu on 2019-05-28
Gonna need a lot more information.  
Where is the email stored?
What programs did you use to access it last?
Do you have backups?

---

### Post by oneleded on 2019-05-28
i wasnt very specific in my last post. sorry for that.. [email]myname@att.net[/email], quit working, about 2 months ago. i got 3 accounts. att updated their mail. now you need a secure key, mainly from OAth.. you can make your own.  if only att recognizes you account. i'm kinda tired of them[att], and am thinking i will get a domain. that's what i'm looking for. a domain that dont cost too much.
i will probably find some yahoo on the phone that knows what is going on, eventually.  the att mail is most likely, an att mess. sometime's i'll get a message, the server is not responding, try again later. other times my mail name is not recognized, nor the password. i only receive mail on one account. i cant send on any account's.
tis a mess. i use thunderbird, but have tried signing in with a browser to no avail.
i still got my mail from 2 months ago, an so, plus what i am still receiving in the 3rd account.

---

### Post by TheFu on 2019-05-29
> **TheFu said:**
> Gonna need a lot more information.  
Where is the email stored?
What programs did you use to access it last?
Do you have backups?

1 answer out of 3 provided.
If thunderbird has a local copy, then it should be local and viewable. That would normally be the situation with any POP3 or POP3S account like most ISPs used to provide. A long time ago, BLS handed over their email to yahoo! Once that happened, I haven't any clue what happened to the email - if it was moved over or legacy mailboxes were retained somewhere. This is about the storage, not the email address.

So you need to determine where the email is stored. There are only a few places, but if you cannot login, it will be hard to get to it. Right?  I foresee a long time on hold dealing with AT&T CSRs. If the mail is on their servers, I know they use very standard protocols, so you'll need to find the email setup page for your location (Ky?) and use those instructions to configure thunderbird.  

There are 2 parts to email.
a) receiving it - on a client that will be either POP3S or IMAPS
b) sending it - on a client that will be SMTPS

POP3S is on port 995/tcp
IMAPS is on port 993/tcp
SMTPS is on one of these ports for authenticated clients 465/tcp, 587/tcp

Those are the standard settings.
[https://www.thunderbirdsupport.com/att-email-settings-with-thunderbird/?sa=X&ved=2ahUKEwij48X57MDiAhVwUN8KHeX-D2EQ9QEwAHoECAsQAg](https://www.thunderbirdsupport.com/att-email-settings-with-thunderbird/?sa=X&ved=2ahUKEwij48X57MDiAhVwUN8KHeX-D2EQ9QEwAHoECAsQAg) has pictures and the server names, if you need them.
[https://forums.att.com/t5/AT-T-Fiber-Account/thunderbird-setup/td-p/5535817](https://forums.att.com/t5/AT-T-Fiber-Account/thunderbird-setup/td-p/5535817) has the settings again.

If you want all email downloaded from AT&T servers, use pop3 or pop3s.  If you want see it from multiple devices, then you probably want to leave it on their servers and use IMAPS.  If you use POP3 and have a storage problem/failed disk at home, then the email is gone, gone, gone.  You'll need to make backups for anything you don't want to loose.  I always figure that Linux users know to make backups. We're smarter than the other people.

---

### Post by oneleded on 2019-05-31
thank's, and i have experience not being able to talk to att since they got bellsouth. this is a while back. i think you are spot on about getting local numbers. this is some about a server connection not working, and trying to conform, to the new standard's, att has, once you get new the secure mail key. course if the server dont recognize your name, or, an account, or it says, try server later. something is going on. in my case, maybe trying to get rid of riffraff, for lack or a better term.
 i want to get a domain, so i can have my own mail box. i just want to get what mail that was sent, since january, 2019..
i run a bit slugish, since 2016, when i went linux. that is just a thing of mine,,.. i got to deal with this.. 
i got all my passwords, plus names, been doing this for a long while on att.net.. ..
as far as domain's, is there a thread that explains it some here? 
i have had free att mail, for a long while. close 15 year's, give or take two yr's. surprised they didnt get rid of me 5 years ago. 
 what is BLS?, or CSR's..
 i forgot to mention, i think they are trying to cut out thunderbird. just a strong impression i get. i may not be correct.

---

### Post by TheFu on 2019-05-31
BLS = BellSouth
CSR = Customer Service Representative

AT&T and BellSouth systems are based on standard protocols. While they might not have CSRs trained to help with Thunderbird, the ports and protocols are all you need. 

Running your own email server is non-trivial and 100x more complex than setting up thunderbird. You cannot send/receive email on a residential connection except with authenticated connections. For someone completely new to this stuff, who isn't really good at networking, will need to run the email server on a commercial network connection or use a VPS.

Sorry, I don't know of any guides with steps, but I haven't looked.  I setup a new email every few years, but it fits into my networks with other systems there. Very non-standard. Last time was a few months ago, but it wasn't just email, it was a communications server with calendaring, contacts, document storage, x.509 certificate support, etc.  BTW, that server isn't directly available to the internet. There is a gateway email system for all inbound and outbound SMTP traffic. So, I really don't know how to setup a trivial little, email box. Sorry.

---

### Post by dragonfly41 on 2019-05-31
Some time ago I migrated my few email accounts from a registry company over to [google domains.]("https://domains.google/") It is quite easy to use and you can point to various hosted sites. Either in google or heroku or digitalocean as just some examples. Other tyres to kick include [dyndns]("https://dyn.com/dns/") and [zoneedit]("https://www.zoneedit.com/")

---

### Post by oneleded on 2019-06-13
> **dragonfly41 said:**
> Some time ago I migrated my few email accounts from a registry company over to [google domains.]("https://domains.google/") It is quite easy to use and you can point to various hosted sites. Either in google or heroku or digitalocean as just some examples. Other tyres to kick include [dyndns]("https://dyn.com/dns/") and [zoneedit]("https://www.zoneedit.com/")
that is the direction i am headed in. thanks

---

### Post by oneleded on 2019-06-13
> **TheFu said:**
> BLS = BellSouth
CSR = Customer Service Representative

AT&T and BellSouth systems are based on standard protocols. While they might not have CSRs trained to help with Thunderbird, the ports and protocols are all you need. 

Running your own email server is non-trivial and 100x more complex than setting up thunderbird. You cannot send/receive email on a residential connection except with authenticated connections. For someone completely new to this stuff, who isn't really good at networking, will need to run the email server on a commercial network connection or use a VPS.

Sorry, I don't know of any guides with steps, but I haven't looked.  I setup a new email every few years, but it fits into my networks with other systems there. Very non-standard. Last time was a few months ago, but it wasn't just email, it was a communications server with calendaring, contacts, document storage, x.509 certificate support, etc.  BTW, that server isn't directly available to the internet. There is a gateway email system for all inbound and outbound SMTP traffic. So, I really don't know how to setup a trivial little, email box. Sorry.
    i wasnt very clear in this, cant help it. its a wonder ya can understand what i say at all on occasion. appreciate the help, apologize for the misdirection. ed
    i want my own domain name, xxx@easy, or what ever. then set up email, or what i need. i dont want to spend a lot of money a year. has any body got info on that., or tried it, was what i meant to say

---

### Post by TheFu on 2019-06-13
If you want to run your own domain, you need 3 things, in addition to the knowledge to configure them to all work together.
* a domain - $2-$20/yr
* a dns provider - $20-$40/yr
* an email provider or host - there are VPS accounts for $5/month.

I'm certain the 3rd in the list above could be handled by some service provider, probably for $10/month per account.  Be careful who you choose, if you care about privacy.  Don't expect any privacy from outlook, google, yahoo, or any of the big names we all know.

If you want to run it from home, then you'll need a business internet account with at least 1 static IP that isn't on the spammer blacklists anywhere in the world for $100+/month.  I pay $112/month, but have a larger public subnet.

In the last year, a startup put out a little box for $400 initial , I think, and $???/yearly subscription that does email. It is meant for wealthy, privacy-conscious, families. I think they handle the DNS and registration parts in the price.

Some other self-hosted solutions:
[https://github.com/sovereign/sovereign](https://github.com/sovereign/sovereign)
[https://mailinabox.email/](https://mailinabox.email/) 

Heck, for just email, you could probably get a shared hosting provider like godaddy to handle almost everything with a point-n-click panel web interface for $10/month.  There are many reasons NOT to give that specific provider any of your money.  I still have 1 domain with them as registrar only - all the other stuff is elsewhere.  I've never run email through a hosting provider, so my 1st hand knowledge about that is extremely limited.

I did run email through dyn.org for a year when I didn't have a static IP setup anywhere. Basically it was an email gateway service sitting between my email server and the internet for both in and outbound emails. Think that was $40/yr. Still have to have all the other things in the list.

If you run your own server at home, in a closet or have a VPS, then you are responsible for everything.  Patching, configuration, uptimes, failures, backups, disaster recovery, and 50 other things. EVERYTHING. Many people find all that is too hard and decide to give up on privacy - use google.  As long as you make the choice with your eyes open, fine.  If you just want an email address that isn't likely to be anti-privacy, check out protonmail.

---

### Post by oneleded on 2019-06-16
Thank's. i'm getting to understand, this is not as inexpensive as i thought, and definitely more complicated. [check out protonmail]. << i will check this out. ATT free mail, is getting more complicated, and they have the habit of changing the rules, to shut ya down for a bit, till ya figure them out.. i think they want to get rid of the free part. i dont got much, i'm worried about, far as e-mail go's. i learned dont write what you dont want read, a while back.
dont talk on the wireless phone, if you are saying something personal, stuff like that.  the wireless phone can get ya caught, if ya tell someone, something ya did, an another person's phone get's the message also. im glad i talked em into giving the message to the police. 1 crime solved. i dont think even the home phone is all that safe, anymore. i said more than enough. too much. thanks again

---

### Post by TheFu on 2019-06-16
If you want private communications, there are a number of methods for that.  Email is a postcard. Always has been.  Anyone between the sender and recipiant can read everything, unless encryption is used BEFORE and decryption is used AFTER the email is transmitted.  GPG can do that, but it is more hassle to use than most people are willing to put up with.  Mom and I used GPG to exchange recipes.  A few friends and I did too, but those friends, who also used gmail, found it too cumbersome.  In reality, my friends lack of consideration about privacy vs convenience was the downfall.  They had all sorts of issues and wanted to use a tablet, not a PC.  I have no idea how many "private" subject discussions they leaked out of convenience.  It got to the point where I stopped responding.  

Should anyone have to choose between privacy and friendship?

I cannot say anything about AT&T that isn't public knowledge.  
Cell phones are not secure for 99.9999% of the world. A govt isn't needed to break them.  Most home phones have been converted to VoIP around here, regardless of the provider. They don't get the same legal protections that POTS phones have.  POTS in the USA are legally protected by wiretap laws, but someone with a little knowledge and physical access nearby can listen without much concern.  Law enforcement has infrastructure directly connected to the POTS network for their needs, but a warrant is required.  None of this helps where SS7 design failures are involved, which is basically worldwide.  Redirecting voice traffic halfway around the world can be done and does happen. The good news is that it isn't en masse, just for targets.  

Data traffic, gets redirected all the time. The BGP router protocol allows it and it is necessary.  IP traffic between 2 US locations less than 100 miles apart has been sent through Iceland or Belarus or China.  BGP changes are announced so that anyone can see them, so redirecting traffic isn't hidden when it crosses IP service providers. In the last few weeks, some [traffic inside Europe was accidentally sent to China]("https://arstechnica.com/information-technology/2019/06/bgp-mishap-sends-european-mobile-traffic-through-china-telecom-for-2-hours/"). It was about 2 hrs long.  This sort of screw up happens more than we know, usually it is human error, but sometimes it is clearly for other reasons.

Anyway, don't leave your tin hat on too long.  That just keeps the waves bouncing around inside. ;)

If you want secure communications, first ensure the other people involved feel the same about privacy and security as you do. Without that assurance, don't bother.

---

### Post by oneleded on 2019-06-19
> **TheFu said:**
> If you want private communications, there are a number of methods for that.  Email is a postcard. Always has been.  Anyone between the sender and recipiant can read everything, unless encryption is used BEFORE and decryption is used AFTER the email is transmitted.  GPG can do that, but it is more hassle to use than most people are willing to put up with.  Mom and I used GPG to exchange recipes.  A few friends and I did too, but those friends, who also used gmail, found it too cumbersome.  In reality, my friends lack of consideration about privacy vs convenience was the downfall.  They had all sorts of issues and wanted to use a tablet, not a PC.  I have no idea how many "private" subject discussions they leaked out of convenience.  It got to the point where I stopped responding.  

Should anyone have to choose between privacy and friendship?

I cannot say anything about AT&T that isn't public knowledge.  
Cell phones are not secure for 99.9999% of the world. A govt isn't needed to break them.  Most home phones have been converted to VoIP around here, regardless of the provider. They don't get the same legal protections that POTS phones have.  POTS in the USA are legally protected by wiretap laws, but someone with a little knowledge and physical access nearby can listen without much concern.  Law enforcement has infrastructure directly connected to the POTS network for their needs, but a warrant is required.  None of this helps where SS7 design failures are involved, which is basically worldwide.  Redirecting voice traffic halfway around the world can be done and does happen. The good news is that it isn't en masse, just for targets.  

Data traffic, gets redirected all the time. The BGP router protocol allows it and it is necessary.  IP traffic between 2 US locations less than 100 miles apart has been sent through Iceland or Belarus or China.  BGP changes are announced so that anyone can see them, so redirecting traffic isn't hidden when it crosses IP service providers. In the last few weeks, some [traffic inside Europe was accidentally sent to China]("https://arstechnica.com/information-technology/2019/06/bgp-mishap-sends-european-mobile-traffic-through-china-telecom-for-2-hours/"). It was about 2 hrs long.  This sort of screw up happens more than we know, usually it is human error, but sometimes it is clearly for other reasons.

Anyway, don't leave your tin hat on too long.  That just keeps the waves bouncing around inside. ;)

If you want secure communications, first ensure the other people involved feel the same about privacy and security as you do. Without that assurance, don't bother.
i definitely understand what you are saying. i wanted to get away from att. because they keep changing the rules, an on occasion, they block me out, till i jump through a bunch or hoop's, to get back. my hat's copper by the way LOLS.. i gave up the tin foil...
you explained this well, an then some. i will just get a better e-mail provider, not att. they are on the verge of charging for email, and , i think would like to get rid of those, who have been using att.mail for free.  OK, i'm, prone to conspiracy, theory.. dont say or print, anything, on line, over the airwaves, that you dont want known. i'm beginning to wander about the house phone, or even snail mail, mail with a stamp. could happen. too much,  orsen well's. :~}
ya helped me a lot, an i appreciate it. in my old age, i still have to be careful of what i say, around my siblings. what a mess of sibling's. an i get SS. oh bother

---

