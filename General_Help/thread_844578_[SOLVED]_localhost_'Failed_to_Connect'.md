---
title: "[SOLVED] localhost 'Failed to Connect'"
date: 2008-06-29
forum: General Help
---

### Post by smandoli on 2008-06-29
Ububtu 8.04 Hardy Heron.  I can browse the Internet, but I can't browse localhost.  For example, I can view "http://www.recoveryman.com/".  But if I try "http://localhost/" or "http://125.0.0.1/", I receive:

```
Failed to Connect
Firefox can't establish a connection to the server at localhost.
Though the site seems valid, the browser was unable to establish a connection ...
```

I'm using Firefox with "No proxy" set.  It doesn't matter if I switch to "Auto-detect proxy settings" or "Use system proxy settings."  I have been trying to set up Squid and DansGuardian.  Presumably the localhost problem is something I caused trying to do that.  But currently, boot up does not launch Squid and DansGuardian is disabled.  

When I run "ping localhost -c 3", I receive a half-dozen lines including this encouragement:
```
3 packets transmitted, 3 received, 0% packet loss
```

My httpd.conf file is empty.  So I add "ServerName localhost" and reload Apache2, but no change.  

When I enter "hostname", I receive "localhost".  When I run "cat /etc/hosts", I receive:
```
127.0.1.1 antec
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
127.0.0.1 localhost
```

In var/log/apache2/error.log.1, recent notes:
```
Suhosin-Patch configured -- resuming normal operations
Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
```

Can you help me fix this?  (Ignore my signature, I'm on Hardy version.)

---

### Post by manfer on 2008-06-29
Look this instructions. It could be the problem but not sure.

----------------------------------------------

If you get this error:

apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

then use a text editor such as "sudo nano" at the command line or "gksudo gedit" on the desktop to create a new file,

sudo nano /etc/apache2/conf.d/fqdn

or

gksu "gedit /etc/apache2/conf.d/fqdn"

then add

ServerName localhost

to the file and save. This can all be done in a single command with the following:

echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn

----------------------------------------------

Instruction taken from ubuntu help on Apache, mySQL, PHP:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by smandoli on 2008-06-29
I put the file in place and it looks good.  Then ran a reload on Apache2.  No change.

---

### Post by manfer on 2008-06-29
Could it be that in hosts you have 127.0.0.1 localhost under ipv6?

Move it up, as first line in file

And other question is it wright, 127.0.1.1 antec? Is antec the computer name where you have the server? Maybe it must be 127.0.0.1 antec.

---

### Post by smandoli on 2008-06-29
Thanks for replying.  I don't know how to change the hosts order.  antec is the name and I have the idea it is correct to make it 127.0.1.1.

---

### Post by manfer on 2008-06-29
First do a backup of file /etc/hosts:

prompt:~$ **sudo cp /etc/hosts /etc/hosts.backup**

Then you have to edit that file as root with any text editor.

prompt:~$ **sudo gedit /etc/hosts**

and you move the line:

127.0.0.1 localhost

which is at the end of document by now to the top of it. Then close file saving changes.

Restart computer to make the hosts load with the changes (maybe a simple close session and login again would be enough but not sure so restart).

---

### Post by smandoli on 2008-06-29
No change.  Thanks again for your counsel.   I am signing off for this evening but I will look forward to my next session.

---

### Post by lswb on 2008-06-29
If you are running a firewall make sure port 80 is open. I don't know how many times I've slapped myself after realizing what I thought was some configuration problem was just due to firewall settings!

---

### Post by smandoli on 2008-06-29
Is that found in /etc/apache2/ports.conf? That says "Listen 8000" at the moment.

---

### Post by manfer on 2008-06-30
I think that should be Listen 80.

---

### Post by editrix on 2008-06-30
> **smandoli said:**
> 

When I enter "hostname", I receive "localhost".  When I run "cat /etc/hosts", I receive:
```
127.0.1.1 antec
```

I had the same problem. In my case, that first line in /etc/hosts had to be changed to:

```
127.0.0.1 localhost.localdomain localhost computername
```

---

### Post by lswb on 2008-06-30
"Is that found in /etc/apache2/ports.conf? That says "Listen 8000" at the moment."

"I think that should be Listen 80."

Yes, 80 is the default port number for web servers. 8000 is non-standard but is often used for a web server configured to run by a user. If a firewall is running, it also must be configured to allow incoming traffic on the port being used.

Try pointing your browser at [http://127.0.0.1:8000](http://127.0.0.1:8000) and see what happens.

---

### Post by manfer on 2008-06-30
> **lswb said:**
> "Is that found in /etc/apache2/ports.conf? That says "Listen 8000" at the moment."

"I think that should be Listen 80."

Yes, 80 is the default port number for web servers. 8000 is non-standard but is often used for a web server configured to run by a user. If a firewall is running, it also must be configured to allow incoming traffic on the port being used.

Try pointing your browser at [http://127.0.0.1:8000](http://127.0.0.1:8000) and see what happens.

I think it is possible that the listen port could be one of the things that changed the installation of the proxy Squid which was installed and then remove as said by user on first post. If that is the case I would reconfigure apache listen port to 80 (the default listen port for a web server).

---

### Post by smandoli on 2008-06-30
I feel sure this is it.  I will be able to try "Listen 80" (and editrix' advice also) in about 6 hours.

---

### Post by smandoli on 2008-06-30
Hey Team, "Listen 80" got it and I can mark this thread Solved.  Thanks !!!

My next post will be about how to have LAMP and DansGuardian filtering ... I have all the pieces, but just haven't been able to configure things.

---

