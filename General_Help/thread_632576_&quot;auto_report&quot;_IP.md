---
title: "&quot;auto report&quot; IP?"
date: 2007-12-05
forum: General Help
---

### Post by uc50_ic4more on 2007-12-05
Hello -

My efforts to advocate for ubuntu have resulted in about 15 of my web clients adopting it. I administer their systems remotely, but 5 of of them have DSL internet connections, and their IP's change every time they turn their computers on. Logging in via SSH/ SFTP and/ or VNC cannot be done, therefore, unless and until I direct my clients to whatismyip.com and report their IP back to me.

Is there a way to have my client's machines send me their IP upon boot? I am thinking a simple shell script ought to do the trick, but I am unsure of exactly what I even *want* to have happen:

- I am behind a router, so if my client pings me it will appear nowhere on a log file on my Mac, and I do not think my router logs are any way I want to spend any amount of time perusing through over morning coffee.

- I thought about enabling a smtp daemon on the client systems and having the systems send a blank message to myself, but both their and my ISP's block emails sent from "localhost" or "127.0.0.1".

My other option, I guess, I to sign all of my clients up at a site like no-ip.com, a dynamic DNS service; then install the client software on my clients systems (which auto updates their IP to the site) and check into the site when I need to administer their systems, but I really wanted to avoid that dependence on a third party.

Does anyone know, then, of perhaps a client/ server program whereby I'd have a daemon listening on a certain port and perhaps my clients machines would send out their IP? Is there another way? A shell script I can have the systems run at boot time?

Thank you!

- uc50ic4more

---

### Post by eggdeng on 2007-12-05
#!/bin/bash
zenity --info --text=" `wget [http://checkip.dyndns.org/](http://checkip.dyndns.org/) -O - -o /dev/null | cut -d: -f 2 | cut -d\< -f 1 ; /sbin/ifconfig eth0 |grep inet\ adr | awk '{ print $2} ' |cut -d: -f 2 `"

I took this from a forum thread some time ago but can't find the original to credit it.

---

### Post by uc50_ic4more on 2007-12-05
> **eggdeng said:**
> #!/bin/bash
zenity --info --text=" `wget [http://checkip.dyndns.org/](http://checkip.dyndns.org/) -O - -o /dev/null | cut -d: -f 2 | cut -d\< -f 1 ; /sbin/ifconfig eth0 |grep inet\ adr | awk '{ print $2} ' |cut -d: -f 2 `"

I took this from a forum thread some time ago but can't find the original to credit it.

eggdeng -

Thank you for the quick reply!

However this script would merely print out a window with the client's IP on the *client's machine*, correct? I need to get the client's IP over to *me*. Instead of "print $2", is something else I can have done?

I also came across this on a Mac forum; a perl script:

```
#!/usr/bin/perl

$my_email = "your\@email.net";

`wget http://checkip.dyndns.org`;
`mail -s Your_ip_address $my_email < index.html`;
`rm index.html`;
```

... But uses "mail", which I assume refers to Apple Mail? On an Ubuntu system, would I have to install (or start at boot) Postfix and replace "mail" in the above script w/ "postfix"?

---

### Post by gazR on 2007-12-05
Hi

I'm in a similar situation - I look after servers for a few of my clients who use DSL with Dynamic IP's.

The best solution that I've found is using a service such as [no-ip]("http://www.no-ip.com") / [dyndns]("http://www.dyndns.com") / [everydns]("http://www.everydns.com") to provide a fully qualified domain name ( e.g. myclient.no-ip.com ) for each of my clients.

The ubuntu repos have an app (no-ip) that you install on each machine and it reports the current IP back to no-ip or whoever you use, and they keep the DNS records upto date.  After that you just connect to myclient.no-ip.com regardless of that actual IP.

hope that helps some.

---

### Post by uc50_ic4more on 2007-12-05
> **gazR said:**
> Hi

I'm in a similar situation - I look after servers for a few of my clients who use DSL with Dymanic IP's.

The best solution that I've found is using a service such as [no-ip]("http://www.no-ip.com") / [dyndns]("http://www.dyndns.com") / [everydns]("http://www.everydns.com") to provide a fully qualified domain name ( e.g. myclient.no-ip.com ) for each of my clients.

The ubuntu repos have an app (no-ip) that you install on each machine and it reports the current IP back to no-ip or whoever you use, and they keep the DNS records upto date.  After that you just connect to myclient.no-ip.com regardless of that actual IP.

hope that helps some.

gazR -

Thanks - Do you recommend any of the above mentioned DDNS services over the others? Is uptime ever a factor?

---

### Post by gazR on 2007-12-05
I've used all of the three on and off for a few years, and from an uptime point of view haven't really noticed any difference.  Some of the offer free and extended pay-for services, others free for the first 5 domains then pay for more et, but they are all much of a muchness.  If your clients use DSL routers you may want to check if they have a DDNS client built in, if so you don't need any software installed on the ubuntu boxes and you just setup port forwarding on the routers.

At the minute I use no-ip for no other reason than I could remember my user account for that one!

---

### Post by uc50_ic4more on 2007-12-05
Thank you for your help, folks - I am now set up at no-ip.com and all seems to be working well!

---

### Post by coastdweller on 2008-02-04
I've just recently opened a can of worms whereby the ability to use an external server running Linux and setting up a ddns server/client relationship between the local network and the remote static server (I run remote cpanel machines).

I say opened a can of worms as its yet another thing I have to learn... linux pft! so much to learn hehe.

---

### Post by tr333 on 2008-02-08
> **uc50_ic4more said:**
> 

I also came across this on a Mac forum; a perl script:

```
#!/usr/bin/perl

$my_email = "your\@email.net";

`wget http://checkip.dyndns.org`;
`mail -s Your_ip_address $my_email < index.html`;
`rm index.html`;
```

... But uses "mail", which I assume refers to Apple Mail? On an Ubuntu system, would I have to install (or start at boot) Postfix and replace "mail" in the above script w/ "postfix"?

You could convert that perl code directly to a BASH/SH script (.pl to .sh) by changing the first line to "#!/bin/bash" or "#!/bin/sh" and removing the backtics '`' and the semicolons ';' from each line.

```

#!/bin/sh

MY_EMAIL="your@email.net"

wget http://checkip.dyndns.org/index.html
mail -s Your_ip_address $MY_EMAIL < index.html
rm index.html

```

The *mail* command used in this is just a commandline program for sending and receiving mail on a unix-based system.  You can install it on ubuntu with the *mailx* package in synaptic.
```
$ man mail
```

---

