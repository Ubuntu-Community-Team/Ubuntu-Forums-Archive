---
title: "Netatalk Sharing with OSX only showing Home Directory"
date: 2013-03-09
forum: General Help
---

### Post by CaptainCalvin1987 on 2013-03-09
I recently setup a Ubunutu 12.10 server with LAMP, I followed this guide([http://adam.merrifield.ca/2012/02/28/access-linux-from-mac-os-x-finder/](http://adam.merrifield.ca/2012/02/28/access-linux-from-mac-os-x-finder/)) to install netatalk so i could share some folders with the LAMP server from my iMac. I followed the guide step by step and the only thing i changed was editing the ```
[COLOR=#333333][FONT=helvetica]$ sudo vim /etc/netatalk/AppleVolumes.default[/FONT][/COLOR]
```[COLOR=#333333][FONT=helvetica] where i added in the following lines.
[/FONT][/COLOR]```
~/                   "$u" options:rw,nohex,usedots
/home/shared            "shared" options:rw,nohex,usedots
/var/www                  "www" options:rw,nohex,usedots

```[COLOR=#333333][FONT=helvetica]

I have restarted the services and even the machine but no matter what i do when i connect to the LAMP server all i see is the home directory, none of the other folders i have shared. Did i miss something?
[/FONT][/COLOR]

---

