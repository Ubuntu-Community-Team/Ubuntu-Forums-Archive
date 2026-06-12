---
title: "program installed but ubuntu reports program not installed"
date: 2018-10-01
forum: General Help
---

### Post by wilsonsalchanik on 2018-10-01
Executing the program 'certbot' returns a message:
-----------------------------------------------------------

```
Command 'certbot' not found, but can be installed with:

sudo apt install certbot
```
-----------------------------------------------------------

So try installing by running [U][I][B]sudo apt install certbot which returns:

[/B][/I][/U]which returns:

------------------------------------------------------------


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
certbot is already the newest version (0.26.1-1+ubuntu18.04.1+certbot+2).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

------------------------------------------------------------



How can I verify certbot is installed and if it is installed launch it?

If it is not installed then how do I convince Ubuntu to install it?

Thanks

Wilson

---

### Post by #&amp;thj^% on 2018-10-01
Your request is a bit vague to me so forgive me>>>but to be clear.
> Certbot is a user-friendly automatic client that fetches and deploys SSL/TLS certificates for your web server. It is an EFF's tool which is used to obtain certs from Let's Encrypt and auto-enable HTTPS on your server. In short, it acts as an official" Let&#8217;s Encrypt client" or &#8220;the Let&#8217;s Encrypt Python client.&#8221;  It utilizes the Automated Certificate Management Environment (ACME) to automatically deploy free SSL certificates that are trusted by the majority of the browsers. Hence, it works for any other CAs which supports ACME protocol.
Here is a couple of useful links to read over for a better understanding.

[https://linoxide.com/linux-how-to/install-letsencrypt-ubuntu/](https://linoxide.com/linux-how-to/install-letsencrypt-ubuntu/)
and
[https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-18-04)
EDIT: I forgot to add how to verify if installed:
```
certbot --version
```

---

### Post by wilsonsalchanik on 2018-10-01
certbot --version reports:

```
Command 'certbot' not found, but can be installed with:

sudo apt install certbot
```


**so it seems it is not installed. Now how does one force the
install given the normal method of:

```
sudo apt install certbot
```

kicks back the message:

```
certbot is already the newest version (0.26.1-1+ubuntu18.04.1+certbot+2).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Thanks[I][B]
[/B][/I]Wilson

---

### Post by deadflowr on 2018-10-01
Look at
```
apt-cache policy certbot
dpkg -l certbot
```
Post back results.
Use code tags please.

---

### Post by wilsonsalchanik on 2018-10-01
Success!  

Both 
apt-cache policy certbot
dpkg -l certbot

indicated the package was installed. 

Don't know why I did not stumble into it earlier
but it finally dawned on me that if:

                    sudo apt install cerbot 

will install the package then:

                    sudo apt remove certbot

would remove it. Volila. 

Both:    
apt-cache policy certbot
dpkg -l certbot

now indicated the package was no longer installed.

Re-installed and all is well.  

Thank you all.

Wilson

---

### Post by deadflowr on 2018-10-01
Nice.
If it works, then please [URL="https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"]mark this thread as solved
[/URL]
An aside, it would have be nice to see the output, in particular for the dpkg -l certbot command, as it might have shown the current status.
No matter, though, good show.

---

