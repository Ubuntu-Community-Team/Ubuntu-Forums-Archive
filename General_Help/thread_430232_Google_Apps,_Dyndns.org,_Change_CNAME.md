---
title: "Google Apps, Dyndns.org, Change CNAME"
date: 2007-05-01
forum: General Help
---

### Post by acegolfer on 2007-05-01
Here's the situation

Currently using dyndns.org for dynamic dns hosting. Trying to use Google Apps. 

Instead of using default http://mail.google.com/a/"me".com, in order to use http://mail."me".com, according to Google, I need to change the CNAME record. The following is google's instruction. But I doubt dyndns.org allows this. I can enable wildcard in dyndns so that http://mail."me".com will direct to my machine. What do I have to do to change CNAME destination to ghs.google.com? By the way, I want to achieve this for several CNAMES: mail, calendar, start, www.

> Changing CNAME record

To use the custom URL mail.cho.homeunix.com, you must change the CNAME record with your domain host.

   1.      Sign in to your domain hosting service.
   2.      Navigate to your DNS Management page. The location and name of this page will vary by host, but can generally be found in Domain Management or Advanced Settings.
   3.      Find the CNAME settings and enter the following as the CNAME value or alias:       mail
   4.      Set the CNAME destination to the following address:       ghs.google.com
   5.      Save changes with your domain host and click "I've completed these steps" below.


---

### Post by freebeer on 2007-05-01
I think I saw something on DynDNS's site regarding that.  You might want to check there.

PS... my golf game sucks.  I only got in around 10 rounds last year.  :(

---

