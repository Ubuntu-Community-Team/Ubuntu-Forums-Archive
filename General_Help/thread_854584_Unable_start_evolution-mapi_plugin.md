---
title: "Unable start evolution-mapi plugin"
date: 2008-07-09
forum: General Help
---

### Post by hujer on 2008-07-09
I have successfully installed evolution MAPI plugin (libmapi, samba4 and evolution-mapi-provider) from debs converted from fedora 9 rpms (downloaded from [http://download.opensuse.org/repositories/home:/jjohnny:/evolution-exchange-mapi-provider/Fedora_9/](http://download.opensuse.org/repositories/home:/jjohnny:/evolution-exchange-mapi-provider/Fedora_9/)). 

I put 'include /opt/samba4/lib' to /etc/ld.so.conf
and ran 'sudo ldconfig'. Then I added paths:

export PATH=/opt/samba4:$PATH
export PKG_CONFIG_PATH=/opt/samba4/lib/pkgconfig:$PKG_CONFIG_PATH
export LD_LIBRARY_PATH=/opt/samba4/lib:$LD_LIBRARY_PATH 

Now I can see MAPI plugin included in the list in evolution plugin list, but when I check the box to include MAPI type in the mail servers type list (add plugin) and reload evolution, nothing happens, the check box of MAPI plugin gets cleared and the mail servers type list does not contain MAPI type. Starting evolution from terminal produces a message: (evolution:8439): e-utils-WARNING **: can't load plugin 'libmapi.so.0: cannot open shared object file: No such file or directory'. 

Does anybody know what am I doing wrong? Or the Fedora rpms are unusable for ubuntu hardy? In this case could anybody recommend other evolution MAPI source suitable for hardy and evo 2.22?

Thanks in advance.

---

### Post by HDave on 2008-07-25
Welcome to the continuing battle to get this working on Ubuntu.

If you start evolution from a terminal rather than a menu pick, you can see what the problem is.  This particular issue has been hit several times by myself and others, the answer can be found here (sorry for the length of the thread, I don't have time to pull the answer out for you right now):

[http://ubuntuforums.org/showthread.php?t=519672&page=5]("http://ubuntuforums.org/showthread.php?t=519672&page=5")

Also check out this:

[http://mail.gnome.org/archives/evolution-list/2008-July/msg00066.html]("http://mail.gnome.org/archives/evolution-list/2008-July/msg00066.html")

Based on what we're seeing now, it is better to compile from source rather than use alien on the RPM's.

---

### Post by CronAcronis on 2008-08-22
Is deb package available or still in progress?

---

### Post by HDave on 2008-08-22
There are some available for Debian Etch now, but the situation does not look promising after reading the following thread:

[http://mailman.openchange.org/pipermail/devel/2008-August/000790.html]("http://mailman.openchange.org/pipermail/devel/2008-August/000790.html")

---

### Post by ThomasNovin on 2008-09-13
Noticed that files got updated today. There is also a file called openchange-*.deb.

Anyone had any luck with them?

I could not install both samba4_4.0-1_i386.deb and samba4-libs_4.0-1_i386.deb:

```
~$ sudo dpkg -i samba4-libs_4.0-1_i386.deb 
(Reading database ... 186510 files and directories currently installed.)
Unpacking samba4-libs (from samba4-libs_4.0-1_i386.deb) ...
dpkg: error processing samba4-libs_4.0-1_i386.deb (--install):
 trying to overwrite `/usr/local/samba/lib/python2.4/site-packages/tdb.py', which is also in package samba4
Errors were encountered while processing:
 samba4-libs_4.0-1_i386.deb

```

---

### Post by ThomasNovin on 2008-09-14
There is now a bug on LP about syncing OpenChange from Debian Lenny. This would add Exchange 2007 support to Ubuntu. The bug id is [260786]("https://bugs.launchpad.net/ubuntu/+bug/260786").

I think it is very possible to get the Debian version working in Ubuntu already though.

---

### Post by ThomasNovin on 2008-09-24
As the observant has already noted, bug #260786 is now resolved and openchange is now in Ubuntu.

[https://launchpad.net/ubuntu/+source/openchange/](https://launchpad.net/ubuntu/+source/openchange/)

---

### Post by kiddyfurby on 2008-09-30
any updates?
openchange does appear to be in intrepid universe, but i can't find any evolution plugin

---

### Post by HDave on 2008-10-01
There was some chatter on this subject on the evolution mailing list.  Looks like a working evo plugin for MAPI is still some months away.  Don't think it will make intrepid...

---

### Post by hardkaare on 2008-10-06
Lets hope someone can make a package for evolution-openchange-mapi.

---

### Post by tgrimley on 2008-10-17
I hope this happen soon so I can totally switch to Ubuntu..

---

### Post by devman on 2008-10-17
> **tgrimley said:**
> I hope this happen soon so I can totally switch to Ubuntu..

I'm in the same boat as you. Exchange access it the only thing blocking my move to Linux on my work PC.

---

### Post by Skerit on 2008-10-21
I'm also not willing to compile evolution just because of 1 plugin.
(That's really one of gnome's problems to me: plugins are a bitch. But I digress ...)

Isn't there some debian package we could use?

---

### Post by devman on 2008-10-21
> **Skerit said:**
> I'm also not willing to compile evolution just because of 1 plugin.
(That's really one of gnome's problems to me: plugins are a bitch. But I digress ...)

Isn't there some debian package we could use?

Then you will have to wait probably. MAPI isn't done yet it is still beta. However it is on the road map for GNOME 2.26 release in March and will probably be in Ubuntu 9.04

---

### Post by HDave on 2008-10-22
The developers have made a ton of progress, but according to the latest emails, they have a long way to go.

Also, according to the newly revised openchange web site, the licensing incompatibility between evolution and openchange (I think) has not yet been resolved.

---

### Post by Ghilteras on 2008-11-26
> **devman said:**
> Then you will have to wait probably. MAPI isn't done yet it is still beta. However it is on the road map for GNOME 2.26 release in March and will probably be in Ubuntu 9.04

this was said for gnome 2.24 too, the problem was that mapi was still in development then

but now we have some unstable mapi to test, and there is the plugin too in the svn. we are just missing the deb package for the plugin and i frankly think it's stupid to wait until march just to have this plugin packaged, it could be easily packaged as experimental provided that the guys of novell and the devs of openchage say that is compatible with the current experimental version of evolution (2.24.2)

cheers

---

### Post by rdasilva on 2009-03-24
The openchange plugin for Evolution is called evolution-mapi and now seems to be in Jaunty Universe.  It can be installed (sudo apt-get install evolution-mapi) and shows up in the Evolution Server Type selection as 'Exchange MAPI'.  woot!

But unfortunately it doesn't seem to be able to authenticate with my Exchange server. I continually get an authentication error:

Authentication failed.
MapiLogonProvider:MAPI_E_LOGON_FAILED

Has anyone gotten evolution-mapi to successfully authenticate/login to an Exchage server?

Our server uses SSL and I do not see any option to set SSL.  Might this be the problem?

---

### Post by ThomasNovin on 2009-03-24
I'm using this on two different Jaunty installs, they both work fine authenticating against Exchange 2007.

Have you filled in your username/domain correctly?

---

### Post by rdasilva on 2009-03-24
I'm using all the information from my exchange.prf file that successfully authenticates via Outlook.  Checked the server/name/domain numerous times since that's what I first suspected.

Thomas, does your Exchange config require SSL?

---

### Post by Ric_ on 2009-03-25
rdasilva I have exactly the same problem with authentication. have you got to the bottom of this problem yet?

Ric_

---

### Post by rdasilva on 2009-03-26
No I haven't, Ric_.  I think it may have something to do with our exchange implementation requiring SSL.  Is your server set to allow only ssl too?

---

### Post by brainee28 on 2009-04-02
Where it asks for your username, domain and server, use an IP instead of a DNS or NETBIOS name. I had this problem and solved it using the IP. It authenticated for me.

Now I'm trying to solve a Send problem. I can send to an internal address just fine. I can type in a manual address (me@me.com) but I can't reply to an outside address; it won't send it out.

---

### Post by rdasilva on 2009-04-06
Thanks for the tip Brainee, but that didn't work... now I just get: MapiLogonProvider:MAPI_E_NETWORK_ERROR

---

### Post by benrboone on 2009-04-07
thanks! I've been waiting for this to work for a long time.  (I was able to use the IP address of the server and athenicate.)  Now my Evolution Email is working with exchange server 2007. still haven't got the calendar to work

---

### Post by eliask08 on 2009-04-22
Hi rdasilva, 

I too am having the same issue.  I've tried entering the server's IP rather than owa's URL, but still nothing (like you, I get the MAPI_E_NETWORK_ERROR).  I have noticed that when I enter the domain name as "domain\user", evolution crashed, so I might be on to something there :P

Elias

---

### Post by Gublerian on 2009-04-26
Same problem as eliask08 and rdasilva here. (network error when I ty it with the ip) My exchange runs with ssl too (and I cant change), so this might be the problem. :confused:

---

### Post by lucianct on 2009-04-26
i have the same problem too. when i enter the server name i get network error and when i enter the owa url i get logon error.

---

### Post by smyrna112 on 2009-04-27
Just to ask i see that some have it working just fine and some (like me) get auth errors, Just to ask 

The ones who have it working are you working on your LAN with an exchange server? 

And some of us (like me) are using an exchange server over the internet or through a hosted service?

---

### Post by Gublerian on 2009-04-28
> **smyrna112 said:**
> Just to ask i see that some have it working just fine and some (like me) get auth errors, Just to ask 

The ones who have it working are you working on your LAN with an exchange server? 

And some of us (like me) are using an exchange server over the internet or through a hosted service?

For me it doesn't work with a hosted exchange server over internet (ssl)

---

### Post by Morm on 2009-04-29
Evolution-mapi did the trick (along with renaming smb.conf). I also imported the self-signed key from Exchange 2007 since we're using SSL, but I'm not sure if that step was necessary. The calendar doesn't work, but at least I can read my email.

---

### Post by gen.alcazar on 2009-04-30
Not sure how many people this will help, but I had the same issue with authentication failure, with the following message:

Authentication failed.
MapiLogonProvider:MAPI_E_LOGON_FAILED

until I realized that this is was a firewall blocking MAPI.  Disabled that for now - works.  Be sure to put the IP address of the server as opposed to the fqdn.

---

### Post by Alibloke on 2009-05-05
I can confirm that using the IP address direct seems to work, otherwise you get the nasty authentication failure message.  After spending an age refreshing my inbox evolution has taken up an incredible amount of RAM (900MB).  I hope this isn't normal.....although it could be due to the 8000 or so messages in there *cough*

---

### Post by burnsidemk on 2009-05-05
I can confirm that the IP address works also.  Unfortunately, I can also confirm evolution is using upwards of 1200 MB of memory on my large Inbox of 3700 messages just to show message headers.

---

### Post by emdalton on 2009-05-05
I have the mapi plugin and I've tried using the IP address-- I'm still getting the logon error. Where should I look for firewall options that might be blocking MAPI?

---

### Post by iMCNEt on 2009-05-06
I had the same issue, and my Exchange server is on my LAN. I typed the ip address (172.16.2.42) without the http before. Make sure to NOT include the http when you are typing the server address. It should work.

---

### Post by niceshaman on 2009-05-08
Hi there,

I very apologize if I give stupid question. But I carefully examined all pages of this topic here and still have error. I tried to connect both from home and from inside our company but have MAPI_E_LOGIN_ERROR. I also tried to ping exchange.mycompany.com, identified IP address and tried to connect to IP instead of domain name... and have the same error... I'm upset. I wanted to attach screenshot, but didn't find how to do that.

I'm a newcomer in Ubuntu, and I hope you will be patient to my questions.

Thank you!

---

### Post by harp2812 on 2009-05-15
I'm also receiving the Authentication failed. MapiLogonProvider:MAPI_E_NETWORK_ERROR error message...

I've tried it with the DNS name, NetBIOS name, and IP address, and I'm on the same network VLAN as the Exchange server (no firewalls)...  Is there some setting on the Exchange server that needs to be enabled?

---

### Post by HDave on 2009-07-08
Mine just hangs trying to do the login over SSL with our without using the IP address.   Anybody get this to work in Jaunty?

---

### Post by TheGorf on 2009-07-13
Just to add my 2 cents to this thread.  I was able to get the plugin installed, but running through the setup helper the first time with Evolution on 9.04 gives me a segmentation fault:

```

** (evolution:5529): DEBUG: Loading Exchange MAPI Plugin 

** (evolution:5529): DEBUG: MAPI listener is constructed with 0 listed MAPI accounts 
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-ExchangeMAPI'
Create profile with gsweet wemadeusa bichon.wemadeusa.loc
libexchangemapi-Message: exchange-mapi-connection.c:2874: exchange_mapi_create_profile: lock(connect_lock)
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Logging into the server... succeeded 
libexchangemapi-Message: exchange-mapi-connection.c:146: exchange_mapi_connection_close: lock(connect_lock)
Segmentation fault

```

This is with Small Business Server 2003.  Off to file a bug.

---

### Post by HellBoyz77 on 2009-08-11
Hello,
i can confirm that using the IP instead of the string Evolution does not crash in the account setup.

However i can't see any message in my inbox ...

---

### Post by fnog on 2009-09-24
I think I've some new info to add to this thread regarding to the "MAPI_E_LOGON_FAILED".

When trying to authenticate using my domain user login, I'me "presented" with a normal "Authentication failed" message window.

debug info:
```
(...)
Loading profile <login>@<domain>     EcDoConnect              : ecLoginPerm (0x3F2)
    MapiLogonEx              : MAPI_E_LOGON_FAILED (0x80040111)
(...)

```



When using the same user login but with a wrong password, I get the following message window:
'
Authentication failed
MapiLogonProvider:MAPI_E_LOGON_FAILED
'.

debug info:
```

(...)
Logging into the server... Failed to bind to uuid xxxxxxxxxxxxxx-00c04fd7bd09 - NT_STATUS_NET_WRITE_FAULT
Failed to bind to uuid xxxxxxxxxxxxxxxxxxxxxxxxxxxx - NT_STATUS_NET_WRITE_FAULT
    MapiLogonProvider        : MAPI_E_LOGON_FAILED (0x80040111)
(evolution:17563): libexchangemapi-DEBUG: Deleting profile <login>@<domain> 
libexchangemapi-Message: exchange-mapi-connection.c:2966: exchange_mapi_create_profile: unlock(connect_lock)

(evolution:17563): e-data-server-ui-WARNING **: Unable to find password(s) in keyring (Keyring reports: No matching results)
(...)

```

Another curious thing, but not less important: with a co-worker login account, I can successfully login.

I've compared both accounts at the domain server, but didn't find locked accounts, or any difference that got my attention...

Hope this helps...

P.S. - I can access to my email both using normal evolution/exchange-plugin setup and web browser access.

---

### Post by Skerit on 2010-01-08
It's strange they're leaving us hanging like this. Not a single mention of SSL anywhere.

Would it be that hard to implement?

---

### Post by ThomasNovin on 2010-01-08
Using 0.28.2 (on Karmic) from [https://launchpad.net/~kbuel/+archive/ppa](https://launchpad.net/~kbuel/+archive/ppa) and that version works quite good!

---

### Post by Skerit on 2010-01-11
That may be, but it still doesn't support SSL

---

