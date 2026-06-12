---
title: "Help viewing PHP pages"
date: 2007-06-12
forum: General Help
---

### Post by nullfactor on 2007-06-12
When attempting to open PHP pages in the Firefox browser, I get a download dialog that asks if I want to open the PHP file in GEDIT, or if I want to save it to the disk.  I want to view the website!  What am I doing wrong?  How can I change this behavior?

Thanks for the tips.

---

### Post by moron on 2007-06-12
This sounds more like a problem with the site you are viewing than Firefox, most likely what is happening is that the website is giving out a bogus Mimetype for the page which causing Firefox to treat it as something that needs to be handled by an external program.  This could be caused by either a misconfiguration the specific script or by a server wide issue.  

It is doubtful it is something on your local machine that is at fault though it is impossible to say without an example.

Can you provide an example URL to a site that demonstrates this behaviour?

Cheers

---

### Post by nullfactor on 2007-06-12
Uh oh... I think this is going to get ugly. :P  The problem exists on a site that I am hosting for personal reasons on an Apache installation that exists right on my computer.  I am attempting to build a MySQL/PHP application to keep better track of my clients and what they owe me.  

This behavior seems to happen on my own PHP pages that I created and also on my installation of phpMyAdmin.  I wonder if I have a misconfigured Apache server, perhaps?  If that's the case... any idea what configuration that might be?

I am beginning to think it's my setup.  Grrrrrrrrrrrrrrr.

Thanks for the reply!

---

