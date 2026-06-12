---
title: "Error installing PHP5/Apache2"
date: 2005-06-08
forum: General Help
---

### Post by benbalbo on 2005-06-08
Hi All!

I've followed the installation instructions at [http://www.ubuntulinux.org/wiki/PHP5FromSource](http://www.ubuntulinux.org/wiki/PHP5FromSource) to get PHP5 working with Apache2, and while I got it working without problems on my laptop, my desktop is throwing this error when starting apache:

>  * Starting web server (Apache2)...
Syntax error on line 6 of /etc/apache2/httpd.conf:
Cannot load /usr/lib/apache2/modules/libphp5.so into server: /usr/lib/libxslt.so.1: undefined symbol: xmlNewDocPI

I've scoured google, this and other forums for more info but can't find anything.

Now the laptop was a fairly new install, whereas the desktop previously had apache2, php4 and php5 installed from source, which I then removed.

I made the mistake of trying to apt-get install mysql-4.1.10 over a manual install of 4.1.9, so then had to apt-get uninstall, clean up and reinstall. I think this might have broken things.

Now the error message points to something xml/xsl related, but trying to apt-get install libxml, libxslt and libxml packages (and *-dev), apt tells me I've got the latest versions already.

Any pointers would be most appreciated, as I'm running out of ideas now.

Many thanks in advance!

Ben

---

### Post by benbalbo on 2005-06-10
I found an alternative way around this. I found [an article on installing php5 from a debian source package](http://ubuntuforums.org/showthread.php?t=7964).

As explained in that thread, it's built tor apache1.x, so you need to edit the debian/rules file and change any reference to apsx to apsx2, and you also had to remove the switches -with-db2 and --with-ming=shared,/usr.

I now have php5 running fine.

Hope this helps someone.

Ben

---

