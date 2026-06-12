---
title: "Proftpd logon URL"
date: 2007-04-02
forum: General Help
---

### Post by stepheny on 2007-04-02
Hi,

I expect that this is a really dumb question because no-one else seems to have the problem but here goes anyway. 

I have installed  Proftpd without any problems and when I use 0.0.0.0 as my IP address I get to the FTP server, but I don't know what URL to use to access my FTP server. My Linux box has the URL "fredbloggs.myftp.org" and the FTP-shared file is in the /home directory, what do I use as an URL for the FTP server.

Thanks in advance for any advice.

---

### Post by atomic0x on 2007-04-02
Is it possible that your router or firewall is blocking ftp traffic?  Check to make sure that you've got ports 20 and 21 open for tcp traffic.  If you have a router you should also check that it knows to forward ftp traffic to your machine.

Another thing.  Are you able to access any other services such as ssh or http at that url?

---

### Post by stepheny on 2007-04-02
Thanks for the quick reply. I am not using port 21 but another port for security reasons and this port is open in my firewall. 

What I need to know is where should I point my FTP client to access the server? 

I thought of "ftp.fredbloggs.myftp.org" or "fredbloggs.myftp.org/ftp-shared" etc but these are wrong. I am sure I am missing something simple here but what is the URL of my FTP server?

---

### Post by stepheny on 2007-04-02
Sorry I didn't answer your second question, yes I can reache my Webpage at [http://fredbloggs.myftp.org](http://fredbloggs.myftp.org).

---

### Post by stepheny on 2007-04-02
Thank you AtomicOx, you were right it was a firewall problem.

---

