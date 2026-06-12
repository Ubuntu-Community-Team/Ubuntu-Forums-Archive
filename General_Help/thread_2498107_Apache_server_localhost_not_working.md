---
title: "Apache server localhost not working?"
date: 2024-05-30
forum: General Help
---

### Post by garyed on 2024-05-30
I been using an Apache server for years without any problems to test my sites using localhost & then uploading to my webhost.
Now localhost gives me an error & Apache won't work. It might have happened after one of the typical updates but I can't remember exactly when.  
It gives me this error:
[B]This site can’t be reachedlocalhost refused to connect.
Try:
Checking the connection
Checking the proxy and the firewall
ERR_CONNECTION_REFUSED[/B]
I was thinking of just reinstalling Apache but I don't know the best way to do it without taking a chance of all my web pages being lost.
Any help appreciated.

---

### Post by currentshaft on 2024-05-30
Well, is apache running? (ps -ef | grep apache)

Does localhost resolve to 127.0.0.1? (dig a localhost +short)

---

### Post by garyed on 2024-05-30
> **currentshaft said:**
> Well, is apache running? (ps -ef | grep apache)

Does localhost resolve to 127.0.0.1? (dig a localhost +short)
Yes & yes

---

### Post by garyed on 2024-05-30
I figured the easiest thing to do would be to just reinstall apache but I'm not sure of the safest way to do it since it's already installed.

---

### Post by currentshaft on 2024-05-30
sr

---

### Post by garyed on 2024-05-30
> **currentshaft said:**
> Doubtful that will do anything if it's successfully running as you say.

Try checking your browser proxy settings or taking a packet capture to see where packets are possiby being dropped.

When I looked back at the results of (ps -ef | grep apache), I think it's really not running because the results are:
>  54557   54198  0 21:44 pts/0    00:00:00 grep --color=auto apache  
I originally thought that meant it was running but when I try to restart apache, I get an error code & when i look further it "**Failed to start Apache HTTP Server**".

---

### Post by garyed on 2024-05-30
Well I uninstalled Apache & then installed it again & now my localhost is working but now i have a different problem. 
PHP is not working now & it is shows it as being installed.  php -v shows php 8.2.2 installed but all my php code show up as text in my php pages.

---

### Post by garyed on 2024-05-31
When I uninstalled Apache that I must have deleted some dependencies that are needed for php to work. 
Now when I try to install php it gives me this error:
>  The following packages have unmet dependencies:
 php8.1 : Depends: libapache2-mod-php8.1 but it is not installable or
                   php8.1-fpm but it is not installable or
                   php8.1-cgi but it is not installable
E: Unable to correct problems, you have held broken packages.
 
Anyone have any ideas hoe to fix that?

---

### Post by currentshaft on 2024-05-31
This is why I advised against uninstalling apache.

Try running "sudo apt-get install -f" to fix broken packages.

---

### Post by garyed on 2024-05-31
> **currentshaft said:**
> This is why I advised against uninstalling apache.

Try running "sudo apt-get install -f" to fix broken packages.

I tried that but it didn't help. 
The result was: "0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded"

---

### Post by garyed on 2024-06-01
Well my localhost is working so I solved that problem but since php is not working I think it would be better to start a separate thread for that particular problem.
Reinstalling apache solved the localhost problem so I'm assuming that I deleted something that apache needs when I uninstalled it & that's a different issue to deal with. 
Thanks to currentshaft for all the ideas & attempts to put me on right track.

---

