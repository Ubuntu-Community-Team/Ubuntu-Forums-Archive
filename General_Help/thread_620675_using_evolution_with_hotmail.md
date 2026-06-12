---
title: "using evolution with hotmail"
date: 2007-11-22
forum: General Help
---

### Post by unisol on 2007-11-22
i tried the how tos for using evolution with hotmail to no avail. i have a hotmail account with msn but cannot access it using evolution. i had the account for years and it used to work by installing inetutils-inetd and hotwayd, and configuring the inetd.conf, but not with gutsy. i can access it using firefox, but not evolution. anyone help?
do you have to do something different when using live.hotmail on msn. or is thunderbird and web extensions the only answer?

---

### Post by Flare183 on 2007-11-23
Here is my How to:
---------------------------------------------------------------------

 HOWTO: Send and Receive Hotmail through Evolution
Okay everyone, after digging around in these forums and googling like I've never googled before, I figured out how to send and receive e-mail through hotmail using Evolution. I'm throwing together a rough HOWTO for others. If things need more clarification, let me know and I'll update it.

First, make sure your system is up to date. Open up a terminal and type:

Code:

sudo apt-get update

Now, install the inet daemon

Code:

sudo apt-get install inetutils-inetd

This takes care of all of our dependencies. Now on to the good stuff...

Code:

sudo apt-get install hotway hotsmtp

This will install hotway, which allows you to read hotmail e-mails by simulating a POP3 server, and hotsmtpd, which allows you to send e-mail through hotmail using SMTP. By default, however, only hotway gets installed properly to your inet daemon, so let's fix this.

Code:

sudo gedit /etc/inetd.conf

Look for a line like this:

Code:

pop3        stream    tcp    nowait    nobody    /usr/sbin/tcpd /usr/bin/hotwayd

By default, hotway leaves a copy of each message it downloads on the server. I prefer it this way, so I can read my e-mail at other locations, but if you don't feel like filling up your hotmail box, change the line to add "-r" to the end, like this:

Code:

pop3        stream    tcp    nowait    nobody    /usr/sbin/tcpd /usr/bin/hotwayd -r

And we also need to add a line to get hotsmtpd working, just paste this at the bottom:

Code:

2500        stream    tcp    nowait    nobody    /usr/sbin/tcpd /usr/bin/hotsmtpd

This will set the inet daemon to listen to incoming calls on port 2500, and forward the connection to the hotsmtp daemon. Now, save your file, exit gedit, and restart your inetd server:

Code:

sudo /etc/init.d/inetutils-inetd restart

If everything is working properly, you'll see this pop up on your screen:

Code:

* Restarting internet superserver inetd                            [ ok ]

Now, close out of your terminal and start up Evolution. It may pop up the first-time use wizard, you can use that if you like. Or, you may have to go to Edit->Preferences and hit the Mail Accounts button on the left. However you choose to do it, here's your information:

Email Address: [email]xxx@hotmail.com[/email] (fill in your normal e-mail address that you use to login to hotmail)

Receive Server type: POP
Server: 127.0.0.1
Username: [email]xxx@hotmail.com[/email] (same as above)
Security: No encryption
Authentication type: Password
(Remember password checkbox is up to you)

Send Server type: SMTP
Server: 127.0.0.1:2500
[X] Server requires authentication (check this box)
Use Secure Connection: No encryption
Authentication Type: PLAIN
Username: [email]xxx@hotmail.com[/email] (same as above)
(Optional Remember password checkbox)

---

### Post by unisol on 2007-11-24
it asks for a password for the server, then refuses to connect. it asks me to log in as user first. i dont nunderstand it worked with pevious versions of ubuntu.

---

### Post by tettayes on 2007-11-24
maybe use webmail retriever for hotmail on wine, then use that information to locate the server information??
using localhost at certail ports can manage getting emails from hotmail i think, however, i have not tried it yet, i am not sure if it is going to work well.
hope it helped, give it a try!

---

### Post by Znort_Ubern00b on 2008-02-27
Having similar problem to this but i get this error message...

Error sending password: -ERR **Hotmail said you must pay money to have WebDAV access**

so looks like it ain't gonna work...what a bunch of cnuts.

---

### Post by ibgeorgeb on 2008-03-02
> **Flare183 said:**
> Here is my How to:
sudo apt-get install hotway hotsmtp


After this step I got "E: Can't find hotway." So ended my excitement for the day of getting Hotmail to work with Evolution. I am using 6.06.

We tried. Thank you.

---

### Post by Oldsoldier2003 on 2008-03-02
> **ibgeorgeb said:**
> After this step I got "E: Can't find hotway." So ended my excitement for the day of getting Hotmail to work with Evolution. I am using 6.06.

We tried. Thank you.
gmail works with evolution...

---

### Post by erginemr on 2008-03-03
Both "hotway" and "hotsmtp" packages exist for Dapper Drake:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=gutsy&release=all&keywords=hotway&sourceid=mozilla-search](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=gutsy&release=all&keywords=hotway&sourceid=mozilla-search)
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=gutsy&release=all&keywords=hotsmtp&sourceid=mozilla-search](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=gutsy&release=all&keywords=hotsmtp&sourceid=mozilla-search)
but they are in the "universe" section of the repositories.

You just should go into "Main Menu -> System -> Administration -> Software Sources" and enable all repositories therein. 

Then, update your software database with:
```
sudo apt-get update
```

Then you are good to go!

---

### Post by bew1979 on 2008-03-03
I have followed the steps listed above and have succesfully got hotmail with evolution but everytime I close evolution and then reopen it i need to restart the inetutils-inetd line from above to be able to then receive my emails, is there any thing I can do to fix this.

---

