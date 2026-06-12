---
title: "tor on VMware Player virtual ubuntu -- soundly private?"
date: 2006-10-25
forum: General Help
---

### Post by whoitwas on 2006-10-25
Hi,

I want to blog anonymously, so I am trying to set up tor on a virtual ubuntu 6.06 running under VMware. I had tried JanusVM, but I was surprised that the virtual machine actually worked to anonymize net traffic on the applications running on the host OS. As soon as I visited one of my regular websites with Firefox, the website knew who I was! Doh! Cookies?

So now, to eliminate all sources of potential "historical" info, I have installed VMware Player on Windows, and then "installed" a virtual Ubuntu 6.06 "within" VMware. Then I installed tor (theonionrouter) as recommended below (slightly edited essence) at corvillus [http://tinyurl.com/ykqe2y](http://tinyurl.com/ykqe2y)
> 
	/etc/apt/sources.list
	Add the following line to the end:
	# Tor
	deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) dapper main
	deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) dapper main

	In terminal, execute the following commands:
	sudo apt-get update
	sudo apt-get install tor privoxy tsocks
	Configure Privoxy to use Tor

	/etc/privoxy/config
	Add the following line to the top:
	forward-socks4a / localhost:9050 .

	If using Privoxy for privacy, disable logging.
	Comment out the following lines with a # before them:
	logfile logfile
	jarfile jarfile

	Configure Tor’s ports to use HTTP/HTTPS
	Add the following lines to /etc/tor/torrc:
	ReachableDirAddresses *:80
	ReachableORAddresses *:443

	Configure tsocks:
	Edit /etc/tsocks.conf and edit the
	server lines at the bottom to look like this

	server = 127.0.0.1
	server_type = 4
	server_port = 9050

	From now, use tsocks to start applications
	tunneled like so:
	tsocks <command>
	   (tsocks firefox %u in my case)

	You can also start a tunneled subshell like this:
	tsocks
	~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
	Configuring individual applications for Tor

	HTTP Proxy: localhost:9118
	(this configuration is 	preferred for privacy
	but does not work for all applications).

	SOCKS 4 Proxy: localhost:9050
	(don’t use this if the above works due to
	the potential for DNS request leakage).

	Alternatively, you can use tsocks to start
	applications that don’t support configuration
	(also can suffer from DNS leakage).

I've done this all, except for "Configuring individual applications for Tor",  below the ~~~~~ line. IP tracing websites report me as having various IP's. Still, I am worried that I have not addressed all essential risks, especially in terms of other apps id'ing me (ubuntu updates, gaim, . . .)

Can you please help me to round out my plan? I will try to compile the answers in good form for others to follow if this  makes a good model.

The questions I come up with:
- I can see that my http requests are being anonymized, but how about https? Since this will be used, how can I check it?
- "configuring individual applications" does not need to be done for Firefox, right?
- do I need to turn off any features of this OS or the browser (JAVA, javascript, cookies, . . .)?
- should I install flash or shockwave?

I mostly plan to blog, but I can envision chat and VoIP, image and document creation (gimp and OpenOffice). I do plan to use this OS image only for activities related to this blogging, so I am, not concerned with having a persistent identity following me around; it just must be the identity I create in that particular virtual machine.

Thanks,
whoitwas

[http://tinyurl.com/ykqe2y](http://tinyurl.com/ykqe2y) = 
[http://corvillus.com/2006/09/18/how-to-set-up-tor-and-privoxy-on-ubuntu-linux/](http://corvillus.com/2006/09/18/how-to-set-up-tor-and-privoxy-on-ubuntu-linux/)```

```

---

### Post by Rhubarb on 2006-10-25
The way I anonymously access the web is by using wine with torpark:
[http://www.torrify.com/](http://www.torrify.com/)

The only problem I have is when you start the program, it presents you with a dialogue box that's too small for the buttons to be read.  - Click on the left one (Continue).

---

### Post by whoitwas on 2006-10-25
Wow! Torpark is great! [http://en.wikipedia.org/wiki/Torpark](http://en.wikipedia.org/wiki/Torpark)

It does force you to close down any open Firefox windows, then it opens a branded Firefox with no bookmarks, cookies, passwords, etc. from other firefox installations. It is just firefox for now, but that is all I want at the moment, and I can easily move back and fourth between torpark and VMware/ubuntu/TOR if I need to.

On a somewhat related note,
CAN SOMEONE SEND ME A GMAIL INVITATION, please? Send it to:
   whoitwas (at) hushmail.com
Hushmail is turning out to be too onerous for general use, and I can't pay for a premium account and remain anonymous. I also can't send myself an invitation for gmail and remain anonymous. Thank you.

I still want to complete my VMware Player/ubuntu/TOR setup. It is more flexible than torpark currently, but with torpark, I am more confident in my privacy.

Thanks Rhubarb.
whoitwas

---

### Post by beerfan on 2006-10-25
All of the solutions posted so far sound far more complex than they need to be. If you want to surf anonymously part time, simply install tor and then install the FoxyProxy Firefox plugin which lets you easily switch proxy configurations.

All of the apps above run on both windows and linux so why you need to run from a vmware install is confusing to me but I guess you must have a reason.

[Edit: I should add the Cookiesafe extension for white/blacklisting cookies. If you need to be anonymous on a specific website only partime then I guess you could use a different Firefox profile if you can't remember to clear your cookies.]

---

### Post by whoitwas on 2006-10-26
> **beerfan said:**
> All of the solutions posted so far sound far more complex than they need to be. If you want to surf anonymously part time, simply install tor and then install the FoxyProxy Firefox plugin which lets you easily switch proxy configurations.

All of the apps above run on both windows and linux so why you need to run from a vmware install is confusing to me but I guess you must have a reason.

[Edit: I should add the Cookiesafe extension for white/blacklisting cookies. If you need to be anonymous on a specific website only partime then I guess you could use a different Firefox profile if you can't remember to clear your cookies.]

Thanks for the headsup on this, beerfan. Foxyproxy looks good and convenient, but I'm not confident yet that using the same firefox that I use for other browsing is wise. A different firefox profile would help with this, but if I turn on the tor features of foxyproxy, it would be no quicker than torpark. I don't like seeing all the writes torpark does to my USB drive, OTOH.

I can see that these choices will probably take me to another forum -- one more specifically devoted to tor partnering applications.

Thanks again,
whoitwas

---

### Post by Rhubarb on 2006-10-31
If you can figure out how to setup Tor properly (have all the applications use a localhost Tor proxy), then you should be able to get any program to work fine anonymously on the internet.
The only catch is that most (if not all?) Tor exit nodes ban the smtp port for sending out emails.

---

### Post by Ptero-4 on 2006-12-17
whoitwas. I sent you a gmail invite. Check your mail.

---

