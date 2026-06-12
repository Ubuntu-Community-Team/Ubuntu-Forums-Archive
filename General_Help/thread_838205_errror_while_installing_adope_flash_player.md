---
title: "errror while installing adope flash player"
date: 2008-06-23
forum: General Help
---

### Post by charanpreethu on 2008-06-23
i followed 
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
this link to download adobe..i downloaded .tar.gz...than i followed the instruction for installing.....but error appeared during installation.
the is ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.
what can do now????how can i install it.

---

### Post by xebian on 2008-06-23
> **charanpreethu said:**
> i followed 
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
this link to download adobe..i downloaded .tar.gz...than i followed the instruction for installing.....but error appeared during installation.
the is ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.
what can do now????how can i install it.

You should use synaptics to install flash.  Install the flashplugin-nonfree package.

---

### Post by beckols on 2008-06-23
Almost anytime you start to download something that is a .tar.gz, check the repo's first because there is a very good chance it will be there.
```
sudo apt-get install flashplugin-nonfree
```

---

