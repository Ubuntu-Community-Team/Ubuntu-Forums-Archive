---
title: "Behind a proxy, can't access repositories (407 error) HELP"
date: 2008-04-28
forum: General Help
---

### Post by MrPaez on 2008-04-28
Hey this issue has been driving me mad. I am at work and I have setup a test desktop running 7.10. At my workplace we have an ISA proxy/firewall.

Whats happening is that when i try to run update or download/install software from the synaptic packager manger I get an error message stating: (407 ISA authentication...blah..blah)

I have put in the correct credentials for access to the proxy, as well as the correct IP for the proxy. I have sufficient rights (domain admin.) so thats not an issue. I have placed the exact same proxy setting config. information in the following areas of 7.10

For Firefox which works and I can get out to the internet. Under System>Preferences>Network Proxy and lastly under Administration>Synaptic Package Manager>Settings>Preferences>Network .

I also created an /etc/apt/apt.conf file with the following lines: 
Acquire::http::Proxy "http://[[user][:pass]@]host[:port]";
Acquire::ftp::Proxy "http://[[user][:pass]@]host[:port]";

without the brackets however.

If anyone has any suggestions on resolving the authentication issues with our environment's ISA I would appreciate it.

PS: sudo apt-get update or any CLI commands generate the same error.

PSS: I rather not download each update and manually install it. Thats why I am looking to resolve this issue.

---

### Post by jocko on 2008-04-28
Have you tried setting the proxy in synaptic (Settings --> Settings --> Network)?

---

### Post by MrPaez on 2008-04-28
Jocko, I am not sure i follow where you are suggesting to change the syanptic settings.

I have set it under  Administration>Synaptic Package Manager>Settings>Preferences>Network   is this the location that you are referring to?

---

### Post by jocko on 2008-04-28
> **MrPaez said:**
> Jocko, I am not sure i follow where you are suggesting to change the syanptic settings.

I have set it under  Administration>Synaptic Package Manager>Settings>Preferences>Network   is this the location that you are referring to?
yes, that's what I meant. I translated from swedish, so I guessed wrong on one of the "Settings"...
I guess it didn't work, then I can't help you...

---

### Post by quanumphaze on 2008-05-01
I have similar difficulties here at uni.

I believe it has something to do with command line apps not using the Gnome proxy settings. For example Firefox would work but something like Links2 would not. I can access the university's sites in Links2 without proxy configured but not any outside network.

Synaptic and Update Manager both use a command line back end and here I would suggest we try to fix the proxy issues first. But I have no idea how to do this.

---

### Post by Stu09 on 2008-10-27
I'm having the exact same problem, but with an ubuntu server being behind an ISA server.
Not being able to access the repositories is quite frustrating.

---

### Post by cormi on 2009-07-13
> **jocko said:**
> Have you tried setting the proxy in synaptic (Settings --> Settings --> Network)?

Thanks this solved my problem too.

---

### Post by Piccy on 2009-07-13
You might want to check the firewall logs to see if its being blocked. Synaptic MAY use a blocked port on the firewall

Another thing to try is to use apt to see if that works

---

### Post by nmvictor on 2009-09-07
I have jaunty installed in one of the computers in our university library.Unfortunately, the university uses a proxy to authenticate access to the internet.I have not been able to access the repositories for almost a month now, same applies to wget, irssi, pidgin nor anything.I have read every posts in ubuntu forums and tried the sugestion but nothings working.Since then, I have to manually download the packages and install them anually and i wish you knew how tiring that is, especially with dependency issues.This is really stressing.Anybody with suggestions to help?I can say that the reason the suggestions i read on similar problems in this forum have not been working because of the username and passwords that we've been assigned.Maybe they contain characters that conflict in a way with some settings i mean, the username is in the form "user.name@proxy.domain" while the password is in the form XXX/YYY/ZZZZ  Please note the '@','.' and '/' characters which i feel could be conflicting with some settings.Any help ????

