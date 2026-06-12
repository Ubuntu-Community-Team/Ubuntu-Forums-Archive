---
title: "problem with software center"
date: 2012-11-07
forum: General Help
---

### Post by aleja296 on 2012-11-07
hi! when I open the software center and I click on installed it happens this problem (all software and record don't give problem, only installed)
[http://www.subirimagenes.net/show-image.php?id=4d29c5dd6ca6272b96e80360d6eb1c45](http://www.subirimagenes.net/show-image.php?id=4d29c5dd6ca6272b96e80360d6eb1c45)
The other day i change a name's directory about this (i read in a forum for use less resources) but I don't remember what changued exactly and I don't find the forum.
Help, plis!!

I find the page of the forum, it's this [http://www.linuxnoveles.com/2012/como-optimizar-ubuntu-12-10/](http://www.linuxnoveles.com/2012/como-optimizar-ubuntu-12-10/)
I aply this instructions:
sudo apt-get remove unity-lens-music
sudo apt-get autoremove unity-scope-musicstores
sudo apt-get remove ubuntuone-client
sudo apt-get remove deja-dup
sudo apt-get autoremove gnome-online-accounts
sudo mv /usr/share/oneconf/oneconf-service /usr/share/oneconf/oneconf-service-old
sudo mv /usr/sbin/aptd /usr/sbin/aptd-old

what instruction make this mistake and how I fix this wrong?

---

### Post by ibjsb4 on 2012-11-07
Please post all errors you are now getting.

Also this may help others to understand what you did

[http://translate.google.com/translate?hl=en&sl=es&u=http://www.linuxnoveles.com/&prev=/search%3Fq%3DLinux%2Bpara%2BNoveles%26hl%3Den%26client%3Dfirefox-a%26hs%3DScR%26tbo%3Dd%26rls%3Dorg.mozilla:en-US:official&sa=X&ei=fWGaUJuhGYf7iwK54oHICQ&ved=0CDQQ7gEwAA](http://translate.google.com/translate?hl=en&sl=es&u=http://www.linuxnoveles.com/&prev=/search%3Fq%3DLinux%2Bpara%2BNoveles%26hl%3Den%26client%3Dfirefox-a%26hs%3DScR%26tbo%3Dd%26rls%3Dorg.mozilla:en-US:official&sa=X&ei=fWGaUJuhGYf7iwK54oHICQ&ved=0CDQQ7gEwAA)

And in terminal enter:

sudo apt-get update

Get any errors from that?

---

### Post by sienile on 2012-11-07
I'm rather wary about hacking apart Unity and its components. Last time I tried that I ended up with an un-bootable install. Persoanlly I would just unhide the hidden startup programs and disable whatever you don't use. You can find instructions for that somewhere on these forums, but I can't remember where. A search for 'hidden startup' should find it.

In regards to your problem, we need more information. Reproduce the error and when the error report window pops up, click the button labeled "Mostrar detalles" and copy the message in the next window and paste it here.

---

