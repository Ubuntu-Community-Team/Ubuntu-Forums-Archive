---
title: "Character coding issue"
date: 2008-04-01
forum: General Help
---

### Post by discorsage on 2008-04-01
This seems to be a very odd issue.

I have an old debian server which has a webserver and a simple web page displaying the name "Frédéric".

When I copied this over to my new ubuntu server, it appears as 'Frï¿½dï¿½ric'.

Oddities - it appears this way through a simple editor, pico.  I tried copying the file several ways - wget, ftp, scp, same result.  If I copy the file back to the debian machine, no problems and it is identical (to grep) to the original.

However, if I do 'more file.html', the characters display correctly.  If I use 'less file.html', they are shown as what must be hexidecimals, highlighted <E9> in the case of the é character.

Does anyone know what is causing this and how I might fix it?

Thanks

---

### Post by discorsage on 2008-04-01
Oops I might not have figured it out.

---

### Post by discorsage on 2008-04-01
Ok, I changed /etc/default/locale :

 LANG="en_US.UTF-8"

to 

LANG=en_US

rebooted, and now the file displays correctly in an editor such as pico, and by using 'less'.

However, it still is not displayed correctly in a browser.

one thing to note, when I run the command 'locale' on each machine, 

ubuntu says LANGUAGE=en_US.UTF-8
debian says LANGUAGE=en_US:en_GB:en

Another odd thing is that my etc/enviornment file says :

ubuntu : LANGUAGE="en_US:en_GB:en"
debian : LANGUAGE="en_US.UTF-8"

I had changed them to make ubuntu like debian, but now I've changed it back to see if it anything changes.

So now the only difference I can see is how these characters look through a web browser - and so I suspect it is time to look at the apache2 configuration.

NOTE : 

My ubuntu server is 6.something
I have a ubuntu 7.10 desktop installation and that has the same problem!

---

### Post by discorsage on 2008-04-01
Ok, this is weird.

A friend of mine suggested I add a space between the "html;" and "charset", and that worked for the browser display issue.

<META content=text/html;charset=iso-8859-1 http-equiv=content-type>

I have no idea why.  The debian server is running apache 1.x, the ubuntu server is running 2.x

But this should not be a server issue, right?  The browser either should accept it without a space or a space!!

In conclusion I believe what fixed my problems were :

changing 
/etc/default/locale
/etc/enviornment

from en_US.UTF-8 to en_US

and 
/var/lib/locale/supported.d/locale
from en_US.UTF-8 UTF-8 to en_US ISO-8859-1

Why this works, I do not know, and I am not sure if one of these steps is not needed.  Also, I am not sure if there is anything wrong with the changes I've made.. why isn't this the default?
ALSO - This fix does not fix ubuntu 7.10 desktop edition


-- -- --
On the browser site, setting the default charset to ISO-8859-1 in the apache config seems to help, but I am not exactly sure why.

---

