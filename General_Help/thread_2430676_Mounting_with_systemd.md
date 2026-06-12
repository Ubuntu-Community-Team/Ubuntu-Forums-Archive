---
title: "Mounting with systemd"
date: 2019-11-05
forum: General Help
---

### Post by theonlytalkinggoat on 2019-11-05
I am trying to setup a disk to mount using a systemd service. I have performed the following...

Created a file in [FONT=courier new]/etc/systemd/system[/FONT] called [FONT=courier new]media-backup.mount[/FONT]. I want the disk to mount in /media/backup

Placed the following in the file:
```

[Unit]Description=Additional drive

[Mount]
What=$(blkid | grep cf96668e-c1cd-43df-a4e8-1923c90a4063 | awk '{print $1}' | sed 's/:$//')
Where=/media/backup/
Type=ext4
Options=defaults


[Install]
WantedBy=multi-user.target

```

Initialized the file using **[FONT=courier new][/FONT]**[FONT=courier new]systemctl enable media-backup.mount[/FONT][B][FONT=courier new]

[/FONT][/B]However, when I try to load the drive, I get
```
 
systemd[1]: Reloading.
systemd-udevd[15802]: udevd message (RELOAD) received
systemd[1]: Mounting Additional drive...
mount[3502]: mount: /media/backup: can't find in /etc/fstab.
media-backup.mount: Mount process exited, code=exited status=1
media-backup.mount: Failed with result 'exit-code'.
Failed to mount Additional drive.

```

When I ask for a status, it tells me....
```

systemctl status media-backup.mount
&#9679; media-backup.mount - Additional drive
   Loaded: loaded (/etc/systemd/system/media-backup.mount; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Tue 2019-11-05 19:54:49 CST; 8s ago
    Where: /media/backup
     What: $(blkid | grep cf96668e-c1cd-43df-a4e8-1923c90a4063 | awk '{print $1}' | sed 's/:$//')
  Process: 3899 ExecMount=/bin/mount $(blkid | grep cf96668e-c1cd-43df-a4e8-1923c90a4063 | awk '{print $1}' | sed 's/:$//') /media/backup


Nov 05 19:54:49 pbx-host systemd[1]: Mounting Additional drive...
Nov 05 19:54:49 pbx-host systemd[1]: media-backup.mount: Mount process exited, code=exited status=1
Nov 05 19:54:49 pbx-host systemd[1]: media-backup.mount: Failed with result 'exit-code'.
Nov 05 19:54:49 pbx-host mount[3899]: mount: /media/backup: can't find in /etc/fstab.
Nov 05 19:54:49 pbx-host systemd[1]: Failed to mount Additional drive.

```

I can mount the drive perfectly fine using [FONT=courier new]mount $(blkid | grep cf96668e-c1cd-43df-a4e8-1923c90a4063 | awk '{print $1}' | sed 's/:$//') /media/backup[/FONT]

What am I doing wrong?

---

### Post by TheFu on 2019-11-05
```
mount[3502]: mount: /media/backup: can't find in /etc/fstab.
```

So, is the mount data listed in the fstab?
I've avoided knowing anything about systemd and avoid using solutions from that team whenever possible. I would use **autofs** for this, which has been working and around for decades.

---

### Post by theonlytalkinggoat on 2019-11-05
Thanks for the quick reply. Nothing to do with this drive, because according to man systemd.mount:

```
Mount units may either be configured via unit files, or via /etc/fstab
```

