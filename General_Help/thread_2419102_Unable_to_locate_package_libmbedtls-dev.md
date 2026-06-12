---
title: "Unable to locate package libmbedtls-dev"
date: 2019-05-16
forum: General Help
---

### Post by mnewber1 on 2019-05-16
I currently have a computer running Windows 10 with an encrypted BitLocker hard drive. The employee who used it has left but the files remain on his drive. We do not have admin access for the computer. We are trying the dislocker route but we are having trouble installing it on the computer. The hard drive is completely full so we can't install Ubuntu on it per say - so we are running Ubuntu 19.04 Disco Dingo on a bootable USB. I am able to install all packages needed for dislocker but **libmbedtls-dev**.

Alternatively, I cannot just do sudo apt install dislocker either because it returns that message of "Unable to locate package." 

These issues may be because we are running off a bootable usb, I am not sure. Please advise thank you so much.

---

### Post by #&amp;thj^% on 2019-05-16
Found here: [https://packages.ubuntu.com/disco/libmbedtls-dev](https://packages.ubuntu.com/disco/libmbedtls-dev)
I'm not sure what link your following but have a look here also: [https://github.com/Aorimn/dislocker/tree/develop](https://github.com/Aorimn/dislocker/tree/develop)

---

### Post by mnewber1 on 2019-05-16
When I open the .deb and click Install - a progress appears, and nothing happens. It will flash and the Install button is still there.

---

### Post by ajgreeny on 2019-05-16
> **mnewber1 said:**
> When I open the .deb and click Install - a progress appears, and nothing happens. It will flash and the Install button is still there.
Put the .deb file in your Downloads folder if it's not already there then run ```
sudo apt install Downloads/*name*.deb
``` changing where I've shown *name* to whatever the file is called.

---

### Post by mnewber1 on 2019-05-16
```

[COLOR=#333333]ubuntu@ubuntu:~/Downloads$ sudo apt install libmbedtls-dev_2.4.2-1+deb9u3_amd64.deb
[/COLOR][COLOR=#333333]Reading package lists... Done
[/COLOR][COLOR=#333333]Building dependency tree      
[/COLOR][COLOR=#333333]Reading state information... Done
[/COLOR][COLOR=#333333]E: Unable to locate package libmbedtls-dev_2.4.2-1+deb9u3_amd64.deb
[/COLOR][COLOR=#333333]E: Couldn't find any package by glob 'libmbedtls-dev_2.4.2-1+deb9u3_amd64.deb'
[/COLOR][COLOR=#333333]E: Couldn't find any package by regex 'libmbedtls-dev_2.4.2-1+deb9u3_amd64.deb'[/COLOR][COLOR=#333333]
[/COLOR]
```

Here is the response, doesn't seem to work either.

---

### Post by deadflowr on 2019-05-16
To use apt install it requires full path.
```
sudo apt install /full/path/to/deb-file.deb
```
But that said, if running a live session, or from usb, check if community(universe ) repository is enabled, or just run the enable command anyway
```
sudo add-apt-repository universe
sudo apt update
```
then see if the package is there.
(Hint: it should be, if it isn't something's wrong with your apt configuration.)

You can also install dislocker from there as well as it too is a universe package.

---

