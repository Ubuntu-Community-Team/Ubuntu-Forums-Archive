---
title: "Port of unity-dodge-windows to 12.10"
date: 2013-01-30
forum: General Help
---

### Post by OpenSourceAl on 2013-01-30
This blog post describes how to make the launcher 12.04 Unity auto-hide when a window is maximized, but otherwise be present (imo the nicest behavior):

[http://www.webupd8.org/2012/05/how-to-get-dodge-windows-and-minimize.html](http://www.webupd8.org/2012/05/how-to-get-dodge-windows-and-minimize.html)

(NOTE: I was not involved in any of the hard work that went into the original script, nor do I have anything to do with the referenced blog; I have merely modified it to work in 12.10. All credit goes to the original author)

Unfortunately it does not work in 12.10

Fortunately there is an easy fix to make it work!

Steps:
1] Follow the instructions in the link above (except don't logout just yet)

2] "sudo gedit" the file /usr/local/bin/unity-dodge-windows and replace it with the following:

[https://gist.github.com/4678022](https://gist.github.com/4678022)

(all this does is replace the gconf edits with dconf edits and a slightly different path)

3] Now logout and log back in again

Enjoy!

---

### Post by OpenSourceAl on 2013-02-01
Update: the publisher of the original script has now updated the debian package so you don't need to mess about to get it working on 12.10

[http://www.webupd8.org/2013/02/how-to-get-unity-launcher-window-dodge.html](http://www.webupd8.org/2013/02/how-to-get-unity-launcher-window-dodge.html)

---

