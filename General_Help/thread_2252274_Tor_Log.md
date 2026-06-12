---
title: "Tor Log"
date: 2014-11-10
forum: General Help
---

### Post by seabird22 on 2014-11-10
Why do I have a tor log at /var/log/tor when I have never installed tor? Furthermore, by looking at the log, it seems like tor has been making connections. Can anyone please explain what is going on? I am running 14.04 Thanks in advance.

---

### Post by bapoumba on 2014-11-10
You must have installed something. I just checked and I do not have it.

---

### Post by seabird22 on 2014-11-10
> **bapoumba said:**
> You must have installed something. I just checked and I do not have it.

I am not sure what it could be?


files in  /var/log/tor

```

-rw-r----- 1 debian-tor adm   4219 Nov 10 13:40 log
-rw-r----- 1 debian-tor adm 141709 Nov 10 11:49 log.1
-rw-r----- 1 debian-tor adm   1029 Nov  8 09:58 log.2.gz
-rw-r----- 1 debian-tor adm   4859 Nov  7 10:31 log.3.gz
-rw-r----- 1 debian-tor adm  10174 Nov  6 10:34 log.4.gz
-rw-r----- 1 debian-tor adm   1856 Nov  5 08:20 log.5.gz


```

contents of /var/log/tor/log

```


Nov 10 11:49:14.000 [notice] Tor 0.2.4.20 (git-0d50b03673670de6) opening new log file.
Nov 10 11:49:57.000 [notice] Interrupt: exiting cleanly.
Nov 10 12:51:52.000 [notice] Tor 0.2.4.20 (git-0d50b03673670de6) opening log file.
Nov 10 12:51:52.000 [notice] Parsing GEOIP IPv4 file /usr/share/tor/geoip.
Nov 10 12:51:52.000 [notice] Parsing GEOIP IPv6 file /usr/share/tor/geoip6.
Nov 10 12:51:52.000 [warn] OpenSSL version from headers does not match the version we're running with. If you get weird crashes, that might be why. (Compiled with 1000105f: OpenSSL 1.0.1e 11 Feb 2013; running with 1000106f: OpenSSL 1.0.1f 6 Jan 2014).
Nov 10 12:51:53.000 [notice] Bootstrapped 5%: Connecting to directory server.
Nov 10 12:51:53.000 [warn] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Network is unreachable; NOROUTE; count 1; recommendation warn)
Nov 10 12:51:53.000 [notice] We now have enough directory information to build circuits.
Nov 10 12:51:53.000 [notice] Bootstrapped 80%: Connecting to the Tor network.
Nov 10 12:51:53.000 [warn] Problem bootstrapping. Stuck at 80%: Connecting to the Tor network. (Network is unreachable; NOROUTE; count 2; recommendation warn)
Nov 10 12:51:54.000 [warn] Problem bootstrapping. Stuck at 80%: Connecting to the Tor network. (Network is unreachable; NOROUTE; count 3; recommendation warn)
Nov 10 12:51:55.000 [warn] Problem bootstrapping. Stuck at 80%: Connecting to the Tor network. (Network is unreachable; NOROUTE; count 4; recommendation warn)
Nov 10 12:51:56.000 [warn] Problem bootstrapping. Stuck at 80%: Connecting to the Tor network. (Network is unreachable; NOROUTE; count 5; recommendation warn)
Nov 10 12:51:59.000 [notice] Bootstrapped 85%: Finishing handshake with first hop.
Nov 10 12:52:00.000 [notice] Bootstrapped 90%: Establishing a Tor circuit.
Nov 10 12:52:01.000 [notice] Tor has successfully opened a circuit. Looks like client functionality is working.
Nov 10 12:52:01.000 [notice] Bootstrapped 100%: Done.
Nov 10 13:21:48.000 [notice] Interrupt: exiting cleanly.
Nov 10 13:40:49.000 [notice] Tor 0.2.4.20 (git-0d50b03673670de6) opening log file.
Nov 10 13:40:49.000 [notice] Parsing GEOIP IPv4 file /usr/share/tor/geoip.
Nov 10 13:40:49.000 [notice] Parsing GEOIP IPv6 file /usr/share/tor/geoip6.
Nov 10 13:40:49.000 [warn] OpenSSL version from headers does not match the version we're running with. If you get weird crashes, that might be why. (Compiled with 1000105f: OpenSSL 1.0.1e 11 Feb 2013; running with 1000106f: OpenSSL 1.0.1f 6 Jan 2014).
Nov 10 13:40:50.000 [notice] Bootstrapped 5%: Connecting to directory server.
Nov 10 13:40:50.000 [warn] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Network is unreachable; NOROUTE; count 1; recommendation warn)
Nov 10 13:40:50.000 [notice] We now have enough directory information to build circuits.
Nov 10 13:40:50.000 [notice] Bootstrapped 80%: Connecting to the Tor network.
Nov 10 13:40:50.000 [warn] Problem bootstrapping. Stuck at 80%: Connecting to the Tor network. (Network is unreachable; NOROUTE; count 2; recommendation warn)
Nov 10 13:40:51.000 [warn] Problem bootstrapping. Stuck at 80%: Connecting to the Tor network. (Network is unreachable; NOROUTE; count 3; recommendation warn)
@                                                    




```

