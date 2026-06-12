---
title: "AMP Installation..."
date: 2007-04-30
forum: General Help
---

### Post by SilentTim on 2007-04-30
... is going very badly!

I would like to have Apache, PHP and MySQL installed. I have Apache 2 installed, I think I have PHP installed, but the two can't seem to talk to each other.

Apache works fine, I can see localhost and put pages in my DocumentRoot, but if I try and browse to a php file, it wants to save it as something else and won't display it in firefox.

When I look in Synaptic Package Manager, I have the following installed:

apache2 and related packages
libapache2-mod-php5

In the past, I've uncommented or added 

```

AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

```

but that doesn't seem to work in this case...

does anyone have any suggestions?

---

### Post by paparucino on 2007-05-01
> **SilentTim said:**
> .

does anyone have any suggestions?
Try with this howto [http://doc.gwos.org/index.php/XAMPP](http://doc.gwos.org/index.php/XAMPP)











UAResolved

---

