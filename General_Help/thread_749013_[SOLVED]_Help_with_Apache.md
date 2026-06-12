---
title: "[SOLVED] Help with Apache"
date: 2008-04-08
forum: General Help
---

### Post by XpulseezarX on 2008-04-08
Ok,
So I am using apache for my website hosted on my machine
I'm trying to make a guest book. I have everything working well, until the CGI script
tries to write the new data to the html file. I have changed permissions to to read, write and execute
for every directory and file, but still have no luck. I think, from browsing around forums, that
something is wrong in my httpd.conf. I want public write access to /guestbook/guestbook.html.
What do i need to add to get this accomplished?? 
the cgi script is written by somebody else, but all the variables are correct as far as i can tell.
the guestbook is @
[www.lazerwolf.dyn-o-saur.com/guestbook/guestbook.html](www.lazerwolf.dyn-o-saur.com/guestbook/guestbook.html) if that helps.
from what i can deifier from error logs, /CGI-bin/guestbook.pl cannot open /guestbook/guestbook.html.
The path is correct, and permissions are all read and write. If posting my httpd.conf would help,
I'll do that to.

And if this thread would be better in another category, please bump me!
Thanks alot!

oh, and here's this also

[Tue Apr 08 01:59:19 2008] [error] [client 71.62.27.89] Can't Open /guestbook/guestbook.html: No such file or directory, referer: [http://www.lazerwolf.dyn-o-saur.com/guestbook/addguest.html](http://www.lazerwolf.dyn-o-saur.com/guestbook/addguest.html)
[Tue Apr 08 01:59:19 2008] [error] [client 71.62.27.89] Premature end of script headers: guestbook.pl, referer: [http://www.lazerwolf.dyn-o-saur.com/guestbook/addguest.html](http://www.lazerwolf.dyn-o-saur.com/guestbook/addguest.html)

---

### Post by indytim on 2008-04-08
Just a WAG..  try coding the output path explicitly rather than using the shorthand notation.

IndyTim

---

### Post by XpulseezarX on 2008-04-08
touche good sir. using the actual unix path name worked great! thanks a billion

---

