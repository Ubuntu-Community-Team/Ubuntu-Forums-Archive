---
title: "Problem serving html files with apache2.2"
date: 2008-06-13
forum: General Help
---

### Post by CireSnave on 2008-06-13
Hi.

  I've got an Ubuntu Server install which I loaded apache 2.2 on top of.  It works great when serving html docs from /var/www/apache2-default/whatever.html but when I try to serve files from subdirectories under that point like /var/www/apache2-default/mydir/whatever.html my browser just sits there doing nothing.. I've checked the directory and file permissions and made all of the directories and files readable by anyone which should eliminate any permission related issues.  Is there something I should look for in the apache config files to allow access to subdirectories?  I've been a linux user for a few years now and can muddle my way through most problems but apache's config is a bit of a beast so I'm somewhat at a loss here.  If anyone can offer suggestions of what I should check they would be appreciated.  Thank you in advance.

Alright...It's been several days since I originally posted this and still there have been no responses so I'll see if adding more information helps.. The main web site served by my server mentioned above is [http://k7hkl.webhop.net](http://k7hkl.webhop.net)  There's almost no content there yet.  It's run by and for my father.  That page resides in /var/www/apache2-default/ ...  I wanted to create a separate page for my own web development so I created a directory under apache2-default called eric and another directory under that called test.  In this test directory I created an html file called test.html.  The only thing on this html file currently are two images.  By directly specifying each of the directories in <directory> tags in my apache config I have it loading the html file but the jpeg images in that same directory (/var/www/apache2-default/eric/test/*.jpg) do not display.  I have double checked all of the file names including capitalization several times now.  I have rewritten the whole web page several times.  I have re-ftp'd the images to that directory several times.  I have even loaded the images directly into image editors on my ubuntu server to make sure they weren't corrupted in some way.  What can I be doing wrong?  This all started because I couldn't get the html files to load.. Now I can't get the images on those web pages to load.  The browser just sits there trying to load....  Please.. Someone must have had this problem.. Can ANYONE give me another idea of where to look?  I can load the html file by going directly to [http://k7hkl.webhop.net/eric/test/test.html](http://k7hkl.webhop.net/eric/test/test.html) and I see the placeholders come up for the two images.  That's as far as it gets.  It just sits there loading.


- Eric

---

### Post by arvevans on 2013-04-04
Did this get resolved?  
If not, send me an email and we can work on it together.

---

### Post by oldos2er on 2013-04-04
Old thread closed.

---

