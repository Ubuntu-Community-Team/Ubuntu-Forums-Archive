---
title: "Internet will not load automatically"
date: 2006-11-29
forum: General Help
---

### Post by Desy on 2006-11-29
Hi all can someone try and help me i can only connect to the internet manually by opening terminal and typing sudo pppd call speedtch. 

I have made a bootscript by typing in:

#!/bin/bash
modprobe ppp_generic
modprobe pppoatm
count=0
while [ $count -lt 40 ]
do
  sync=$(dmesg | grep 'ADSL line is up')
  if [ ! -z "$sync" ]
  then
    pppd call speedtch
    exit 0
  fi
  sleep 1
  count=$((1+$count))
done
echo "The Speedtouch firmware didn't load"

Then installed the files using:

sudo install -m 744 dial /etc/init.d &&
sudo ln -s ../init.d/dial /etc/rc2.d/S95dial &&
sudo ln -sf ppp/resolv.conf /etc/resolv.conf

But it still wont connect on boot up.

Also when i do connect manually when i go into the ubunto website the connection locke up and i have to reboot, is there a bug fix for this.

Thanks;)

---

