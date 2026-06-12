---
title: "Mail Client Connecting to MS Exchange Server"
date: 2008-06-03
forum: General Help
---

### Post by tshrinivasan on 2008-06-03
Hi,

We decided to Migrate from MS Office to OpenOffice in our organization. we have around 3000 users.

All are using MS Outlook as their default mail client. They have the centralised addressbook and calendering in the Exchange itself.

The Mail server is in the hands of IT Department. So we can not urge them to migrate to Any other mail server.

Is there any open source mail client connecting to MS exchange server to get the centralised addressbook and calenders, etc?

If so, we can easily move all of them to Linux.

Thanks for your suggestions.

T.Shrinivasan.
[http://goinggnu.wordpress.com](http://goinggnu.wordpress.com)

---

### Post by ilrudie on 2008-06-03
I use evolution with the exchange setup script to connect to my company's exchange servers.  It's really not 100% reliable and once or twice a day it will lose the connection and I have to restart it but its pretty good.  You must have Outlook Web Access running though.  Evolution can't talk directly to exchange.  Let me know if you want more information on how I configured Evolution.

---

### Post by the_maassk on 2008-06-03
I use Evolution to access my mail from Exchange. It does however behave funny at times and I do not get my Inbox view updated with all the mails that should be there. Maybe because I access my mails in a multitude of ways (Outlook, Evolution and OWA).

---

### Post by ellgor on 2008-06-03
Hi,

Take a look at Kmail and its accompanying package Kontact, its got more features than Evo and its more stable, probably easier to use as well, hope this is of help.

Regards, Ellgor.

---

### Post by tshrinivasan on 2008-06-04
Hi ilrudie,

Please guide me more on this.
We have OWA and on connecting to OWA, it shows the error that "I can connect only with 2003 and above". But we have 2007 server.

Any help, please.

Thanks for all folks for help.

---

### Post by ilrudie on 2008-06-04
> **tshrinivasan said:**
> Hi ilrudie,

Please guide me more on this.
We have OWA and on connecting to OWA, it shows the error that "I can connect only with 2003 and above". But we have 2007 server.

Any help, please.

Thanks for all folks for help.

tshrinivasan,

I do not recall exactly what I did to get this working so I apologize but here are the highlights that I can recall:

I successfully configured evolution with OWA by running:
/usr/bin/exchange-connector-setup-2.22
I don't recall if I had to sudo it to succeed or not.  Try it without first.  It brings up a GUI which is fairly easy to understand.  There were a few hangups configuring it my first time through but much of that was me just not understanding the how OWA works.  I will try to recall some of the hangups I encountered.  If you need more help I will build a test box at work and configure OWA access again to jog my memory.

1)  The OWA url was [https://OWASERVERNAME/USERNAME](https://OWASERVERNAME/USERNAME)
the s in https was very important and it got hungup if you didnt have it.
The best way to get this is to sign on the the OWA server from firefox and get the URL of the default page that loads.  I believe just copying that over was all I did there.
2)  Unless there is a seperate domain field I beleive I was required to enter my username like 'DOMAIN\USERNAME' in the username field.
3)  When I had the option to "test" my settings testing would return that everything was ok but the button to go forward in the setup process was greyed out now.  I just noted every what every setting was and went back a screen.  I then went forward again and proceeded to make all the changes over again and proceed without testing this time (annoying!)
4)  For some reason the GUI defaults to plain text password.  I changed this to the other option which was something to the effect of "secure password".
5)  I just played around with the settings changing one thing at a time until I tweaked it and got it to work.  If you get through that first GUI and into Evolution you are like 99% there.  I believe there was one extra setting to tweak after making it through the script to achieve nice integration.

I hope that helps.  If you want more information just let me know and as I mentioned I will build and configure a test box and take careful notes of everything I change so you can follow along more easily.  Just keep trying and make 1 change at a time so don't get 1 part right and break another at the same time.  It took a little effort up front on my part but it has been well worth it for me.

Good luck!

**NOTE:  Hardy is what I am using for this.  I got it working under Gutsy but a bug which has been fixed in Hardy prevented my sent mail from going into the sent mail folder in exchange.  Instead an error box popped up every time I sent a message saying the email was placed in my local sent folder.  The message got sent but the error was annoying me so I was happy to see this resolved under Hardy!**

---