---

### Post by tiagosales on 2009-09-07
Do you try to go in System > Preferences > Network Proxy?

In Proxy Configuration Tab, mark Manual Proxy configuration and put the IP and port of the Proxy Server, click in details for authentication's information.

Click on Apply System-Wide..., so put the priveleged user's password, and try run apt-get or refresh synaptic package information.

Sales, Tiago.

---

### Post by AlexanderDGreat on 2009-12-26
Hi I'm behind a firewall, I can't apt-get update. I've already tried ALL suggestions here: [https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGet#Setting%20up%20apt-get%20to%20use%20a%20http-proxy]("https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGet#Setting%20up%20apt-get%20to%20use%20a%20http-proxy")

But they're NOT working for me! I'm using Karmic Koala on server and client. Pls. Help!

---

### Post by lalamax3d on 2010-01-13
ok, i m on same page, alexander.
have you find solution to your problem. please let me know
previously ( ubuntu / kubuntu jaunty) apt.conf file was located in /etc/apt/ but now, i m unable to find this file.so my probslems are

1- where is apt.conf file in kubuntu karmic??
2- whats the difference between /etc/bash.bashrc and .profile file. i mean adding line below to both files is recommended by lots of ppl
"export http_proxy=user:pass@proxy:port"
and none actually worked for me right now??
3- tpyically in firefox i set proxy and it asks for user / pass. my user is precisely "wtpk\haseebah" and it worked. but in konqueror in have to type only "haseebah" it doesn't ask for "wtpk/" and if i type this it won't accept user...? any ideas

4- in kubuntu network proxy settings, if i type http::proxy "http://wtpk\haseebah:Password2@172.26.143.12:8080/ and save and check output in kate (.kde/share/config/kioslaverc) its confused because of issue i explained in third point.

ahhhhhhhhhhhh. i wish this proxy issue should have been resolved now. its quite old and setting it at one global place should ideally fix this everywhere including terminal

---

### Post by techstop on 2010-01-13
> **AlexanderDGreat said:**
> Hi I'm behind a firewall, I can't apt-get update. I've already tried ALL suggestions here: [https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGet#Setting%20up%20apt-get%20to%20use%20a%20http-proxy]("https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGet#Setting%20up%20apt-get%20to%20use%20a%20http-proxy")

But they're NOT working for me! I'm using Karmic Koala on server and client. Pls. Help!

If it's a Microsoft ISA proxy using NTLM authentication, then you need to install ntlmaps to solve your problem. See here;

[http://michaelcarden.net/blog/?p=58](http://michaelcarden.net/blog/?p=58)

I have to install ntlmaps for ubuntu machines at work behind an ISA proxy.

HTH.

---

### Post by AlexanderDGreat on 2010-01-13
@lalamax3d - you know, for some strange reason, I was able to update using sudo gedit /etc/apt/sources.list and changing all http to ftp. How come it worked this time?

However, I don't need this method now. I've just setup a 2 NIC Server with NAT to the clients, and all their updates are fine. The server is their gateway and has transparent Squid Proxy as well. In the end, I don't even setup proxy settings individually to my clients, squid server intercepts all their http requests. All emails, web, and updates work for them automatically.

---

### Post by veenkumar2003 on 2010-01-29
After trying as in the link [http://michaelcarden.net/blog/?p=58](http://michaelcarden.net/blog/?p=58) I get the below errors..Can anyone pls help me on this...

Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
  Connection failed
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release.gpg
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_IN
  Connection failed
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Translation-en_IN
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_IN
  Connection failed
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Translation-en_IN
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_IN
  Connection failed
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Translation-en_IN
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_IN
  Connection failed
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Translation-en_IN
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release.gpg
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Translation-en_IN
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Translation-en_IN
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Translation-en_IN
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Translation-en_IN
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release
8% [Waiting for headers] [Waiting for headers]


Thanks in advance

---

