---
title: "No module named repository"
date: 2016-08-06
forum: General Help
---

### Post by xeddog on 2016-08-06
I have started getting messages like these for a couple of applications lately.  The first one I noticed was Deja-Dup when it quit working.  I get the error > BackendException: Could not initialize backend: No module named repository  I googled and found a few references to other problems where the module name was gi.repository, and to resolve it I should install python-gi.  My error just says repository, and python-gi and python3-gi are already installed anyway.  

Today, I noticed that software center would not start.  When starting it from a terminal I see this: > twoblues@Stealth:~$ /usr/bin/software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 25, in <module>
    from gi.repository import Gtk, GObject
ImportError: No module named repository
twoblues@Stealth:~$   This one DOES say gi.repository.  So something has broken, but what???

Wayne

P.S.  I should maybe note that Deja Dup was working perfectly as of July 28, but broken August 4 when it tried to do a weekly backup.  As for software center, I haven't used it in a long time so I can only assume it broke at the same time.

Ubuntu 16.04 (upgraded from 15.10)
Intel I-7 processor with 16GB RAM
1TB esata disk for / filesystem
1TB esata disk for /home

---

### Post by CantankRus on 2016-08-06
This may help.
On my xenial install /usr/bin/software-center does not exist and is no longer installed by default.
Xenial uses **gnome-software**.
If I was to install software-center  it drags in these packages...
```
apt-xapian-index gir1.2-gmenu-3.0 libxapian-1.3-5 oneconf oneconf-common python-aptdaemon python-aptdaemon.gtk3widgets python-attr python-blinker python-cups
  python-debtagshw python-defer python-dirspec python-jwt python-oauthlib python-oneconf python-pam python-piston-mini-client python-pyasn1-modules
  python-serial python-service-identity python-twisted-bin python-twisted-core python-twisted-web python-ubuntu-sso-client python-xapian python3-blinker
  python3-cffi-backend python3-cryptography python3-httplib2 python3-idna python3-jwt python3-oauthlib python3-oneconf python3-piston-mini-client
  python3-xapian1.3 software-center software-center-aptdaemon-plugins ubuntu-sso-client
```

You could uninstall software-center and then remove all the dependencies that are no longer needed.
```
sudo apt remove software-center
sudo apt autoremove
```

Then update
```
sudo apt update && sudo apt upgrade
```

---

### Post by xeddog on 2016-08-08
Thanks Cant, but the problem isn't really software-center but DeJa-VU/Duplicity.  I just mentioned software-center in the hopes that it might increase the chances of finding out what happened.

Wayne

---

### Post by xeddog on 2016-08-08
Here is a little bit more info.  I set an environment variable to turn on deja-dup debugging and then ran deja-dup in a terminal.

> twoblues@Stealth:~$ DEJA_DUP_DEBUG=1
twoblues@Stealth:~$ export DEJA_DUP_DEBUG
twoblues@Stealth:~$ deja-dup --backup
DUPLICITY: INFO 1
DUPLICITY: . Using archive dir: /home/twoblues/.cache/deja-dup/b16a3518b4c50a4c361a59824ff5c6de

DUPLICITY: INFO 1
DUPLICITY: . Using backup name: b16a3518b4c50a4c361a59824ff5c6de

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.acdclibackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.azurebackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.b2backend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.botobackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.cfbackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.copycombackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.dpbxbackend Failed: No module named dropbox

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.gdocsbackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.giobackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.hsibackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.hubicbackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.imapbackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.lftpbackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.localbackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.mediafirebackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.megabackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.multibackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.ncftpbackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.onedrivebackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.par2backend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.pydrivebackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.rsyncbackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.ssh_paramiko_backend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.ssh_pexpect_backend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.swiftbackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.sxbackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.tahoebackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Import of duplicity.backends.webdavbackend Succeeded

DUPLICITY: INFO 1
DUPLICITY: . Using temporary directory /home/twoblues/.cache/deja-dup/tmp/duplicity-ytcQ4M-tempdir

DUPLICITY: INFO 1
DUPLICITY: . Backend error detail: Traceback (most recent call last):
DUPLICITY: .   File "/usr/bin/duplicity", line 1546, in <module>
DUPLICITY: .     with_tempdir(main)
DUPLICITY: .   File "/usr/bin/duplicity", line 1540, in with_tempdir
DUPLICITY: .     fn()
DUPLICITY: .   File "/usr/bin/duplicity", line 1375, in main
DUPLICITY: .     action = commandline.ProcessCommandLine(sys.argv[1:])
DUPLICITY: .   File "/usr/lib/python2.7/dist-packages/duplicity/commandline.py", line 1109, in ProcessCommandLine
DUPLICITY: .     globals.backend = backend.get_backend(args[0])
DUPLICITY: .   File "/usr/lib/python2.7/dist-packages/duplicity/backend.py", line 223, in get_backend
DUPLICITY: .     obj = get_backend_object(url_string)
DUPLICITY: .   File "/usr/lib/python2.7/dist-packages/duplicity/backend.py", line 211, in get_backend_object
DUPLICITY: .     raise BackendException(_("Could not initialize backend: %s") % str(sys.exc_info()[1]))
DUPLICITY: . BackendException: Could not initialize backend: No module named repository
DUPLICITY: . 

DUPLICITY: ERROR 23 BackendException
DUPLICITY: . BackendException: Could not initialize backend: No module named repository

twoblues@Stealth:~$ 


---

