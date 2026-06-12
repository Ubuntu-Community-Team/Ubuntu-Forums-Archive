---
title: "Flash plugin cannot uninstall"
date: 2006-10-29
forum: General Help
---

### Post by wootton on 2006-10-29
I have found lots of information on various flash plugin problems, but nothing that has helped me, so please bare with me.

I have installed the flash plugin manually from Adobe's site, copying over the two required files into my mozilla/plugin dir.

However, any command involving apt, or if I try to use the package manager with Ubuntu, then I get the following error:

[FONT="Courier New"]E: The package flashplugin-nonfree needs to be reinstalled, but I can't find an archive for it.[/FONT]

I've tried all of the following
[FONT="Courier New"]
sudo apt-get remove flashplayer-mozilla
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree[/FONT]

They all result in the same error (stated earlier in this post).

Can anyone help?

---

### Post by wootton on 2006-10-29
I have been stuck with this problem now for about 3 weeks and really don't want to have to reinstall Ubuntu.  Why is this such a problem?

---

### Post by NeoLithium on 2006-10-29
The easiest way to install the flash plugin, is to use automatix, which you can get [here]("http://www.getautomatix.com") with easy installation instructions. It'll install it painlessly on your system.

---

### Post by wootton on 2006-10-29
I found a solution.  Using Google, I found this site [https://launchpad.net/distros/ubuntu/+bug/56413](https://launchpad.net/distros/ubuntu/+bug/56413) , I change the command to this:

sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree

It worked.

---

### Post by wootton on 2006-10-29
Hi NeoLithium,

I can not use automatix, because the error I described earlier (E: The package flashplugin-nonfree needs to be reinstalled, but I can't find an archive for it.), stopped me from doing so.

The flash pluing has installed fine, when I did it manually from Adobe's site, but I could use my system's package management or install anything because of the error.

Thank you for your reply though.

---

