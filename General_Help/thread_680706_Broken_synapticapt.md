---
title: "Broken synaptic/apt"
date: 2008-01-28
forum: General Help
---

### Post by r!ots on 2008-01-28
Hey guys,

last week I tried to uninstall my ATI 7.12 drivers, so I would be able to install the new 8.01 drivers. I was using this guide: [GutsyInstallationGuide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

There it says to uninstall any packages containing 'fglrx' in their name using synaptic. I did that but upon uninstalling 'xorg-driver-fglrx' it produced the following error message:

> E: xorg-driver-fglrx: subprocess post-removal script returned error exit status 2


When I try 'sudo apt-get install -f' I get the following output:

```
adrian@idefix:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xorg-driver-fglrx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 27.0MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 115781 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: rename involves overwriting `/etc/xdg/compiz/compiz-manager' with
  different file `/etc/xdg/compiz/compiz-manager.ubuntu', not allowed
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Someone told me to uninstall first compiz and then the fglrx-driver, but at the moment I can't install or uninstall anything using synaptic/apt , as I always receive the above error message.
Can anyone help, plz?

---

### Post by gvartser on 2008-01-28
See the following forum thread:

[http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/](http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/)

/g

---

### Post by r!ots on 2008-01-29
That didn't help. How often do I have to repeat those commands? I did it about 20 times without a change and actually I don't think it will work eventually.

Does anyone know what this line is supposed to mean:

> dpkg-divert: rename involves overwriting `/etc/xdg/compiz/compiz-manager' with
  different file `/etc/xdg/compiz/compiz-manager.ubuntu', not allowed
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2


I guess this is where something goes wrong, but I couldn't find any information on it.

---

### Post by r!ots on 2008-01-29
Well I just solved it. 
I removed /etc/xdg/compiz/compiz-manager manually and then it worked.
Thanks for you help anyway.

---

### Post by gvartser on 2008-01-29
Ahh nice that you found a solution, sorry that I couldn't help you out..

Best regz,
/G

---

### Post by danwood76 on 2008-01-29
You dont actually need to uninstall the previous versions of the fglrx drivers to install the next as it will only load the last one you installed at boot up.
I havent un installed the last 4 versions on my machine and have had no problems at all.

You can always manually remove the old version afterwards by removing the kernel modules.

regards,
Danny

---

