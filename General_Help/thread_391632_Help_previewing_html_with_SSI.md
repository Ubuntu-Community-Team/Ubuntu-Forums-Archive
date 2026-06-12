---
title: "Help previewing html with SSI"
date: 2007-03-23
forum: General Help
---

### Post by dr_d12 on 2007-03-23
Hi; I need some advice on the best way to proceed.

...the setup:

I'm using Ubuntu to make a website. My old one was built with frames (it's been a while). I'm using simple html with an external css stylesheet set up to act like frames.

I want my site navigation on the side of each page, but don't want to edit each page each time I add a page to the site. So, I think I want to use a basic SSI like:

<div id="rightcontent">
<!--#include virtual="./navigation.html"-->
</div>

...the problem:

but now I can't drop my .html file on the browser to preview my progress. 

...the question:

I guess I need a web server to process the SSI for previewing. Ubuntu runs my laptop, XP on my desktop "work computer". I think these are my choices:

Install LAMP on my laptop for previewing. (would this even work?)
or
Turn the desktop into a dual-boot XP / Ubuntu desktop and install LAMP, then FTP the site to the server over the LAN for previewing.
or
Try to install a server on XP Home. I'm trying to get away from this windows stuff though.

Thanks,
Dave

---

### Post by dr_d12 on 2007-03-23
Google helped me find a package called XAMPP 
[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

I downloaded it and came back to this forum and found these installation / setup instructions:
[http://www.ubuntuforums.org/showthread.php?t=223410&page=3&highlight=Xampp](http://www.ubuntuforums.org/showthread.php?t=223410&page=3&highlight=Xampp)

Files dropped in ~/public_html now show up on my browser under [http://localhost/username/](http://localhost/username/)
SSI was enabled by default.

I can't believe how easy that was.
sweet.

---

