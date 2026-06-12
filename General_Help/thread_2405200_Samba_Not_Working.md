---
title: "Samba Not Working"
date: 2018-11-02
forum: General Help
---

### Post by merlinus on 2018-11-02
Up until a recent software/security upgrade, no problems.  Now I cannot select folders to share.  The error message tells me that sharing services are not installed, but they are.

I uninstalled samba and reinstalled it, to no avail.  I also used terminal commands to start samba, and did not receive any error messages, but it is not running.

---

### Post by l33ch on 2018-11-04
did you just uninstall samba, what about smbclient cifs-utils? I would remove all those and reinstall them all again, then reedit/check smb.conf. 
Try uninstalling via:
```
sudo apt-get remove samba smbclient cifs-utils
```
Then reinstall:
```
sudo apt-get install samba smbclient cifs-utils
```

If purging doesn't remove them then:
Maybe try using :
sudo apt-get autoclean
Force removal of packages. &#9760;Use with caution

```
sudo apt-get --force-yes remove samba cifs-utils smbclient
```

and reinstall:

sudo apt-get install samba smbclient cifs-utils

Other than that, not really sure.

---

### Post by HermanAB on 2018-11-04
The best way to debug SMB is with smbclient from the command line.  The errors will tell you *exactly* what is wrong.  Google the error messages if you don't understand them.

---

### Post by merlinus on 2018-11-05
Uninstall worked fine, but here are the reinstall messages:

Unpacking cifs-utils (2:6.8-1) ...
Processing triggers for ufw (0.35-5) ...
Setting up cifs-utils (2:6.8-1) ...
update-alternatives: using /usr/lib/x86_64-linux-gnu/cifs-utils/idmapwb.so to provide /etc/cifs-utils/idmap-plugin (idmap-plugin) in auto mode
Processing triggers for ureadahead (0.100.0-20) ...
Setting up smbclient (2:4.7.6+dfsg~ubuntu-0ubuntu2.2) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for systemd (237-3ubuntu10.3) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Setting up samba (2:4.7.6+dfsg~ubuntu-0ubuntu2.2) ...
Samba is not being run as an AD Domain Controller.
Please ignore the following error about deb-systemd-helper not finding samba-ad-dc.service.
Failed to preset unit: Unit file /etc/systemd/system/samba-ad-dc.service is masked.
/usr/bin/deb-systemd-helper: error: systemctl preset failed on samba-ad-dc.service: No such file or directory
Processing triggers for libc-bin (2.27-3ubuntu1) ...

And I still get the same error message when trying to share folders (need to install samba).

Thanks anyway for trying!

---

### Post by merlinus on 2018-11-05
> **HermanAB said:**
> The best way to debug SMB is with smbclient from the command line.  The errors will tell you *exactly* what is wrong.  Google the error messages if you don't understand them.

Here is the output.  I cannot see any error messages, however.

smbclient
WARNING: The "syslog" option is deprecated
Usage: smbclient [-?EgBVNkPeC] [-?|--help] [--usage]
        [-R|--name-resolve=NAME-RESOLVE-ORDER] [-M|--message=HOST]
        [-I|--ip-address=IP] [-E|--stderr] [-L|--list=HOST]
        [-m|--max-protocol=LEVEL] [-T|--tar=<c|x>IXFqgbNan]
        [-D|--directory=DIR] [-c|--command=STRING] [-b|--send-buffer=BYTES]
        [-t|--timeout=SECONDS] [-p|--port=PORT] [-g|--grepable]
        [-B|--browse] [-d|--debuglevel=DEBUGLEVEL]
        [-s|--configfile=CONFIGFILE] [-l|--log-basename=LOGFILEBASE]
        [-V|--version] [--option=name=value]
        [-O|--socket-options=SOCKETOPTIONS] [-n|--netbiosname=NETBIOSNAME]
        [-W|--workgroup=WORKGROUP] [-i|--scope=SCOPE] [-U|--user=USERNAME]
        [-N|--no-pass] [-k|--kerberos] [-A|--authentication-file=FILE]
        [-S|--signing=on|off|required] [-P|--machine-pass] [-e|--encrypt]
        [-C|--use-ccache] [--pw-nt-hash] service <password>

---

