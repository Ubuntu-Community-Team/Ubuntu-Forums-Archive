---
title: "KPC650 EVDO script"
date: 2008-04-29
forum: General Help
---

### Post by ksauber on 2008-04-29
This was written for a KPC650 EVDO card, but can be modified for others.
Bits and pieces were taken from the fine work of others.

I use a KPC650 EVDO card in a remote location and experience frequent dropouts/disconnects due to a weak signal, so I wrote this to reset the connection as quickly as my location will consistently allow.

Maybe this will solve somebody else's problem as well.

#!/bin/bash
#  
#  For general use.  

#    Modify these variables to fit your EVDO card

mount_point="/dev/ttyUSB0"
phone_number="4083095236"

sudopass=`zenity --entry --hide-text --title "Password" --text "Enter your sudo password here"`

#   Set sudo password
pwdset="false"
count=0
while [ "$pwdset" != "true" ] && [ $count -lt 3 ]; do
sudo -k
count=$(($count+1))
if (echo $sudopass | sudo -S echo -n "" 2> /dev/null); then
pwdset="true"
fi
done

#   Check every 10 seconds if ppp process is alive

while true; do {

    if [ `pgrep ppp` ]; then {
    sleep 10

} else {

sudo pppd $mount_point 115200 debug noauth defaultroute usepeerdns connect-delay 10000 user $phone_number@vzw3g.com password vzw show-password crtscts lock lcp-echo-failure 4 lcp-echo-interval 65535 connect "chat -v ABORT 'NO CARRIER' ABORT 'ERROR' ABORT 'NO DIALTONE' ABORT 'BUSY' ABORT 'NO ANSWER' '' ATZ OK-AT-OK ATDT#777 CONNECT \d\c "

sleep 20

#   Add gateway

gateway=`tail /var/log/messages | grep remote | awk '{print $9}'`
if [ ! $gateway == "" ]; then
   sudo route add default gw $gateway
 else
   sleep 20
fi


}  fi
}  done &

---

