---
title: "Delay starting daemon?"
date: 2017-06-22
forum: General Help
---

### Post by goodomens on 2017-06-22
My transmission-bt daemon seems to start too quickly causes issues with my NFS share (I get an error "No data found! Ensure your drives are connected or use "Set Location," which I think is caused by the share not coming up in time).

I've tried adding this to the start script (in init.d):

```
    log_daemon_msg "Checking if shares are mounted" "$NAME"
    count=0
    while [ ! -f /home/pi/nas/public/Downloads/check.txt ]
    do
        log_daemon_msg "Waiting 30 seconds to allow for mounting" "$NAME"
        sleep 30
        count=$((count+1))
        if [ $count -eq 10 ]; then
            log_daemon_msg "Giving up after 10 retries. Please check network and mounts" "$NAME"
            exit 1
        fi
    done
    log_daemon_msg "Starting bittorrent daemon" "$NAME"
    start_daemon
    ;;
```

But the script seems to ignore any changes I make (i've even tried putting in a sleep 30 line).  I've also try adding 99 to the symblink file (my computer is at run level 5 for some reason).  This is a vanilla 17 server install

Thanks!

---

