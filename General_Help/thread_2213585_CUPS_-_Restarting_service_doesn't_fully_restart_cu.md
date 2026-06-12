---
title: "CUPS - Restarting service doesn't fully restart cups -- Unable to bind socket"
date: 2014-03-27
forum: General Help
---

### Post by Jens_Bodal on 2014-03-27
So if I do a reboot of my linux machine cups will load up fine.  

However restarting the server doesn't seem to fully stop the cups daemon

```
sudo lsof -i:631

COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
cupsd   2037 root   10u  IPv4  16143      0t0  TCP *:ipp (LISTEN)
cupsd   2037 root   11u  IPv6  16144      0t0  TCP *:ipp (LISTEN)

sudo /etc/init.d/cups stop
sudo lsof -i:631

COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
cupsd   2037 root   10u  IPv4  16143      0t0  TCP *:ipp (LISTEN)
cupsd   2037 root   11u  IPv6  16144      0t0  TCP *:ipp (LISTEN)

sudo tail -f /var/log/cups/error_log

E [27/Mar/2014:09:31:39 -0700] Unable to bind socket for address 0.0.0.0:631 - Address already in use.
E [27/Mar/2014:09:31:39 -0700] Unable to bind socket for address [v1.::]:631 - Address already in use.

```

Yesterday this was causing a lot of issues with trying to configure cups as restarting the service wouldn't allow me to log into it and I would have to change the listen port, restart it, then change the listen port back and restart again to have it show on the correct port.  Any idea what would be causing this?

As I said when I restart the machine the bind socket error isn't in the logs, but when I restart cups it shows up and will sometimes cause issues.

```

dpkg -l | grep -i cups

ii  cups                                 1.7.0~rc1-0ubuntu5.2                    i386         Common UNIX Printing System(tm) - server
rc  cups-browsed                         1.0.40-0ubuntu1.1                       i386         OpenPrinting CUPS Filters - cups-browsed
ii  cups-client                          1.7.0~rc1-0ubuntu5.2                    i386         Common UNIX Printing System(tm) - client programs (SysV)
ii  cups-common                          1.7.0~rc1-0ubuntu5.2                    all          Common UNIX Printing System(tm) - common files
ii  cups-daemon                          1.7.0~rc1-0ubuntu5.2                    i386         Common UNIX Printing System(tm) - daemon
ii  cups-filters                         1.0.40-0ubuntu1.1                       i386         OpenPrinting CUPS Filters
ii  cups-pk-helper                       0.2.5-0ubuntu1                          i386         PolicyKit helper to configure cups with fine-grained privileges
ii  cups-ppdc                            1.7.0~rc1-0ubuntu5.2                    i386         Common UNIX Printing System(tm) - PPD manipulation utilities
ii  cups-server-common                   1.7.0~rc1-0ubuntu5.2                    all          Common UNIX Printing System(tm) - server common files
ii  cupswrappermfc7340                   2.0.2-1                                 i386         Brother MFC7340 CUPS wrapper driver
ii  libcups2:i386                        1.7.0~rc1-0ubuntu5.2                    i386         Common UNIX Printing System(tm) - Core library
ii  libcupscgi1:i386                     1.7.0~rc1-0ubuntu5.2                    i386         Common UNIX Printing System(tm) - CGI library
ii  libcupsfilters1:i386                 1.0.40-0ubuntu1.1                       i386         OpenPrinting CUPS Filters - Shared library
ii  libcupsimage2:i386                   1.7.0~rc1-0ubuntu5.2                    i386         Common UNIX Printing System(tm) - Raster image library
ii  libcupsmime1:i386                    1.7.0~rc1-0ubuntu5.2                    i386         Common UNIX Printing System(tm) - MIME library
ii  libcupsppdc1:i386                    1.7.0~rc1-0ubuntu5.2                    i386         Common UNIX Printing System(tm) - PPD manipulation library
ii  libfontembed1:i386                   1.0.40-0ubuntu1.1                       i386         OpenPrinting CUPS Filters - Font Embed Shared library
ii  printer-driver-gutenprint            5.2.9-1ubuntu2                          i386         printer drivers for CUPS
ii  python-cups                          1.9.63-0ubuntu1                         i386         Python bindings for CUPS
ii  python-cupshelpers                   1.4.2+20130920-0ubuntu1.2               all          Python modules for printer configuration with CUPS

```

---

