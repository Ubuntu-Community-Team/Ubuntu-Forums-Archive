---
title: "Does ClamAV Auto update through System Update?"
date: 2007-10-26
forum: General Help
---

### Post by mmilitia9 on 2007-10-26
I think I just installed ClamAV... It just says "Virus Scanner" under Accessories.. Anyway.. When I open it and go to Help, Update.. it says I have to be root.. but I dont have a root password.. So does the definitions/signatures get updated when the system gets notifed theres an update or what?

Thanks,

Dominick



(Please dont post anything about not needing to depend on a virus scanner.. I do.  Send lots of files to Windows users)

---

### Post by mahousaru on 2007-10-26
If you want the updates to update for u, u need 

```

sudo apt-get clamav-data

```

Personally I just have a cronjob that does a freshclam -quiet

---

### Post by mmilitia9 on 2007-10-26
dominick@unknown:~$ sudo apt-get clamav-data
[sudo] password for dominick:
E: Invalid operation clamav-data


... Now what?

---

### Post by zaphod777 on 2007-10-26
I thought that this is why we run lunix we don't have to worry abou t this stuff right?

---

### Post by ThrobbingBrain66 on 2007-10-26
> **mmilitia9 said:**
> dominick@unknown:~$ sudo apt-get clamav-data
[sudo] password for dominick:
E: Invalid operation clamav-data


... Now what?

He meant ```
sudo apt-get install clamav-data
```

[quote=zaphod777]
I thought that this is why we run lunix we don't have to worry abou t this stuff right?[/quote]

As he stated, he sends lots of files to Windows users.  In this case, not using a virus scanner would be irresponsible.

---

### Post by mahousaru on 2007-10-26
@ThrobbingBrain66 - Hee hee thanks for the correction *blush*

We Linux users are a caring lot, we could sit in our ivory towers lauding over the poor windows users drowning in the never ending sea of malware, but we invest a little bit of our resources in helping keep them safe :)

---

### Post by mmilitia9 on 2007-10-26
I ran what he said to run.. Now in Applications, Accessories... "Virus Scanner" disappeared?  

Ughh..

---

### Post by mahousaru on 2007-10-26
Hmmm

Fire up synamtic, using System, Administration, Synamtic Package Manger

Search - clamav

Make sure clamav is installed.  It looks like clamav-data removes freshclam (makes sense as u are updating with ubuntu instead), but it might have removed clamav as well

---

### Post by mmilitia9 on 2007-10-26
Nope.. it's installed. 

Clamav
Clamav-base
Clamav-data
lib-clamav2

Are all green.

Now.. when I went to applications and "Add/remove" I typed in "Virus scanner"  That was once installed.. now it isnt..

Im confused exactly what the command above even did actually.. lol 

Soo, what do I do to make sure I have a properly working manually update/scanning clamav?

---

### Post by mahousaru on 2007-10-26
Well to check from the command line bring up terminal and run

```

clamscan -V

```

The version should be:

man, version 2.4.4, 2007-02-12

as of this post.

If I was you just re-install virus scanner again so you have the front end.  check to see using symnatic to see if clamav-data is still there.  If not and freshclam is back instead, use that to update using a cron script.

---

### Post by mmilitia9 on 2007-10-26
Known viruses: 161242
Engine version: 0.91.2
Scanned directories: 0
Scanned files: 0
Infected files: 0
Data scanned: 0.00 MB
Time: 2.319 sec (0 m 2 s)


The only reason why it wouldnt update before is because it would ask me for a root passwork that i dont have.. so it was confusing.. but right now I'm going to try have clamav-data and redown the Virus scanner thing from add/remove.. brb

---

### Post by mmilitia9 on 2007-10-26
It wont allow me to install the front end with clamav-data installed.  I just installed freshclam again.. 

How do I update the definitions?  I just tried help>Update.. but it asks for root

---

### Post by mmilitia9 on 2007-10-26
Anyone got any ideas?  All I wanna freaking do is make sure ClamAV is fully updated with the latest virus defs?  

You would think it was as simple as Help, Update.. but it asks for root and I don't want to make a root password.. cuz I assume thats bad to have one since Ubuntu took the approach of not making u make one.. Anyway.. how do I update the damn thing?

---

### Post by Maestro23 on 2007-10-26
Have you checked: [http://www.clamav.org/support/](http://www.clamav.org/support/)

---

### Post by mahousaru on 2007-10-26
Personally I have a script in cron.daily that just updates it automatically with no intervention on my part. Scrpts sitting in:

/etc/cron.daily
/etc/cron.hourly
/etc/cron.weekly
/etc/cron.monthly 

all run as root so you don't need to put a password in.  well that is the theory since I only just added clamav so can't say for 100% until the next updates come out ;).  All I can say it used to run swimmingly on my opensuse box

First lauch edit with root rights

```

sudo gedit /etc/cron.daily/freshclam.sh

```

copy n paste the following into gedit

```

#!/bin/sh

/usr/bin/freshclam --quiet

```

Set the script as executable

```

chmod 755 /etc/cron.daily/freshclam.sh

```

Wait until you see the defs updated on the clamav site, check your version with:

```

clamscan --version

```

---

