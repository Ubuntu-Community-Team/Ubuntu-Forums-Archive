---
title: "Very stupid Compiz problem in Hardy..."
date: 2008-04-26
forum: General Help
---

### Post by Anton Chigurh on 2008-04-26
Hi,

I know Compiz is sometimes difficult to install but this time I tried any possible troubleshooting guide and it still won't work.

It's since I updated to Hardy.
I checked the whitelist for fglrx, I installed drivers with envy again and again, I uninstalled and reinstalled compiz several times, I checked software sources, I allowed restricted drivers ...

glxgears is working, glxinfo says everything is fine... 

The error message is: "Could not enable desktop effects"

But before upgrading I just had to install drivers (ati) via Envy, allow restricted drivers and add the compiz packages (core, main, extra and so on).

This time no matter what I do, it fails ...

Here is my compiz output:
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
/usr/bin/compiz: 406: /usr/local/bin/compiz: not found

THX for any help!!

---

### Post by Zorael on 2008-04-26
Try this.
```
$ sudo ln -s /usr/bin/compiz /usr/local/bin/compiz
```


I'm not sure you want to have Xgl installed, so if things go really, really slow, remove the **xserver-xgl** package.

---

### Post by Anton Chigurh on 2008-04-26
Sorry that didn't work...

btw. if I put "$" in front of the command it says "command not found".

---

### Post by Forlong on 2008-04-26
Try this:
```
sudo dpkg-divert --rename --remove /etc/xdg/compiz/compiz-manager
```

---

