---
title: "Remove a program"
date: 2013-01-27
forum: General Help
---

### Post by colmeweb on 2013-01-27
Hey everybody,

I just installed something to try to fix a problem. From this site.

[http://askubuntu.com/questions/219990/no-sound-over-hdmi-12-10-amd-a4-5300-apu-msi-fm-a55m-e33](http://askubuntu.com/questions/219990/no-sound-over-hdmi-12-10-amd-a4-5300-apu-msi-fm-a55m-e33)

And this is the code I used 

```

sudo add-apt-repository ppa:makson96/fglrx
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fglrx-legacy

```

This puts a watermark on my screen and I would like to delete it all I need is one line in the terminal, Thanks for helping with my ignorance.

---

### Post by papibe on 2013-01-27
Hi colmeweb.

First uninstall the driver:
```
sudo apt-get purge fglrx-legacy
```
Then remove the ppa you added:
```
sudo add-apt-repository [COLOR="Red"]**-r**[/COLOR] ppa:makson96/fglrx
```
Then update your sources:
```
sudo apt-get update
```
Restart your computer.

Let us know how it goes.
Regards.

---

### Post by HiImTye on 2013-01-27
run:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:makson96/fglrx
sudo apt-get update
```
and then one of either:
```
sudo apt-get install --reinstall fglrx-legacy
sudo apt-get dist-upgrade
```
or
```
sudo apt-get remove fglrx-legacy
sudo apt-get install fglrx
sudo apt-get dist-upgrade
```

---

### Post by Yellow Pasque on 2013-01-27
@HilmTye: fglrx won't work without the ppa...

---

### Post by HiImTye on 2013-01-27
it should from the repos, if not use the bottom set of lines. I use nvidia, myself

---

### Post by colmeweb on 2013-01-28
Thanks Papibe,

Worked like a charm.

---

