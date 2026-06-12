---
title: "PHP and cURL (paypal php sdk) [HELP!]"
date: 2005-08-17
forum: General Help
---

### Post by Icaros on 2005-08-17
According to my phpinfo(), I have cURL installed and enabled.  

I'm trying to install the paypal php sdk, and when I run the install, it tells me cURL is not installed.

The only thing I noticed is that on the phpinfo(), where all the ./configure --with's are, there is no --with-curl.

I used apt-get to install php4 for ubuntu by following the guides, and if I were to use ./configure --with-curl, where would the original source be located?  

I've download php 4.3.10, and tried using ./configure but without any luck.  (It seems to work, but when I view phpinfo(), it still isn't listed under ./configure -- and yes I restarted apache2.)

I'm stumped on this one... anyone know what to do?

EDIT: Being a noob to linux, I was doing the ,/configure correctly but forgot to follow up with 'make' and 'install'.  Works fine now.

---

### Post by Brian Puccio on 2005-08-17
Did you try to apt-get install this package:

[http://packages.ubuntu.com/hoary/web/php4-curl](http://packages.ubuntu.com/hoary/web/php4-curl)

---

