---
title: "Why I cannot login in gtalk by gaim"
date: 2005-10-17
forum: General Help
---

### Post by realwhz on 2005-10-17
Hi,

I have just moved from debian to ubuntu.  But I find the gaim shipped by ubuntu can not login in google talk system.  I configure my account according to the instructions in [http://www.google.com/support/talk/bin/answer.py?answer=24073](http://www.google.com/support/talk/bin/answer.py?answer=24073)
but it does not work at all.  When I login in, after the stage of initializing stream, an error of "Read Error" occurs.  Could you tell me what's with gaim, or is it my fault?

Thank you :-)

---

### Post by ecobuntu on 2005-10-17
did you follow the directions exactly like they asked?  It seems pretty straight forward.  If you did, then maybe you've found a bug.

---

### Post by dspp on 2005-10-18
[QUOTE=realwhz]Hi,

I have just moved from debian to ubuntu.  But I find the gaim shipped by ubuntu can not login in google talk system.  I configure my account according to the instructions in [http://www.google.com/support/talk/bin/answer.py?answer=24073](http://www.google.com/support/talk/bin/answer.py?answer=24073)
but it does not work at all.  When I login in, after the stage of initializing stream, an error of "Read Error" occurs.  Could you tell me what's with gaim, or is it my fault?

Thank you :-)[/QUOTE]

