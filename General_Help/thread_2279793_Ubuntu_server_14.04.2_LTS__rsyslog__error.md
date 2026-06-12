---
title: "Ubuntu server 14.04.2 LTS  rsyslog  error"
date: 2015-05-26
forum: General Help
---

### Post by uteliux on 2015-05-26
[COLOR=#474B51][FONT=Tahoma]Hello, then i`m trying to upgrade server i`m getting this error:[/FONT][/COLOR]

[COLOR=#474B51][FONT=Tahoma]The user `syslog' is already a member of `adm'.[/FONT][/COLOR]
[COLOR=#474B51][FONT=Tahoma]invoke-rc.d: initscript rsyslog, action[/FONT][/COLOR][COLOR=#474B51][FONT=Tahoma] "restart" failed.[/FONT][/COLOR]
[COLOR=#474B51][FONT=Tahoma]dpkg: error processing package rsyslog [/FONT][/COLOR][COLOR=#474B51][FONT=Tahoma](--configure):[/FONT][/COLOR]
[COLOR=#474B51][FONT=Tahoma]subprocess installed post-installation script returned error exit status 1[/FONT][/COLOR]
[COLOR=#474B51][FONT=Tahoma]E: Sub-process /usr/bin/dpkg returned an error code (1)

seems rsyslog is not starting log file is empty...

[/FONT][/COLOR][COLOR=#474B51][FONT=Tahoma]uttt@******:~$ sudo service rsyslog status[/FONT][/COLOR]
[COLOR=#474B51][FONT=Tahoma]* rsyslogd is not running[/FONT][/COLOR][COLOR=#474B51][FONT=Tahoma]




[/FONT][/COLOR]

---

### Post by tgalati4 on 2015-05-26
I presume that you are performing an in-place upgrade.  Perhaps you went from 12.04 to 14.04?  Try rebooting, install any updates to 14.04.2 and then look in /var/log/syslog for errors.

You can then try to reconfigure *rsyslog* using:

```
sudo dpkg-reconfigure rsyslog
```

When performing an in-place upgrade (as opposed to a fresh, clean install) you have pre-installation, installation, and post-installation scripts for each package.  With a mixture of old and new packages, there is plenty of opportunity for breakage.

If the reconfigure doesn't fix it, then remove it and reinstall it:

```
sudo apt-get purge rsyslog
sudo apt-get install rsyslog
```

I have a feeling there is something else going on.  Rsyslog is a pretty straight-forward service.  What else is not working?

---

### Post by uteliux on 2015-05-27
tgalati4 thx for your reply. Yes system was updated from 12.04 to 14.04. Rebooted several times, rsyslog not working.. 

dpkg-reconfigure tried before it gives "/usr/sbin/dpkg-reconfigure: rsyslog is broken or not fully installed" 

Spamassassin is not starting to:

[B]Restarting SpamAssassin Mail Filter Daemon: setlogsock(): type='unix': path not available at /usr/share/perl5/Mail/SpamAssassin/Logger/Syslog.pm line 100.
setlogsock(): type='tcp': TCP service unavailable at /usr/share/perl5/Mail/SpamAssassin/Logger/Syslog.pm line 121.
logger: failed to add syslog method: logger: syslog initialization failed
spamd.
[/B]It is safe to reinstall rsyslog? 
sudo apt-get purge rsyslog
sudo apt-get install rsyslog

/var/log/syslog is empty :( :(

---

### Post by uteliux on 2015-05-29
up

---

### Post by uteliux on 2015-06-02
no suggestions? : (

---

### Post by uteliux on 2015-06-02
**sudo apt-get install **[B]--reinstall rsyslog[B]1

 [/B][/B]Shows:[B]
[B]not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for rsyslog:amd64[/B]
[/B]

---

