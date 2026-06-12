---
title: "Apache2 &amp; Drupal - Virtual Sites Not Working on Boot"
date: 2013-09-08
forum: General Help
---

### Post by fherman on 2013-09-08
I am using both Drupal6 and Drupal 7 with same problem.  When the system boots, apache2 starts, but appears to not redirect for drupal multiple sites.  When the browser points to any of the virtual sites, only the apache2 dummy page comes up.  If I then restart apache2 with:
 service apache2 restart

then the virtual sites work.  I have looked in the logs and see no errors, and it looks like the browser is correctly trying to access the drupal pages.  The mod_redirect apache2 module is enabled.

As a workaround, I put the above restart command in the /etc/rc.local file, and doing so allows the drupal virtual websites to work properly on boot.

I'm not sure if this is an apache2 or a ubuntu problem, because prior to moving the server from fedora to ubuntu I did not have this problem.

Any suggestions where to look?

Tnx

---

### Post by tgalati4 on 2013-09-08
I think it is a timing problem.  Drupal requires a database (mysql, postgres, whatever you set up).  Perhaps in Fedora, the database spun up faster.  So if you have a database timeout, then drupal doesn't launch properly and you have nothing to serve.  By rebooting apache2, you have given more time for the database to bootup so that Drupal can now start serving pages.  Look in /var/log for the timecode when the database spins up and compare it to the apache start time, which is also in the logs.  

If this is the problem, then you would have to put a *sleep 4* in the apache2 boot script in /etc/init.d to allow a little more time for the database to be ready for query.

---

### Post by fherman on 2013-09-08
I tried your suggestion, and it worked.

However, since I need to make sure that I am using the stock packages, I reverted back to my workaround.

I did think it was a timing issue, but I didn't think about the use of the sleep command.

Thank you

Fred

---

### Post by Kevin_Arnold on 2013-09-08
With the information you've given I would have told you there is no way the suggested fix would work... but it sounds like it did.

I do want to just correct something, though. If Apache were properly pointing to your drupal sites at boot but MySQL just wasn't up and running yet, you'd get a drupal error message... not the Apache "It Works!" page.

Knowing this, I'd suggest that you have some other issue at the base of this. I can't explain why restarting Apache or waiting for a while before getting it all set up fixes it, though.

---

