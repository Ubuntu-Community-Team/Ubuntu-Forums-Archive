---
title: "hdparm.conf"
date: 2014-03-08
forum: General Help
---

### Post by theproject2 on 2014-03-08
Hi,

i actually have a problem with hdparm.conf. (Ubuntu Server 12.04) After susoending hdparm seems to be ignored:

/dev/sdb {
spindown_time = 121
}
/dev/sdc {
spindown_time = 121
}

So i tried that one(sleep.d):

#!/bin/bash

case "$1" in    thaw|resume)              
  hdparm -S 121 /dev/sdb        
  hdparm -S 121 /dev/sdc        
;;
esac

But it dosnt seem to work either,Does someone know how to fix that?

---

### Post by theproject2 on 2014-03-09
no one?

---

### Post by Dave_L on 2014-03-09
You might experiment with sdparm, and see if it works better:
[http://manpages.ubuntu.com/manpages/lucid/en/man8/sdparm.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/sdparm.8.html)

---

### Post by theproject2 on 2014-03-11
Thanks, but - may i'm wrong - the disks are connected via sata and not via scsi. Somehow i have to reaply the hdparm settings after resume, therefore i tried the stuff with /pm/sleep.d/ - May someone know where the log files are located, so could figure out if the script is actually called or not

---

### Post by Dave_L on 2014-03-11
Check /var/log/pm-suspend.log

You could also add your own logging for debug purposes:

```
#!/bin/bash

LOG='/tmp/hdparmtask.log'

date >>"$LOG"
echo "$0" "$1" >>"$LOG"

case "$1" in thaw|resume)
   echo Resuming >>"$LOG"
   hdparm -S 121 /dev/sdb
   hdparm -S 121 /dev/sdc
   ;;
esac

```

Make sure the file in /etc/pm/sleep.d/ is executable (permissions 755).

Using the hardcoded device names (sdb,sdc) might be problematic, since those names get assigned dynamically.

---

### Post by theproject2 on 2014-03-11
> **Dave_L said:**
> Check /var/log/pm-suspend.log    Checked that, no log file located there.    > **Dave_L said:**
>  You could also add your own logging for debug purposes:   ```
 #!/bin/bash   LOG='/tmp/hdparmtask.log'   date >>"$LOG" echo "$0" "$1" >>"$LOG"  case "$1" in thaw|resume)     echo Resuming >>"$LOG"     hdparm -S 121 /dev/sdb     hdparm -S 121 /dev/sdc     ;;  esac 
```   Ill tried it, but actually no log file is created. Sry may i made something wrong, i am kinda new to this   > **Dave_L said:**
>  Make sure the file in /etc/pm/sleep.d/ is executable (permissions 755).  Using the hardcoded device names (sdb,sdc) might be problematic, since those names get assigned dynamically.  It is executable ( sudo chmod +x filename). Yep i know, thought about disk by uuid for the long run, after i get this working somehow :)

---

### Post by Dave_L on 2014-03-11
Please post the output from:
```
ll -h /etc/pm/sleep.d/
```

Also post your script in that directory, using [ code ] ... [ /code ] tags.

---

### Post by theproject2 on 2014-03-11
```

drwxr-xr-x 2 root root 4.0K Mar  8 10:51 ./
drwxr-xr-x 3 root root 4.0K Mar  6 13:09 ../
-rwxr-xr-x 1 root root  210 Dec  6 11:06 10_grub-common*
-rwxr-xr-x 1 root root  580 Nov  9  2011 10_unattended-upgrades-hibernate*
-rwx------ 1 root root  125 Mar  9 11:18 15_powersave*
-rwx------ 1 root root  198 Mar 11 14:03 20_hdparm*

```

edit: i will make them executable via chmod 755

---

### Post by theproject2 on 2014-03-11
```

#!/bin/bash

LOG='/tmp/hdparmtask.log'

date >>"$LOG"
echo "$0" "$1" >>"$LOG"

case "$1" in thaw|resume)
   echo Resuming >>"$LOG"
   hdparm -S 121 /dev/sdb
   hdparm -S 121 /dev/sdc
   ;;
esac

```

---

### Post by theproject2 on 2014-03-11
I made them executable via chmod 755

```

drwxr-xr-x 2 root root 4.0K Mar  8 10:51 ./
drwxr-xr-x 3 root root 4.0K Mar  6 13:09 ../
-rwxr-xr-x 1 root root  210 Dec  6 11:06 10_grub-common*
-rwxr-xr-x 1 root root  580 Nov  9  2011 10_unattended-upgrades-hibernate*
-rwxr-xr-x 1 root root  125 Mar  9 11:18 15_powersave*
-rwxr-xr-x 1 root root  194 Mar 11 14:29 20_hdparm*

```

but still disks are not going to sleep anymore, and there is no logfile

---

### Post by theproject2 on 2014-03-12
Somebody please help me, it drives me nuts...

---

### Post by matt_symes on 2014-03-13
Hi

Try using  the full path to hdparm.

On my machine
```

matthew-S206:/home/matthew % which hdparm
/sbin/hdparm
matthew-S206:/home/matthew %
```

Kind regards

---

### Post by theproject2 on 2014-03-13
How do i figure that out? I only found the config file located in /etc

edit: got it, ill try it :)

---

### Post by theproject2 on 2014-03-15
Problem solved. Finally! The Thing was, i always used uswusp for suspending the server via sudo s2ram. After i switched to pm-suspend everything worked as it should. The Server was going to suspend and after resuming the hdparm.conf settings were acknowledged.

Anyway thanks for your patience and effort :)

---

