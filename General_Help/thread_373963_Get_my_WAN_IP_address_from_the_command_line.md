---
title: "Get my WAN IP address from the command line?"
date: 2007-03-01
forum: General Help
---

### Post by Flecko on 2007-03-01
Hello all,

Ok, first a little background. I am running a computer network on a router at home. I have 3 or so computers on it. In front of the router is my dsl modem. I run an SSH server on one of the computers and like to access it during the day from work, but here is where the problem comes in. My IP address gets renewed randomly throughout the day, so at work, I will occasionally just lose my connection because the IP address I wrote down from the morning doesn't work anymore.

So I had an idea. I could make a cron job on my SSH server that would grep the output of ifconfig to get my ip, and then use sendmail to email that to myself at work. All great in theory, but the IP that ifconfig returns is, of course, my LAN IP and not my WAN IP. 

So, my question to everyone is, is there a nice way to get my WAN IP from the command line so I can use sendmail to get it to myself at work? I've tried traceroute(it skips my WAN address) and a few other tricky ideas with no luck.

Any takers? I'd really appreciate the help.
Thanks everyone,
-Flecko

---

### Post by AlcoJaguar on 2007-03-01
You could download the [www.whatismyip.com](www.whatismyip.com) page with wget in a script, then open the file (which will download as index.html) and use regex to pull out the line "Your IP is *.*.*.*". You could then just take slice off the first 11 characters and use the resulting string as your WAN IP address.

Let me know if that helped or if you need me to clarify.

Ed.
Or better yet you could register a free personal domain name at [www.no-ip.org](www.no-ip.org) and set up the dynamic DNS updater on your system at home to update your domain name record on their name server whenever your WAN IP changes. Dynamic DNS works great for constantly changing ip addresses (That's why it's dynamic :)).

---

### Post by Flecko on 2007-03-01
Thanks for the quick reply.

I found a website that makes it somewhat easier: [http://checkip.dyndns.org/](http://checkip.dyndns.org/)
It'll give you a simple static index.html with minimal formatting...which should theoretically make extracting the IP easier. The trick is, I'm extremely rusty with grep and awk...and I'm having trouble finding a webpage that has an easy guide. 

Any pointers?
Thanks again,
-Flecko

EDIT: I'm getting closer. Doing this: wget [http://checkip.dyndns.org/](http://checkip.dyndns.org/) && awk '/:/ {print $6}' index.html
Gets me this: 71.166.99.103</body></html>

Any additional ideas?

---

### Post by Nikron on 2007-03-01
Or you can register at dyndns.org, use the free dynamic dns service, and have a x.dyndns.org domain name that points to your WAN IP.  I know there's a script out there that you can run as a cronjob to auto update your account on dyndns when you WAN IP changes...

---

### Post by Flecko on 2007-03-01
I figured it out.

Thanks guys,
-Flecko

---

### Post by Aikon- on 2007-11-14
> **Flecko said:**
> I figured it out.

Thanks guys,
-Flecko

It would be nice if you could include your solution(s) when you figure something out; this will help other users that find themselves in similar situations.

-Aikon

---

### Post by jpspyro on 2007-12-06
Hey, i always wanted to be able to get my ip address from anywhere. 
I wrote a perl script that will grab the ip address on the computer that it is ran from and send via SMS to your phone (if supported via sendSMS-v0.2.4.pl).

```

#!/usr/bin/perl

@fileContents;
$fileCrop;
$IP;
$SMSargs;

getIndexHTML();
parseFile();
cropFile();
sendSMS();

print $IP;

sub getIndexHTML {
	system 'rm index.html';
	system 'wget -q http://checkip.dyndns.org/';}

sub parseFile {
	open(FILE, "index.html");
	@fileContents = <FILE>;
	close(FILE); 
        system 'rm index.html'; }

sub cropFile {
	$fileCrop = substr($fileContents[0],76);
	$IP = substr($fileCrop,0,-16); }

sub sendSMS {
	$SMSargs = "perl sendSMS-v0.2.4.pl -r 1112223333 -p CINGULAR -s IPsender -m ".$IP;
	system $SMSargs; }

```

replace 1112223333 with your cell number and change CINGULAR to whatever provider you use:

```
 
      ALLTEL - Alltel Wireless             ATTWS - AT&T Wireless
      BELLCA - Bell Canada                 CINGULAR - Cingular
      CELLONE - Cellular One               CRICKET - Cricket [deprecated]
      SKYTEL - SkyTel                      SPRINT - Sprint PCS
      TMOBILE - T-Mobile    

```


this script requires sendSMS  ([http://caspian.dotconf.net/menu/Software/SendSMS/]("http://caspian.dotconf.net/menu/Software/SendSMS/"))
 
you could also change the script to use sendEmail to your email address. ([http://caspian.dotconf.net/menu/Software/SendEmail/]("http://caspian.dotconf.net/menu/Software/SendEmail/") ) 

I'm just finished writing this for now, next i will create a way to invoke this script via a webpage or even by sending and email to the host computer.

EDIT: I'm currently working on a way to dial-in to your computer and enter a series of numbers(password) to execute this script. So you would just be able to dial your home number and have your IP address sent to your cell.

---

