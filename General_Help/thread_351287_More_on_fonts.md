---
title: "More on fonts"
date: 2007-02-01
forum: General Help
---

### Post by beercz on 2007-02-01
Hi folks

I am developing a website and have set up one of my machines on my LAN to be a LAMP server for testing my site before publication.  On my LAN my LAMP server is Ubuntu and the hosting machine is a Debian LAMP server.

On my Ubuntu server I have installed more true type fonts and can use these fonts in the web pages if a local user is browsing the pages.

However, from another machine on my LAN the pages do not show the fonts.

To install the fonts I did the following:

> At the command line I logged in as root;
I changed to the /usr/shared/fonts/truetype directory [cd /usr/shared/fonts/truetype];
I then made a new directory called extras [mkdir extras];
I then switched to this new directory [cd extras]
I then copied my ttf files into this directory [cp /home/ian/Desktop/* .] (these are the only files on my Desktop);
I then change the file permissions on these files [chmod 644 *];
I then checked the permissions [ls -l]'
[QUOTE]root@ianpc:/usr/share/fonts/truetype/extras# ls -la
total 240
drwxr-xr-x  2 root root   4096 2007-02-01 23:26 .
drwxr-xr-x 27 root root   4096 2007-02-01 23:23 ..
-rw-r--r--  1 root root  31304 2007-02-01 23:24 ETHNOCEN.TTF
-rw-r--r--  1 root root 195544 2007-02-01 23:24 nu_century_gothic.ttf

I then updated my font cache [fc-cache -v -f];
I then logged out and logged into gnome as a normal user.
[/QUOTE]
When I log in to the local machine (the LAMP server) and browse my web pages in FireFox I can see the text on the page using the new fonts.
When I use another machine to browse to the same LAMP server, the same text switches to the default font (Times New Roman I thnk).

Anyone know why I can't see the correctly formatted text when browsing from a remote machine?

Thanks in advance.

---

