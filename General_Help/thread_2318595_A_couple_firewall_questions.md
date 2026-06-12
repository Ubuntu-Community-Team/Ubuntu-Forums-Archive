---
title: "A couple firewall questions"
date: 2016-03-27
forum: General Help
---

### Post by sofasurfer on 2016-03-27
1) Is it true that a firewall is not needed in Ubuntu (14.4)? I have a lot of pc slowness and functionality issues and I want to verify that it is not the result of intrusion.

2) I do not like the idea of UFW because of the file editing needs. Getting too old and lazy to mess with that stuff. Is Firestarter (I know, obsolete) better, worse, simpler , harder?

Instead of going through the process of backing up my pc, installing a new OS, reloading my backups, reinstalling extra packages, etc, etc, I thought I would just make sure my system is secure, clean out some junk, scan for viruses and see if it improves things. As far as updating my OS without a clean install, I have never done that and do not want to chance damaging things further.

---

### Post by TheFu on 2016-03-28
If you run services, then you need a firewall. If you don't, then you don't - unless you want to prevent outbound connections (which is smart).

There is only 1 firewall on any Linux system - the kernel firewall. Everything else is just an interface to that. Pick your poison, but don't use unsupported software. Perhaps gufw is what you want?

There is no way for anyone here to know if your system has been hacked.  I would just restore from a backup that happened before the issues began. 

If your system is slow, that is more likely due to bloated software being run. What is bloated .... well, that is highly subjective.  To me, Unity is bloated.  Scanning for viruses will 99% scan for Windows viruses, not Linux ones. It is part of being a good neighbor, but not usually useful to Linux systems.  There could be lots of other reasons for a poorly performing system. Power issues, a failing component, bad networking or bad network configuration.  To determine what is the issue - check the log files.  [http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)

Sounds to me like the first thing you need, if you don't already have it, is to get a good backup and recovery solution working. If you own a computer, you need this. Ensure that versioned backups are part of it, not just 1-time, images.  Images are fine for that "other OS", but a huge waste of storage for Linux systems, IMHO.

BTW - it is "14.04" ... this implies a month - the leading zero is important to computers parsing this stuff.  I'm unaware of any 14.4 release, though humans will quickly assume the answer you mean. ;)  Being exact when it comes to computers is VERY important, as you know.

Good for running an LTS release.  I'm with you on that.

---

### Post by mcduck on 2016-03-28
You pretty much only need a firewall if you:

- run servers that are open to network
- you need to limit access to those servers (say, only allow connections from certain IP addresses)
- those servers lack built-in configuration options for limiting the access in the way you want. Most server software already can do this on their own.
- or possibly if you run a commercial server and need to deal with things like DDoS protection and so on, in which case some firewall tools can help you.
- for limiting outbound connections, in case you can't trust users of the system (blocking access to certain web sites or services)
- for limiting outbound connections because you can't trust software installed on the system (which brings up the question of why wold you knowingly install untrustworthy software in the first place? Doing so would compromise your security, firewall or no firewall...)

So, more than likely, you don't need a firewall. Unless it's a commercial server, or some rare special case. for everything else it's a question of configuring any installed server software correctly, and  only installing software from sources you can trust.

What comes to slow system, rather than worrying about firewall or security issue, I'd start by trying to find out what's using the resources. Is something using lots of CPU time or eating through your RAM? I there any repeating error messages in your system log files? Are you running correct drivers for your graphics card etc?

---

### Post by HermanAB on 2016-03-28
If your system is slow, run top to see what is going on.  Also check your DNS performance with dig.  Maybe one of them is lame.

---

### Post by sofasurfer on 2016-03-28
> **TheFu said:**
> If you run services, then you need a firewall. If you don't, then you don't - unless you want to prevent outbound connections (which is smart).

There is only 1 firewall on any Linux system - the kernel firewall. Everything else is just an interface to that. Pick your poison, but don't use unsupported software. Perhaps gufw is what you want?

There is no way for anyone here to know if your system has been hacked.  I would just restore from a backup that happened before the issues began. 

If your system is slow, that is more likely due to bloated software being run. What is bloated .... well, that is highly subjective.  To me, Unity is bloated.  Scanning for viruses will 99% scan for Windows viruses, not Linux ones. It is part of being a good neighbor, but not usually useful to Linux systems.  There could be lots of other reasons for a poorly performing system. Power issues, a failing component, bad networking or bad network configuration.  To determine what is the issue - check the log files.  [http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)

Sounds to me like the first thing you need, if you don't already have it, is to get a good backup and recovery solution working. If you own a computer, you need this. Ensure that versioned backups are part of it, not just 1-time, images.  Images are fine for that "other OS", but a huge waste of storage for Linux systems, IMHO.

BTW - it is "14.04" ... this implies a month - the leading zero is important to computers parsing this stuff.  I'm unaware of any 14.4 release, though humans will quickly assume the answer you mean. ;)  Being exact when it comes to computers is VERY important, as you know.

Good for running an LTS release.  I'm with you on that.

Good info. Thanks.

---

