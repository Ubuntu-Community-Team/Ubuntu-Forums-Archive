---
title: "Root apps at startup - rc.local not working as expected"
date: 2018-03-21
forum: General Help
---

### Post by kazakore on 2018-03-21
Ubuntu Studio 16.04

Been trying to get my VPN to automatically startup when logging it but no matter how I enter the line into rc.local to try and get it to load at login with root privileges it doesn't work!

There is nothing else in the rc.local file to cause issues. (I did previously have a cpupower command to set governors to Performance but this program has been depreciated and it appeared my system has remembered the setting so I removed the line rather than replaced it with the cpufreq-set equivalent.)

So what am I doing wrong? Has rc.local as a whole been depreciated? Never had such issues with getting something that needs root privileges to load at login in the past!



Semi-related. What is the correct way to set the intel-pstate CPU settings these days? Despite me getting reports that my governor is set to Performance with both the Min and Max frequencies as being 3.0GHz all four cores state they are running well below this, at around 2.4GHz.

---

### Post by kazakore on 2018-03-21
OK I think it may be related to rc.local running before X is loaded and the VPN loading its GUI configurator from the command.

```
~$ systemctl status rc-local.service 
&#9679; rc-local.service - /etc/rc.local Compatibility
   Loaded: loaded (/lib/systemd/system/rc-local.service; static; vendor preset: enabled)
  Drop-In: /lib/systemd/system/rc-local.service.d
           &#9492;&#9472;debian.conf
   Active: failed (Result: exit-code) since Wed 2018-03-21 16:56:00 GMT; 10min ago
  Process: 2163 ExecStart=/etc/rc.local start (code=exited, status=1/FAILURE)

Mar 21 16:56:00 blublub rc.local[2163]:   warnings.warn(str(e), _gtk.Warning)
Mar 21 16:56:00 blublub rc.local[2163]: Using GTK2
Mar 21 16:56:00 blublub rc.local[2163]: changing directory to /usr/lib/python2.7/dist-packages/mullvad
Mar 21 16:56:00 blublub rc.local[2163]: Setting logging directory to /root/.cache/mullvad/log
Mar 21 16:56:00 blublub rc.local[2163]: Unable to access the X Display, is $DISPLAY set properly?
Mar 21 16:56:00 blublub sudo[2165]: pam_unix(sudo:session): session closed for user root
Mar 21 16:56:00 blublub systemd[1]: rc-local.service: Control process exited, code=exited status=1
Mar 21 16:56:00 blublub systemd[1]: Failed to start /etc/rc.local Compatibility.
Mar 21 16:56:00 blublub systemd[1]: rc-local.service: Unit entered failed state.
Mar 21 16:56:00 blublub systemd[1]: rc-local.service: Failed with result 'exit-code'.

```


I guess the proper way to do it will be make an OpenVPN configuration file and run that at startup then....

---

### Post by SeijiSensei on 2018-03-21
In general, the network connection on Ubuntu only happens after the user logs in.  So when rc.local is run at boot, there is no network that OpenVPN can use.  It's possible to futz with the network settings so that the connection comes up at boot, or you can run the OpenVPN script after you've logged in with the network operating.

---

### Post by kazakore on 2018-03-21
I think with OpenVPN there is an option to run set it up as a deamon and run via systemd so I'll have a proper look at that tomorrow...

---

### Post by vanadium on 2018-03-22
rc.local must be set executable, so perhaps you may check that if this is applicable to your situation (I am on 17.10, where rc.local is not present by default. It is sufficient to creating the file, but it must have execute permissions).

---

