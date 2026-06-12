---
title: "Dropbox CLI Client Weird Behavior"
date: 2019-11-18
forum: General Help
---

### Post by Kirk Schnable on 2019-11-18
Hey everyone,

I have Dropbox.com's CLI Linux client running on a headless VM.  It connects to an account with a very small amount of data that is infrequently updated.

Basically the purpose of this server is that my parents have a scanner that can scan-to-FTP, and so I made a VM with an FTP server and a shared folder with each of their Dropbox accounts so they can scan to the "FTP" named their Dropbox, and the files will appear for them.

This setup has worked well for years - being rebuilt occasionally on to newer OS versions as needed.

I noticed the other day some strange bandwidth usage on the Internet connection and tracked it back to the Dropbox VM.  This is literally an internal server with no public access that just sits there running the Dropbox client and VSFTPD, there's nothing else installed and I never login to this server and do anything but occasional updates. 

After a several month stint of not touching it, suddenly it's doing this weird bandwidth usage, like pulling in a few megabit every hour or so.

[IMG]https://iota.lt/d/DnDUkVFytG/sGhUySkz.png[/IMG]

I ran apt updates and rebooted the VM but the behavior continues.

Has anyone seen anything like this before?  I looked through the .dropbox folder but it doesn't seem any of the log files are human readable. 

I might try reinstalling and relinking the Dropbox client but that's all I can think to do to try to resolve this behavior.  If there's anything else I could look at to determine the cause, maybe file a bug report if applicable, I would...

Thanks,
Kirk

---

### Post by jetsam on 2019-11-19
Wild speculation; have a gander at the scanner.  Could it be running some update check and getting caught in an update loop or something?  Everything with a network connection and a sophisticated enough firmware might get up to something when it thinks it's not in use.  It's probably benign, but it's worth investigation.  

Easy test: unplug the scanner for a while and see if the traffic stops.

---

### Post by Kirk Schnable on 2019-11-20
> **jetsam said:**
> Wild speculation; have a gander at the scanner.  Could it be running some update check and getting caught in an update loop or something?  Everything with a network connection and a sophisticated enough firmware might get up to something when it thinks it's not in use.  It's probably benign, but it's worth investigation.  

Easy test: unplug the scanner for a while and see if the traffic stops.

This bandwidth usage is between the FTP server VM and the Internet.  The scanner does not appear to be the source of the usage here.  

Additionally the traffic is all inbound\download, so it's not like the FTP VM is updating files on the Dropbox instance, it's like the Dropbox client is just redownloading file lists over and over again or something.

---

