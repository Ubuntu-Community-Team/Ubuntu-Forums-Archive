---
title: "Server Related Issues"
date: 2008-06-16
forum: General Help
---

### Post by rockstarrem on 2008-06-16
Hello all,

I'm having a few problems with running my server on Ubuntu Desktop. Here are my issues:

1. I need to make the default port for SSH different than port 22 as my host blocks it.
2. I need to make the Apache port different than 80 because my host blocks it.

I have tried different methods of achieving this but I would like a straight up answer on how to do all of this. I would like to access my computer outside of my home network with a program like PuTTY, but so far I can only successfully connect to my computer on my network. I am running Ubuntu Desktop 8.04. 

Please, I'd really appreciate some straight-forward help with this, it would be much appreciated.

---

### Post by azurepancake on 2008-06-16
To change the default port for Apache, you simply need to edit the /etc/apache2/ports.conf file..

```
sudo nano /etc/apache2/ports.conf
```

..and change the "Listen 80" line to whatever port you want to use. Then restart the Apache server by typing..

```
sudo /etc/init.d/apache2 restart
```

..into a terminal.

For SSH, edit the "/etc/ssh/sshd_config" file.. 

```
sudo nano /etc/ssh/ssh_config
```

..and change "Port 22" to what ever port you want to use. Restart SSH with.. 

```
sudo etc/init.d/sshd restart
```

I hope this helps!

---

### Post by rockstarrem on 2008-06-16
Hello,

Thanks for the reply. The file for Apache doesn't exist. I will test the SSH now though :).

---

### Post by azurepancake on 2008-06-16
> **rockstarrem said:**
> Hello,

Thanks for the reply. The file for Apache doesn't exist. I will test the SSH now though :).

My apologies! The correct path is actually..

```
/etc/apache2/ports.conf
```

..and to restart Apache it is..

```
sudo /etc/init.d/apache2 restart
```

---

### Post by rockstarrem on 2008-06-16
Hmm, I changed the ports to 8080 and asked someone to connect and still nothing. I restarted the server and everything. It works locally though. I have ports 443 and 8080 forwarded and all, any suggestions?

---

### Post by azurepancake on 2008-06-16
You've might of done this already, but just to make sure - when the person tried to connect, did they specify the port when they typed the address? 

Like.. 

```

http://www.website.com:8080

or

http://71.43.112.22:8080

```

If the person trying to connect remotely is getting a "403 error" or some kind of error message regarding permissions, you might need to correct the permissions of your server root.

---

### Post by rockstarrem on 2008-06-16
Yeah, I did that, good thinking though. I don't really know what else to do.

---

### Post by azurepancake on 2008-06-16
> **rockstarrem said:**
> Yeah, I did that, good thinking though. I don't really know what else to do.

I remember when I setup my Apache server quite a bit ago, (port 80 was also being blocked for me as well) I was having permission errors when trying to access it remotely, until I changed the permissions of the server root. The only thing I can think of is giving your server root 777 permissions to test it out.

I am not sure how secure this, but you might want to give it a shot just to see..  

```
sudo chmod 777 /where/you/keep/your/website
```

Thats all I can think of for now, if anything else comes up I'll update. Hopefully someone will come along with the answer you are looking for!

---

### Post by rockstarrem on 2008-06-16
I don't know if this will help but here's what I'm getting when I restart:

> 

dom@dom-desktop:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                [Mon Jun 16 15:37:30 2008] [warn] module php5_module is already loaded, skipping
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Mon Jun 16 15:37:41 2008] [warn] module php5_module is already loaded, skipping
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]


---

### Post by azurepancake on 2008-06-16
It seems there is perhaps a misconfiguration with the FQDN or "Fully Qualified Domain Name".

I did a quick search for any information on this error and came across a site where several people who were having the same problem, fixed it. This is what they did.. 

You edit the /etc/apache2/apache2.conf file and at the end of the file, add:

```

# added servername to avoid the could not determine fqdn error
servername myserver

```

(the "servername" part might already be in your file waiting to be edited. If its commented, uncomment it)

Place your server name in place of "myserver". So in your case, it should be something like..

```
www.mywebpage.com:8080
```

As for the PHP already loaded error, it seems this occurs when there are multiple "LoadModule" directives for 'php5_module' in your httpd.conf file. Removing one of them should fix that particular error.

Let me know how it works.

---

### Post by rockstarrem on 2008-06-17
Hello,

Thanks for the reply, fell asleep early, sorry for not responding earlier. Sadly this didn't work. Why is it I always run into all the trouble :(. Any other ideas?

---

### Post by azurepancake on 2008-06-18
My apologies for the delay. 

If you could post your /etc/apache2/apache2.conf file and /etc/apache2/apache2.conf it might help others and my self find out what Apache's problem is. I'm a bit clueless right now, but perhaps if I can see how things are configured, I can maybe spot out the problem.

---

