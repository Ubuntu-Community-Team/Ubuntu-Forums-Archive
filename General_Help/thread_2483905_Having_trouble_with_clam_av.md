---
title: "Having trouble with clam av"
date: 2023-02-12
forum: General Help
---

### Post by dorasmith24 on 2023-02-12
I'm having trouble with updating clamav.

First it says my ClamAV installation is outdated.

I read what to do about that and it seems to have more than one version installed.

I ran      sudo apt purge --autoremove clamav* clamav-base* clamav-daemon* clamav-freshclam* clamdscan* libclamav9* libtfm1*
and getting same exact thing.  It's telling me my version is the one I installed four years ago.

    Then I run whereis clamav and it seems not to find it, but I run where is freshclam and it tells me 

freshclam: /usr/local/bin/freshclam /usr/local/etc/freshclam.conf

so I run 

sudo apt-get purge --autoremove freshclam.*

and it says it removed it, but then when I do whereis freshclam it still finds two versions of it.




AND it's also telling me it can't download main.cvd from database.clamav.net and getpatch:  Can't download main-59.cdiff from database.clamav.net
Giving up on database.clamav.net...
Sun Feb 12 22:07:33 2023 -> Update failed. Your network may be down or none of the mirrors listed in /usr/local/etc/freshclam.conf is working. Check [https://www.clamav.net/documents/official-mirror-faq](https://www.clamav.net/documents/official-mirror-faq) for possible reasons.

The faqs don't say anything about it.   My network is not down.   

First how do I actually get rid of all installed versions of clamav? 

Then why can't I connect to the download site.

---

### Post by dorasmith24 on 2023-02-13
I manually removed each file.  Then I found more files in another directory and removed them.  
Then I successfully installed the current version in Synaptic.  But in terminal I couldn't find or start anything.   Clamscan was supposedly locked.  
I tried rebooting.  Didn't help.
Then I tried Clamtk.  Not intuitive, and not fast, either - but it is working.  Even though in terminal nothing works.

---

### Post by monkeybrain20122 on 2023-02-13
What do you need it for? It is a useless bloatware. You don't need antivirus on Linux and moreover it scans Windows virus and is terrible at that too.

---

### Post by Frogs Hair on 2023-02-13
> First it says my ClamAV installation is outdated. This is why I abandon Clam years ago.As stated, Clam only scans for Windows exploits so I let Windows programs do that work if sharing suspect files which rarely if ever comes up. There are Linux exploits in the wild but, home users are rarely affected and effective programs to scan for them are proprietary and not free.

---

### Post by SeijiSensei on 2023-02-13
Unless you are maintaining a mail server, or a file server with irresponsible users running Windows clients without antivirus, you don't need ClamAV at all.

---

