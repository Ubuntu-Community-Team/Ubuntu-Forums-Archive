---
title: "Building Nmap"
date: 2014-10-03
forum: General Help
---

### Post by elysian2 on 2014-10-03
I am trying to build the latest version of nmap 6.47 in 14.04 but I've been getting an error.


```

apt-get -y install build-essential
wget -qO- http://nmap.org/dist/nmap-6.47.tgz | tar xz -C /tmp/ && cd /tmp/nmap-6.47/ && ./configure && make && make install

```

```

...
make[1]: Entering directory `/tmp/nmap-6.47/nsock/src'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/tmp/nmap-6.47/nsock/src'
cd ncat && make
make[1]: Entering directory `/tmp/nmap-6.47/ncat'
Compiling liblua
make[2]: Entering directory `/tmp/nmap-6.47/liblua'
make[2]: `liblua.a' is up to date.
make[2]: Leaving directory `/tmp/nmap-6.47/liblua'
make[1]: Leaving directory `/tmp/nmap-6.47/ncat'
Compiling libnetutil
cd libnetutil && make
make[1]: Entering directory `/tmp/nmap-6.47/libnetutil'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/tmp/nmap-6.47/libnetutil'
make nmap build-zenmap build-ndiff build-nping
make[1]: Entering directory `/tmp/nmap-6.47'
make[1]: `nmap' is up to date.
cd zenmap && /usr/bin/python3 install_scripts/utils/version_update.py "6.47"
make[1]: Leaving directory `/tmp/nmap-6.47'
.py", line 135
    print ">>> Updating %s" % os.path.join(base_dir, VERSION)
                          ^
SyntaxError: invalid syntax
make[1]: *** [zenmap/zenmapCore/Version.py] Error 1
make: *** [all] Error 2

```

---

### Post by elysian2 on 2014-10-03
When building from the github source, I seem get a different error.

```

g++ -c -I./liblinear -I./liblua -I./libdnet-stripped/include -I./libpcre  -I./libpcap -I./nbase -I./nsock/include -DHAVE_CONFIG_H -DNMAP_NAME=\"Nmap\" -DNMAP_URL=\"http://nmap.org\" -DNMAP_PLATFORM=\"x86_64-unknown-linux-gnu\" -DNMAPDATADIR=\"/usr/local/share/nmap\" -D_FORTIFY_SOURCE=2 -g -O2 -Wall -fno-strict-aliasing   nse_lpeg.cc -o nse_lpeg.o
Compiling nmap
rm -f nmap
g++ -Wl,-E  -Lnbase -Lnsock/src/   -o nmap charpool.o FingerPrintResults.o FPEngine.o FPModel.o idle_scan.o MACLookup.o main.o nmap_dns.o nmap_error.o nmap.o nmap_ftp.o NmapOps.o NmapOutputTable.o nmap_tty.o osscan2.o osscan.o output.o payload.o portlist.o portreasons.o protocols.o scan_engine.o service_scan.o services.o TargetGroup.o Target.o targets.o tcpip.o timing.o traceroute.o utils.o xml.o nse_main.o nse_utility.o nse_nsock.o nse_dnet.o nse_fs.o nse_nmaplib.o nse_debug.o nse_pcrelib.o nse_binlib.o nse_bit.o nse_lpeg.o -lnbase -lnsock libpcre/libpcre.a libpcap/libpcap.a  libnetutil/libnetutil.a ./libdnet-stripped/src/.libs/libdnet.a ./liblua/liblua.a ./liblinear/liblinear.a -ldl 
cd zenmap && /usr/bin/python3 setup.py build 
  File "setup.py", line 350
    mode = ((os.stat(uninstaller_filename)[ST_MODE]) | 0555) & 07777
                                                          ^
SyntaxError: invalid token
Makefile:310: recipe for target 'build-zenmap' failed
make[1]: *** [build-zenmap] Error 1
make[1]: Leaving directory '/tmp/nmap'
Makefile:115: recipe for target 'all' failed
make: *** [all] Error 2

```

---

### Post by elysian2 on 2014-10-03
Apparently I was missing a python package. Thanks for the help everyone.

---

