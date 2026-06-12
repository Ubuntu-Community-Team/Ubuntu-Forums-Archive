---
title: "CUPS installation failing"
date: 2015-02-23
forum: General Help
---

### Post by karsten_df on 2015-02-23
hi all,
This is my first thread in ubuntu forums, so hopefully my question is at the right place. 
I'm having troubles with CUPS (1.7.2) on my (headless) server box (14.04.2, all updates installed).
Initial problem was that the CUPS web interface refused to work for the 'administration' or 'printers' tabs - apparently the cgi scripts could not get started.
I then decided to re-install CUPS completely, which seems to have been a very bad idea as I now obviously can't even get CUPS to start up any more.
[LIST]
[*]Re-installation was done via "sudo apt-get install cups cups-client cups-bsd". 
[*]Installation procedure runs without obvious issues (just auto-adds 'printer-driver-gutenprint') 
[*]but: after this (and also after re-boot), there is no cupsd or cups-browsed process, 'which cupsd' does not return anything, and:
_there is no /usr/sbin/cupsd at all_.. 
[/LIST]
Seems the package management for CUPS is screwed up completely now!
I guess I'm really lost now.. hope someone has a few hints for me..

Karsten

---

### Post by karsten_df on 2015-02-23
.. after several frustrating hours of trying to fix this still no success:
[LIST]
[*]a lot of files from the 'cups' package (cups_1.7.2-0ubuntu1.2_amd64.deb) are simply not installed,
although I tried to force installation in several way, from the archives, but also from a downloaded .deb file
(sudo dpkg --force-overwrite -i cups_1.7.2-0ubuntu1.2_amd64.deb) 
[*]no error messages during the process of removal / installation neither at the command line, nor in /var/log/dpkg.log 
[/LIST]
It seems that apt-get / dpkg simply does not copy a number of files, maybe because it assumes that these are already in place?
Is there any way to bypass such mechanisms?

---

### Post by tgalati4 on 2015-02-23
So you are saying that the CUPS daemon is not installed?

> tgalati4@Mint17 ~ $ which cupsd
/usr/sbin/cupsd


Something is obviously broken.  Look through your log files and post any errors you find.

```
more /var/log/dpkg.log
```

Spacebar to page through, "q" to quit.  Then clean up your repository cache and check your package manager:

```
sudo apt-get clean
sudo apt-get check
```

---

### Post by karsten_df on 2015-02-24
thanks for your assistance, tgalati4!

I've attached a snippet of dpkg.log which should show my last attempts yesterday to first install, and after checking that many files still were missing, de-installing cups again. Maybe you could find something unusual in there - for me, they look quite inconspicuous.

Both

> sudo apt-get clean 
sudo apt-get check

returned no error (and left no traces in dpkg.log).
I have to leave for office now, but will continue on the topic tonight. Again, thanks for your help!

---

### Post by karsten_df on 2015-02-24
ok, some updates -

I manually extracted the packages cups, cups-client and printer-driver-gutenprint into a temp directory, and actually there's no '<some_temp_dir>/usr/sbin/cupsd' file there either. 
Checking via 
> dpkg -S /usr/sbin/cupsd
showed that cupsd is part of the package cups-daemon which obviously does not get installed on my system when I install cups, cups-client and printer-driver-gutenprint. 

Hmmm... then 
> sudo apt-get purge cups-daemon
removed cups* cups-core-drivers* cups-daemon* printer-driver-gutenprint*

now re-installing cups, and, voila,
> karsten@ubuserv2:~&#10219; which cupsd
/usr/sbin/cupsd
karsten@ubuserv2:~&#10219; cupsctl
_debug_logging=0
_remote_admin=0
_remote_any=0
_share_printers=0
_user_cancel_any=0
BrowseLocalProtocols=dnssd
DefaultAuthType=Basic
JobPrivateAccess=default
JobPrivateValues=default
MaxLogSize=0
SubscriptionPrivateAccess=default
SubscriptionPrivateValues=default
WebInterface=Yes


that looks good for a start. Let's see if CUPS now is coming up.

---

