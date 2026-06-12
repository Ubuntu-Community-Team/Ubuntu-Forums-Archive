---
title: "Firefox not as fast as usual!"
date: 2005-10-22
forum: General Help
---

### Post by JeffBlouin on 2005-10-22
Hi,

       When I'm surfing on internet, firefox take longer than on windows to load a web page. The status bar say looking up for... (the website ex: google.com) for a time (15 sec) and after the page appear very quickly. The problem is the wait before the page start to show.  What is strange is that my download speed is very fast (tested on testmy.com ).

I'm using high speed internet and the problem is the same with eth0 and wireless...

Thanks

---

### Post by heimo on 2005-10-22
Goto System->Administration->Networking and make sure that on DNS tab you have your ISPs DNS servers ip addresses (if you do dual boot, you can get those on Windows using *ipconfig /all*) On Firefox, type *about:config *at the address bar, search for *ipv6 *and set *network.dns.disableIPv6* to *true*. Edit /etc/modprobe.d/aliases file:
```
sudo gedit /etc/modprobe.d/aliases
```
and change *alias net-pf-10 ipv6* to *alias net-pf-10 off* and reboot.

This will disable ipv6 (new ip protocol, you will be using ipv4) and make sure that you have correct dns servers configured. You can test your DNS performance on command line (terminal) using dig. Type dig ubuntuforums.org (or some address you haven't accessed recently) and see how fast the reply is.

---

### Post by codejunkie on 2005-10-22
[quote=JeffBlouin]Hi,

 When I'm surfing on internet, firefox take longer than on windows to load a web page. The status bar say looking up for... (the website ex: google.com) for a time (15 sec) and after the page appear very quickly. The problem is the wait before the page start to show. What is strange is that my download speed is very fast (tested on testmy.com ).

I'm using high speed internet and the problem is the same with eth0 and wireless...

Thanks[/quote] follow this guide it will speed up firefox alot [http://ubuntuguide.org/#loadwebsitefasterfirefox]("http://ubuntuguide.org/#loadwebsitefasterfirefox") that should increase the speed quite a bit. if that dosen't help disabling ipv6 will do the trick for you certin isp's and routers don't seem to handle it well. to do that you need to copy and paste this command in the terminal 
```
sudo cp /etc/modprobe.d/aliases /etc/modprobe.d/aliases-backup
``` then
```
sudo gedit /etc/modprobe.d/aliases
```find this line  
```
alias net-pf-10 ipv6
``` and change it to ```
alias net-pf-10 off
``` save the file and reboot. this should put firefox's speed up to par with windows hope this helps and let me know how it works for ya.
Edit: heimo beat me to it.

---

### Post by JeffBlouin on 2005-10-22
Thank you both!

Firefox speed as increase by 100%. I still find it a little slower than on windows but i can live with that to be free of Bill...


Thanks

---

### Post by JeffBlouin on 2005-10-24
Hi,

        The spped is better now that I did what was sugggested but there is still a big wait  (10 secondes before the page start to show...)   I tried the exact same setup at my office and the pages show up very quick (same connection same provider...)  The only difference is that at my office the router is a Linksys and at home it's a USRobotic, Could there be a wrong setup in the USR router... 

Thanks

---

### Post by JeffBlouin on 2005-10-29
Hi,

       I finally boost my internet speed by using the plugin fasterfox!  Any negative feedback on this plugin?

Thanks for the help!

---

### Post by bionnaki on 2005-10-29
fasterfox has some modifications that will make browsing quicker - you can also do these manually, of course.

have you tried firefox 1.5 yet?
[http://www.ubuntuforums.org/showthread.php?t=79283](http://www.ubuntuforums.org/showthread.php?t=79283)

20x faster

---

