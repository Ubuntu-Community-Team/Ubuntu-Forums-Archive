---
title: "Enabling PHP4 With Apache"
date: 2007-02-24
forum: General Help
---

### Post by kebbelj on 2007-02-24
By blind luck, I somehow got Apache enabled at 127.0.0.1, but I can't run PHP programs either at the command line or inside Firefox

~ I've installed  php4  with Synaptics
~ I've installed the php4 module for Apache with Synaptics
 ~ The httpd.conf file can find and load the libphp4.so 

The command line says *command not found *when I try running a program and Firefox opens a dialog box that asks  *What should Firefox do with this file?*.


P.S.Guide to answering-- I'm totally new to Ubuntu, but I'v been using Yellowdog, Redhat, and Fedora Linux for years as a hobby. I'm neither novice nor guru.

---

### Post by chggr on 2007-02-24
Why did you install php4 and not php5?

Your problem should be solved by installing the package libapache2-mod-php4 and php4-cgi, which is the module that enables php support on apache2 and cgi support.

---

### Post by kebbelj on 2007-02-24
I have folders for Apache and Apache2. When I did* apache -v,*, the response told me I was running 1.3.1. Since php5 won't work with 1.3.1, or so I've been told, I downloaded php4.

However ... when I rebooted my computer to do something on the Windows side. Two things happened. **First,** I noticed a shutdown message for Apache 2 as the computer shut down. **Second,** when I rebooted again in Linux about twenty minutes later, php4 was running.

Question 1. Is it possible to have two versions of Apache running side-by-side?

Question 2. How do I get Apache 2 running and configured for php5? I already have php5 downloaded.

---

### Post by chggr on 2007-02-24
You will use the synaptic package manager to see which versions of Apache you have installed.
Just go to System -> Administration -> Synaptic Package manager and search for the keyword apache. If you have both apache and apache2 installed, i recommend that you uninstall apache and keep apache2. Then you can search for the keyword php and install php5 and the apache2 module for php.

---

### Post by ~LoKe on 2007-02-24
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Apache_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Apache_HTTP_Server)

---

### Post by kebbelj on 2007-02-24
1. I deleted apache and php4
2. To be safe, I reinstalled apache 2 and php5
3. i restarted apache2 from the command line. It worked, and so did PHP5.

How do I set up Apache so it starts up every time I boot Linux from this dual-boot laptop? (It already boots automatically for me in XP.)

Thank you for your help so far.

P.S. I went to [http://ubuntuguide.org/wiki/Ubuntu_E...he_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu_E...he_HTTP_Server). The page had lots of peripheral stuff (graphics, links, etc.), but no content and this error message ... 
[B]

(There is currently no text in this page) [/B]

---

### Post by ~LoKe on 2007-02-24
You copy and pasted the text.  Just click on the link, or right click -> open in a new tab.

---

### Post by annda on 2007-02-24
@kebbelj: apache most probably starts at boot. how do you know it doesn't? do you see an error message when you type localhost or 127.0.0.1 in the address line of your browser?

---

### Post by kebbelj on 2007-02-24
When I visited 127.0.0.1, I got an error message instead of having the page load.

I did an apache restart at the command line and the page did load. Perhaps I was too hasty. Maybe I should have rebooted my computer once or twice before I posted here. I'll do that now.

---

### Post by kebbelj on 2007-02-24
The 127.0.0.1 page did not reload after either restart.

I typed *sudo apache -k start * at the command line. I got thie message ... 

*apache2: Could not determine the server's fully qualified domain name, using 127 .0.1.1 for ServerName*

When I refreshed the page, it and the test.php page both ran.

---

### Post by annda on 2007-02-24
i must admit i have no idea why apache doesn't start on boot. it always has for me. check services activated on boot and activate httpd or apache2 as needed.

---

