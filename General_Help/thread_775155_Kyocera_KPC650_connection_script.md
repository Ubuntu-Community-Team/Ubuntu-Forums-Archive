---
title: "Kyocera KPC650 connection script"
date: 2008-04-29
forum: General Help
---

### Post by ksauber on 2008-04-29
This script was written for the KCP650 EVDO wireless broadband card, however it can be easily modified to support other wireless broadband cards.

I use the EVDO card in a remote location and experience frequent dropouts/disconnects.  This script is intended to reset the connection as quickly as my location will consistently allow.

Hopefully this will solve somebody else's problem as well.

--------------------------------------------

#!/bin/bash
#  This works well for me.  However, I make no claims that anybody else will find it useful.
#
#  For general use.  

#    Modify these variables to fit your EVDO card

mount_point="/dev/ttyUSB0"
phone_number="1234567890"   ##  10 digit EVDO phone number

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

### Post by islandlvr on 2008-06-20
Hi - I'm new to Ubuntu, and have the same broadband card.  Does your script work under 8.04 version?:p

---

