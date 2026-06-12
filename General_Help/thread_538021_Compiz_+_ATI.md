---
title: "Compiz + ATI"
date: 2007-08-29
forum: General Help
---

### Post by gavinjb on 2007-08-29
Hi,

I have just re-installed Ubuntu 7.04 and thought I would try again and see if I could get Compiz to work on Ubuntu this time (I have managed without much problems on Mandriva so I know my machine can support it, I just don't like Mandriva). anyway I followed a how to ([http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)) and got the following error when running compiz-replace

```

Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

```

I did a search on this forum and found a how to on installing XGL ([http://ubuntuforums.org/showthread.php?t=488385&highlight=compiz+ati+howto](http://ubuntuforums.org/showthread.php?t=488385&highlight=compiz+ati+howto)), but all I get is a corrupted screen when following this tutorial, I have installed the ATI Propriatry drivers with Envy as my card (ATI Mobility Radeon X1400) is not listed as supported by the open source drivers.

Can someone please help, as I would love to get Compiz running (plus I would like to see several Vista lovers mouths on the floor after seeing Compiz running :) )

Thanks,


Gavin,

---

### Post by superyounan1 on 2007-08-31
try installing the fglrx drivers manually by following these instructions:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)
(method 2)

then use these instructions to install compiz fusion:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Compiz-Fusion_.28a_Compiz-Beryl_fusion.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Compiz-Fusion_.28a_Compiz-Beryl_fusion.29)

hope that helps

---

