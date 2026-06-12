---
title: "some cron help"
date: 2019-08-09
forum: General Help
---

### Post by mafia1245 on 2019-08-09
so i use mhddfs to pool some drives for a single storage point.... however the mhddfs likes to cut out for some reason. anyway i wrote a small bash script to reset it. and i want to run this via cron automatically so i don't have to keep ssh'ing in and manually running it. i set it up like below but its not working --- i still have to manually run it. any advice?


crontab -e 
```
*/10 * * * * bash ~/Documents/restor.sh
```


restore.sh
```
#! /bin/bash
if [ !  -f "/storage/.not-mounted" ] ; then
    sudo umount -l /storage
    echo ****[PW]**** | cmd
    sudo mount -a
fi
```

---

### Post by spjackson on 2019-08-10
sudo doesn't work from cron because it needs to prompt for the password. Take out the sudo and put it in root's crontab with 'sudo crontab -e'.

---

### Post by mafia1245 on 2019-08-10
ok thanks --- ill try that and get back to you

---

