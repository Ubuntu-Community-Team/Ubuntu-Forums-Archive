---
title: "My work place just setup a proxy...407 Proxy Authentication Required"
date: 2007-10-24
forum: General Help
---

### Post by tech9 on 2007-10-24
Hi All,

   I have looked at all the other threads that deal with "407 Proxy Authentication Required" I have tried all the options installing ntlmaps and configuring them. 

Here are some of the steps that I have taken so far

I have Set my synaptic network proxy option to point to our proxy server

I configured System>Preferences>Network Proxy to point to my works proxy server

I made sure that I put in my network credentials in for authentication

I created a file called apt.conf under /etc/apt
and input the following string...
Acquire::http::Proxy "http://127.0.0.1:5865";

I created a file called proxy under /etc/apt/apt.conf.d
and input the following string...
Acquire::http::Proxy "http://127.0.0.1:5865";

I have edited the server.cfg file under /etc/ntlmaps
to reflect unix mode instead of DOS mode...
also network credentials appear to be fine

I have restarted the system several times in between configurations and after.

I am able to use FireFox and get to where I need to go, but I cannot get the "apt-get" function to work because of this stupid proxy that was put in place...

Still getting "407 Proxy Authentication Required" when trying to update system "sudo apt-get update"



**Can anyone help or provide other suggestions to bypass this proxy?**

:-k

---

### Post by tech9 on 2007-10-24
sigh:icon_frown:](*,)

---