contents of /var/log/tor/log.1 ( I only included the last part of the log as the whole log is really long)

```


Nov 09 19:01:36.000 [notice] Bootstrapped 100%: Done.
Nov 10 01:01:31.000 [notice] Heartbeat: Tor's uptime is 6:00 hours, with 0 circuits open. I've sent 160 kB and received 2.45 MB.
Nov 10 01:01:31.000 [notice] Average packaged cell fullness: 77.577%
Nov 10 01:01:31.000 [notice] TLS write overhead: 13%
Nov 10 01:39:40.000 [notice] Interrupt: exiting cleanly.
Nov 10 11:16:29.000 [notice] Tor 0.2.4.20 (git-0d50b03673670de6) opening log file.
Nov 10 11:16:29.000 [notice] Parsing GEOIP IPv4 file /usr/share/tor/geoip.
Nov 10 11:16:29.000 [notice] Parsing GEOIP IPv6 file /usr/share/tor/geoip6.
Nov 10 11:16:29.000 [warn] OpenSSL version from headers does not match the version we're running with. If you get weird crashes, that might be why. (Compiled with 1000105f: OpenSSL 1.0.1e 11 Feb 2013; running with 1000106f: OpenSSL 1.0.1f 6 Jan 2014).
Nov 10 11:16:30.000 [notice] Bootstrapped 5%: Connecting to directory server.
Nov 10 11:16:30.000 [warn] Problem bootstrapping. Stuck at 5%: Connecting to directory server. (Network is unreachable; NOROUTE; count 1; recommendation warn)
Nov 10 11:16:30.000 [notice] We now have enough directory information to build circuits.
Nov 10 11:16:30.000 [notice] Bootstrapped 80%: Connecting to the Tor network.
Nov 10 11:16:30.000 [warn] Problem bootstrapping. Stuck at 80%: Connecting to the Tor network. (Network is unreachable; NOROUTE; count 2; recommendation warn)
Nov 10 11:16:31.000 [warn] Problem bootstrapping. Stuck at 80%: Connecting to the Tor network. (Network is unreachable; NOROUTE; count 3; recommendation warn)
Nov 10 11:16:31.000 [warn] Problem bootstrapping. Stuck at 80%: Connecting to the Tor network. (Network is unreachable; NOROUTE; count 4; recommendation warn)
Nov 10 11:16:31.000 [warn] Problem bootstrapping. Stuck at 80%: Connecting to the Tor network. (Network is unreachable; NOROUTE; count 5; recommendation warn)
Nov 10 11:16:31.000 [warn] Problem bootstrapping. Stuck at 80%: Connecting to the Tor network. (Network is unreachable; NOROUTE; count 6; recommendation warn)
Nov 10 11:16:31.000 [warn] Problem bootstrapping. Stuck at 80%: Connecting to the Tor network. (Network is unreachable; NOROUTE; count 7; recommendation warn)
Nov 10 11:16:31.000 [warn] Problem bootstrapping. Stuck at 80%: Connecting to the Tor network. (Network is unreachable; NOROUTE; count 8; recommendation warn)
Nov 10 11:16:32.000 [warn] Problem bootstrapping. Stuck at 80%: Connecting to the Tor network. (Network is unreachable; NOROUTE; count 9; recommendation warn)
Nov 10 11:16:33.000 [warn] Problem bootstrapping. Stuck at 80%: Connecting to the Tor network. (Network is unreachable; NOROUTE; count 10; recommendation warn)
Nov 10 11:16:35.000 [notice] Bootstrapped 85%: Finishing handshake with first hop.
Nov 10 11:16:37.000 [notice] Bootstrapped 90%: Establishing a Tor circuit.
Nov 10 11:16:38.000 [notice] Tor has successfully opened a circuit. Looks like client functionality is working.
Nov 10 11:16:38.000 [notice] Bootstrapped 100%: Done.
Nov 10 11:49:14.000 [notice] Received reload signal (hup). Reloading config and resetting internal state.
Nov 10 11:49:14.000 [notice] Read configuration file "/usr/share/tor/tor-service-defaults-torrc".
Nov 10 11:49:14.000 [notice] Read configuration file "/etc/tor/torrc".


```

