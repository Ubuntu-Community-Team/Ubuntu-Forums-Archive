---
title: "Description of &quot;upstart&quot;?"
date: 2006-10-26
forum: General Help
---

### Post by steve196 on 2006-10-26
Is there a real concrete description of the "upstart" feature, what  configuration files it loads, what the syntax of those files is, what parts are compatible with init etc.?
I have seen the wiki page but it does not have any concrete info.

---

### Post by PriceChild on 2006-10-26
As far as i know... we're still using the old init scripts... just in a different order/timing.

Upstart will be fully implemented in feisty with its own scripts.

---

### Post by eczarny on 2006-10-26
You can head over to [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/) to read up on Upstart. From what I can understand from the release notes Upstart is in fact a feature of Edgy.

Although, it hasn't been fully implemented to match the original specification.

---

### Post by steve196 on 2006-10-26
There is a "specification" page on the site you mentioned, but it does not actually specify anything.

---

### Post by az on 2006-10-26
Upstart is really young.  You really should ask on the upstart-devel maililng list if the stuff in /usr/share/doc/upstart is not satisfactory.  I see there is no upstart-doc package....

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=upstart&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=upstart&searchon=names&subword=1&version=edgy&release=all)

And while you are at it, please drop off any documention you come up with onto the wiki (or the docteam).  That would be highly appreciated.

If you want, just drop it all into a page and post that page url here.  I'll help format it.

On a side note, I *really* like the chosen name for this tool.  The init system has been in use for eons and no one dared touch them (don't fix it unless it is broken).  I think a lot of people are overwhelmed by all the different names and subdivision in the software we run (X, gnome, cups, udev....)   It's a name like this that really hits the nail on the head in describing not only what the thing does, but puts into perspective the golas of the project.

---