### Post by tgalati4 on 2015-02-24
The quickest check:  [http://localhost:631](http://localhost:631)

Your dpkg log looked normal.

*cups* is a meta package--it describes the complete set of dependencies required to get CUPS up and running:

> tgalati4@Mint17 ~ $ apt-cache depends cups
cups
  Depends: libavahi-client3
  Depends: libavahi-common3
  Depends: libc6
  Depends: libcups2
  Depends: libcupscgi1
  Depends: libcupsimage2
  Depends: libcupsmime1
  Depends: libcupsppdc1
  Depends: libgcc1
  Depends: libstdc++6
  Depends: libusb-1.0-0
 |Depends: debconf
  Depends: <debconf-2.0>
    cdebconf
    debconf
  Depends: libc-bin
    libc-bin:i386
  Depends: cups-core-drivers
    cups-core-drivers:i386
  Depends: **cups-daemon**
    cups-daemon:i386
  Depends: poppler-utils
    poppler-utils:i386
  Depends: procps
    procps:i386
  Depends: ghostscript
    ghostscript:i386
  Depends: lsb-base
  Depends: cups-common
  Depends: cups-server-common
  Depends: cups-client
    cups-client:i386
  Depends: cups-ppdc
    cups-ppdc:i386
  Depends: cups-filters
  Suggests: cups-bsd
    cups-bsd:i386
 |Suggests: foomatic-db-compressed-ppds
  Suggests: foomatic-db
    foomatic-db-compressed-ppds
  Suggests: printer-driver-hpcups
  Suggests: hplip
  Suggests: cups-pdf
  Suggests: udev
    udev:i386
  Suggests: smbclient
  Recommends: avahi-daemon
    avahi-daemon:i386
  Recommends: colord
    colord:i386
 |Recommends: cups-filters
  Recommends: foomatic-filters
  Recommends: printer-driver-gutenprint
 |Recommends: cups-filters
  Recommends: <ghostscript-cups>
  Breaks: foomatic-filters
  Breaks: foomatic-filters:i386
  Breaks: <ghostscript-cups>
  Breaks: <ghostscript-cups:i386>
  Replaces: <ghostscript-cups>
  Replaces: <ghostscript-cups:i386>
  Conflicts: cups:i386


Perhaps you had a bad download or some strange error during the *cups-daemon* package installation.  It's hard to say, because the logs didn't seem to catch it.

---

### Post by karsten_df on 2015-02-24
so the issue seems to be / have been that the dependencies seemed to be met while they actually weren't. 
By now I've removed all of the dependencies of package cups with a 'cups' in the name, and re-installed cups. That's obviously not an exact method, but I was hestitant to remove all the non-cups stuff..

Now, finally the web interface is up again. And I'm back to the very original error - most tabs (administration, printers, ..) produce an 'internal server error'.
Actually my installation is German, so the English terms I'm using are not necessarily correct..
/var/log/cups/error_log is empty after having received the 'internal server error'.

There was however one strange error during the install (again translated from the German message, not necessarily exactly the same as the original English message):
> AppArmor-Parser-Error for /etc/apparmor.d/usr.sbin.cups-browsed in /etc/apparmor.d/usr.sbin.cups-browsed in line 6: 'abstractions/cups-client' could not be opened
The referred apparmor file is attached. I had to rename it to <file>.txt to be able to upload it.
Since cups-client is actually one of the packages I've purged, it should have been installed correctly via the cups dependencies.

Looking at /etc/apparmor.d/abstractions/, this directory does indeed not contain a file named cups-client
> karsten@ubuserv2:~&#10219; dpkg -S /etc/apparmor.d/abstractions/cups-client
apparmor: /etc/apparmor.d/abstractions/cups-client
Should I remove / reinstall apparmor then?

---

### Post by tgalati4 on 2015-02-24
apparmor is the file-protection program.  It prevents a virus or rogue program from changing the contents of system files.  It's possible that apparmor needs purging and reinstallation, because it is preventing the CUPS server from running.  Because you manually installed cups-client, it got added to the apparmor list of tracked files.  

This is what my file looks like:

> tgalati4@Mint17 /etc/apparmor.d $ cat usr.sbin.cups-browsed 
#include <tunables/global>

/usr/sbin/cups-browsed {
  #include <abstractions/base>
  #include <abstractions/nameservice>
  #include <abstractions/cups-client>
  #include <abstractions/dbus>
  #include <abstractions/p11-kit>

  /etc/cups/cups-browsed.conf r,
  /{var/,}run/cups/certs/* r,
  /tmp/** rw,

  # Site-specific additions and overrides. See local/README for details.
  #include <local/usr.sbin.cups-browsed>
}


I don't have the file in /abstractions directory either, so I don't think that is the issue.

Try running cupsd -f and watch the messages.

```
sudo service cups stop
sudo cupsd -f
```

Then bring up the web page move around and then try to print something.

---

### Post by karsten_df on 2015-02-25
Not much news so far.

Purging / reinstalling apparmor actually did not change anything obvious. 
Running cupsd in the foreground  did not print any messages while browsing the cups web interface (and getting the 'internal server error'). 
I tried the same thing on my desktop PC (same ubuntu version 14.04.02, but with unity GUI instead of headless server install) - the web interface performs correctly here, but also no printouts from cupsd -f.

Looking at the processes with 'cups' in their name:
(cups running in the background in both cases)

Server box (faulty):
> karsten@ubuserv2:~&#10219; ps -ef |grep cups                                                                                                         
root      1087     1  0 07:43 ?        00:00:00 /usr/sbin/cups-browsed
root      9405     1  0 07:56 ?        00:00:00 /usr/sbin/cupsd -f


desktop pc (working fine):
> karsten@ubu-T60:~$ ps -ef |grep cups
root      1156     1  0 Feb19 ?        00:00:04 /usr/sbin/cups-browsed
root     24897     1  0 07:37 ?        00:00:00 /usr/sbin/cupsd -f
lp       24905 24897  0 07:37 ?        00:00:00 /usr/lib/cups/notifier/dbus dbus:// 


Could that point to something?

---

### Post by karsten_df on 2015-09-23
I'm adding to this old thread, since I've finally solved my problem now - 
maybe this helps someone stumbling upon this..

with cups debug logging turned on (cupsctl --debug-logging), I found a suspicious line in /var/log/cups/error_log:
> [CGI] Fatal: no entropy gathering module detected
Some googling pointed to a permission problem with /dev/random or /dev/urandom, which were both 
> crw-rw---- 1 root someone
changing this to
> crw-rw-rw- 1 root root
actually solved my problem, and CUPS runs happily everafter, hopefully...

---

### Post by tgalati4 on 2015-09-23
Glad you figured it out.  I've never seen that issue before.  What program did you install that modified your random number generators?  Why does cups even need a random number generator?  Well at least this issue only took 7 months to figure out.  Some problems never get fixed.

---

