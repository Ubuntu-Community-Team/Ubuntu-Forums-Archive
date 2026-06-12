---
title: "Firefox invoked remotely launches locally!!!"
date: 2007-09-27
forum: General Help
---

### Post by ionlimon on 2007-09-27
This mush be one of the weirdest things that happened to me. I have a laptop running Kubuntu 7.04 (Feisty Fawn) and on occasion I need to run Firefox remotely on a machine running Debian Linux. I type clearly "firefox" in the terminal in which I have ssh-ed to the Debian machine, and after about 30s, Firefox starts on ... my own local machine! I tried it also from a desktop running Kubuntu Feisty Fawn, same result! I don't understand this at all, the only thing I can think is that the Firefox script that searches for the paths and libraries and all that, somehow manages to tunnel to my local machine and find the local Firefox location and launch it locally. But how is that possible? And how can that be avoided?
The most frustrating thing is that if I connect to the Debian machine from Windows, using either Cygwin or XWin32, Firefox launches remotely just fine! This is really annoying considering how I always bash Windows compared to Linux : ) ...
I'd appreciate any insight in this story

---

### Post by maybeway36 on 2007-09-27
I suppose you could try firefox-bin and iceweasel. This is a very strange problem, I agree.

---

### Post by Zwack on 2008-01-23
This is standard behaviour... If there is a local copy of firefox running already then it doesn't open the remote copy for some reason.  Try running "firefox -local" which works for me.

It looks like the mess of scripts used to start firefox have a lot of cruft in them to try and stop you opening a "remote" session when you already have a local one... It's a pain because "firefox http://localhost:631/" is different remotely from locally.

Z.

---

### Post by Lostincyberspace on 2008-01-23
Are you sure it is local and not remote actually, is there something different between the two to set them of?

---

### Post by Zwack on 2008-01-24
> **Lostincyberspace said:**
> Are you sure it is local and not remote actually, is there something different between the two to set them of?

Pretty sure... localhost has different websites on the different hosts.  So if you are trying to look at a remote website that is only available on localhost you can tell the difference.  for example CUPS binds it's web interface to 127.0.0.1:631.  It can only be seen from that host.

Z,

---

### Post by ionlimon on 2008-02-24
Zwack is right. Unfortunately his solution does not work for me, seems that whatever version of Firefox is installed on the remote server does not accept -local as an option. In fact I ran firefox -h for a list of command line options for the remote firefox installation and -local was not among them. At the moment my workaround is to use Konqueror which does launch remotely just fine, but I am still wondering what possessed the creators of Firefox to make it launch locally when one tries to run it remotely: presumably you already know you can run it on your computer, so if you try to launch it remotely you must have a reason for it!
Thanks anyway for your advice!

---

### Post by Zwack on 2008-03-05
> **ionlimon said:**
> Zwack is right. Unfortunately his solution does not work for me, seems that whatever version of Firefox is installed on the remote server does not accept -local as an option. In fact I ran firefox -h for a list of command line options for the remote firefox installation and -local was not among them. !

Interesting... -local is not listed as an option for me either... But it does work differently when given that option.  "firefox" is not a simple invocation it seems to be a nest of environment setting scripts that do different things depending on the circumstances.

Z.

---

