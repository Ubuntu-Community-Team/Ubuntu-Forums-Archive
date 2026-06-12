---
title: "Tiny ERP doesn't run"
date: 2006-11-24
forum: General Help
---

### Post by worxguy on 2006-11-24
I installed both the Tiny ERP client and server packages using Synaptic in Edgy. The application attempts to start but nothing happens; it just stalls; nothing appears.
thanks for any help,
worxguy

---

### Post by K.Mandla on 2006-11-25
Moved to General Help, in hopes of finding ... well, some help. :D

---

### Post by NRTech on 2006-12-16
> **worxguy said:**
> I installed both the Tiny ERP client and server packages using Synaptic in Edgy. The application attempts to start but nothing happens; it just stalls; nothing appears.
thanks for any help,
worxguy

I just in stalled this application as well with the same result.  On checking some sites there is mention of supporting packages (dependencies) which I don't recall seeing during the installation.
I am also running Edgy.  If I find anything, I'll let you know.  Same to others who have been successful with this, please post your results.

---

### Post by alejandrops on 2006-12-16
install from the sources downloaded from tinyerp.com.
works for me in edgy

---

### Post by NRTech on 2006-12-18
The location of the Ubuntu download/install instruction for Tiny ERP is as follows;

[http://tinyerp.com/documentation/installation/.--.-2.1.9-ubuntu.html](http://tinyerp.com/documentation/installation/.--.-2.1.9-ubuntu.html)

---

### Post by worxguy on 2006-12-20
Thanks for the help guys. I tried your recommendations but didn't get far with any of them. You can tell, from my lack of beans, that I'm not heavy on the tech side. Perhaps it's best to wait until there is better integration with Ubuntu.  And, from what I did see of Tiny, it is major over-kill for my purposes. I was looking for a simple accounting/crm application.
Thanks again,
worxguy

---

### Post by rotten777 on 2006-12-20
You may want to check their forum:
[http://tinyerp.org/forum/](http://tinyerp.org/forum/)

Is there any logging with it? No errors?

---

### Post by tuxman13 on 2007-06-01
I might be stating the obvious...did you setup postgresql with an erp ? If not follow these instruction:
[http://www.tinyerp.com/documentation/installation/.-4.1-setup-a-postgresql-user-and-database.html](http://www.tinyerp.com/documentation/installation/.-4.1-setup-a-postgresql-user-and-database.html)
after that start the tinyerp server and leave it run. Start tinyerp client and setup a new database. Should work, although I had some problems with python 2.5.. everything worked perfectly with 2.4 (just install 2.4 as well and run the server and client with it).  It is quite versatile,  especially if you add more modules to it. If you just need a program for personal accounting try gnucash.

---

### Post by shahjapan on 2007-07-16
If possible please copy & paste the error log.

---

### Post by user2037 on 2007-07-30
It appears there are some issues with how Tiny ERP is packaged. On Fiesty the tinyerp-server package appears to run but the client is unable to connect.

Copying /etc/default/tinyerp-server to /etc/tinyerp-server.conf crashes the server with a parsing error. Apparently Tinyerp-server expects the a different form for the config file.

There is no evidence that a log is created from the server package. One would think it would log to /var/log/tinyerp-server.log. Editing /etc/default/tinyerp-server to redirect stdout and stderr to a file is also fruitless.

Running /usr/lib/tinyerp-server.py directly from bash does produce some output though the client is still unable to connect. Only after starting tinyerp-client from a terminal did the server produce any useful output: 

```

Mon, 30 Jul 2007 10:19:20 INFO:web-services:starting XML-RPC services, port 8069
Mon, 30 Jul 2007 10:19:20 INFO:web-services:You are not using the SSL layer
Mon, 30 Jul 2007 10:19:20 INFO:web-services:the server is running, waiting for connections...
----------------------------------------
Exception happened during processing of request from ('127.0.0.1', 57562)
Traceback (most recent call last):
  File "SocketServer.py", line 464, in process_request_thread
    self.finish_request(request, client_address)
  File "SocketServer.py", line 254, in finish_request
    self.RequestHandlerClass(request, client_address, self)
  File "SocketServer.py", line 522, in __init__
    self.handle()
  File "BaseHTTPServer.py", line 316, in handle
    self.handle_one_request()
  File "BaseHTTPServer.py", line 310, in handle_one_request
    method()
  File "SimpleXMLRPCServer.py", line 446, in do_POST
    self.report_404()
  File "SimpleXMLRPCServer.py", line 497, in report_404
    self.connection.shutdown(1)
  File "<string>", line 1, in shutdown
error: (107, 'Transport endpoint is not connected')
----------------------------------------

```

Most forum posts report success using the tarball and not packages.

---

