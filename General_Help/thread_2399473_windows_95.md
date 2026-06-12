---
title: "windows 95"
date: 2018-08-25
forum: General Help
---

### Post by cmcanulty on 2018-08-25
I just read this web page about installing Windows 95 on Linux just for fun and I get a dependency error but as you can see in screenshot the dependency is already installed. It is a .deb file for 64 bit from github

[https://www.theverge.com/2018/8/23/17773180/microsoft-windows-95-app-download-features](https://www.theverge.com/2018/8/23/17773180/microsoft-windows-95-app-download-features)

[https://github.com/felixrieseberg/windows95/releases](https://github.com/felixrieseberg/windows95/releases)

then I get an error that it is an app and won't install, anybody able to do this?

Windows 95, in an app. I'm sorry.


[ATTACH=CONFIG]280850[/ATTACH]

---

### Post by westie457 on 2018-08-25
Did this earlier.
Open the deb file with 'gdebi'
You will get the warning/error. Click 'Install'
When that has finished, find the icon 'Windows95' and you are running the app.

---

### Post by cmcanulty on 2018-08-25
I was using gdebi I get this and then if I click install it immediately crashes. I am running xubuntu 18.04

[ATTACH=CONFIG]280852[/ATTACH]

---

### Post by westie457 on 2018-08-25
Does ```
~/Downloads$ sudo dpkg -i windows95_1.1.0_amd64.deb
```
show the error

---

### Post by Yellow Pasque on 2018-08-25
> **cmcanulty said:**
> as you can see in screenshot the dependency is already installed.

As I can see, libgconf2-4 is not installed. libgconf-2-4 is installed. (Tricky hyphens)

---

### Post by raleigh3 on 2018-08-25
I can install it either. And all dependencies are met.

---

### Post by SagaciousKJB on 2018-08-25
```

sudo dpkg -i windows95_1.1.0_amd64.deb
sudo apt-get update --fix-missing
sudo apt-get install -f

```

Worked for me.  The apt-get install -f was needed to install libgconf2-4 after running apt-get update --fix-missing

Thanks, now I can enjoy installing Windows 95 for the first time ever.

---

### Post by cmcanulty on 2018-08-26
Sagacious, Thanks so much, your fix worked. If you have time can you explain what the options you had in the commands do.

---

### Post by cmcanulty on 2018-08-26
To make a nice icon for windows 95 I have attached a jpeg

[ATTACH=CONFIG]280858[/ATTACH]

---

### Post by SagaciousKJB on 2018-08-26
Well in this instance I already had a clue that it was a dependency issue, so I knew once the package was installed in the package database with dpkg, that I could use apt's --fix-missing and -f options to find and install the missing dependency. They don't always work, but often enough.

Basically this process, but I skipped dpkg configure since I already knew it was a dependency issue.

[http://www.iasptk.com/ubuntu-fix-broken-package-best-solution/](http://www.iasptk.com/ubuntu-fix-broken-package-best-solution/)

---

### Post by cmcanulty on 2018-08-26
Thanks for the additional info

---

### Post by PaulW2U on 2018-08-27
Or avoid all dependency issues and install the snap - [https://forum.snapcraft.io/t/windows95-snap/7059](https://forum.snapcraft.io/t/windows95-snap/7059). :D

---

### Post by raleigh3 on 2018-08-29
How do I uninstall it ?

I tried sudo apt remove windows95.

---

### Post by westie457 on 2018-08-29
In the terminal ```
sudo dpkg -r name of package
```
Or open the .deb file with GDebi, the options will be 'Reinstall package' and 'Remove package'.
Either way will work.

---

