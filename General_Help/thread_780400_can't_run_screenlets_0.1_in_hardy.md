---
title: "can't run screenlets 0.1 in hardy"
date: 2008-05-03
forum: General Help
---

### Post by stansford on 2008-05-03
hi,
I've installed the latest screenlets v0.1 from getdeb and I get the following error when I try and run screenlets-manager:

Traceback (most recent call last):
File "/usr/share/screenlets-manager/screenlets-manager.py", line 28, in <module>
import screenlets
File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 75
SyntaxError: Non-ASCII character '\xc3' in file /usr/lib/python2.5/site-packages/screenlets/__init__.py on line 75, but no encoding declared; see [http://www.python.org/peps/pep-0263.html](http://www.python.org/peps/pep-0263.html) for details
Error in sys.excepthook:
Traceback (most recent call last):
File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 78, in apport_excepthook
report_file = open(pr_filename, 'wt')
IOError: [Errno 13] Permission denied: '/var/crash/_usr_share_screenlets-manager_screenlets-manager.py.1000.crash'

Original exception was:
Traceback (most recent call last):
File "/usr/share/screenlets-manager/screenlets-manager.py", line 28, in <module>
import screenlets
File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 75
SyntaxError: Non-ASCII character '\xc3' in file /usr/lib/python2.5/site-packages/screenlets/__init__.py on line 75, but no encoding declared; see [http://www.python.org/peps/pep-0263.html](http://www.python.org/peps/pep-0263.html) for details


Can anyone help me solve this please?
In an effort to sort it I've also installed the following packages that other have recommended but none of them solved the problem:

python-feedparser
python-gnome2-extras
python-chardet

and I've rebooted! -oh and screenlets 0.0.12 works from the repos, but I want to use the latest one!

---

### Post by andyrue304 on 2008-05-03
I installed from the synaptic and all seems well...

Sorry I can't be more help!

---

### Post by FuturePilot on 2008-05-03
Have you purged the old version before installing the latest version? They need to be purged, not just removed.

---

### Post by stansford on 2008-05-03
> **FuturePilot said:**
> Have you purged the old version before installing the latest version? They need to be purged, not just removed.

Thanks for the replies.

I installed v0.1 on a clean hardy install. I've only moved over to a previous version after failing to run 0.1, so I didn't think there was anything to purge.

---

### Post by stansford on 2008-05-03
> **andyrue304 said:**
> I installed from the synaptic and all seems well...

Sorry I can't be more help!


Andyrue304 - thanks for replying. If you installed via synaptic, did you install v0.1? I thought the repositories were behind and you had to go to getdeb for the latest version.

When I used the repos they gave me 0.0.12.

---

### Post by cjm5229 on 2008-05-03
I haven't gotten it to run either, I have installed the getbeb version. I have compiled it from source, and used the deb from Screenlets website and none are working. I had it working up until the Hardy RC came out after that it quit. The Screenlets that I already had running still work but the Screenlets manager crashes everytime I try to start it. I haven't tried the one in the repos.

OK, I tried the one in the repo's and yes I did purge the old one first and it still doesn't work it is version 0.0.12

---

### Post by andyrue304 on 2008-05-07
> **stansford said:**
> Andyrue304 - thanks for replying. If you installed via synaptic, did you install v0.1? I thought the repositories were behind and you had to go to getdeb for the latest version.

When I used the repos they gave me 0.0.12.

Just checked and I got v0.0.12 got confused by the extra 0 so thought I had the correct version! D'oh!

---

### Post by cjm5229 on 2008-05-09
I did a fresh reinstall of Hardy and it works now, I think it has a conflict with some other App, not sure which one though. I now have a problem with the weather screenlets, none will connect to weather.com.

---

### Post by stansford on 2008-05-11
> **cjm5229 said:**
> I did a fresh reinstall of Hardy and it works now, I think it has a conflict with some other App, not sure which one though. I now have a problem with the weather screenlets, none will connect to weather.com.

yeah me too. Did a clean install and it worked OK. So problem solved. Thanks everyone.

---

