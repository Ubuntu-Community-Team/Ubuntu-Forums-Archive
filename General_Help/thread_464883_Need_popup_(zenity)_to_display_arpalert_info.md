---
title: "Need popup (zenity) to display arpalert info"
date: 2007-06-05
forum: General Help
---

### Post by mikuskuikku on 2007-06-05
I installed arpalert and got it working (not that hard).
But now I need something to popup when arpalert sends an alarm.
I wrote a script to do this for me, and let arpalert call this script every time i got an alarm.
The script calls zenity to show me the information on my screen (like a popup).
Everything works just fine when I test it.
It works when i do
```
/etc/init.d/arpalert restart
```

But... it don't work when i startup my computer!
Arpalert starts up automatically, and my script writes to the log file, but it can't get zenity to popup until i manually restart /etc/init.d/arpalert.
I run arpalert as root to have permission to run zenity.

Here's the script that runs everytime arpalert gives an alarm.
```

#!/bin/sh
VERBOSE=""
LOGG="yes"
SOURCEPATH="/etc/arpalert/"
MACOWNERLIST="${SOURCEPATH}maclist.dat"
LOGFILE="${SOURCEPATH}alert.log"
TIMESTAMP="`date`"
OWNER="`grep $1 $MACOWNERLIST | cut -f 2`"
NEWNAME="`nbtscan -s ';' $2 | cut -d ';' -f 2 | tr -d '<>'`"
HEADER=""

case "$5" in
        0)      HEADER="0 ip change"
                ;;
        1)      HEADER="1 mac address only detected but not in whithe list"
                ;;
        2)      HEADER="2 mac address in black list"
                ;;
        3)      HEADER="3 new mac address"
                ;;
        4)      HEADER="4 unauthorized arp request"
                ;;
        5)      HEADER="5 abusive number of arp request detected"
                ;;
        6)      HEADER="6 ethernet mac address different from arp mac address"
                ;;
        7)      HEADER="7 global flood detection"
                ;;
        8)      HEADER="8 new mac adress without ip"
                ;;
        9)      HEADER="9 mac change"
                ;;
esac

if [ "$HEADER" ] ; then
/usr/bin/zenity --warning --title="${HEADER}" --text="OWNER =${OWNER}
COMPUTERNAME = ${NEWNAME}
----------
TIMESTAMP = ${TIMESTAMP}
MAC = ${1}
NEW IP = ${2}
OLD IP = ${3}
REPORTER = ${4}
VENDOR = ${6}"
fi

[ "$LOGG" ] && echo "$TIMESTAMP - $* (${OWNER})" >> $LOGFILE

exit 0

```

---

### Post by atlas95 on 2008-05-28
Hello,
could you say me howto configure arpalert and how to call this script?
I launch this script, I have activate log but no popup appears after launch this script.

Thanks...

My arpalert.conf

