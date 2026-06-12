---
title: "Solved: 407 Proxy Authentication Required (Feisty)"
date: 2007-04-03
forum: General Help
---

### Post by TitanKing on 2007-04-03
Problem you are having is:

When trying to use Synaptic or anything that uses Synaptic you get:
407 Proxy Authentication Required

Fix this by:
1. System->Preferences->Network Proxy-> Set : Direct Internet Connection.
2. System->Administration->Synaptic Package Manager->Settings->Preferences->Network->Manual Proxy Configuration-> "Set Proxy Setting" and set "Authentication".

There you go, this should do the trick...

Regards,
Titan

---

### Post by TitanKing on 2007-04-05
> **TitanKing said:**
> Problem you are having is:

When trying to use Synaptic or anything that uses Synaptic you get:
407 Proxy Authentication Required

Fix this by:
1. System->Preferences->Network Proxy-> Set : Direct Internet Connection.
2. System->Administration->Synaptic Package Manager->Settings->Preferences->Network->Manual Proxy Configuration-> "Set Proxy Setting" and set "Authentication".

There you go, this should do the trick...

Regards,
Titan

Mmm... the only problem this creates is that now apt-get has problems connecting, aaaargh!

---

### Post by TitanKing on 2007-04-05
Ah finally got it:

In both :
1. System->Preferences->Network Proxy-> Set : Direct Internet Connection.
2. System->Administration->Synaptic Package Manager->Settings->Preferences->Network-> Set : Direct Internet Connection.

Then create a filename in:
/etc/apt/apt.conf

add the following lines:
```

Acquire::http::Proxy "http://username:password@proxy:port";
Acquire::ftp::Proxy "ftp://username:password@proxy:port";

```
and save the file.

In the terminal run:
```

sudo apt-get update

```

Both apt and synaptic should work now. (You might need to restart your networking or your PC)

Regards,
Titan

---

### Post by mincho on 2007-05-01
still asking.....

please help...

---

### Post by nommo on 2007-08-24
Aaaargh..! I am running Xubuntu in VMware (managed to get IT support to let me run Linux in Virtualisation), I got the install to go online, but I seem to be wrestling with this proxy problem with synaptics. I want to update the system and install stuff :D

Anyway - I keep seeing people talking about opening up "System->Preferences->Network Proxy" but of course Xubuntu doesn't have that option. Can anyone point me in the right direction as to where I might turn off the system proxy settings?

I have edited my /etc/apt/apt.conf to point to the correct proxy settings.

Thanks
Paul

---

### Post by jorno on 2007-09-10
I don't know if anyone still has this problem, but I found my solution in another post.

The steps mentioned here earlier are good and all, BUT if those of  you who's got this problem is in a Windows environment with a Microsoft ISA Proxy that need authentication, this is the solution that worked for me:

You need to install NTLMAPS.

[http://packages.ubuntu.com/feisty/web/ntlmaps](http://packages.ubuntu.com/feisty/web/ntlmaps)
* Go there, and download, either from within Firefox (if you manage to get Proxy working with Firefox - I did, but not apt-get or Synaptics or anything else).
* Download the package for ntlmaps (this is for Ubuntu Feisty)
* Start a terminal, find your downloaded package, and type:
*sudo dpkg -i ntlmaps_0.9.9.0.1-6_all.deb*
This should guide you trough the installation of the package...

BUT, my problems didn't stop there!
After, I had to edit /etc/ntlmaps/server.cfg manually.
( *sudo vim /etc /ntlmaps/server.cfg* )
Then I saw that the config-file was formatted with DOS (not UNIX), so I had to tell vim to convert it to UNIX-format. Do this in vim:
*:set fileformat=unix*
*:wq*
This should convert the file, and save it.
I also had to change some of the options:
Under the [CLIENT_HEADER] section, I had to comment out the first Accept and User-Agent part (Windows 98), and then uncomment the next part (Windows 2000 emulation).
Then I filled in "NT_HOSTNAME" (remembered what PC number this workstation had in Windows), and "NT_DOMAIN").

After those changes, restart ntlmaps:
*/etc/init.d/ntlmaps restart*

