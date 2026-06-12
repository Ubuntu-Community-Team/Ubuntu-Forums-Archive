---
title: "How to Install Bluefish Editor"
date: 2006-07-26
forum: General Help
---

### Post by tripwire45 on 2006-07-26
I can't locate this package in Synaptic and using apt-get doesn't help, either. Bluefish isn't an obscure piece of software, it's a simple text editor for web development. Using apt-get in Debian installs Bluefish right away. Any clues about how to install it on Ubuntu 6.06?

---

### Post by Jagot on 2006-07-26
Bluefish is in the universe repo which you need to enable to obtain it.  See here:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Or here:

[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

You can also get it in Add/Remove (bottom of the Applications menu).  Go to Programming and then select 'Show unsupported applications'.

---

### Post by tripwire45 on 2006-07-26
Thanks, Jagot. Worked like a charm. :)

---

### Post by stopsatgreen on 2006-08-01
I have Bluefish 1.04 on my system but want to get 1.05 which has been available since February. However, in Synaptic only version 1.04 is available; how do I get 1.05?

---

### Post by punkass on 2006-08-01
oops - not sure how to delete a post

---

### Post by punkass on 2006-08-01
> **stopsatgreen said:**
> I have Bluefish 1.04 on my system but want to get 1.05 which has been available since February. However, in Synaptic only version 1.04 is available; how do I get 1.05?

I just grabbed it from the Debian servers.

[http://ftp.us.debian.org/debian/pool/main/b/bluefish/bluefish_1.0.5-2_i386.deb](http://ftp.us.debian.org/debian/pool/main/b/bluefish/bluefish_1.0.5-2_i386.deb)

and used Gdebi to install it.

And it worked fine.

---

### Post by tripwire45 on 2006-08-01
Tell me more about Gdebi. Apt-get tells me that I have the latest version on board but it looks like it's supposed to be a GUI interface. Where does it live?

EDIT: Nevermind. I downloaded the new Bluefish package and Gdebi was the default installer. Worked like a charm. :D

---

### Post by stopsatgreen on 2006-08-02
OK, great, thanks.

But out of interest, why wouldn't Synaptic offer the latest version even if it's been out for 5 months?

---

### Post by stopsatgreen on 2006-08-02
Oops! Duplicate :(

---