```

#
# Copyright (c) 2005-2010 Thierry FOURNIER
# $Id: arpalert.conf.in 667 2007-11-17 14:26:13Z  $
# 
# Default config file
# 

# white list
maclist file = "/etc/arpalert/maclist.allow"

# black list
maclist alert file = "/etc/arpalert/maclist.deny"

# dump file
maclist leases file = "/var/lib/arpalert/arpalert.leases"

# list of authorized request
#auth request file = /etc/arpalert/authrq.conf

# log file
log file = "/var/log/arpalert.log"

# pid file
lock file = "/var/run/arpalert.pid"

# log level
use syslog = true

# log level
log level = 6

# user for privilege separation
user = arpalert

# rights for file creation
umask = 177

# only for debugging: this dump paquet received on standard output
dump packet = false

# run the program as daemon ?
daemon = false

# minimun time to wait between two leases dump
dump inter = 5

#Configure the network for catch only arp request.
#The detection type "new_mac" is desactived.
#This mode is used for CPU saving if Arpalert is running on a router
catch only arp = true

# comma separated interfaces to lesson
# if not precised, the soft select the first interface.
# by default select the first interface encontered
interface = eth0,wlan0

# script launched on each detection
# parameters are:
#  - "mac adress of requestor"
#  - "ip of requestor"
#  - "supp. parm."
#  - "ethernet device listening on"
#  - "type of alert"
#  - optional : "ethernet vendor"
# type of alert:
# 0: ip change
# 1: mac address only detected but not in whithe list
# 2: mac address in black list
# 3: new mac address
# 4: unauthorized arp request
# 5: abusive number of arp request detected 
# 6: ethernet mac address different from arp mac address
# 7: global flood detection
# 8: new mac adress without ip
# 9: mac change
action on detect = ""

# module launched on each detection
mod on detect = ""
# this chain is transfered to the init function of module loaded
mod config = ""

# script execution timeout (seconds)
execution timeout = 10

# maximun simultaneous lanched script
max alert = 20

# what data are dumped in leases file
dump black list = false
dump white list = false
dump new address = true

# after this time a mac adress is removed from memory (seconds) (default 1 month)
mac timeout = 259200

# after this limit the memory hash is cleaned (protect to arp flood)
max entry = 1000000

# this permit to send only one mismatch alert in this time (in seconds)
anti flood interval = 5  

# if the number of arp request in seconds exceed this value, all alerts are ignored for 
# "anti flood interval" time
anti flood global = 50

# vendor name
# add the mac vendor field in logs, alerts script and/or module execution
mac vendor file = "/etc/arpalert/oui.txt"
log mac vendor = true
alert mac vendor = true
mod mac vendor = true

# log if the adress is referenced in hash but is not in white list
log referenced address = false
alert on referenced address = false
mod on referenced address = false

# log if the mac adress is in black list
log deny address = true
alert on deny address = true
mod on deny address = true

# log if the adress isn't referenced
log new address = true
alert on new address = true
mod on new address = true

# log if the adress isn't referenced (for mac adress only)
log new mac address = true
alert on new mac address = true
mod on new mac address = true

# log if the ip adress id different from the last arp request with the same mac adress
log ip change = true
alert on ip change = true
mod on ip change = true

# log if the ip adress id different from the last arp request with the same mac adress
log mac change = true
alert on mac change = true
mod on mac change = true

# unauthorized arp request:
# log all the request not authorized in auth file
log unauth request = false
alert on unauth request = false
mod on unauth request = false
# dont analyse arp request for unknow hosts (not in white list)
ignore unknown sender = false
# ignore arp request with mac adresse of the lessoned interfaces for the authorizations checks
ignore me = true
# ignore windows self test
ignore self test = false
# suspend time method:
# 1: ignore all unauth alerts during "anti flood interval" time
# 2: ignore only tuple (mac address, ip address) during "anti flood interval" time
unauth ignore time method = 2

# log if the number of request per seconds are > "max request"
log request abus = true
alert on request abus = true
mod on request abus = true
# maximun request authorized by second
max request = 1000000

# log if the ethernet mac address are different than the arp amc address (only for requestor)
log mac error = true
alert on mac error = true
mod on mac error = true

# log if have too many arp request per seconds
log flood = true
alert on flood	= true
mod on flood = true


```


and the popup script in $HOME/bin/arp-popup.sh

```

#!/bin/sh
VERBOSE="yes"
LOGG="yes"
SOURCEPATH="/etc/arpalert/"
MACOWNERLIST="${SOURCEPATH}maclist.dat"
LOGFILE="/var/log/arpalert.log"
TIMESTAMP="`date`"
OWNER="`grep $1 $MACOWNERLIST | cut -f 2`"
NEWNAME="`nbtscan -s ';' $2 | cut -d ';' -f 2 | tr -d '<>'`"
HEADER=""

case "$5" in
        0)      HEADER="0 ip change"
                ;;
        1)      HEADER="1 mac address only detected but not in whithe list"
                ;;
        2)      HEADER="2 mac address in black list"
                ;;
        3)      HEADER="3 new mac address"
                ;;
        4)      HEADER="4 unauthorized arp request"
                ;;
        5)      HEADER="5 abusive number of arp request detected"
                ;;
        6)      HEADER="6 ethernet mac address different from arp mac address"
                ;;
        7)      HEADER="7 global flood detection"
                ;;
        8)      HEADER="8 new mac adress without ip"
                ;;
        9)      HEADER="9 mac change"
                ;;
esac

if [ "$HEADER" ] ; then
/usr/bin/zenity --warning --title="${HEADER}" --text="OWNER =${OWNER}
COMPUTERNAME = ${NEWNAME}
----------
TIMESTAMP = ${TIMESTAMP}
MAC = ${1}
NEW IP = ${2}
OLD IP = ${3}
REPORTER = ${4}
VENDOR = ${6}"
fi

[ "$LOGG" ] && echo "$TIMESTAMP - $* (${OWNER})" >> $LOGFILE

exit 0

```

---

