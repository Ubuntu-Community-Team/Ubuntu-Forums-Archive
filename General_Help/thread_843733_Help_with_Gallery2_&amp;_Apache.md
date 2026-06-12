---
title: "Help with Gallery2 &amp; Apache"
date: 2008-06-28
forum: General Help
---

### Post by caseyg on 2008-06-28
Hello All, I have apache2, gallery2, mySQL, PHPadmin all running successfully on my server. I'm new to gallery2. How do I configure my webpage to view gallery2 albums? Is this something written in html per say pointing to the album from a button on the website??? Thanks in advance.

---

### Post by fragos on 2008-06-29
Most gallery programs creat an HTML gallery website with the images you gave it. The home page of this site is linled to like any other page. For example:

<a href="http://fragostech.com/album.html">My Album</a>

---

### Post by epedersen on 2008-06-30
So far I've found that it's easier to link my main page to a separate Gallery site, such like:

[http://thisisnotarealsite/gallery2](http://thisisnotarealsite/gallery2) 

To do this, you will probably want to create a symbolic link within your /var/www folder that points to the Gallery 2 installation /usr/share/gallery2 ...

eg:  $   sudo ln -s /usr/share/gallery2 MyPictures

This would allow people to browse your Gallery2 site as: 

[http://thisisnotarealsite/MyPictures](http://thisisnotarealsite/MyPictures)

---

### Post by epedersen on 2008-06-30
Further to my previous post (which you can safely ignore), this may be helpful:

[http://ubuntuforums.org/showthread.php?t=788065](http://ubuntuforums.org/showthread.php?t=788065)

---