And point all your proxy-settings to: [http://127.0.0.1:5865](http://127.0.0.1:5865)

Make a file: */etc/apt/apt.conf*
Acquire::http::Proxy "http://127.0.0.1:5865";

And then try "*apt-get update*".

You could also insert this into:
System -> Preferences -> Network Proxy

And in Synaptics:
System -> Administration -> Synaptics -> Settings -> Preferences -> Network:
Manual proxy configuration:

127.0.0.1 port 5865 (no authentication)


This should do the trick! It did for me.. Please ask if there is something not clear yet, or if I should correct any of this. (Sorry, English is not my native tongue).

---

### Post by nommo on 2007-09-13
Hey Jorno

Thanks for your post!

That seems like it could be the solution for me (even if I can't work out how to find the xubuntu equiv of "System->Preferences->Network Proxy" !), as i am indeed behind an ISA proxy/firewall - i have worked through your instructions - but sadly when I try to do my sudo apt-get update at the end, I get the following errors:

Could not connect to 127.0.0.1:5865 (127.0.0.1). - connect (111 Connection refused)

Any ideas what I might be doing wrong?

---

### Post by jorno on 2007-09-13
Either doesn't NTLMAP run properly, or there are some problems in the config file.

When you run "*sudo vim /etc/ntlmaps/server.cfg*", how does it look like? Does it have an "^M" at the end of each line? If so, you have to convert it to UNIX-format as described in my last post.

When you run "*netstat -anp | grep 5865*", what is your output?

Maybe you could post your entire /etc/ntlmaps/server.cfg ?  (just hide your username and password from the config-file before posting!)


// jorno

---

### Post by nommo on 2007-09-13
> **jorno said:**
> When you run "*sudo vim /etc/ntlmaps/server.cfg*", how does it look like? Does it have an "^M" at the end of each line? If so, you have to convert it to UNIX-format as described in my last post.

I did indeed run the convert to unix command in VIM, but when I look at it in VIM - it still has the "^M" at the end of each file... hmm

> **jorno said:**
> When you run "*netstat -anp | grep 5865*", what is your output?

Nada.. nothing shown - I guess that means that NTLM isn't running properly? Actually I just tried restarting the service again, and ran the netstat command once more and got this:
```

tcp        0      0 0.0.0.0:5865            0.0.0.0:*               LISTEN     5318/python
```

Trying a sudo apt-get update still results in errors, albeit of a slightly different nature:

```
Err http://archive.ubuntu.com feisty/main Translation-en_GB
  Connection failed
```


> **jorno said:**
> Maybe you could post your entire /etc/ntlmaps/server.cfg ?  (just hide your username and password from the config-file before posting!)

If I can work out how to copy the whole file to the 'clipboard' I would... 

I am a bit of a (X)ubuntu n00b as you can probably tell! I really appreciate the help though...

e2a:
```
#========================================================================
[GENERAL]

LISTEN_PORT: 5865

# If you want APS to authenticate you at WWW servers using NTLM then just leave this
# value blank like PARENT_PROXY: and APS will connect to web servers directly.
# You can specify more than one proxy by leaving a space between each one, and
# APS will detect when one fails and automatically fail-over to the next. EG:
#PARENT_PROXY:first_proxy second_proxy third_proxy
# And NOTE that NTLM cannot pass through another proxy server.
PARENT_PROXY: fire.eco.local

PARENT_PROXY_PORT: 8080

# APS will poll the upstream proxy and attempt to fail-over to a new one if it doesn't
# get a response within an appropriate time frame.  The amount of time that it will
# wait for a response before attempting fail-over is specified, in seconds, below:
PARENT_PROXY_TIMEOUT:15

# Set to 1 if you want to grant this authorization service to clients from other computers.
# NOTE: all the users from other hosts that will be using you copy of APS for authentication
# will be using your credentials in NTLM auth at the remote host.
ALLOW_EXTERNAL_CLIENTS:0

# If you want to allow some other but not all computers to use your proxy for authorization,
# just set ALLOW_EXTERNAL_CLIENTS:0 and put friendly IP addresses here.
# Use space as a delimiter.
# NOTE that special addesses don't work here (192.168.3.0 for example).
FRIENDLY_IPS:

# Requested URLs are written to "url.log" file. May be useful.
URL_LOG:0

# When a network service listens for connections, there is a maximum number of connection
# attempts to that service that the underlying OS will allow to backlog waiting for a response
# before the OS will start dropping new connection attempts with 'Connection refused'.  The
# standard method of determining the maximum number of backlogged connections is to use the
# SOMAXCONN constant, which is supposed to represent the maximum number that an OS will support
# (for example, 5 on Windows 2000 Pro, and 200 on Windows 2000 server).  However, because this
# is a statically compiled value in a Python distribution, usually this instead represents the
# the most conservative value (5 on all Windows platforms, and 128 on the GNU/Linux variant I
# tried).  So if you are running (for example) a massively threaded/parallel download manager,
# the default value of, say, 5, or whatever SOMAXCONN happens to be set to, may be too low and
# cause some connections to fail.  The value below can be set to any integer (it seems that
# Python just silently caps values above the hard limit for the underlying platform), or it can
# be set to the special value of SOMAXCONN (i.e. MAX_CONNECTION_BACKLOG:SOMAXCONN), to use
# whatever this value happens to be set to in your Python build.  Setting this higher than
# necessary may cause APS to consume more memory than you needed to.
MAX_CONNECTION_BACKLOG:5

#========================================================================
[CLIENT_HEADER]

# This section describes what and how the server should change in the clients headers.
# Made in order to prevent parent proxy from seeing that you are using wget instead of IE5.5

#Accept: image/gif, image/x-xbitmap, image/jpeg, image/pjpeg, application/vnd.ms-excel, application/msword, application/vnd.ms-powerpoint, */*
#User-Agent: Mozilla/4.0 (compatible; MSIE 5.5; Windows 98)

# for windows 2000 emulation ;)
User-Agent: Mozilla/4.0 (compatible; MSIE 5.5; Windows NT5)

# You can uncomment these chages in client's header to mimic IE5+ better, but in this case
# you may expirience problems with *.html if your client does not really handle compression.
#Accept-Encoding: gzip, deflate

#========================================================================
[NTLM_AUTH]

# Optional value, if leaved blank then APS will use gethostname() to determine
# host's name.
# NOTE1: If you Linux host name differs from Windows host name then it may be that
#        MS server wont recognize you host at all and wont grant you access
#        to resources requested. Then you have to use this option and APS will use
#        this name in NTLM negotiations.
# NOTE2: There are several reports that you can successfully use "foreign" host name
#        here. Say, if user may access a resource from 'host1' and may not from 'host2'
#        then there is a chance that APS running on 'host2' with NT_HOSTNAME:host1 will
#        be able to be granted access to the restricted resource. However use this on
#        you own risk as such a trick may be considered as a hack or something.
NT_HOSTNAME:HOST007

# Windows Domain.
# NOTE: it is not full qualified internet domain, but windows network domain.
NT_DOMAIN:domain.local 

# What user's name to use during authorization. It may differ form real current username.
# If you enable NTLM_TO_BASIC, below, you can either leave this blank or simply
# hash it out.
USER: my.name

# Password. Just leave it blank here and server will request it at the start time,
# or, if you enable NTLM_TO_BASIC, below, you can either leave this blank or simply
# hash it out, and you *won't* be prompted for a password at start time.
PASSWORD: password

# These two options replace old FULL_NTLM option.
# NTLM authentication consists virtually of two parts: LM and NT. Windows95/98 use
# only LM part, WindowsNT/2000 can use NT and LM or just NT part.
# Almost always using just LM part will be enough. I had several reports
# about LM and NT requirement and no about just NT.
# So try to setup 1, 1 only if you have enough reasons to do so and when you understand
# what you are doing.
# 0, 0 is an illegal combination
# NOTE: if you change these options then you have to setup flag option accordingly.
LM_PART:1
NT_PART:0

# Highly experimental option. See research.txt for details.
# LM - 06820000
# NT - 05820000
# LM + NT - 07820000
NTLM_FLAGS: 06820000

# This option makes APS try to translate NTLM authentication to very usual "Basic"
# scheme. Almost all http clients know it. With this option set to 1 user will be requested
# by his browser to enter his credentials and these username and password will be used by
# APS for NTLM authentication at MS Proxy server or Web server.
# In such a case different users can use one runnig APS with their own credentials.
# NOTE1: currently translation works so it allows only one try for entering
#        username/password. If you make a mistake you will have to restart you browser.
# NOTE2: With debug:1 basic username/password will be written in log file in clear
#        text format. I could try hide it, but the basic scheme is so weak that anybody
#        who had access to APS would be able to get it.
NTLM_TO_BASIC:0

#========================================================================
[DEBUG]

# Set this to 1 if you want to see debug info in many log files. One per connection.
DEBUG:0

# Set this to 1 to get even more debug info.
BIN_DEBUG:0

# Set this to 1 to see some strange activity on screen. Actually you won't want it.
SCR_DEBUG:0

# Not actually a debug option but gives you some details on authentication process
# into *.auth logs. Also see research.txt.
AUTH_DEBUG:0
```

---

### Post by jorno on 2007-09-13
Ok, so I guess it's your config file that's incorrect....

The conversion from dos to unix file, would probably do the trick... Try once more.

Open the file in vim , type :set fileformat=unix

So then when you try to save the file  ( :w ), you'll something like this at the bottom of vim:
"ntlmaps.conf" 7L, 80C written 

IF you get this:
"ntlmaps.conf" [dos] 7L, 87C written  - you'll know that it's still DOS-format.


I also did see you got one "User-Agent" line, but no "Accept"-line in the [CLIENT_HEADER] section.
Try removing the # in front of the first "Accept"-line.

( I know my guide initially said remove those first two lines, but in my config there were several "Accept"-lines also.)


Hope this helps!


// jorno

---

### Post by nommo on 2007-09-13
> **jorno said:**
> Open the file in vim , type :set fileformat=unix

So then when you try to save the file  ( :w ), you'll something like this at the bottom of vim:
"ntlmaps.conf" 7L, 80C written 

IF you get this:
"ntlmaps.conf" [dos] 7L, 87C written  - you'll know that it's still DOS-format.

I got this: "/etc/ntlmaps/server.cfg" 143L, 7188C written

> **jorno said:**
> 
I also did see you got one "User-Agent" line, but no "Accept"-line in the [CLIENT_HEADER] section.
Try removing the # in front of the first "Accept"-line.

( I know my guide initially said remove those first two lines, but in my config there were several "Accept"-lines also.)


I have uncommented the 'accept' line now for windows 2000 emulation (Accept-Encoding: gzip, deflate
) - I have tried restarting NTLM again but it still gives errors... it does seem to be waiting for headers though when I do a sudo apt-get update.. I will try restarting the system..

> **jorno said:**
> 
Hope this helps!

Of course! I feel like I am getting somewhere now! Thanks again

e2a: I get this now:

30% [Waiting for headers]

followed by:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg
  Connection failed

So - is this all to do with tricking the ISA server into thinking that my apt-get commands are being done in IE or similar..? Perhaps I need to add some more of those Accept lines..?

---

### Post by jorno on 2007-09-13
Well, it seems we came a bit longer now... But there are still some errors.. Hmhm...

Make sure your DOMAIN, USER and PASSWORD are all set in the config the right way. May be a double-check does the trick. As of my info, it is;
NT_DOMAIN = SIKT  (without the .local-part , dunno if you got that?)
USER = joeodb
PASSWORD = not4you  (this is not my password of course) ;)

You could also try experimenting with these:
> # These two options replace old FULL_NTLM option.
# NTLM authentication consists virtually of two parts: LM and NT. Windows95/98 use
# only LM part, WindowsNT/2000 can use NT and LM or just NT part.
# Almost always using just LM part will be enough. I had several reports
# about LM and NT requirement and no about just NT.
# So try to setup 1, 1 only if you have enough reasons to do so and when you understand
# what you are doing.
# 0, 0 is an illegal combination
# NOTE: if you change these options then you have to setup flag option accordingly.
LM_PART:1
NT_PART:0

If this does not work, I'm not sure if I'll be able to help you... But let me know how it goes, and I'll try googling your problem. ;-)

---

### Post by nommo on 2007-09-13
[http://michaelcarden.net/blog/?p=58](http://michaelcarden.net/blog/?p=58)

googling is something i **can** do :)

i found this: [http://michaelcarden.net/blog/?p=58](http://michaelcarden.net/blog/?p=58)

there are a few more potential issues from what i can see... i am going to have to stop faffing for today and actually do some work though ;) so i will carry this on tomorrow - thanks for the help so far...

---

### Post by stuppaz on 2007-09-13
Hi, I have the same problems talked above.

First I setted in Sistem/Proxy the proxy configuration for synaptic I did the same. But using apt-get I caught always the same error: proxy authentication required.
After I created the apt.conf file and setted the two lines:
Acquire::http::Proxy "http://xxx:xxx@xxxxx:3128";
Acquire::ftp::Proxy "ftp://xxx:xxx@xxxxx:3128";

but nothing append.

Thanks for help

---

### Post by nommo on 2007-09-17
OK - here is the latest...

I have scoured the internet for any further possible bugs and/or workarounds - I tried tweaking the settings in "/etc/ntlmaps/server.cfg" - the one that seemed to make a difference was when I put the IP address of the ISA server rather than the hostname - I rebooted - eh voila!

Update manager - check!
Synaptics - check!
apt-get - no joy yet.. (see below)
firefox - check!

```
sudo apt-get install ircii
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  ircii
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 486kB of archives.
After unpacking 3211kB of additional disk space will be used.
Err http://gb.archive.ubuntu.com feisty/universe ircii 20051015-2
  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/i/ircii/ircii_20051015-2_i386.deb  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

So - that could be called progress IMHO...

---

### Post by jagdish.eashwar on 2007-09-17
hi,

i haven't been able to get the ntlmaps to work .

my organisation has a parent proxy and several downstream proxies.
the authentication is done on the respective downstream proxies.
could this be the reason?  does ntlmaps work only with the parent proxies?

besides, i understand from the computer department that we do not have any domains in our network.
could this be another reason?

jagdish eashwar

---

### Post by nommo on 2007-09-18
Well - I finally did it! 

apt-get is fixed now too..

The final fix for me was to do with the syntax of the entry in /etc/apt/apt.conf.d/proxy

Previously it was in this format:

```
ACQUIRE {
http://proxy "http://127.0.0.1:5865/"
}
```

When I changed it to this format:

```
Acquire::http::Proxy "http://127.0.0.1:5865/";

```

It just worked!! :guitar:

Sorry I can't help anyone else troubleshoot, as I am inept and inexperienced! ;)

I hope someone finds something useful in my fumbling...

---

### Post by radian007 on 2008-02-29
Hi all ...

I have some kind of the same problem , but as a user .

I am accessing the internet through a proxy server with username and password in my campus .

the proxy is controled by SQUID 3.0 ( The servers are Linux )

Well , it is about 5 days , that I have a great problem .

I can access internet easily , with my IE , FireFox , Opera etc. ... ( just by setting the lan configurations , proxy settings , and finally entering my user name and password )

BUTTTT ....

When I try to use for example, IDM ( Internet Downloadmanager ) or FlashGet , or DAP or .... although all proxy settings and username and passwords are correct ! when the program try to access internet , it FAILS ! and says :

" HTTP/1.0 407 Authontication Requierd ........ "

just like I have entered the username and password uncorrect ! ( which is not true at all ) ...

before then , there was no problem , but here there IS !

is there any way to solve it ?

( i am a USER )

---

### Post by leboea on 2008-03-05
Thanks 100 times!!
This methods really works

From Mpholo Leboea South Africa Bloemfontein

---

### Post by dinesh2n on 2008-05-03
Acquire::http::Proxy "http://127.0.0.1:3128/";
here 3128 is my port no.....
 this is worked for me also....
 thank you!!

---

