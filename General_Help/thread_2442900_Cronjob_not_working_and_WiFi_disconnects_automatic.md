---
title: "Cronjob not working and WiFi disconnects automatically"
date: 2020-05-08
forum: General Help
---

### Post by daddyodevil on 2020-05-08
My main problem is that my wifi gets disconnected automatically showing a  '?'(question mark) on the icon in the panel. I can switch it off and  back on to make it function normally again.

My chipset -

    ```
[FONT=courier new]
lspci | grep -i wireless
02:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)[/FONT]

```

Things I have tried -

Setting the following to 1, 2, 0 - ```
/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

Replacing my original files by the ones here - ```
https://github.com/kvalo/ath10k-firmware/tree/master/QCA6174
```

And some things here and there that I don't remember.

The solution that finally works for me is running the following script every time after boot  -

    ```

#!/usr/bin/env bash
DISCONECT_COMMAND="nmcli d disconnect wlp2s0"
RECONECT_COMMAND="nmcli d connect wlp2s0"
SLEEP_INTERVAL=10
    
function is_down {
    ! ping -q -c 1 -W 1 "$1" &>/dev/null
}
    
  
while true; do
    # check multiple sites, if one is up then there is internet
    if  is_down "google.com" && is_down "1.1.1.1" &&  is_down "facebook.com" && is_down "8.8.8.8" ; then 
        eval "$DISCONECT_COMMAND"
    date
        eval "$RECONECT_COMMAND"
    fi
    sleep "$SLEEP_INTERVAL";
    done

```


But I am having to this manually as writing a cronjob for it didn't help.

My crontab file -

    ```

...
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
# 
# For more information see the manual pages of crontab(5) and cron(8)
# 
# m h  dom mon dow   command
    
@reboot sleep 600 && /home/puku/reconnect_wifi.sh

```

My crontab logs (not giving the whole thing)-

```

...
May  7 16:30:01 ayanG CRON[4626]: (root) CMD ([ -x  /etc/init.d/anacron ] && if [ ! -d /run/systemd/system ]; then  /usr/sbin/invoke-rc.d anacron start >/dev/null; fi)
May  7 17:17:01 ayanG CRON[4900]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  7 17:25:57 ayanG cron[1042]: (CRON) INFO (pidfile fd = 3)
May  7 17:25:57 ayanG cron[1042]: (CRON) INFO (Running @reboot jobs)
May  7 17:25:57 ayanG CRON[1102]: (puku) CMD (sleep 600 && /home/puku/reconnect_wifi.sh)
May  7 17:30:01 ayanG CRON[3606]: (root) CMD ([ -x  /etc/init.d/anacron ] && if [ ! -d /run/systemd/system ]; then  /usr/sbin/invoke-rc.d anacron start >/dev/null; fi)
May  7 18:17:01 ayanG CRON[4999]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  7 18:30:01 ayanG CRON[5329]: (root) CMD ([ -x  /etc/init.d/anacron ] && if [ ! -d /run/systemd/system ]; then  /usr/sbin/invoke-rc.d anacron start >/dev/null; fi)
May  7 19:17:01 ayanG CRON[6507]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  7 19:30:01 ayanG CRON[6927]: (root) CMD ([ -x  /etc/init.d/anacron ] && if [ ! -d /run/systemd/system ]; then  /usr/sbin/invoke-rc.d anacron start >/dev/null; fi)
May  7 20:17:01 ayanG CRON[7981]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  7 20:30:01 ayanG CRON[8768]: (root) CMD ([ -x  /etc/init.d/anacron ] && if [ ! -d /run/systemd/system ]; then  /usr/sbin/invoke-rc.d anacron start >/dev/null; fi)
May  7 21:17:01 ayanG CRON[12760]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  7 21:30:02 ayanG CRON[14544]: (root) CMD ([ -x  /etc/init.d/anacron ] && if [ ! -d /run/systemd/system ]; then  /usr/sbin/invoke-rc.d anacron start >/dev/null; fi)
...

```

I am using Ubuntu 20.04 with 5.4.0-29-generic kernel, but this problem was there is in 18.04 as well and Ubuntu derivatives.
Any help is really appreciated.

---

### Post by wildmanne39 on 2020-05-08
Hello and welcome to the forum.

Thread closed. Please use your thread located here:

[https://ubuntuforums.org/showthread.php?t=2442836](https://ubuntuforums.org/showthread.php?t=2442836)

we do not allow more then one thread per topic.

If you do not receive a reply you can bump your thread once every twelve hours to keep it in view.

Thanks

---

