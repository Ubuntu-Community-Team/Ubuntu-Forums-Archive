---
title: "Unable to update or open ubuntu software centre"
date: 2014-03-11
forum: General Help
---

### Post by richidib on 2014-03-11
Hey everyone,

sorry if this is in the wrong section, my first time :)

I have been having this ongoing issue, I cannot open Ubuntu software centre or Synaptic as well.
I have googled it with no luck.

I have been getting this error message as well, 'the package sabnzbdplus needs to be reinstalled, but I can't find an archive for it.' as well.

Can anyone please help me?

---

### Post by ian-weisser on 2014-03-11
Where did you get sbanzdbplus from? It's not in the Ubuntu repositories...

---

### Post by richidib on 2014-03-11
My son tried to install sbanzdbplus for some reason, I am not to sure what it is.
I am not to sure how to remove it, from the repositories

---

### Post by slickymaster on 2014-03-11
> **richidib said:**
> Hey everyone,

sorry if this is in the wrong section, my first time :)

I have been having this ongoing issue, I cannot open Ubuntu software centre or Synaptic as well.
I have googled it with no luck.

I have been getting this error message as well, **[COLOR=#ff0000]'the package sabnzbdplus needs to be reinstalled, but I can't find an archive for it.[/COLOR]**' as well.

Can anyone please help me?

This type of error mostly occur when you try to install a debian package in to ubuntu system
Try the following command at a terminal window:```
sudo dpkg --remove --force-remove-reinstreq sabnzbdplus
```

---

### Post by ajgreeny on 2014-03-11
There is a ppa for it so that could be how your son tried to install it.  [http://wiki.sabnzbd.org/install-ubuntu-repo](http://wiki.sabnzbd.org/install-ubuntu-repo)

Have a look in **/etc/apt/sources.list.d** to see if there is a file for that repository.

However for a start, to remove whatever is installed see if you can find any installation files with ```
locate sabnzbd
``` and report back here what is found, as it could be that your son tried to install using the archive of source files and code.

---

### Post by richidib on 2014-03-11
> **slickymaster said:**
> This type of error mostly occur when you try to install a debian package in to ubuntu system
Try the following command at a terminal window:```
sudo dpkg --remove --force-remove-reinstreq sabnzbdplus
```


Thank you for the reason, learn something new everyday.

When I type that into terminal I get the following
[INDENT=2]
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 374842 files and directories currently installed.)
Removing sabnzbdplus ...
: not found/sabnzbdplus: 10: /etc/default/sabnzbdplus: 
: not found/sabnzbdplus: 13: /etc/default/sabnzbdplus: 
: not found/sabnzbdplus: 18: /etc/default/sabnzbdplus: 
: not found/sabnzbdplus: 22: /etc/default/sabnzbdplus: 
' not founddaemon: user 'richard
invoke-rc.d: initscript sabnzbdplus, action "stop" failed.
dpkg: error processing sabnzbdplus (--remove):
 subprocess installed pre-removal script returned error exit status 1
: not found/sabnzbdplus: 10: /etc/default/sabnzbdplus: 
: not found/sabnzbdplus: 13: /etc/default/sabnzbdplus: 
: not found/sabnzbdplus: 18: /etc/default/sabnzbdplus: 
: not found/sabnzbdplus: 22: /etc/default/sabnzbdplus: 
' not founddaemon: user 'richard
invoke-rc.d: initscript sabnzbdplus, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 sabnzbdplus
[/INDENT]

But it still does not work :(

---

### Post by richidib on 2014-03-11
> **ajgreeny said:**
> There is a ppa for it so that could be how your son tried to install it.  [http://wiki.sabnzbd.org/install-ubuntu-repo](http://wiki.sabnzbd.org/install-ubuntu-repo)

Have a look in **/etc/apt/sources.list.d** to see if there is a file for that repository.

However for a start, to remove whatever is installed see if you can find any installation files with ```
locate sabnzbd
``` and report back here what is found, as it could be that your son tried to install using the archive of source files and code.

Hey mate,

When I type locate sabnzbd

It actually does find something,an application, and when I click it it takes me to [https://localhost:9090](https://localhost:9090)

Thanks for the help

---

### Post by slickymaster on 2014-03-11
> **richidib said:**
> Thank you for the reason, learn something new everyday.

When I type that into terminal I get the following[INDENT=2]
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 374842 files and directories currently installed.)
Removing sabnzbdplus ...
: not found/sabnzbdplus: 10: /etc/default/sabnzbdplus: 
: not found/sabnzbdplus: 13: /etc/default/sabnzbdplus: 
: not found/sabnzbdplus: 18: /etc/default/sabnzbdplus: 
: not found/sabnzbdplus: 22: /etc/default/sabnzbdplus: 
' not founddaemon: user 'richard
invoke-rc.d: initscript sabnzbdplus, action "stop" failed.
dpkg: error processing sabnzbdplus (--remove):
 **[COLOR=#ff0000]subprocess installed pre-removal script returned error exit status 1[/COLOR]**
: not found/sabnzbdplus: 10: /etc/default/sabnzbdplus: 
: not found/sabnzbdplus: 13: /etc/default/sabnzbdplus: 
: not found/sabnzbdplus: 18: /etc/default/sabnzbdplus: 
: not found/sabnzbdplus: 22: /etc/default/sabnzbdplus: 
' not founddaemon: user 'richard
invoke-rc.d: initscript sabnzbdplus, action "start" failed.
dpkg: error while cleaning up:
 **[COLOR=#ff0000]subprocess installed post-installation script returned error exit status 1[/COLOR]**
Errors were encountered while processing:
 sabnzbdplus
[/INDENT]

But it still does not work :(

Hmmm, those might be the culprits. You could try to edit _/var/lib/dpkg/info/sabnzbdplus.postrm_ and _var/lib/dpkg/info/sabnzbdplus.prerm_ files, adding "|| true" to the end of the if lines. This will reverse the logic and force the condition instead of aborting.

To edit them, just run the following for the PRE-removal script:```
gksudo gedit /var/lib/dpkg/info/sabnzbdplus.prerm
``` and for the POST-removal script:```
gksudo gedit /var/lib/dpkg/info/sabnzbdplus.postrm
```

---

### Post by richidib on 2014-03-11
> **slickymaster said:**
> Hmmm, those might be the culprits. You could try to edit _/var/lib/dpkg/info/sabnzbdplus.postrm_ and _var/lib/dpkg/info/sabnzbdplus.prerm_ files, adding "|| true" to the end of the if lines. This will reverse the logic and force the condition instead of aborting.

To edit them, just run the following for the PRE-removal script:```
gksudo gedit /var/lib/dpkg/info/sabnzbdplus.prerm
``` and for the POST-removal script:```
gksudo gedit /var/lib/dpkg/info/sabnzbdplus.postrm
```



Thank you very much!
This did fix the issue, thank you all for the help, very helpful.

---

### Post by slickymaster on 2014-03-11
Glad you got it fixed. Happy *buntuing.

---

