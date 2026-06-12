---
title: "Ubuntu Software Center closes after startup"
date: 2014-06-09
forum: General Help
---

### Post by tomas11 on 2014-06-09
Hi i have issue with USC 
Here is code: ```
namai@namai-System-Product-Name:~$ software-center
2014-06-09 20:31:57,669 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2014-06-09 20:31:58,376 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2014-06-09 20:31:58,379 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2014-06-09 20:31:58,385 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2014-06-09 20:31:58,385 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2014-06-09 20:31:58,457 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Magistral&#279;s klaida (core dumped)

```

---

### Post by bapoumba on 2014-06-09
Not sure which Ubuntu version you are running.
Here is an older bug report, please see comments # 9 & 10
[https://bugs.launchpad.net/software-center/+bug/829067](https://bugs.launchpad.net/software-center/+bug/829067)

I've seen other similar errors from issues in the sources.list. please post the outputs to :

```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*

sudo apt-get update
sudo apt-get upgrade
```

When doing so, please use code tags to paste the outputs : [http://ubuntuforums.org/misc.php?do=bbcode#code](http://ubuntuforums.org/misc.php?do=bbcode#code)

---

