---
title: "Problem with Ubuntu server"
date: 2015-05-28
forum: General Help
---

### Post by g8vkv2 on 2015-05-28
Hello,

I'm a newbie on this forum and I have an odd problem.

Background ...

I have a home network made up of

Ubuntu 14.04 headless server (web and mail server and NAS)
iMac
Macbook Air
PC
various tablets
a few Raspberry Pis

So, not too large, but big enough to keep me busy

My ISP is Free (a French ISP) and the router is a "Freebox" - it's nothing special, but has the advantage of allowing a certain degree of tweakability.

Problem ...

The problem is the Server. It's a "homebrew" box with an ASRock J1600, decent amount of RAM, SSD + HDDs, and the OS (14.04) is always kept up to date. It's been in place for about 12 months and has proved utterly reliable.

The problem started about 2 weeks ago, when it appeared that the Freebox router "froze". The WiFi was present but not joinable. I couldn't access the Internet from the iMac (which is hard cabled into the router). The problem cleared after a period of time (ranging from 15mins to an hour).

After much investigation, I discovered that the heart of the problem was the Ubuntu server. It would, from time to time, generate traffic which appeared to saturate the LAN.

Today I hooked up a screen and keyboard and found the following during one of these "lockout" periods.

1. The server was "up", but with a CPU utilisation of 30% (which is way above its idle %)

2.  The process which was using the CPU was called zer0 (thats "zer" with a number "0")

There were 2 instances of process zer0 running. I killed them both and the lockout stopped.

So, my question if you like (after all this rambling) is - does anyone know what zer0 is? I can't find any evidence of its existence.

Many thanks in advance for any ideas.
g8vkv

---

### Post by etescartz on 2015-05-28
I don't think that was a legitimate process. I think your web and mail server and NAS got hacked.

Considering the services that you mentioned running on your Ubuntu server , chances are it was used for spam email delivery. 
Depending on software selection and the security that you already set up (or didn't) , to keep operations safe, you could try scanning the root partition with antivirus and malware freely available.

My suggestion in this case would be to update all packages on your server and give ClamAV, spamassassin , rkhunter and Maldet a try.

Maybe even backup the important files and do a complete reinstall of the OS and setup the security software and reinstall the email services only after that is all configured properly.

Good Luck!

---

### Post by dragonfly41 on 2015-05-28
Here are some tips to get more information on a process .. [http://www.cyberciti.biz/tips/linux-report-current-working-directory-of-process.html](http://www.cyberciti.biz/tips/linux-report-current-working-directory-of-process.html)

Or use strace.

---

### Post by mastablasta on 2015-05-28
i would first check what the process was actually doing and try to identify it before nuking the whole thing. It might be part of a program you installed. I checked the web and there are quite a few zer0 things. could be file deletion software, email cleaner etc etc.

since we do not know how you set it up it's hard to say what you have. so first unplug form internet, backup the files and then search what the process is actually doing.

if oyu got hacked and did not do any backups then you are in for a long one. or nuke the whole thing and start over. secure it properly.

---

### Post by g8vkv2 on 2015-05-28
Thanks folks!

I have to say I wasn't thinking about malware (not seeing the wood for the trees?)

I did a scan and found two files infected with tsunami.b, which I have now zapped.

Thanks again.

---

### Post by mastablasta on 2015-05-28
you might want to read this: [http://hardenubuntu.com/](http://hardenubuntu.com/)

---

### Post by g8vkv2 on 2015-05-28
Thanks for the read.

I do many of those. Some I'm loath to do (for example disable NFS, because my Raspberry Pi farm uses the server to store its files)

The odd thing is, I have Clam running, but something still managed to infect. I also have Fail2ban and all that kind of stuff running.

What I might do though, is to have a cron job run each day to do a scan and report any problems by mail. At least then I can pick things up quickly.

Anyway, thanks again for catalysing my brain!
g8vkv

---

