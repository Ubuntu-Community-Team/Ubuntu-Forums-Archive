---
title: "ClamTk outdated"
date: 2013-03-20
forum: General Help
---

### Post by motorcity909 on 2013-03-20
Hi all

I noticed today that the antivirus definitions in ClamTk are showing as 'outdated' - see attached clam-screenshot.png

I've tried to run **freshclam** in a terminal but get this output:

```
xxx@xxx:~$ sudo freshclam
[sudo] password for xxx: 
ClamAV update process started at Wed Mar 20 11:51:16 2013
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.97.6 Recommended version: 0.97.7
DON'T PANIC! Read http://www.clamav.net/support/faq
main.cvd is up to date (version: 54, sigs: 1044387, f-level: 60, builder: sven)
WARNING: getpatch: Can't download daily-16682.cdiff from db.local.clamav.net
WARNING: getpatch: Can't download daily-16682.cdiff from db.local.clamav.net
WARNING: getpatch: Can't download daily-16682.cdiff from db.local.clamav.net
WARNING: getpatch: Can't download daily-16682.cdiff from db.local.clamav.net
WARNING: getpatch: Can't download daily-16682.cdiff from db.local.clamav.net
WARNING: Incremental update failed, trying to download daily.cvd
WARNING: Can't download daily.cvd from db.local.clamav.net
Trying again in 5 secs...
```

Any clue on how I get this updated please?

Thanks
Dave

---

### Post by r.stiltskin on 2013-03-20
Have you tried completely removing and then installing clamav?  That should get you the latest definitions, although the version warning will remain since 0.97.6 seems to be the latest version in Ubuntu repos.

---

### Post by motorcity909 on 2013-04-14
An update came through via the daily Xubuntu updates and that updated Clamav to 0.97.7 but the definitions still show as 'outdated'.

I removed it and re-installed it via the Software Centre and still 'outdated'.

Any advice would be much appreciated - or an alternative AV?

Many thanks
Dave

---

### Post by cwsnyder on 2013-04-14
First, **clamtk** is a package for the GUI only.  **clamav** is the main (command-line only) package called by **clamtk**, and **freshclam** is the command-line portion of the package used to update the **clamav** definitions.

You should attempt a re-installation of **clamav**, not **clamtk**, as **clamtk** is dependent on **clamav**, but **clamav** is not dependent on **clamtk**.

Otherwise, check the FAQs at [https://github.com/vrtadmin/clamav-faq/blob/master/faq/faq-cvd.md](https://github.com/vrtadmin/clamav-faq/blob/master/faq/faq-cvd.md) as suggested in the error message you are getting.

---

### Post by motorcity909 on 2013-04-15
Thanks cwsynder.  I removed both via Synaptic and then reinstalled but still the definitions showed as 'outdated'

Next, I download the latest daily.cvd file from [http://www.clamav.net/lang/en/](http://www.clamav.net/lang/en/) and overwrote the existing daily.cvd in var/lib/clamav with that newly downloaded file.

I then opened Clam and the definitions now show as 'current'.  Sorted!

Cheers
Dave

---

### Post by r37u2a49ci on 2013-04-25
Re:ClamTK outdated

Thanks cwsynder. I downloaded the latest daily.cvd file from [http://www.clamav.net/lang/en/](http://www.clamav.net/lang/en/) and overwrote the existing daily.cvd in var/lib/clamav with the newly downloaded file. I then opened Clam and the definitions now show as 'current'. Thanks Dave for your post also.:P

---

