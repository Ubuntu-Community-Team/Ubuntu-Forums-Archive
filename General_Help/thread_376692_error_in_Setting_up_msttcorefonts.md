---
title: "error in Setting up msttcorefonts"
date: 2007-03-05
forum: General Help
---

### Post by allan10carlo86 on 2007-03-05
I am a new ubuntu user....

and I want to know how to solve this kind of problem in my laptop whenever i want to download something using sudo apt-get install

some error occurs 


it goes like this

Setting up msttcorefonts (1.2ubuntu3) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)



---- Please help me to solve this problem so that I could be able to download new softwares again.

allan10carlo86

---

### Post by chewearn on 2007-03-05
You have invalid entry for the proxy server.  Does your internet connection requires a proxy server?  If yes, enter the correct one.; if not remove them.

Synaptic -> Settings -> Preferences -> Network tab

---

### Post by letubenaiah on 2007-06-16
Thanks!  I was having the same problem and this fixed it!  The only difference was that I had to make my changes from 

System >> Preferences >> Network Proxy

---

### Post by odwyerda on 2008-04-30
I put in my college proxy setting and still get the error,
one thing my proxy asks for my user name and password, firefox asks for it but Ubuntu never does, no idea why, that may be part of the problem but I dont know what to do

---

