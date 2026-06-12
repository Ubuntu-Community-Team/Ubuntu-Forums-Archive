---
title: "How do I install Apache web server?"
date: 2007-01-26
forum: General Help
---

### Post by scantoria on 2007-01-26
I am new to linux and not sure on how to install programs just yet. I went to apache.org and downloaded version 2.2.4.tar.gz file. is this the correct installation file? How do install it?

Thanks,

Steve

---

### Post by pod25 on 2007-01-26
Go to :
System/Administration/Synaptic Package Manager

Then scroll down until you see Apache2.
Highlight it then right click your mouse, then select Mark For Installation.
Then across the top in the Synaptic Package Manager window select Apply.

Ubuntu then does the rest.

Good luck.

---

### Post by lamego on 2007-01-26
You really should start by reading the official guide:
[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by pod25 on 2007-01-26
> **lamego said:**
> You really should start by reading the official guide:
[https://help.ubuntu.com/](https://help.ubuntu.com/)

Who was that directed at ?

---

### Post by az on 2007-01-26
To install the LAMP stack, see here:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by energiya on 2007-01-26
try [xampp]("http://www.apachefriends.org/en/xampp-linux.html"). It's very easy to install and contains Apache, MySql, PHP, etc.

---

### Post by matthewstory on 2007-01-26
if you're doing it with php make sure you use the mpm prefork package not the worker package:

sudo aptitude install apache2-mpm-prefork

that'll do it.

---

### Post by proxima estacion on 2007-01-26
> **lamego said:**
> You really should start by reading the official guide:
[https://help.ubuntu.com/](https://help.ubuntu.com/)

Thats not really a very helpful comment for someone who is new to Apache or Linux

---

### Post by matthewstory on 2007-01-27
not to be a bit flamy here . . . but you should read the manual to learn how to install programs, and honestly being able to install apache using apt doesnt' mean you'll be able to configure the thing . . . so you should read that as well.  Back in the day that comment would have been rtfm, not the polite way that this user put it.  I don't think it's too much to suggest to someone new to a linux distribution to have them read the manual . . . but maybe that's just me . . . anyway, really, please let's not flame about this.

---

### Post by ~LoKe on 2007-01-27
> **proxima estacion said:**
> Thats not really a very helpful comment for someone who is new to Apache or Linux

Sure it is.  It's about the most help he could get, rather than "type this, download this, and run this."

---

### Post by tagra123 on 2007-01-27
Here's a more quick start quide for most things you may want.

Breezy:
[http://ubuntuguide.org/wiki/Ubuntu](http://ubuntuguide.org/wiki/Ubuntu)

Dapper (Recommended)  (Long Term Support)
[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

Edgy: 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

