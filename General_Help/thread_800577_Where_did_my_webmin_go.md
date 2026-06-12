---
title: "Where did my webmin go?"
date: 2008-05-20
forum: General Help
---

### Post by hooligan36 on 2008-05-20
After I updated my SSH a few days ago, I can not access webmin from my office. I used to be able to. I mainly used it to acces my server and download the occasional file.

Is there a good option for something that would allow me to access all of my files over the internet? Preferably in a graphical interface?

---

### Post by peitschie on 2008-05-20
Hi...

I'm not sure if this is related... but did you have to update any ssh keys (there was a security vunerability that blacklisted a bunch of keys: [http://www.ubuntu.com/usn/usn-612-4)?](http://www.ubuntu.com/usn/usn-612-4)?)  What's the exact error message you get when you try and access webmin?

---

### Post by hooligan36 on 2008-05-20
Yes, I do remember seeing something during the update about keys. When I try to access it I just get a page saying explorere could not open the page, i might want to chek the network settings. 

I can access it from my laptop inside my home network.

---

### Post by peitschie on 2008-05-20
Hrm.

Things worth checking:[LIST]
[*]Are you running any firewalls?  E.g., ufw
[*]Make sure your IP hasn't been changed by your ISP...?
[*]Have you reset the box since the update...?
[/LIST]

Some of these may seem obvious, but it helps us establish a base to work from :)

Once these simple tests have passed, the next question is can you test to see if the box is accessible from the internet (check router settings etc.).  It might be worth temporarily opening an ssh port up to the net and trying to login from that.  You can force the connection to use the external-facing IP by simply connecting to that IP (e.g., ssh 54.172.XX.XX).

---

### Post by hooligan36 on 2008-06-02
Are you running any firewalls? E.g., ufw 
Make sure your IP hasn't been changed by your ISP...? 
Have you reset the box since the update...? 

I have no firewalls up. 

IP is still the same, ( I can access my gallery).

Box has been reset many times.

I can access it from the outside, I don't know how to generate new keys.

---

### Post by peitschie on 2008-06-03
Hmm.  So it sounds like it is specifically the https.  Try resetting your keys using the instructions displayed here: [http://www.debian.org/security/key-rollover/#ssl-cert](http://www.debian.org/security/key-rollover/#ssl-cert)

More information about this issue can be found here: [http://wiki.debian.org/SSLkeys](http://wiki.debian.org/SSLkeys)

Another question.. are you able to access it from the same LAN?

---