then files below are in red and the contents appear to be encrypted.

```
 

-rw-r----- 1 debian-tor adm   1029 Nov  8 09:58 log.2.gz
-rw-r----- 1 debian-tor adm   4859 Nov  7 10:31 log.3.gz
-rw-r----- 1 debian-tor adm  10174 Nov  6 10:34 log.4.gz
-rw-r----- 1 debian-tor adm   1856 Nov  5 08:20 log.5.gz

```

any help would be appreciated. If you need any other logs please let me know.

---

### Post by bapoumba on 2014-11-10
Running an extension in a browser ?

---

### Post by seabird22 on 2014-11-10
my google chrome extensions are as follows.

[COLOR=#303942][FONT=Ubuntu]Google Docs[/FONT][/COLOR][COLOR=#303942][FONT=Ubuntu] [/FONT][/COLOR][COLOR=#303942][FONT=Ubuntu]0.7
HTTPS Everywhere 2014.9.11
LastPass: Free Password Manager 3.1.65

thanks again.[/FONT][/COLOR]

---

### Post by O9aIevckc0 on 2014-11-10
you must have installed either tor or something that depends on tor
the log shows tor connecting to the tor network (as tor should)

 why do you think those files appear to be encrypted though?

---

### Post by seabird22 on 2014-11-10
> **abpabp said:**
> you must have installed either tor or something that depends on tor
the log shows tor connecting to the tor network (as tor should)

 why do you think those files appear to be encrypted though?

when loaded with vi, the document is all random characters. let me show you what I mean. 

below are the contents of log.2.gz

```


^_<8b>^H^@©/^T^@^Cå<99>]OãF^T<86>ïû+<8e>Vª
R       c'N<82>¹ë<96>*¨V<80><96>*zQíÅÄ><8e>G83ÑÌ<98>lþ}<8f>^]×"_Î^PRli%¸ ñyç9Ç^Nó^LÜ©g`#ðXØ÷Â`Ôc<8c>Á?RY^Qá7øª4°<9e>ß^[ô|^FgSa/X^\°     ë^OGôÅb^\<9e><83><9a>£^Tr
^R^W<90>©)$"ÃÞOwUl¿<88>el=öVZÔ:<9f>Û^Pð»°Eu<94>!<97>Ùòea0
^GÞñ<»XvD>pm<8a>Ëÿ¸¹¿}<80>Û<87>çAY^E<97>¹Ñ<97>&å^Z/*Ò<97>STbþÚ¨áþ¨á<9e>¬^E×ò^[ÜS^O<8f><8f><9f>á^Y)QIH´<9a>A<8a><¦<9f>!Vh<80>Ö<84>^Y·Q
6Åúº^Eþ¢^Qt.Ë   ,<84>M{p<9b>ÀRå0EKo^K^]C¤¹IÑüJ<95><9c>BÄ4µ0AX¤Ë^^<9c>}T³91Çe1=^U<8c>y,HÂ<9a><88>0{^^<82>çÁ'<9c><80>Ï¼þõÚzUÉp³$<81>!üÉeQ18ßìÝ_<9f>ãoJYc5<9f>Ï<89>#ø9<84><8f>JJ<8c>ÊçÄ*<88><85>¦^_<94>^<82>AM<9d>ïI[MòA«I<86>3<98>Ô<99><94>Ò<83>G<9b>GO@í;ÄÃÙ^]Ú<85>ÒO ^LäR#<8f>RN¡×pwÿåþ¯¯7×^P©\Zðh^T^X©Ù^LeÌmy?<88>á¼¹Ù¿<91>îå^BRþ<8c><80>RåÓô^E<81><90><89>Ò³U^V¡Mr<91>Ñý^S:Ê<85>5¯<99>â<98>mõY<7ÅçI®<9a>{Ó^T^]â<9d>§è;M±ß^V^¿Ûx<83>nã^EÝÆ^[v^[oÔm¼±^SÞ -¼+'¼ -<<8f>9ñ<8d><9a>~Ë^W»Ù'!<85>I^K<9a><94>Ë<98>´ã   W;s"´±<90>ª-<8d>¹j<88>¼*:¼1<96><90>«T^¶WmB^[Q^AÛöµ<94>^[0y^T¡1I<9e>eËRÐ(<99>×^YðY©'^C<99> Ò(^SHÃHr^Y^U#à<99>°ËbrÅ^D<8b>Ù7¯·<86>N&Bì¿+ùB^AÇ¡Ï¶,×AG}?ô¯Âà<94>:º;ò(^]u<8c>rÒÑ*Ëÿ^Qut½÷·êè®IvHGw7{^B^]u<98>â+tô<98>)¾£<8e>Vx]ÕÑ¶ñ^NèhÛx^Gt´m¼^C:Ú6Þ^A^]m^[ï<80><8e>Vx]ÕÑ
¯³:Zñ^M[ãsÛÞF*ñ^]Þ8ú,ô<83>^Sê¼C¤«ÎWQ;þ^\üÿèüîõ<9a>u~^LÌ£^OHØï¿Rç©<90><9e>^L¶ó´r¤Îï<8b><Bç<9d>£^\t~3ëGÒùºwï^T:¿<99>Ö1<9d>ß×ì<9b>uÞi<8a>Î:^?Ü^TßMçk¼ÖN^[<8d>:ß>^£Î·<8f>×¨óíã5ê|ûx<8d>:ß>^£Î×x*<9d>6^Zu¾Ækí´Ñ¬ó5_{Ç^M·í*½ã<86>ÃÆá<9d>RçëÈ&'vÓù:jü>:¿o½<83>:OUã*^?G|Á^HÅ3UhÌ^T<8f>Á<88>)-^Lgi>?ïÑ»Å<8b>¥ã+<99>^H^Z<80>,®4hË[.<8a>³@q9ÍÈ^^^<89>âW1¹^ÝãÒ°?l(6}_^TöFE^W1&<Ï¬¹ ^Wuôáè^UÐFÿe<97>1ÿ^Bð¬@;<97>#^@^@


```



Is there a command to show all the apps installed and all the running apps? I want to try to figure this out. 

Thanks again.

---

### Post by bapoumba on 2014-11-11
The .gz file is compressed. You need to extract it before you get to actually read what is in there :)

---

### Post by O9aIevckc0 on 2014-11-11
to get a list of installed programs 

dpkg --get-selections  or
dpkg -l

you should probably send the output to a file  e.g. dpkg --get-selections >proglist 
or dpkg -l proglist
then view it with less as it will probably be long 

to get a list of currently running processes   ps -aux

for the files you mentioned
my guess is they are just compressed log files (pretty normal) would explain the garbaled text in vi
first copy one of those files to your home directory eg  cp  log.2.gz  ~ 
then cd to home 
next gunzip log.2.gz
that should extract the file inside it then you can look at the file (probably just a log file)
(gunzip will remove log.2.gz)

if this solves your problem please mark this thread as solved

---

### Post by btindie on 2014-11-11
> **martin_b2 said:**
> I am not sure what it could be?

then files below are in red and the contents appear to be encrypted.

```
 

-rw-r----- 1 debian-tor adm   1029 Nov  8 09:58 log.2.gz
-rw-r----- 1 debian-tor adm   4859 Nov  7 10:31 log.3.gz
-rw-r----- 1 debian-tor adm  10174 Nov  6 10:34 log.4.gz
-rw-r----- 1 debian-tor adm   1856 Nov  5 08:20 log.5.gz

```

any help would be appreciated. If you need any other logs please let me know.
Files ending with .gz are just gzip compressed to save on disk space, they're not encrypted. They're compressed as part of the logrotate jobs in /etc/logrotate.d/*

You should be able to view them by just using 'less' as it runs it through lesspipe which works out the format and automatically uncompresses it. If that doesn't work you can simply use zless, there's no need to first 'gunzip' the file.

As for Tor. You can work out what might have installed it by checking the reverse dependencies of the tor package.
```
apt-cache rdepends tor
```

This may identify which installed deb depends on tor. It gets the reverse dependencies for tor and greps them from the list of installed debs.
```
dpkg -l | egrep -w "($(apt-cache rdepends tor | tail -n +3 | sed -e 's/^[ ]\+|\?//' | paste -sd\|))"
```

---

### Post by seabird22 on 2014-11-11
> **btindie said:**
> Files ending with .gz are just gzip compressed to save on disk space, they're not encrypted. They're compressed as part of the logrotate jobs in /etc/logrotate.d/*

You should be able to view them by just using 'less' as it runs it through lesspipe which works out the format and automatically uncompresses it. If that doesn't work you can simply use zless, there's no need to first 'gunzip' the file.

As for Tor. You can work out what might have installed it by checking the reverse dependencies of the tor package.
```
apt-cache rdepends tor
```

This may identify which installed deb depends on tor. It gets the reverse dependencies for tor and greps them from the list of installed debs.
```
dpkg -l | egrep -w "($(apt-cache rdepends tor | tail -n +3 | sed -e 's/^[ ]\+|\?//' | paste -sd\|))"
```

result of ```
apt-cache rdepends tor
```

```


Reverse Depends:
  tor:i386
  vidalia
  torsocks
  torchat
  tor-geoipdb
  tor-geoipdb
  tor-geoipdb
  tor-dbg
  tor-arm
  redsocks
  python-txtorcon
  parcimonie
  onioncat
  obfsproxy
  anon-proxy


```

result of ```
dpkg -l | egrep -w "($(apt-cache rdepends tor | tail -n +3 | sed -e 's/^[ ]\+|\?//' | paste -sd\|))"
```


```


ii  tor-geoipdb                                           0.2.4.20-1                                          all          GeoIP database for Tor
ii  torsocks                                              1.3-3                                               amd64        use SOCKS-friendly applications with Tor


```

thanks again.

---

### Post by seabird22 on 2014-11-16
Well, I ended up having to do a re-install since i could not figure out what was using tor, and I don't ever remember installing it.

---

