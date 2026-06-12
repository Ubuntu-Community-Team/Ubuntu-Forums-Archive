---
title: "How to syncronize email between Hotmail/Yahoo email and Evolution/Thunderbird?"
date: 2007-08-22
forum: General Help
---

### Post by tjoel99 on 2007-08-22
Windows Outlook live provides a fantastic feature in which Hotmail and Outlook email are completely sync'd up.  You delete an email or move a document in Outlook, and it happens in Hotmail; you create a folder in Hotmail, and it shows up in your Outlook folder, etc.

I want to do this in Linux.  Can you help me?

---

### Post by Chymera on 2007-08-22
just click the evolution icon and configure it... You can use any mail client you want, just make sure you have pop3 access (gmail  and yahoo.de provide that feature for free .... yahoo.com/co.uk/es/ie have it too, but only for premium accounts). Just follow the pretty instructions :-P

---

### Post by g2g591 on 2007-08-22
how bout for hotmail?

---

### Post by jdrodrig on 2007-08-22
I think you are thinking on IMAP format not POP3....right?

---

### Post by forrestcupp on 2007-08-22
If you don't have POP3 support in your Yahoo, you can use YPOPS to make it have POP3.

---

### Post by senor_smile on 2007-08-24
So, I still don't see a solution to the original question.  

Does anyone know of a way to synchronize with a ...@hotmail.com account, the same way outlook/outlook express does in windows?

---

### Post by theonlykman on 2007-09-09
If I understand [this]("http://en.wikipedia.org/wiki/Comparison_of_webmail_providers") correctly, neither yahoo nor hotmail/windows live allow you to sync with a client unless you dish out the cash. So unless you have a premium hotmail account, you won't be able to do it in linux (unless you have outlook or windows live mail desktop virtualized somehow).

---

### Post by angelman99 on 2007-11-05
I have a HotMail Premium account (had it for years and got sick of it timing out) and I put in the details from the MS website

Under Server Information, in the Incoming mail server (POP3) box, type **pop3.live.com**. In the Outgoing mail server (SMTP) box, type **smtp.live.com**.

Server Port Numbers, in the Incoming server (POP3) box, type 995. In the Outgoing server (SMTP) box, type 25. Under both Incoming server (POP3) and Outgoing server (SMTP), select the This server requires an encrypted connection (SSL) check boxes, and then click OK.

So Receiving is
**pop3.live.com:995**

Sending is
**smtp.live.com:25**

And I get:

Error while performing operation.

Could not connect to smtp.live.com: Input/output error

I did a ping -a smtp.live.com and used that ip address :25 that got the same result.
I do get my incoming mail messages though. Just can't send.
So close.

---

### Post by mahousaru on 2007-11-05
If you can't get pop or imap to work,you can grab email off Hotmail if you have an old account with hotway

You need to install xinetd first which is a super server that controls other services, basically it intercepts a connection checks to see if it is a service it manages, if you are using tcp wrappers checks the host allow list to see if its allowed then if fires up the service.  By default all services are disabled when you install it.

```
sudo apt-get install xinetd
```

then u need to install hotway

```
sudo apt-get install hotway
```

Then create a conf for hot way

```
sudo gedit /etc/xinet.d/hotwayd
```

paste in the following code

```

service hotwayd                                                                 
{                                                                               
only_from = 127.0.0.1                                                           
disable = no                                                                    
type = unlisted                                                                 
socket_type = stream                                                            
protocol = tcp                                                                  
wait = no                                                                       
user = nobody                                                                   
groups = yes                                                                    
server = /usr/bin/hotwayd                                                       
#server_args = -p http://proxy:8080                                             
port = 110                                                                      
}   

```

This uses the standard 110 port so if you run your own pop server you will need to change it to a better value.

restart xinetd with

```
sudo /etc/inid.d/xinetd restart
```

Create an account in your mail client with normal details but pointing to the server 127.0.0.1 and port 110

Do you need a firewall?  No because the definition says it can be only access from the lo interface.

---

### Post by Nesmontu on 2007-11-05
Despite trying lots of stuff (like hotway), I never got hotmail working in Evolution.
For Thunderbird though there's an easy-to-use, easy-to-configure plugin for different webmail accounts, including hotmail to be found here [http://webmail.mozdev.org/](http://webmail.mozdev.org/)
Instructions on that site are pretty straightforward -- good luck :)

---

### Post by angelman99 on 2007-11-06
Is this line right?

```
sudo gedit /etc/xinet.d/hotwayd
```

This worked for me

```
sudo gedit /etc/xinetd.d/hotwayd
```

And the line to restart xinetd with

```
sudo /etc/inid.d/xinetd restart
```

Should maybe be

```
sudo /etc/init.d/xinetd restart
```

Tip: Don't drink and type.


And now I get:

> Error while performing operation.

Welcome response error: Operation now in progress

---

### Post by mahousaru on 2007-11-06
Opps sorry for the typos was a bit tired that day.

Check the messages log when you try to restart xinetd to see if there are any errors.  Are you running your own pop3 server?

---

### Post by angelman99 on 2007-11-07
I'm new at this, I have no idea how to check whether I have a POP3 server running.
Which raises another question (being from a Windows background) where do I find the list of programs that are being loaded at startup(/boot)?

---

### Post by mahousaru on 2007-11-07
You can check your services with
System, Administration, Services

Ubuntu doesn't have one installed by default so you need to have installed it.  At a guess I would say you don't have one running.  Have you checked the messages log for any errors when you restart xinetd?  You can check with 

System, Administration, System Log

---

### Post by angelman99 on 2007-11-07
confirmed - no POP3 service running.

The Log Viewer won't let me copy and paste :(

Log has reading configuration file line 14,28,26,25,26,14
Log also has the following entries twice:
removing chargen
removing daytime
removing discard
removing echo
removing time

But does have anything indicating an error.

---

