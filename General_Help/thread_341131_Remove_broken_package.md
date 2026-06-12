---
title: "Remove broken package"
date: 2007-01-18
forum: General Help
---

### Post by Flecko on 2007-01-18
Hello all.

This is a somewhat complicated question involving the accidental installation of VMware player. First of all, my install of edgy has been working great, no complaints...but one day I decided I needed to install VMware player to test out an image I found on the internet. The thing is, I forgot that it was available in the Edgy repositories. I downloaded and started to install it manually from the VMware page when I realized it was available in the repositories. So I stopped the install.

Next, I tried to install it through synaptic. This didn't go well as it had problems with the files left behind from the manual install. So I tried again to manually install it the whole way through to see if it would work. Of course it didn't. So now I'm left with a system that upon every run of synaptic will complain about a broken package for VMware, and won't let me remove it or do anything to fix it.

I don't really care about running VMware, but is there a way for me to fix synaptics complaints about the broken package?

Thanks everyone!
-Flecko

---

### Post by an.echte.trilingue on 2007-01-18
How exactly did you install this?  
dpkg with a .deb?
alien with the .rpm?
from the tarball?

It makes a big difference.

If you compiled it, there should be a ./uninstall script in the folder.

Otherwise, you can try
```
sudo dpkg --force-uninstall-reinstreq <package-name>
sudo apt-get update
sudo apt-get --fix-broken upgrade
```

---

### Post by Flecko on 2007-01-21
I installed VMware-player(half-way) using the install scrip that came with it. It wasn't built from source. It doesn't appear to have any uninstall script that i can find or am aware of.

Also, the first dpkg command you gave me doesn't work(exist?) "sudo dpkg --force-uninstall-reinstreq vmware" I looked into the dpkg commands, and can't find a similar one. I'll keep looking, but in the meantime, do you have any more suggestions?

Thanks!
-Flecko

---

### Post by lamego on 2007-01-21
Reinstall it from the .tar, there is a manual uninstall script.

---

### Post by Flecko on 2007-01-22
Thankyou!!

That worked. I definitely tried to reinstall VMware Player from the .tar before and running into errors, but it worked great this time.

Thankyou so much!
-Flecko

---

