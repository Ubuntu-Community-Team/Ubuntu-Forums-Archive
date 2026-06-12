---
title: "Server Lockup due to Samba Writes of large files"
date: 2007-07-11
forum: General Help
---

### Post by GMU_ninja on 2007-07-11
I setup a Ubuntu server and installed and configured samba.  The server has a RAID5 array setup with 360GB of storage.  I access the server through SSH.  It is working great normally.
I started downloading very large files using Azureus (on Windows) and saving them to a samba share on the server.  (So the file goes from the Internet, to Windows, and then to Ubuntu.  Inefficient, I know, but it is practical for my setup and this application.)
I was downloading a large torrent (24 files, each about 350MB, totaling over 8GB), and my server locked up.  I restarted my server and reconnected the samba shares.  When I started rechecking the torrent, it locked up the server again.  Nothing useful is in the server logs or the samba logs.  It spits out a bunch of garbage to the current tty, but nothing I can read.

If any additional information is required, just tell me how to get it.  I'm not a beginner, but I may not know everything and it would save me time.

Any ideas on where to start would be appreciated.

Ubuntu rocks!

I just got the system lockup again, and this time it said something close to this on the main tty:
<0>  Kernel Panic:  Aieee, killing interrupt handler!

---

### Post by HermanAB on 2007-07-11
Hmm, Linux is usually extremely reliable and Samba is very good too, so I would suspect a hardware problem.  Typically it can be either your ethernet adaptor, RAM or a cooling fan problem, since anything else will typically cause the machine to not work at all.

Have a look at the logs while the transfer is going and see where it stops:
$ sudo tail -f /var/log/messages

If the case feels warm, take the covers off and see if the machine keeps going.

Try the cpuburn test program, or simply cat /dev/random to /dev/null to heat the machine up and see what happens.

I hope that gives you some ideas!

Herman

---

### Post by dfreer on 2007-07-11
> **GMU_ninja said:**
> I started downloading very large files using Azureus (on Windows) and saving them to a samba share on the server.  (So the file goes from the internet, to Windows, and then to Ubuntu.  Inefficient, I know, but it is practical for my setup and this application.)

Inefficient indeed. :(
Sad to say, but your best bet is most likely going to involve cutting windows out of the equation and just use the server to download your files. If you are having problems with that, I can help you there. But if it is impossible to use bittorrent on your server, you might want to try downloading the torrents locally (on the windows machine), and then when they are **done** transfer them to the server.

---

