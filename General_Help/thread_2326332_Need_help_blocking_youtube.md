---
title: "Need help blocking youtube"
date: 2016-05-30
forum: General Help
---

### Post by clint8 on 2016-05-30
My son has figured out how to get around site block is there any way for me to block youtube via the command line.
I am using Ubuntu 16.04

---

### Post by QDR06VV9 on 2016-05-30
Have a look here [http://www.addictivetips.com/ubuntu-linux-tips/how-to-block-unwanted-website-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-block-unwanted-website-in-ubuntu-linux/)
Pretty straight forward.
EDIT: Maybe I should show an example of how i do it.
```
sudo nano /etc/hosts
```
Add to the bottom
[COLOR=#ff0000]"127.0.0.1       www.youtube.com"
[/COLOR]Save with Keyboard combo "Ctrl+o" and hit Enter to save and "Ctrl+x" to exit
 Mine shows this.
```
#
# /etc/hosts: static lookup table for host names
#

#<ip-address>   <hostname.domain.org>   <hostname>
127.0.0.1       localhost.localdomain   localhost
::1             localhost.localdomain   localhost
[COLOR=#ff0000]127.0.0.1       www.youtube.com[/COLOR]

# End of file


```
And now no youtube...Screenshot Below.
It is an instant rule so no need to restart anything.


Kind Regards

---

### Post by howefield on 2016-05-31
Perhaps your router has means of blocking access to certain websites, benefit (or hindrance :) ) being it is not machine specific in the way /etc/hosts is. Harder to circumvent if only have the password to the router/modem/whatever.

---

### Post by dragonfly41 on 2016-05-31
You can create a free account at OpenDNS.com for content control ...

[https://www.opendns.com/home-internet-security/](https://www.opendns.com/home-internet-security/)

---

