---
title: "Apache2 - some general questions..."
date: 2007-02-12
forum: General Help
---

### Post by JimTDI on 2007-02-12
Hi Everyone!  A couple of general Apache2 questions, as Apache2 is new to me (as of this last weekend)!  Was running Apache 1 before...

We've got a site of our own, and we also host 5 virtual hosts (named based) right now, all seems to work pretty good so far on Apache2.

According to what I have seen and read, the setup for the "default" site shows the document root as /var/www.  Does that mean I should put the files that make up "our" main site, into /var/www/ (html files and all?), and then the virtual hosts into their own directories, off of /var/www/theirsite1, /var/www/theirsite2, etc...

Right now I have ALL sites including ours in their own directories, with the document root of the "default" pointing to /var/www/oursite.  Something just doesn't feel right to me to dump a bunch of html and image files and such for our main site right into /var/www itself...

Am I rambling... ??  :-)

Also, I'm trying to call a cgi-bin web page hit counter on our main site, and on the main pages of a few of those we host, but am having problems.  The Apache2 error log shows the cgi-bin directory is missing from /var/www/oursite/cgi-bin

Does each site really need it's own cgi-bin directory?  I thought all sites should be able to share the cgi files in /usr/lib/cgi-bin, but am I wrong?  Does each site need a stanza in their virtual host for cgi-bin, or should their configuration read it from the default site if it's not present in their virtual host settings?

Thanks for any help you can give!  Ubuntu rocks!!

---

### Post by kidders on 2007-02-12
Hi there,

> **JimTDI said:**
> Does that mean I should put the files that make up "our" main site, into /var/www/ (html files and all?), and then the virtual hosts into their own directories, off of /var/www/theirsite1, /var/www/theirsite2, etc...Personally, I wouldn't do that, as it would effectively mean that /var/www/theirsite2 would be accessible via [http://localhost/theirsite2/](http://localhost/theirsite2/), which would be strange.

> **JimTDI said:**
> The Apache2 error log shows the cgi-bin directory is missing from /var/www/oursite/cgi-binAfaik it's highly dangerous to put your cgi-bin directory below your web root like that. I would feel much happier if your web root was /var/www/oursite/htdocs or something. (ie your CGI & document root directories are in different directory trees.)

> **JimTDI said:**
> Does each site really need it's own cgi-bin directory?Yes. No. Well... sort of. There's no particular reason each site's CGI directory (assuming you even want one for each site) can't be the same, but you still have to configure it independently for each site.

I hope that helps.

---

### Post by JimTDI on 2007-02-14
That helps alot kidders - thank you for your reply!

---

