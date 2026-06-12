---
title: "gfax and jhylafax problem"
date: 2006-07-17
forum: General Help
---

### Post by giucas on 2006-07-17
Hallo,
I have a problem with gfax. I have configured and restarted (has requested) gfax, now when I run the application it crashes with the following errors:

Unhandled Exception: System.ArgumentOutOfRangeException: < 0
Parameter name: length
in <0x000cf> System.String:Substring (Int32 startIndex, Int32 length)
in <0x00075> gfax.Hylafax:get_ip_addr (System.String ipdata)
in <0x00086> gfax.Hylafax:getfolder (System.String folder)
in <0x0000d> gfax.Hylafax:status (System.String queue)
in <0x00089> gfax.Fax:get_queue_status (System.String queue)
in <0x00103> gfax.Gfax:update_queue_status (System.String queue)
in <0x00cff> gfax.Gfax:.ctor (System.String fname, System.String[] args)
in <0x006b8> gfax.gfax:Main (System.String[] args)

I got the same error on 4 different ubuntu 6.06 tls
----------------------------------------------------
I also tryed to use jhylafax but I get the following error:

130 Warning, no inverse address mapping for client host name "stat.<my-public-ip-address>.atlanet.it".
	at gnu.inet.ftp.FtpClientProtocol.connect(FtpClientProtocol.java:1429)
	at gnu.inet.ftp.FtpClientProtocol.open(FtpClientProtocol.java:116)
	at net.sf.jhylafax.JHylaFAX.getConnection(JHylaFAX.java:404)
	at net.sf.jhylafax.SendDialog$2.run(SendDialog.java:313)
	at net.sf.jhylafax.JobQueue$1.run(JobQueue.java:54)
	at java.lang.Thread.run(Thread.java:595)
-------------

Where <my-public-ip-address> are the 4 numbers of my public ip separated by a -

Can you help me?

---