### Post by bapoumba on 2007-10-25
If you are using ntlmaps, does it mean this is an ISA proxy ?
[http://ubuntuforums.org/showpost.php?p=3340662&postcount=25](http://ubuntuforums.org/showpost.php?p=3340662&postcount=25)
Did you follow these instructions? Are you sure about the port? Would you need authentication?

---

### Post by tech9 on 2007-10-25
> **bapoumba said:**
> If you are using ntlmaps, does it mean this is an ISA proxy ?
[http://ubuntuforums.org/showpost.php?p=3340662&postcount=25](http://ubuntuforums.org/showpost.php?p=3340662&postcount=25)
Did you follow these instructions? Are you sure about the port? Would you need authentication?

Hi bapoumba,

Thank you for being the only one to reply and help me with this problem.

Actually, Jorno's post is what I tried.

Yes, I am behind and (Microsoft) ISA Proxy, and I know that I need authentication, because when I try to access any web site, I am challenged to authenticate when using firefox. I put in my username and password and then gain access to the sites I try to access.

I am 100% sure about the ports being correct - I have followed Jorno's instructions - and went trough them several times (line by line) to make sure that I was not missing something.

I just cannot get the apt-get function working.

Thank you again for helping me...

T9

---

### Post by bapoumba on 2007-10-25
If you need authentication, this may help you:
[http://ubuntuforums.org/showpost.php?p=2219483&postcount=15](http://ubuntuforums.org/showpost.php?p=2219483&postcount=15)

---

### Post by tech9 on 2007-10-25
Does this have to be in /ect/apt/apt.conf or /ect/apt.conf.d/proxy ?

ACQUIRE {
http:proxy "http://domain\user;password@proxy:8080/"
}

Also, for the proxy do you suggest host name or IP?

Thanks!

---

### Post by bapoumba on 2007-10-25
I'd say /etc/apt/apt.conf.
Did you check the link in the post (it's labeled old thread)?
[http://ubuntuforums.org/showthread.php?t=63496](http://ubuntuforums.org/showthread.php?t=63496)

Sorry I cannot help you more than that, I never had to use an ISA proxy myself :)

---

### Post by tech9 on 2007-10-25
> **bapoumba said:**
> If you need authentication, this may help you:
[http://ubuntuforums.org/showpost.php?p=2219483&postcount=15](http://ubuntuforums.org/showpost.php?p=2219483&postcount=15)

ok... I tried putting in the line of code into proxy and now I am getting this error...
E: Syntax error /etc/apt/apt.conf.d/proxy:1: Unsupported directive 'Acquire::http::Proxy'

---

### Post by tech9 on 2007-10-25
> **bapoumba said:**
> I'd say /etc/apt/apt.conf.
Did you check the link in the post (it's labeled old thread)?
[http://ubuntuforums.org/showthread.php?t=63496](http://ubuntuforums.org/showthread.php?t=63496)

Sorry I cannot help you more than that, I never had to use an ISA proxy myself :)

I think it needs to be /etc/apt/conf.d/proxy because I am running 7.10

---

### Post by tech9 on 2007-10-25
> **bapoumba said:**
> I'd say /etc/apt/apt.conf.
Did you check the link in the post (it's labeled old thread)?
[http://ubuntuforums.org/showthread.php?t=63496](http://ubuntuforums.org/showthread.php?t=63496)

Sorry I cannot help you more than that, I never had to use an ISA proxy myself :)

ok, well thanks for your efforts... I will read through the thread and putz with it until - hopefully I get it to work.

---

### Post by bapoumba on 2007-10-25
could you please paste the file? (you can use [ noparse ] [ /noparse ] (without the spaces) to prevent the code to be interpreted into smileys :))

---

### Post by tech9 on 2007-10-25
> **bapoumba said:**
> could you please paste the file? (you can use [ noparse ] [ /noparse ] (without the spaces) to prevent the code to be interpreted into smileys :))

This is what I had originally in /ect/apt.conf.d/proxy

#Acquire::http::Proxy "http[://127.0.0.1:5865/";

and made sure that I pointed all proxy settings in the system to this.

---

### Post by bapoumba on 2007-10-25
> **tech9 said:**
> This is what I had originally in /ect/apt.conf.d/proxy

#Acquire::http::Proxy "http[://127.0.0.1:5865/";

and made sure that I pointed all proxy settings in the system to this.
You need to remove the # in front of the line. A # means it is a comment, and is not taken into account (hopefully...).

---

### Post by tech9 on 2007-10-25
here is my server.cfg file for ntlmaps

#========================================================================

[GENERAL]



LISTEN_PORT: 5865


# If you want APS to authenticate you at WWW servers using NTLM then just leave this

# value blank like PARENT_PROXY: and APS will connect to web servers directly.

# You can specify more than one proxy by leaving a space between each one, and

# APS will detect when one fails and automatically fail-over to the next. EG:

#PARENT_PROXY:first_proxy second_proxy third_proxy

# And NOTE that NTLM cannot pass through another proxy server.

PARENT_PROXY: my parent proxy IP adress


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



Accept: image/gif, image/x-xbitmap, image/jpeg, image/pjpeg, application/vnd.ms-excel, application/msword, application/vnd.ms-powerpoint, */*

#User-Agent: Mozilla/4.0 (compatible; MSIE 5.5; Windows 98)



# for windows 2000 emulation ;)

User-Agent: Mozilla/4.0 (compatible; MSIE 5.5; Windows NT5)



# You can uncomment these chages in client's header to mimic IE5+ better, but in this case

# you may expirience problems with *.html if your client does not really handle compression.

Accept-Encoding: gzip, deflate



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

NT_HOSTNAME: Computer



# Windows Domain.

# NOTE: it is not full qualified internet domain, but windows network domain.

NT_DOMAIN: name of NT domain


# What user's name to use during authorization. It may differ form real current username.

# If you enable NTLM_TO_BASIC, below, you can either leave this blank or simply

# hash it out.

USER: myusername


# Password. Just leave it blank here and server will request it at the start time,

# or, if you enable NTLM_TO_BASIC, below, you can either leave this blank or simply

# hash it out, and you *won't* be prompted for a password at start time.

PASSWORD: mypassword


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

---

### Post by tech9 on 2007-10-25
> **bapoumba said:**
> You need to remove the # in front of the line. A # means it is a comment, and is not taken into account (hopefully...).

shoot... I meant to post that without the "#" -  I know that would comment out the code. I was testing something - yes I did remove it - same problems - sorry

---

### Post by tech9 on 2007-10-25
> **bapoumba said:**
> You need to remove the # in front of the line. A # means it is a comment, and is not taken into account (hopefully...).

Well, I feel like I am getting somewhere... I know now that the file the proxy needs is /etc/apt.conf.d/proxy and not /ect/apt/apt.conf

Now it seems like I am missing something in the server.conf file for ntlmaps

I get this...

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
  Could not resolve ':@127.0.0.1'

when running sudo apt-get update

Thanks for all your suggestions bapoumba :)

---

### Post by tech9 on 2007-10-25
> **bapoumba said:**
> You need to remove the # in front of the line. A # means it is a comment, and is not taken into account (hopefully...).

Many Thanks to bapoumba...

The resolution was installing the ntlmaps - instructions by jorno, creating a proxy file under /etc/apt.conf.d/

adding Acquire::http::Proxy "http://127.0.0.1:5865/";

and last but not least - SET ALL PROXY SETTINGS TO "Direct Internet Connection" FOR BOTH

System>Preference>Network Proxy and
Synatptic>Settings>Network

This Fixed it for me... Hope this helps someone! :guitar:

---

### Post by RooiRampokker on 2007-11-01
Hi all,

I'm also stuck with the same problem (behind a Microsoft ISA proxy) an none of the suggestions posted here have worked for me.

1. I set "System->preferences->network proxy" to manual and entered http proxy details (including username/password)
2. I set Synaptic->setttings->prefences->network to "DOMAIN\USERNAME:PASSWORD@IP_TO_PROXY"
3. I created /etc/apt/apt.conf and saved it with: "Acquire::http::Proxy "http://jDOMAIN\USERNAMEl:PASSWORD@IP_TO_PROXY:PORT/"
4. I installed and configured ntlmaps as instructed by Jorno
5. I've also tried variations on all the above (IP instead of name, port 5865 instead of 8080 (although I'm 100% sure its supposed to be 8080, etc)

All roads lead to: "407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )"

Of everything I found while googling for an answer, this thread seems to make the most sense (although it doesn't solve my problem either)

Can anyone please help?

---

### Post by tech9 on 2007-11-01
> **RooiRampokker said:**
> Hi all,

I'm also stuck with the same problem (behind a Microsoft ISA proxy) an none of the suggestions posted here have worked for me.

1. I set "System->preferences->network proxy" to manual and entered http proxy details (including username/password)
2. I set Synaptic->setttings->prefences->network to "DOMAIN\USERNAME:PASSWORD@IP_TO_PROXY"
3. I created /etc/apt/apt.conf and saved it with: "Acquire::http::Proxy "http://jDOMAIN\USERNAMEl:PASSWORD@IP_TO_PROXY:PORT/"
4. I installed and configured ntlmaps as instructed by Jorno
5. I've also tried variations on all the above (IP instead of name, port 5865 instead of 8080 (although I'm 100% sure its supposed to be 8080, etc)

All roads lead to: "407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )"

Of everything I found while googling for an answer, this thread seems to make the most sense (although it doesn't solve my problem either)

Can anyone please help?

After you install ntlmaps,,,

create a proxy file under /etc/apt.conf.d/

adding Acquire::http::Proxy "http://127.0.0.1:5865/";

and last but not least - SET ALL PROXY SETTINGS TO "Direct Internet Connection" FOR BOTH

System>Preference>Network Proxy and
Synatptic>Settings>Network

---

### Post by EkTool on 2008-05-09
I am running Ubuntu 8.04 on MS VPC hosted on Vista Ultimate.
I was having the exact same issues as you with a MS ISA Proxy that blocked my package manager.  After struggling with multiple links throughout this post and others I found a site that walks you through configuring ntlmaps.  It worked like a charm for me.

[http://www.linuxquestions.org/linux/answers/Networking/HOWTO_Install_and_Configure_NTLMaps_for_use_with_an_ISA_Proxy](http://www.linuxquestions.org/linux/answers/Networking/HOWTO_Install_and_Configure_NTLMaps_for_use_with_an_ISA_Proxy)

---

