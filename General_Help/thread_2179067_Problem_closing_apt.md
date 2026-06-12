---
title: "Problem closing apt"
date: 2013-10-06
forum: General Help
---

### Post by grockle on 2013-10-06
ubuntu 10.04

A little advise please,
I was using apt to download and install googleearth, we had a short power cut, after this i tried to download again and get these  2 error msg,

"Previous installation hasn't been completed"
and
"Unable to get exclusive lock"

It looks like apt or another package manager is still running, but i am unable to find a way to force a quit.

Any advise please,
cheers
grockle

---

### Post by overdrank on 2013-10-06
Hi and are you able to update?
You can try
```
sudo dpkg --configure -a
```
```
sudo apt-get -f install
```
I believe the support for 10.04 has ended except for the sever edition.

---

### Post by grockle on 2013-10-06
```

sudo dpkg --configure -a

error msg,   status database area is locked by another process


sudo apt-get -f install

error msg,    Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)

```

Yes i did try the above, without any luck

It's got me beat


grockle

---

### Post by overdrank on 2013-10-06
This link may have a solution
[http://askubuntu.com/questions/15433/how-do-i-fix-a-could-not-get-lock-var-lib-dpkg-lock-problem](http://askubuntu.com/questions/15433/how-do-i-fix-a-could-not-get-lock-var-lib-dpkg-lock-problem)

---

### Post by jblake12518 on 2013-10-06
Here is a link to the step by step.

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

Try this & then redo the instalation.

[h=2]Uninstallation[/h] You can uninstall Google Earth as any other package. From the terminal you can do it using the following commands: 

[LIST]
[*]Find the exact package name: 
dpkg --list 'google-earth*' | cat which may show that the package name is google-earth-stable.
[*]Uninstall the package: 
sudo dpkg -P google-earth-stable
[/LIST]
If you installed Google Earth by a method that included running sh GoogleEarthLinux.bin (now depreciated), the unistallation can be done by pasting the following command in a [terminal]("https://help.ubuntu.com/community/UsingTheTerminal"): 

[LIST]
[*][IMG]https://help.ubuntu.com/moin_static192/light/img/icon-info.png[/IMG] This command is all on one line. Copy it and paste it in your terminal. 
[/LIST]
sudo rm -rf /opt/google-earth && sudo rm /usr/share/mime/application/vnd.google-earth.* /usr/share/mimelnk/application/vnd.google-earth.* /usr/share/applnk/Google-googleearth.desktop /usr/share/mime/packages/googleearth-mimetypes.xml /usr/share/gnome/apps/Google-googleearth.desktop /usr/share/applications/Google-googleearth.desktop /usr/local/bin/googleearthYou  may also wish to remove your user preferences folder, although this is  not necessary if you intend to reinstall later. This directory contains  Google Earth settings and the cache: 
rm -rf ~/.googleearth

---

### Post by grockle on 2013-10-06
overdrank,

many thanks for the help, although it's not fixed, i will mark this as solved.

I think the power cut messed up quite a lot of things.

Will install 13.10 in a couple of weeks.

Thanks again

grockle

---