Instructions from Google that work fine with Gaim installed with 5.10.
[http://www.google.com/support/talk/bin/answer.py?answer=24073](http://www.google.com/support/talk/bin/answer.py?answer=24073)

---

### Post by realwhz on 2005-10-18
Hi,

I did configure gaim strictly according to the instructions of the faq of gtalk on the website of google.  In fact, before I turn to ubuntu, I was using gaim to access gtalk all the time.

I also cleaned the package cache and reinstalled the gaim and the required libraries.  Then I deleted the directory .gaim and re-configure gaim again.  But I got a same error result.  By the way, I also can not use other jabber service, such as my account on jabber.org.  Can anyone tell me which library will be used  in authenticating when loginning to jabber server?

By the way, I got some bt info by gdb:

Program received signal SIGABRT, Aborted.
[Switching to Thread -1219414336 (LWP 29328)]
0xffffe410 in __kernel_vsyscall ()
(gdb) bt
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb76569b1 in raise () from /lib/tls/i686/cmov/libc.so.6
#2  0xb76582c9 in abort () from /lib/tls/i686/cmov/libc.so.6
#3  0xb768a6ea in __fsetlocking () from /lib/tls/i686/cmov/libc.so.6
#4  0xb7690f54 in malloc_trim () from /lib/tls/i686/cmov/libc.so.6
#5  0xb76912ca in free () from /lib/tls/i686/cmov/libc.so.6
#6  0xb779c054 in g_free () from /usr/lib/libglib-2.0.so.0
#7  0xb6aa0295 in jabber_register_parse () from /usr/lib/gaim/libjabber.so
#8  0x08072443 in gaim_connection_disconnect ()
#9  0x08072535 in gaim_connection_disconnect_cb ()
#10 0xb7797006 in g_main_context_wakeup () from /usr/lib/libglib-2.0.so.0
#11 0xb77954ee in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#12 0xb77984f6 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#13 0xb77987e3 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#14 0xb7c84e65 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#15 0x080f4827 in main ()


And, the gaim -d produces the following messages:

$ gaim -d
sound: Initializing sound output drivers.
plugins: registering plugin-load signal
plugins: registering plugin-unload signal
plugins: probing /usr/lib/gaim/autorecon.so
plugins: probing /usr/lib/gaim/docklet.so
plugins: probing /usr/lib/gaim/extplacement.so
plugins: probing /usr/lib/gaim/gaim-remote.so
plugins: probing /usr/lib/gaim/gestures.so
plugins: probing /usr/lib/gaim/gevolution.so
plugins: probing /usr/lib/gaim/history.so
plugins: probing /usr/lib/gaim/iconaway.so
plugins: probing /usr/lib/gaim/idle.so
plugins: probing /usr/lib/gaim/libgg.so
plugins: probing /usr/lib/gaim/libirc.so
plugins: probing /usr/lib/gaim/libjabber.so
plugins: probing /usr/lib/gaim/libmsn.so
plugins: probing /usr/lib/gaim/libnapster.so
plugins: probing /usr/lib/gaim/libnovell.so
plugins: probing /usr/lib/gaim/liboscar.so
plugins: probing /usr/lib/gaim/libyahoo.so
plugins: probing /usr/lib/gaim/libzephyr.so
plugins: /usr/lib/gaim/libzephyr.so is unloadable: libzephyr.so.3: cannot open shared object file: No such file or directory
plugins: probing /usr/lib/gaim/notify.so
plugins: probing /usr/lib/gaim/relnot.so
plugins: probing /usr/lib/gaim/spellchk.so
plugins: probing /usr/lib/gaim/ssl-gnutls.so
plugins: probing /usr/lib/gaim/ssl-nss.so
plugins: probing /usr/lib/gaim/ssl.so
plugins: probing /usr/lib/gaim/statenotify.so
plugins: probing /usr/lib/gaim/tcl.so
plugins: probing /usr/lib/gaim/ticker.so
plugins: probing /usr/lib/gaim/timestamp.so
plugins: probing /usr/lib/gaim/nautilus.so
plugins: probing /home/hzwang/.gaim/smileys
plugins: probing /home/hzwang/.gaim/accounts.xml
plugins: registering plugin-load signal
plugins: registering plugin-unload signal
prefs: Reading /home/hzwang/.gaim/prefs.xml
prefs: Reading /etc/gaim/prefs.xml
prefs: Finished reading /etc/gaim/prefs.xml
plugins: Loading saved plugin /usr/lib/gaim/docklet.so
tray icon: plugin loaded
tray icon: created
plugins: Loading saved plugin /usr/lib/gaim/notify.so
pounces: Error reading pounces: Failed to open file '/home/hzwang/.gaim/pounces.xml': No such file or directory
status: Error reading statuses: Failed to open file '/home/hzwang/.gaim/status.xml': No such file or directory
Session Management: ICE initialized.
Session Management: Connecting with no previous ID
Session Management: Handling new ICE connection... done.
Session Management: Connected to manager (GnomeSM) with client ID 103420368b000112963637200000078130089
Session Management: Using gaim as command
Session Management: Received first save_yourself
Session Management: Received save_complete
tray icon: embedded
accounts: Writing accounts to disk.
account: Connecting to account 0x81ea2e8. gc = 0x837ed78
connection: Connecting. gc = 0x837ed78
connection: Calling serv_login
server: gaim 1.5.0 logging in [email]xxxxxx@gmail.com[/email]/Gaim using Jabber
dns: Created new DNS child 29983, there are now 1 children.
dns: Host 'talk.google.com' resolved
proxy: Connecting to talk.google.com:5222 with no proxy
proxy: Connect would have blocked.
proxy: Connected.
jabber: Sending: <?xml version='1.0' ?>
jabber: Sending: <stream:stream to='gmail.com' xmlns='jabber:client' xmlns:stream='http://etherx.jabber.org/streams' version='1.0'>
accounts: Writing accounts to disk.
jabber: Recv (168): <?xml version="1.0" encoding="UTF-8"?><stream:stream from="gmail.com" id="E6A63A73" version="1.0" xmlns:stream="http://etherx.jabber.org/streams" xmlns="jabber:client">
jabber: Recv (189): <stream:features><starttls xmlns="urn:ietf:params:xml:ns:xmpp-tls"/><mechanisms xmlns="urn:ietf:params:xml:ns:xmpp-sasl"><mechanism>X-GOOGLE-TOKEN</mechanism></mechanisms></stream:features>
jabber: Sending: <starttls xmlns='urn:ietf:params:xml:ns:xmpp-tls'/>
account: Disconnecting account 0x81ea2e8
connection: Disconnecting connection 0x837ed78
jabber: Sending: <presence type='unavailable'><status>Logged out</status></presence>
jabber: Sending: </stream:stream>
blist: Destroying
connection: Destroying connection 0x837ed78
accounts: Writing accounts to disk.
dns[29983]: nobody needs me... =(
sighandler: Caught signal 2
plugins: Unloading plugin Gadu-Gadu
plugins: Unloading plugin IRC
plugins: Unloading plugin Jabber
plugins: Unloading plugin MSN
plugins: Unloading plugin Napster
plugins: Unloading plugin GroupWise
plugins: Unloading plugin AIM/ICQ
plugins: Unloading plugin Yahoo
plugins: Unloading plugin Tcl Plugin Loader
plugins: Unloading plugin System Tray Icon
tray icon: destroyed
tray icon: removing callbacks
tray icon: plugin unloaded
plugins: Unloading plugin Message Notification
plugins: Unloading plugin GNUTLS
plugins: Unloading plugin SSL


I can, however, login in MSN with gaim.  What a pity.

---

### Post by davebgimp on 2005-10-18
Have you checked whether your firewall or router (assuming that you have one) might be preventing connections on port 5222? I forward that port from my router and connect to gtalk, no sweat.

---

### Post by realwhz on 2005-10-29
Hi, Davebgimp,

Thank you for your suggestion.  But I'm sure whether I have understand your opinion :(

In fact, the ubuntu I'm using is Breezy Badger 5.10.  I just installed it without modifying it yet.  So, does Ubuntu install a firewall by default installation?  Well, I have tried to connect jaber.org by command `telnet jaber.org 5222'.  It report connected at first.  So does it mean I can connect to the port 5222 of this jaber server?  Additionally, the offical gtalk client from google can connect to its server successfully (of course in Windows).  It seems that the lab's firewall does not prevent us connecting to the port 5222 of gtalk server.

So, how can I solve this problem?  Has anyone using ubuntu 5.10 encountered the same problem?  Thank you all very much.

---

### Post by realwhz on 2005-10-30
I have just tried another jabber client, psi.  It can connect to jabber sucessfully.  So, it seems that a ubuntu spefific bug of gaim has been reached, since the gaim in original debian works well.  What a pity :(

---

### Post by Pathogenix on 2005-10-30
I've also got this problem on the laptop (running Breezy) but not on the desktop (running... um... Breezy) I don't know what the difference is, I've mailed the GTalk development team and I'm yet to hear anything useful back from them.

IIRC though, I had the same problem running Hoary on the laptop, I manually upgraded to the latest build of GAIM but it did no good.

---

### Post by realwhz on 2005-10-30
Thank you, Pathogenix :-)

So, it is really a strange and complex problem ...

By the way, can you have a try to use jabber.org, other than gtalk itself.  I can't connect to jabber.org too now :(  I wonder if it is a problem of jabber module of gaim shipped by ubuntu.

---

### Post by Pathogenix on 2005-11-01
Yo.

I've got GTalk back up and working after compiling from source with these instructions:

[http://gaim.sourceforge.net/faq-ssl.php#q14](http://gaim.sourceforge.net/faq-ssl.php#q14)

Why it worked first time on the desktop is beyond me, but see if that fixes you.

---

### Post by l.capriotti on 2006-03-12
GTalk server is running on port 80, too.
If you are blocked by a firewall not allowing connection to port 5222 you can try  connecting to port 80.

Luigi

---

### Post by fonggiding on 2006-04-19
When I use gaim to log onto gtalk it takes forever and usually doesn't connect. Is this a problem that other people are getting. I sometimes have to press re-try 4-6 times. If there is a problem with my internet(fiberoptic) then is there another port that I should try? I live in Japan so I was wondering if that could have contributed to the slowness. Not a critical problem but if there is an easy answer I would be greatful.

---

### Post by cvmostert on 2006-05-04
[QUOTE=l.capriotti]GTalk server is running on port 80, too.
If you are blocked by a firewall not allowing connection to port 5222 you can try  connecting to port 80.

Luigi[/QUOTE]

Great advice, i also had the "read error" problem with google talk in gaim,

after changing port 5222 to 80, it loged on and it has not logged out ... yet.


much obliged

---

### Post by yetanotherpunter on 2006-05-16
heya I am still having issues, changing form pt 5222 to 80 stops any error messaged sbeing diplayed but just seems to hang on connecting. any ideas?

---

### Post by dpaint4 on 2006-08-04
> **l.capriotti said:**
> GTalk server is running on port 80, too.
If you are blocked by a firewall not allowing connection to port 5222 you can try  connecting to port 80.

Luigi

THIS IS FANTASTIC. Thanks so much. Google didn't say this at all on their site, but now I can use Google Talk from work on my laptop. I guess my workplace has port 5222 blocked.

I hope nothing makes Google stop also allowing port 80 because I'm THRILLED that I can do this now.

---

### Post by maheshjagadeesan on 2007-01-04
> **realwhz said:**
> Thank you, Pathogenix :-)

So, it is really a strange and complex problem ...

By the way, can you have a try to use jabber.org, other than gtalk itself.  I can't connect to jabber.org too now :(  I wonder if it is a problem of jabber module of gaim shipped by ubuntu.

Have you tried enabling "Force old SSL" ?

---

### Post by baidaraka on 2007-04-04
Hi, same problem with me, i am using ubuntu edgy 6.10, I am tried the instruction of goodle that they have mention on their site,
port 5222 is not blocked my service provider, because it get connect by telnet, 
i am new user to linux, So what to do now? Should i have remove and reinstall my gaim pakage?

---

