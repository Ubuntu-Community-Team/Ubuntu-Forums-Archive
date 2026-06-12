---
title: "Asterisk on Ubuntu"
date: 2005-10-20
forum: General Help
---

### Post by isaiah55 on 2005-10-20
I am a newbie to Asterisk and only beed using Ubuntu for about 6 months, so pretty green here as well...

What I would like to do is set up Asterisk on my Ubuntu box.  Ths install I can do, but it is the setup and configuration of Asterisk I'm a bit lost on.
Does anyone have any good tips or configuration info?
Or even better the Holy Grail - A step by step guide for setting up Asterisk on Ubuntu.

Cheers

Paul

P.S. Thanks in advance :p

---

### Post by Daveo on 2005-12-05
Asterisk is a great PBX, but for someone (I'm only assuming so please forgive me) who may be new to linux or new to asterisk it's probably better to give this a go first. 

[http://asteriskathome.sourceforge.net/](http://asteriskathome.sourceforge.net/)

Now, it runs on CENTos and not ubuntu, however having said that, you can build the server you need using the web interface and then backup the config and port it over to ubuntu. 

I would LOVE for a ubuntu version of asterisk@home, if anyone feels like a project, there's your place to start. :-)

But seriously, if you want to give asterisk a go on ubuntu, try [www.asterisk.org](www.asterisk.org) for some documentation or the IRC channel #asterisk on irc.freenode.org. 

Good Luck!

:p

---

### Post by isaiah55 on 2005-12-05
Daveo,

Thanks heaps your your reply.  Asterisk@Home looks excellent, it is a bummer though that it isn't available on Ubuntu...

I think it would also be great if someone, with much better knowledge than myself, was able to port it across. 

I am still hoping someone out there has a good generic configuration file for Asterisk or am I just showing my ignorance on the subject?

Cheers

Isaiah55

---

### Post by n8zuz on 2005-12-05
Actually, what we need is AMP (Asterisk Management Portal) to be put in a .deb package for Ubuntu as AMP is what we are missing that *@H has.

I looked into AMP but I too am too new to tackle this one.  I'm too spoiled with synaptic's package manager.

Jeff

---

### Post by isaiah55 on 2005-12-05
Hi N8zuz,

Thanks for the heads up.  It gave me something to Google :) 
I found ACTOS, which seems work with Debian.  Would this do the trick? - [http://www.voip-info.org/wiki/view/ACTOS]("http://www.voip-info.org/wiki/view/ACTOS")

Cheers

Isaiah55

---

### Post by Xceptiona1 on 2005-12-22
I just heard about Asterisk and would like to install it at my house. I too am looking for an Ubuntu guide / package to do so. I already have an ubuntu server and would like to keep it that way if possible.

EDIT* I found this post and will attempt it tonight.
[http://ubuntuforums.org/showthread.php?t=22462&](http://ubuntuforums.org/showthread.php?t=22462&)

---

### Post by brickbat on 2006-01-02
I installed asterisk at home.  It was really easy.  It took me about an hour.

Got it to do quite a bit really quickly but internal and external routing is like passing kidney stones.

ciao
bb

---

### Post by daller on 2006-02-11
Asterisk is only text-based?

...I've read that it should be better than Skype!

Anyone knows about a real skype alternative? (Non-geeky!)

---

### Post by isaiah55 on 2006-02-11
[SIZE="1"][INDENT]Asterisk is only text-based?

...I've read that it should be better than Skype!

Anyone knows about a real skype alternative? (Non-geeky!)[/INDENT][/SIZE]

Wow comparing Skype to Asterix is like comparing a fully blown telecommunications system to your home phone...
They are not even in the same ball park...

VOIP clients in my opinion are a dime a dozen.  It really depends what you want to use it for.  Do you want to make calls to landlines or just computer to computer?  Does it need to be web enabled etc etc.  And then there is the question of the VOIP provider. OK let me start from scratch...
Skype provides not only a software client but also the VOIP service hence it is easy to install and configure.  However you can happily separate the 2.  For example use a software client like Eyebeam or X-Ten Lite and have your SIP or IAX for example service provided through a VIOP provider like [www.oztralia.com.au]("http://www.oztralia.com.au").
(Asterix on the other hand basically looks after how the call is handled when you recieve it or make it - Quite a few VOIP providers use Asterix to operate their service...)

So when you are asking does anyone know a real alternative to Skype we would need to know more information about what you want to use it for etc.
Skype is the easiest to setup on linux that I know of but definitely not the best for quality and CPU usage...

Cheers

Isaiah55

---

### Post by VancouverTT on 2006-02-12
I think eyeBeam is a top-quality SIP client.  In fact, I think eyeBeam makes a better candidate for Ubuntu love than the proprietary Skype tie-in-lock-in.

Here's a good step-by-step instruction on how to configure CounterPath's older X-Lite softphone to work with Asterisk:

[http://www.voip-info.org/wiki-Asterisk+phone+xten+xlite](http://www.voip-info.org/wiki-Asterisk+phone+xten+xlite)

I think you can still download the Linux X-Lite client for free.

---

### Post by mayowa on 2006-02-24
Guys pls i need ur help. I installed ubuntu however, i am having problems running the asterisk after installing using the respositories. When i type /usr/sbin/asterisk -vvvvr it says unable to connect to remote asterisk.  I have no idea where to start or what i did wrong.  

Must asterisk only be installed on a server, i think the ubuntu was not installed as a server. if that is the problem i am reinstalling now on another hard dsik. i however, would like to resolve this which config file am i too change if asterisk can work on a client ubuntu system.

I am already used to asterisk commands form my voip course in school but i never installed one on ubutu b4.

---

### Post by mayowa on 2006-02-24
Guys pls i need ur help. I installed ubuntu however, i am having problems running the asterisk after installing using the respositories. When i type /usr/sbin/asterisk -vvvvr it says unable to connect to remote asterisk. I have no idea where to start or what i did wrong. 

Must asterisk only be installed on a server, i think the ubuntu was not installed as a server. if that is the problem i am reinstalling now on another hard dsik. i however, would like to resolve this which config file am i too change if asterisk can work on a client ubuntu system.

I am already used to asterisk commands form my voip course in school but i never installed one on ubutu b4.

---

### Post by mayowa on 2006-02-24
Hi guys ran more test on my ubuntu. I tried the  asterisk -c command and was giving the following 

Asterisk , Copyright (C) 1999-2004 Digium.
Written by Mark Spencer <markster@digium.com>
=========================================================================
[ Booting.......Feb 24 19:01:23 WARNING[12422]: res_musiconhold.c:205 spawn_mp3: Found no files in '/usr/share/asterisk/mohmp3'
Feb 24 19:01:23 WARNING[12422]: res_musiconhold.c:278 monmp3thread: unable to spawn mp3player
......Feb 24 19:01:23 NOTICE[12422]: res_odbc.c:133 load_odbc_config: registered database handle 'mysql1' dsn->[MySQL-asterisk]
Feb 24 19:01:23 NOTICE[12422]: res_odbc.c:133 load_odbc_config: registered database handle 'mysql2' dsn->[MySQL-asterisk]
Feb 24 19:01:23 NOTICE[12422]: res_odbc.c:415 load_module: res_odbc loaded.
.Feb 24 19:01:23 NOTICE[12422]: config.c:888 ast_config_register: Registered Config Engine odbc
Feb 24 19:01:23 NOTICE[12422]: res_config_odbc.c:190 load_module: res_config_odbc loaded.
.........Feb 24 19:01:24 WARNING[12422]: chan_skinny.c:2587 reload_config: Unable to get our IP address, Skinny disabled
.........................................................................................Feb 24 19:01:27 NOTICE[12422]: chan_capi.c:2635 load_module: CAPI not installed!
Feb 24 19:01:27 WARNING[12422]: loader.c:345 ast_load_resource: chan_capi.so: load_module failed, returning -1
Feb 24 19:01:27 WARNING[12422]: chan_capi.c:2811 unload_module: Unable to unregister from CAPI!
Feb 24 19:01:27 WARNING[12422]: loader.c:440 load_modules: Loading module chan_capi.so failed!


Pls help out i attached the script file generated from asterisk -vvvvvc command for those intrested.

mayowa:-k

---

### Post by kennedymat on 2006-03-02
Try typing "asterisk -cv" instead. The -c tells you it to start the console, and the -v tells it to print some diagnostic output as well. 

You have been using the "-r", which tells it to connect to an asterisk that is already running in the background.  I don't think that is what you are trying to do.

I can say that I got Asterisk running right out of the gate by installing Ubuntu 5.10, then getting the Asterisk package, then going to the console and typing:

sudo asterisk -cv

I was able to configure two SIP phones and they registered properly.  I even completed a call between them!

That's where the fun ended.  I'm having some Asterisk specific problems, now.

---

### Post by kennedymat on 2006-03-02
I can help you with the warning about the mp3 player and files.  The package comes with no mp3 files in the music on hold folder.  Just copy any mp3 file into that folder and the warnings will go away.

---

### Post by kennedymat on 2006-03-02
Deleted

---

### Post by mayowa on 2006-04-14
thanks a lot i got over this by buying a book on asterisk and using asterisk at home. Apparently u are right i was trying to connect to an asterisk already working in the background or on another server. (actually i worked remotely  with an asterisk PBX on my school network but never installed it my self before). Yup u are right about  the mp3 too. 

What problems are u having i can simulate it on my working system or debug it using grep. Thanks so much for the reply

---

### Post by Cavaco on 2006-04-20
Hi ,

I found it quite easy to install Asterisk on Urbantu (that is a relative statement) If you look at the Voip Wiki and follow the steps for Debian you should be ok. There are a couple of packages you will need to get hold of ... can't remember which ones , but you'll figure it out as you go along.

So (1) download the latest Asterisk tar 
(2) unzip / untar
(3) Have a look here [http://www.voip-info.org/wiki-Asterisk+Linux+Debian](http://www.voip-info.org/wiki-Asterisk+Linux+Debian)

Hope this helps !

---

### Post by isaiah55 on 2006-04-20
Thanks Cavaco that is excellent.  I am sure it will be of help.  If I get a chance soon I will do the install and hopefully post some step by step instructions...
Installing Asterisk is one thing - configuring it is a completely different kettle of fish, and it is the configuration that I would love some help with.  Does any one have any suggestions to make life easier?

Cheers

---

### Post by brickbat on 2006-07-29
Asterisk at home is the best thing to start off with...unless you really really need it in Ubuntu.

---

### Post by deepscan on 2006-09-28
> **isaiah55 said:**
> Installing Asterisk is one thing - configuring it is a completely different kettle of fish, and it is the configuration that I would love some help with.  Does any one have any suggestions to make life easier?
Cheers

Try [The Dumb-Me guide]("http://members.optusnet.com.au/~bsharif/asterisk/AsteriskForDumbMe.htm"), it helped me a lot.

---

