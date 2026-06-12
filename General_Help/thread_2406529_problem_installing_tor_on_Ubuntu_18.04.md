---
title: "problem installing tor on Ubuntu 18.04"
date: 2018-11-21
forum: General Help
---

### Post by hunterkasy on 2018-11-21
I am trying to get through the process of installing tor on my computer. I get to this step of adding the key and I get an error.

gpg2 --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | apt-key add -

tyler@tyler-HP-Compaq-8200-Elite-CMT-PC:~$ gpg2 --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | apt-key add -
E: This command can only be used by root.

this is what I get by using sudo:

tyler@tyler-HP-Compaq-8200-Elite-CMT-PC:~$ sudo gpg2 --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | apt-key add -
gpg: WARNING: unsafe ownership on homedir '/home/tyler/.gnupg'
E: This command can only be used by root.

---

### Post by wildmanne39 on 2018-11-21
I believe tor has been dead for a long time or not updated but you can install and use tor browser.

[https://www.torproject.org/projects/torbrowser.html.en](https://www.torproject.org/projects/torbrowser.html.en)

---

### Post by logix2 on 2018-11-22
Tor is not dead, and they maintain an active Debian / Ubuntu repository, which has packages newer than the ones available in Ubuntu. You can use this alternative command to add the Tor repository key:

```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89

```

I recently wrote on my blog about [installing Tor]("https://www.linuxuprising.com/2018/10/how-to-install-and-use-tor-as-proxy-in.html") and setting everything up in Ubuntu. If I'm not allowed to post this, please remove this line, but I think it might help @[COLOR=#000000]hunterkasy.[/COLOR]

---

### Post by wildmanne39 on 2018-11-22
This is what I was talking about:

[https://blog.torproject.org/plain-vidalia-bundles-be-discontinued-dont-panic](https://blog.torproject.org/plain-vidalia-bundles-be-discontinued-dont-panic)

I have not looked at that in years, I switched to tor browser and never looked at it again, if it works for you I am glad.

---

### Post by logix2 on 2018-11-23
Only Vidalia was discontinued, the Qt GUI used to control Tor. Yes, now it's a bit harder to use as you must control it from the command line, for example to get a new identity there's no simple button and you must reload the Tor systemd service ("sudo systemctl reload tor"). Tor Browser is just for web browsing, but you need Tor if you want to "torify" some application.

---

### Post by c0def52 on 2019-08-21
> **logix2 said:**
> Tor is not dead, and they maintain an active Debian / Ubuntu repository, which has packages newer than the ones available in Ubuntu. You can use this alternative command to add the Tor repository key:

```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89

```

I recently wrote on my blog about [installing Tor]("https://www.linuxuprising.com/2018/10/how-to-install-and-use-tor-as-proxy-in.html") and setting everything up in Ubuntu. If I'm not allowed to post this, please remove this line, but I think it might help @[COLOR=#000000]hunterkasy.[/COLOR]

I've tried to execute the command and got the following error output:
```

sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89
Executing: /tmp/apt-key-gpghome.9EywPAnYmA/gpg.1.sh --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89
gpg: packet(13) too large
gpg: read_block: read error: Invalid packet
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```
[B]
UPD

[/B]I executed ```
**sudo **gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | **sudo **apt-key add -
```
It generated gpg: WARNING: unsafe ownership on homedir but processed with OK

---

### Post by QIII on 2019-08-21
@c0def52 --

Rather than hijacking a thread, particularly an old one, please start your own thread.  Although symptoms may be similar, underlying causes are often quite dissimilar.  Please feel free to reference this thread in your new one.

Closed.

---