Since [COLOR=#000000][FONT=&quot]media-backup.mount[/FONT][/COLOR] is a unit file, shouldn't it get its mount location from the "Where" parameter?

---

### Post by Holger_Gehrke on 2019-11-06
I don't believe unit files are parsed through the shell, so a command line expansion $(...) probably doesn't work there.
The What-line should read
```

What=UUID=cf96668e-c1cd-43df-a4e8-1923c90a4063

```
Just tested it with a USB-Stick mounting into a directory in my $HOME and got it to work that way.

Holger

---

### Post by theonlytalkinggoat on 2019-11-06
> [COLOR=#000000]I don't believe unit files are parsed through the shell, so a command line expansion $(...) probably doesn't work there.[/COLOR]

You're right, it won't. It will only accept environment variables... but you can set environmental variables, in the file. 

```
man systemd.exec

 
       Environment=
           Sets environment variables for executed processes. Takes a space-separated list of
           variable assignments. This option may be specified more than once, in which case all
           listed variables will be set. If the same variable is set twice, the later setting
           will override the earlier setting. If the empty string is assigned to this option, the
           list of environment variables is reset, all prior assignments have no effect. Variable
           expansion is not performed inside the strings, however, specifier expansion is
           possible. The $ character has no special meaning. If you need to assign a value
           containing spaces to a variable, use double quotes (") for the assignment.


           Example:
               Environment="VAR1=word1 word2" VAR2=word3 "VAR3=$word 5 6"
           gives three variables "VAR1", "VAR2", "VAR3" with the values "word1 word2", "word3",
           "$word 5 6".
           See environ(7) for details about environment variables.
```




Here is what I ended up doing.
Create a script in [FONT=courier new]/usr/local/bin[/FONT] called [FONT=courier new]backup-mount.sh [/FONT]The variable, MOUNT_POINT will change, depending on your needs.
In the file, insert...
```

#!/bin/bash



usage()
{
    echo "Usage: $0 {add|remove} device_name"
    exit 1
}
if [[ $# -ne 2 ]]; then
    usage
fi

ACTION=$1
DEVBASE=$2
DEVICE="/dev/${DEVBASE}"

MOUNT_POINT=$(/bin/mount | /bin/grep ${DEVICE} | awk '{print $3}')
do_mount()
{
    if [[ -n ${MOUNT_POINT} ]]; then
        echo "Warning: ${DEVICE} is already mounted at ${MOUNT_POINT}"
        exit 1
    fi 

    MOUNT_POINT="/media/backup"
    OPTS="rw"
    if ! /bin/mount -o ${OPTS} ${DEVICE} ${MOUNT_POINT}; then
            echo "Error mounting ${DEVICE} (status = $?)"
            /bin/rmdir ${MOUNT_POINT}
            exit 1
        fi
    echo "**** Mounted ${DEVICE} at ${MOUNT_POINT} ****"
}
do_unmount()
{
    /bin/umount -l ${DEVICE}
    echo "********** Unmounted ${DEVICE}"

    if [[ -n $(/usr/bin/find /media/backup -maxdepth 0 -type d)  ]]; then
        if /bin/grep -q /media/backup /etc/mtab; then
            echo "***** Removing /media/backup empty folder"
            /bin/rmdir /media/backup
        fi
    fi


}
case "${ACTION}" in
    add)
        do_mount
        ;;
    remove)
        do_unmount
        ;;
    *)
        usage
        ;;
esac



```

Make the file executable [FONT=courier new]chmod 744 backup-mount.sh[/FONT]

[FONT=&amp][FONT=arial][FONT=verdana]In[/FONT] [FONT=courier new]/etc/udev/rules.d[/FONT][FONT=verdana] I created the file [/FONT][FONT=courier new]99-backup.rules[/FONT].[FONT=verdana] This will allow udev to execute the service, when the specific drive is plugged in. As I add additional backup drives, I can add further rules, with different serial numbers.[/FONT]

[/FONT][/FONT]```
ACTION=="add", KERNEL=="sd[a-z][0-9]", SUBSYSTEMS=="usb", ATTRS{serial}=="DB28765442117", RUN+="/bin/systemctl start backup-mount@%k.service"
ACTION=="remove", KERNEL=="sd[a-z][0-9]", SUBSYSTEMS=="usb", ATTRS{serial}=="DB28765442117", RUN+="/bin/systemctl stop backup-mount@%k.service"

```

Don't forget to run [FONT=courier new]udevadm control --reload[/FONT]

Finally, created a file in [FONT=courier new]/etc/systemd/system[/FONT] called [FONT=courier new]backup-mount@.service. [FONT=arial][FONT=verdana]The @ is necessary, as it will allow the script to insert the drive's designation, so I believe.[/FONT]
[/FONT][/FONT]```
[Unit]
Description=Mount USB Drive on %i
[Service]
Type=oneshot
RemainAfterExit=true
ExecStart=/usr/local/bin/backup-mount.sh add %i
ExecStop=/usr/local/bin/backup-mount.sh remove %i

```

Run the command [FONT=courier new]systemctl daemon-reload[FONT=verdana]
Plug in the drive and watch [FONT=courier new]/var/log/syslog [/FONT]to see if there are any errors.[/FONT][/FONT]

---

### Post by TheFu on 2019-11-06
OMG!  autofs is 1000x easier.

---

