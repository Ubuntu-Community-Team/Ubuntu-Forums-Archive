---
title: "Conky and cron"
date: 2016-05-20
forum: General Help
---

### Post by iaincstott on 2016-05-20
Hi guys, hope someone here fancies throwing their 2 cents in.

I am trying to customize conky to display some info, including status of raspberry pi with ping. So conky runs fine, and the script called from my cronjob works fine when ran from the terminal, but when ran from crontab I have a feeling the script crashes on the array ping_ips.

Anyway, here is my script that is called from crontab

```
#!/bin/bash

##Setup working env
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
working_dir=/home/iainstott/.conky/Iains_Desktop/
log_file=~/log_file
rm -rf ${log_file}
touch ${log_file}


##Set Ping IP and list
raspi1=192.168.1.1
raspi2=192.168.1.2
raspi3=192.168.1.3
raspi4=192.168.1.4
raspi5=192.168.1.5
raspi6=192.168.0.129
raspiD=192.168.0.130
server=192.168.0.110
ping_ip=(${raspi1} ${raspi2} ${raspi3} ${raspi4} ${raspi5} ${raspi6} ${raspiD} ${server})


##Central Heating 
heating_dir=/home/pi/GitRepo/centralheating
summer=${heating_dir}/resources/summer
status=${heating_dir}/resources/webstatus
manual=${heating_dir}/resources/status




for i in "${ping_ip[@]}"
do
  if ping -c 1 -W 1 $i > /dev/null; then
  echo "On-Line" >> ${log_file}
  else
  echo "Off-Line" >> ${log_file}
  fi
done


ssh pi@${raspi5} "cat ${summer}" >> ${log_file}
ssh pi@${raspi5} "cat ${manual}" >> ${log_file}
ssh pi@${raspi5} "cat ${status}" >> ${log_file}
echo >> ${log_file}
nm-tool |grep --only-matching '*[^ ][^:]*' |sed 's/^*//' >> ${log_file}
/sbin/ifconfig $1 | grep "inet addr" | awk -F: '{print $2}' | awk '{print $1}' | grep -v '127.0.0.1' >> ${log_file}
wget http://ipinfo.io/ip -qO - >> ${log_file}


sh /home/iainstott/.conky/conky-startup.sh



```

crontab cotains...
```
*/1 * * * * bash /home/iainstott/.bin/conky_cron
```

and I have put
```
SHELL=/bin/bash
```

at the top of my crontab.

Does anyone have any other ideas.

Cheers
Iain

---

