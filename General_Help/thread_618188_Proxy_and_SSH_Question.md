---
title: "Proxy and SSH Question"
date: 2007-11-20
forum: General Help
---

### Post by kpkeerthi on 2007-11-20
This is not an issue that is related ubuntu perhaps. So mods.. please feel free to move this topic to appropriate forum if required.

Here goes...

I'm behind a proxy at work and access to most of the websites are blocked. I'm lucky that I can access ubuntuforums (still). I could not ftp to any of the internet servers either. I want to setup an SSH server on my home PC and be able to ssh into it from my work PC. But how do I know for sure that the proxy at work does allow SSH traffic (port 22)? Unfortunately I could not ask this to my network admin. So guys... throw some light. 

Thanks.

---

### Post by 1/0 on 2007-11-20
You could just try to connect from work. If its closed you will get an error. 

I'd say your best choice is to use an anonymizer, such as:

* [http://anonymouse.org/anonwww.html](http://anonymouse.org/anonwww.html)
* [http://www.hidemyass.com/](http://www.hidemyass.com/)
* [http://www.shadowsurf.com/](http://www.shadowsurf.com/)

That is, if sites like those aren't already blocked...

---

### Post by Prospero2006 on 2007-11-20
Ok, here is what you do:

Set your ssh server at home to listen on port 443. 
Your work proxy probably allows traffic to pass through the proxy
on port 443 because that is an encrypted port. The proxy can't distinguish
between what is and what isn't web traffic on that port. It just sends the packets
back and forth.

So, once your ssh server is listening on 443, you have to set this parameter in your 
/etc/ssh/ssh_config file
```

ProxyCommand connect-proxy -H (Your.Proxy.ip):(proxyport) %h %p


```

(You'll probably have to apt-get install connect-proxy.)

Ok, now you're sshing through the proxy on port 443. 

The next step is to set up a squid proxy of your own at home
and tunnel your web requests to use that instead of the work proxy.

Here is the script I 'would' use to create that tunnel, but of course I would never do so at my own work. 

```

usr/bin/screen autossh -M 0 -i /home/pros/.ssh/id_rsa -v -L127.0.0.1:5555:localhost:3128 pros@www.webloguniverse.com:443 > /home/pros/report.out

```
Here is what that does:
It creates a port on the machine executing the script (127.0.0.1) In this case 5555. It connects that port directly to port 3128 on my home machine which is running my own squid proxy. It does this by tunneling the traffic through port 443.
You can now set your browser to use 127.0.0.1:5555 as the proxy.

It also uses autossh and screen which keep the connection persistent in case it drops and runs it in the background.
(Of course you'll need to generate an id_rsa and id_rsa.pub keypair for passwordless authentication.)
I hope that helps.

Pros

---

