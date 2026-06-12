---
title: "Synaptic behind a proxy gives (104 Connection reset by peer)"
date: 2006-12-20
forum: General Help
---

### Post by afternine on 2006-12-20
Hi!

I'm using Kubuntu 6.10 Edgy in a vmware virutal machine (a test sandbox and I don't like Adept, since it gives even less fedback than Synaptic) and having troubles with getting updates. I've managed to install Synaptic, configured the proxy and can get the update headers. I can also get to [http://main.archive.ubuntu.com](http://main.archive.ubuntu.com) with a browser, no problems. However, when I try to get the packages, I get many of these:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.15.91-2ubuntu0.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.15.91-2ubuntu0.3_i386.deb)
  Error reading from server - read (104 Connection reset by peer)

This happens for most of the packages, but not for all of them, some of them actually get downloaded. 

I have in my proxy configured in my apt.conf, if I do "cat /etc/apt/apt.conf" I get 

Acquire::http::Proxy "http://myproxy.blah:8080/";

Is there someting more I can do to diagnose the problem?

Bye

---

### Post by mooha on 2006-12-21
I am on the way to get upset and I think I am going to give up soon, can any one help please, I am behind a proxy server with authenfication, I did put the user and password thing on the apt.conf but no way, can anyone help ?

I tried all methods that was given by users here in forum.

So why apt-get or Adept or synaptic dont use the proxy system configuration to download pakages?

Do I have to activate Root login in graphic and try it out?  ](*,) 

I am confused.

Any help is apreciated, thanks

---

