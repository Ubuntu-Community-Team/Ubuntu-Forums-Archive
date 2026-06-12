---
title: "Assistance with bash script for syncing removeable drives"
date: 2016-05-08
forum: General Help
---

### Post by norjms on 2016-05-08
I'm having an issue trying to get a bash script to work. I want to sync directories to usb hard drives. It needs to first ensure that the drives are mounted and that the syncing app isn't already running. If it isn't then start the app. If the drive isn't mounted then skip it and move on to the next drive. Here is what I have so far:

```
#!/bin/bash
if mount | grep /mnt/rdrivea > /dev/null; then
    echo "rdrivea is mounted"
        if
                driveastat=$(ps -Af | lsyncd)
                $driveastat | grep /mnt/rdrivea > /dev/null; then
                echo "rdrivea is already mounted"
        else
                lsyncd -pidfile /home/norjms/logs/rdriveb.pid -direct /mnt/array/data/ /mnt/rdrivea/
        fi
else
    echo "rdrivea is not mounted"
    rdriveapid=$(</home/norjms/logs/rdrivea.pid)
    kill $rdriveapid
fi
if mount | grep /mnt/rdriveb > /dev/null; then
    echo "rdriveb is mounted"
        if
                drivebstat=$(ps -Af | lsyncd)
                $drivebstat | grep /mnt/rdriveb > /dev/null; then
                echo "rdriveb is already mounted"
        else
                lsyncd -pidfile /home/norjms/logs/rdriveb.pid -direct /mnt/array/data/ /mnt/rdriveb/
        fi
else
    echo "rdriveb is not mounted"
    rdrivebpid=$(</home/norjms/logs/rdriveb.pid)
    kill $rdrivebpid
fi
```

I am getting this error right now.

```
./check.drives: line 20: USAGE:: command not found
```

Thanks for the assistance

---

### Post by SeijiSensei on 2016-05-08
Try moving "drivebstat=$(ps -Af | lsyncd)" above the preceding "if".

---

### Post by steeldriver on 2016-05-08
Did you perhaps mean

```

drivebstat=$(ps -Af | [COLOR=#0000ff]grep[/COLOR] lsyncd)

```

I'm not sure what the next line is supposed to do (I'm not familiar with lsyncd) - maybe what you really want is just

```

if ps -Af | grep lsyncd | grep /mnt/rdriveb ...

```

?

---

### Post by norjms on 2016-05-08
Just adding some notes so you can understand what I'm trying to accomplish```

#!/bin/bash

#checks to see if the drive is mounted as it is a usb drive
if mount | grep /mnt/rdrivea > /dev/null; then
    echo "rdrivea is mounted"
        if
                #sends output of ps -Af | lsyncd to $driveastat var
driveastat=$(ps -Af | lsyncd)
                #if the drive is mounted at /mnt/rdrivea and lsyncd is already running then I want to escape to the next drive check
$driveastat | grep /mnt/rdrivea > /dev/null; then
                echo "rdrivea is already mounted"
        else
#if the drive is mounted but lsyncd is not running start lsyncd to initiate the sync process and writes the process pid to /home/norjms/logs/rdriveb.pid
                lsyncd -pidfile /home/norjms/logs/rdriveb.pid -direct /mnt/array/data/ /mnt/rdrivea/
        fi
else
echo "rdrivea is not mounted"
    #drive is not mounted so I want to kill any unneeded lsync processes
rdriveapid=$(</home/norjms/logs/rdrivea.pid)
   kill $rdriveapid
fi
#do it all over again for another drive
if mount | grep /mnt/rdriveb > /dev/null; then
    echo "rdriveb is mounted"
        if
                drivebstat=$(ps -Af | lsyncd)
                $drivebstat | grep /mnt/rdriveb > /dev/null; then
                echo "rdriveb is already mounted"
        else
                lsyncd -pidfile /home/norjms/logs/rdriveb.pid -direct /mnt/array/data/ /mnt/rdriveb/
        fi
else
    echo "rdriveb is not mounted"
    rdrivebpid=$(</home/norjms/logs/rdriveb.pid)
    kill $rdrivebpid
fi


```
There maybe a better way to accomplish this but this is my weak attempt at it

---

