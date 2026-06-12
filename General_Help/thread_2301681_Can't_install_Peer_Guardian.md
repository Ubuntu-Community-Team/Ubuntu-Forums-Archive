---
title: "Can't install Peer Guardian"
date: 2015-11-04
forum: General Help
---

### Post by persio on 2015-11-04
I'm trying to install PGL following the official instructions and I'm getting this:  ```
# sudo add-apt-repository ppa:jre-phoenix/ppa  This PPA provides offical packages of PeerGuardian Linux (pgl) for all supported Ubuntu series. This archive enhances http://moblock-deb.sourceforge.net, where I offer Debian packages for the current Debian series.  PeerGuardian Linux (pgl) is a privacy oriented firewall application. It blocks connections to and from hosts specified in huge blocklists (thousands or millions of IP ranges). Its origin seeds in targeting aggressive IPs while you use P2P. PeerGuardian Linux is actively developed. However the team is very small and with few spare time. Contributors are welcome! Check out http://peerguardian.sourceforge.net.  For Ubuntu hardy you will find the precessors of pgl here: nfblock/moblock, blockcontrol and mobloquer. They aren't developed any more.  More info: https://launchpad.net/~jre-phoenix/+archive/ubuntu/ppa Press [ENTER] to continue or ctrl-c to cancel adding it  gpg: keyring `/tmp/tmpwnl3d2go/secring.gpg' created gpg: keyring `/tmp/tmpwnl3d2go/pubring.gpg' created gpg: requesting key 9C0042C8 from hkp server keyserver.ubuntu.com gpg: /tmp/tmpwnl3d2go/trustdb.gpg: trustdb created gpg: key 9C0042C8: public key "Launchpad PPA for jre-phoenix" imported gpg: Total number processed: 1 gpg:               imported: 1  (RSA: 1) OK
``` ```
# gpg --keyserver keyserver.ubuntu.com --recv-keys C0145138 gpg: directory `/root/.gnupg' created gpg: new configuration file `/root/.gnupg/gpg.conf' created gpg: WARNING: options in `/root/.gnupg/gpg.conf' are not yet active during this run gpg: keyring `/root/.gnupg/secring.gpg' created gpg: keyring `/root/.gnupg/pubring.gpg' created gpg: requesting key C0145138 from hkp server keyserver.ubuntu.com gpg: /root/.gnupg/trustdb.gpg: trustdb created gpg: key C0145138: public key "jre-phoenix (moblock-deb maintainer) " imported gpg: no ultimately trusted keys found gpg: Total number processed: 1 gpg:               imported: 1  (RSA: 1) 
``` ```
# gpg --export --armor C0145138 | sudo apt-key add - OK 
``` The problem seems to arise here:  ```
$sudo apt-get update (...) Fetched 119 kB in 28s (4.125 B/s)                                                                                                                                                                W: GPG error: http://download.opensuse.org  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A7D1D38BEB6D886 W: Failed to fetch http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu/dists/wily/main/binary-amd64/Packages  404  Not Found  W: Failed to fetch http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu/dists/wily/main/binary-i386/Packages  404  Not Found  W: Failed to fetch http://ppa.launchpad.net/noobslab/evolvere/ubuntu/dists/wily/main/binary-amd64/Packages  404  Not Found  W: Failed to fetch http://ppa.launchpad.net/noobslab/evolvere/ubuntu/dists/wily/main/binary-i386/Packages  404  Not Found  E: Some index files failed to download. They have been ignored, or old ones used instead.
``` ```
$ sudo apt-get install pgld pglcmd pglgui Reading package lists... Done Building dependency tree        Reading state information... Done E: Unable to locate package pgld E: Unable to locate package pglcmd E: Unable to locate package pglgui 
```  I'm running Lubuntu 15.10. Any ideas? (sorry, I don't know why it didn't keep the linebreaks)

---

### Post by QDR06VV9 on 2015-11-04
That is because he has not made wily available yet in his PPA
You may have to edit you [COLOR=#111111][FONT=Consolas]/etc/apt/sources.list for that PPA only.
[/FONT][/COLOR]```
gksudo gedit /etc/apt/sources.list
```
You may have to use leafpad instead of gedit.
[COLOR=#111111][FONT=Consolas]Then the lines should be two of them, should read
[/FONT][/COLOR]```
deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu vivid main [COLOR=#111111][FONT=Consolas]
[/FONT][/COLOR]
deb-src http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu vivid main 
```
[COLOR=#111111][FONT=Consolas]
So change only the word wily to vivid
Then update
```
sudo apt-get update

```[/FONT][/COLOR]```
sudo apt-get install pgld pglcmd pglgui
```[COLOR=#111111][FONT=Consolas]
Then don't forget to update your rules.
```
sudo pglcmd update
```
Should be good to go from there.
Kind Regards[/FONT][/COLOR]

---

### Post by persio on 2015-11-05
Worked like a charm! Thank you very much runrickus! Namaste! :)

---

### Post by Bucky Ball on 2015-11-05
Good news. Please see the first link in my signature to help others. Enjoy. :)

---

### Post by QDR06VV9 on 2015-11-05
I am very honored By your greeting, (Namaste) a knowing that we are all made from the same One Divine Consciousness.
A Grateful Thank You! Best Regards.):P

---

### Post by jre on 2015-11-17
FYI: I updated the pgl packages today, they are available for xenial, wily, vivid, trusty and precise now.
So now there is no need anymore to install from another dist.

---

### Post by QDR06VV9 on 2015-11-17
Thanks! jre && Appreciate your work.


@persio it might be a good idea now to change your source file back to wily.
Should know how to change them, Regards

---

### Post by jre on 2015-11-17
Thanks runrickus, also for your initial and (at that time) correct answer. It's really very good to see a healthy ecosystem.

---

