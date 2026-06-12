---
title: "Looking for power ups monitoring software"
date: 2014-01-02
forum: General Help
---

### Post by offir on 2014-01-02
i plugged my computer ups
The software that comes with the ups designed for windows


I'm looking for the equivalent for Linux


I need to log
What is the input voltage to the ups

Is there a parallel software for Linux
And is it possible to do that

---

### Post by tgalati4 on 2014-01-02
What is the model of the UPS?  There is some monitoring available, but without the fancy graphics.

tgalati4@Mint14-Extensa ~ $ apt-cache search apc ups
nut-snmp - network UPS tools - SNMP driver
apcupsd - APC UPS Power Management (daemon)
apcupsd-cgi - APC UPS Power Management (web interface)
apcupsd-doc - APC UPS Power Management (documentation/examples)
collectd-core - statistics collection and monitoring daemon (core system)
conky-all - highly configurable system monitor (all features enabled)
conky-cli - highly configurable system monitor (basic version)
conky-std - highly configurable system monitor (default version)
gkrellmapcupsd - gkrellm plugin displaying the current processor speed
libdapclient3 - Client library for the Network Data Access Protocol
libdapserver7 - Server library for the Network Data Access Protocol
powstatd - Configurable UPS monitoring daemon

[https://help.ubuntu.com/community/apcupsd](https://help.ubuntu.com/community/apcupsd)

---

### Post by offir on 2014-01-02
Model of the ups is "pr 1550"
 [http://www.advice.co.il/data/files/speci%20partnerpc1550%20enN.pdf]("http://www.advice.co.il/data/files/speci%20partnerpc1550%20enN.pdf")

I need it just because of one thing
I need to write a log
Which registered the voltage of the entrance to the ups

Around the clock for a specific period of time
Because of power problems in our area

---

### Post by tgalati4 on 2014-01-02
Install *apcupsd*, plug in the USB cable and see if it can communicate.  It will write log files to /var/log, you can then use the *logger* command to add time-stamped entries into /var/log/syslog.  You can then filter these entries with *grep* and then have just the power data.  Or you can write a cronjob to output the data to a file during the period of interest.

Search the web for acpuspd for different ways to use it.  There are also remote network monitoring tools to the get that data.  But first, see if the USB protocol is compatible with APC's command set.

---

### Post by offir on 2014-01-05
I did not manage a setup or activation
Maybe I did something wrong



this 
```
sudo edit /etc/apcupsd/apcupsd.conf
```

make 
```
Warning: unknown mime-type for "/etc/apcupsd/apcupsd.conf" -- using "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"

```



this
```
/etc/apcupsd/apcupsd.conf

```

make 
```
bash: /etc/apcupsd/apcupsd.conf: Permission denied

```


this
```
sudo /etc/init.d/apcupsd start 
```

make
```
Please check your configuration ISCONFIGURED in /etc/default/apcupsd
```


```
sudo vi /etc/apcupsd/apcupsd.conf
```

make
```
## apcupsd.conf v1.1 ##
#
#  for apcupsd release 3.14.6 (16 May 2009) - debian
#
# "apcupsd" POSIX config file

#
# ========= General configuration parameters ============
#

# UPSNAME xxx
#   Use this to give your UPS a name in log files and such. This
#   is particulary useful if you have multiple UPSes. This does not
#   set the EEPROM. It should be 8 characters or less.
#UPSNAME

# UPSCABLE <cable>
#   Defines the type of cable connecting the UPS to your computer.
#
#   Possible generic choices for <cable> are:
#     simple, smart, ether, usb
#
#   Or a specific cable model number may be used:
#     940-0119A, 940-0127A, 940-0128A, 940-0020B,
#     940-0020C, 940-0023A, 940-0024B, 940-0024C,
#     940-1524C, 940-0024G, 940-0095A, 940-0095B,
#     940-0095C, M-04-02-2000
#
UPSCABLE smart

# To get apcupsd to work, in addition to defining the cable
# above, you must also define a UPSTYPE, which corresponds to
# the type of UPS you have (see the Description for more details).
# You must also specify a DEVICE, sometimes referred to as a port.
# For USB UPSes, please leave the DEVICE directive blank. For
# other UPS types, you must specify an appropriate port or address.
#
# UPSTYPE   DEVICE           Description
# apcsmart  /dev/tty**       Newer serial character device,
#                            appropriate for SmartUPS models using
#                            a serial cable (not USB).
#
# usb       <BLANK>          Most new UPSes are USB. A blank DEVICE
#                            setting enables autodetection, which is
#                            the best choice for most installations.
#
# net       hostname:port    Network link to a master apcupsd
#                            through apcupsd's Network Information
#                            Server. This is used if you don't have
#                            a UPS directly connected to your computer.
#
# snmp      hostname:port:vendor:community
#                            SNMP Network link to an SNMP-enabled
#                            UPS device. Vendor is the MIB used by
#                            the UPS device: can be "APC", "APC_NOTRAP"
#                            or "RFC" where APC is the powernet MIB,
#                            "APC_NOTRAP" is powernet with SNMP trap
#                            catching disabled, and RFC is the IETF's
#                            rfc1628 UPS-MIB. You usually want "APC".
#                            Port is usually 161. Community is usually
#                            "private".
#
# dumb      /dev/tty**       Old serial character device for use
#                            with simple-signaling UPSes.
#
# pcnet    ipaddr:username:passphrase
#                            PowerChute Network Shutdown protocol
#                            which can be used as an alternative to SNMP
#                            with AP9617 family of smart slot cards.
#                            ipaddr is the IP address of the UPS mgmt
#                            card. username and passphrase are the
#                            credentials for which the card has been
#                            configured.
#
UPSTYPE apcsmart
DEVICE /dev/ttyS0

# POLLTIME <int>
#   Interval (in seconds) at which apcupsd polls the UPS for status. This
#   setting applies both to directly-attached UPSes (UPSTYPE apcsmart, usb,
#   dumb) and networked UPSes (UPSTYPE net, snmp). Lowering this setting
#   will improve apcupsd's responsiveness to certain events at the cost of
#   higher CPU utilization. The default of 60 is appropriate for most
#   situations.
#POLLTIME 60

# LOCKFILE <path to lockfile>
#   Path for device lock file. Not used on Win32.
LOCKFILE /var/lock

# SCRIPTDIR <path to script directory>
#   Directory in which apccontrol and event scripts are located.
SCRIPTDIR /etc/apcupsd

# PWRFAILDIR <path to powerfail directory>
#   Directory in which to write the powerfail flag file. This file
#   is created when apcupsd initiates a system shutdown and is
#   checked in the OS halt scripts to determine if a killpower
#   (turning off UPS output power) is required.
PWRFAILDIR /etc/apcupsd

# NOLOGINDIR <path to nologin directory>
#   Directory in which to write the nologin file. The existence
#   of this flag file tells the OS to disallow new logins.
NOLOGINDIR /etc


#
# ==== Configuration statements for Network Information Server ====
#

# NETSERVER [ on | off ] on enables, off disables the network
#  information server. If netstatus is on, a network information
#  server process will be started for serving the STATUS and
#  EVENT data over the network (used by CGI programs).
NETSERVER on

# NISIP <dotted notation ip address>
#  IP address on which NIS server will listen for incoming connections.
#  This is useful if your server is multi-homed (has more than one
#  network interface and IP address). Default value is 0.0.0.0 which
#  means any incoming request will be serviced. Alternatively, you can
#  configure this setting to any specific IP address of your server and
#  NIS will listen for connections only on that interface. Use the
#  loopback address (127.0.0.1) to accept connections only from the
#  local machine.
NISIP 127.0.0.1

# NISPORT <port> default is 3551 as registered with the IANA
#  port to use for sending STATUS and EVENTS data over the network.
#  It is not used unless NETSERVER is on. If you change this port,
#  you will need to change the corresponding value in the cgi directory
#  and rebuild the cgi programs.
NISPORT 3551

# If you want the last few EVENTS to be available over the network
# by the network information server, you must define an EVENTSFILE.
EVENTSFILE /var/log/apcupsd.events

# EVENTSFILEMAX <kilobytes>
#  By default, the size of the EVENTSFILE will be not be allowed to exceed
#  10 kilobytes.  When the file grows beyond this limit, older EVENTS will
#  be removed from the beginning of the file (first in first out).  The
#  parameter EVENTSFILEMAX can be set to a different kilobyte value, or set
#  to zero to allow the EVENTSFILE to grow without limit.
EVENTSFILEMAX 10

# ========== Configuration statements used if sharing =============
#            a UPS with more than one machine

#
# Remaining items are for ShareUPS (APC expansion card) ONLY
#

# UPSCLASS [ standalone | shareslave | sharemaster ]
#   Normally standalone unless you share an UPS using an APC ShareUPS
#   card.
UPSCLASS standalone

# UPSMODE [ disable | share ]
#   Normally disable unless you share an UPS using an APC ShareUPS card.
UPSMODE disable

#
# ===== Configuration statements to control apcupsd system logging ========
#

# Time interval in seconds between writing the STATUS file; 0 disables
STATTIME 0

# Location of STATUS file (written to only if STATTIME is non-zero)
STATFILE /var/log/apcupsd.status

# LOGSTATS [ on | off ] on enables, off disables
# Note! This generates a lot of output, so if
#       you turn this on, be sure that the
#       file defined in syslog.conf for LOG_NOTICE is a named pipe.
#  You probably do not want this on.
LOGSTATS off

# Time interval in seconds between writing the DATA records to
#   the log file. 0 disables.
DATATIME 0

# FACILITY defines the logging facility (class) for logging to syslog.
#          If not specified, it defaults to "daemon". This is useful
#          if you want to separate the data logged by apcupsd from other
#          programs.
#FACILITY DAEMON

#
# ========== Configuration statements used in updating the UPS EPROM =========
#

#
# These statements are used only by apctest when choosing "Set EEPROM with conf
# file values" from the EEPROM menu. THESE STATEMENTS HAVE NO EFFECT ON APCUPSD.
#

# UPS name, max 8 characters
#UPSNAME UPS_IDEN

# Battery date - 8 characters
#BATTDATE mm/dd/yy

# Sensitivity to line voltage quality (H cause faster transfer to batteries)
# SENSITIVITY H M L        (default = H)
#SENSITIVITY H

# UPS delay after power return (seconds)
# WAKEUP 000 060 180 300   (default = 0)
#WAKEUP 60

# UPS Grace period after request to power off (seconds)
# SLEEP 020 180 300 600    (default = 20)
#SLEEP 180

# Low line voltage causing transfer to batteries
# The permitted values depend on your model as defined by last letter
#  of FIRMWARE or APCMODEL. Some representative values are:
#    D 106 103 100 097
#    M 177 172 168 182
#    A 092 090 088 086
#    I 208 204 200 196     (default = 0 => not valid)
#LOTRANSFER  208

# High line voltage causing transfer to batteries
# The permitted values depend on your model as defined by last letter
#  of FIRMWARE or APCMODEL. Some representative values are:
#    D 127 130 133 136
#    M 229 234 239 224
#    A 108 110 112 114
#    I 253 257 261 265     (default = 0 => not valid)
#HITRANSFER 253

# Battery charge needed to restore power
# RETURNCHARGE 00 15 50 90 (default = 15)
#RETURNCHARGE 15

# Alarm delay
# 0 = zero delay after pwr fail, T = power fail + 30 sec, L = low battery, N = never
# BEEPSTATE 0 T L N        (default = 0)
#BEEPSTATE T

# Low battery warning delay in minutes
# LOWBATT 02 05 07 10      (default = 02)
#LOWBATT 2

# UPS Output voltage when running on batteries
# The permitted values depend on your model as defined by last letter
#  of FIRMWARE or APCMODEL. Some representative values are:
#    D 115
#    M 208
#    A 100
#    I 230 240 220 225     (default = 0 => not valid)
#OUTPUTVOLTS 230

# Self test interval in hours 336=2 weeks, 168=1 week, ON=at power on
# SELFTEST 336 168 ON OFF  (default = 336)
#SELFTEST 336





```


this
```
apcaccess status
```

make 
```
Error contacting apcupsd @ localhost:3551: Connection refused
```




What am I doing wrong

---

### Post by tgalati4 on 2014-01-05
Use nano for editing configuration files:

```
sudo nano /etc/apcupsd/acpupsd.conf
```

You have the device as:  DEVICE /dev/ttyS0

Perhaps the device is different:  /dev/ttyS1

```
lsusb
```

Make sure that the apc ups daemon is running:

```
ps -ef | grep apcupsd
```

---

### Post by SeijiSensei on 2014-01-05
The configuration file states:

```
For USB UPSes, please leave the DEVICE directive blank.
```

Here is my apcupsd.conf, though it is for a CentOS server so the directory locations may be slightly different.

```

UPSCABLE usb
UPSTYPE usb
DEVICE 
LOCKFILE /var/lock
SCRIPTDIR /etc/apcupsd
PWRFAILDIR /etc/apcupsd
NOLOGINDIR /etc
ONBATTERYDELAY 6
BATTERYLEVEL 5
MINUTES 3
TIMEOUT 0
ANNOY 300
ANNOYDELAY 60
NOLOGON disable
KILLDELAY 0
NETSERVER on
NISIP 0.0.0.0
NISPORT 3551
EVENTSFILE /var/log/apcupsd.events
EVENTSFILEMAX 10
UPSCLASS standalone
UPSMODE disable
STATTIME 0
STATFILE /var/log/apcupsd.status
LOGSTATS off
DATATIME 0

```

Most of these are the default settings.

---

### Post by offir on 2014-01-05
> tgalati4

    Re: Looking for power ups monitoring software
    Use nano for editing configuration files:


    ```
sudo nano /etc/apcupsd/acpupsd.conf
```

    You have the device as: DEVICE /dev/ttyS0

    Perhaps the device is different: /dev/ttyS1


    ```
lsusb
```

    Make sure that the apc ups daemon is running:


    ```
ps -ef | grep apcupsd
```




```
sudo nano /etc/apcupsd/acpupsd.conf

```

make a blank file I added
Image

```
 lsusb
```

give 

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0d9f:0002 Powercom Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0557:2213 ATEN International Co., Ltd 
Bus 002 Device 002: ID 0557:7000 ATEN International Co., Ltd Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


```
ps -ef | grep apcupsd
```

give
```
offir     3804  3785  0 18:50 pts/0    00:00:00 grep --color=auto apcupsd

```

---

### Post by tgalati4 on 2014-01-05
Spelling is important in linux.  In fact it is so important that many things won't work if not spelled correctly.

sudo nano /etc/apcupsd/**acp**upsd.conf

Your ups server daemon (apcupsd) is not running; it should be shown in the process list.

```
sudo service apcupsd restart
```

---

### Post by offir on 2014-01-06
I wrote it correctly
Or rather
I did copy-paste
In both cases the result is the same
Opens an empty file
Like the picture I added to previous post
What am I supposed to write in the file ?


```
sudo service apcupsd restart
```

I wrote it down
But as before it did not work
I guess because the previous step has not been completed

---

### Post by tgalati4 on 2014-01-06
Look in /etc/default for an example configuration file.  Then copy that over to the new file with any custom changes that you want to make.

---

### Post by tgalati4 on 2014-01-06
Did you perform this step?

Then you must edit the file /etc/default/apcupsd and change the ISCONFIGURED no to ISCONFIGURED yes. 

[https://help.ubuntu.com/community/apcupsd](https://help.ubuntu.com/community/apcupsd)

Also, there should be a program called *apctest*.  See if that runs.

The configuration file can be located in /etc/default/apcupsd (the default configuration) and the custom configuration (your changes go here) /etc/apcupsd/apcupsd.conf.  Post the output of both.

---

