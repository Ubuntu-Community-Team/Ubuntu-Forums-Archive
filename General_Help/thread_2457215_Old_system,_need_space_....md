---
title: "Old system, need space ..."
date: 2021-01-27
forum: General Help
---

### Post by dbee on 2021-01-27
I have an old computer, that i'm fond of. Mostly cause it's configured with git, wp-env, docker, a microsd card etc... and i don't want to go through the hassle of setting that all up again on a new system

this particular computer only has 30GB hd. 
```

dara@dara-HP-Stream-Laptop-11-y0XX:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            928M     0  928M   0% /dev
tmpfs           190M  1.4M  189M   1% /run
/dev/mmcblk0p2   29G   26G  1.5G  95% /
tmpfs           950M  122M  828M  13% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           950M     0  950M   0% /sys/fs/cgroup
/dev/mmcblk0p1  511M  8.5M  503M   2% /boot/efi
tmpfs           190M   28K  190M   1% /run/user/1000
/dev/mmcblk1    115G   61M  109G   1% /media/dara/microsd

```
I have only 1.5GB left on the system. I'm already pruning docker on boot.
```

$ crontab -l
@reboot rm -rf /home/dara/wp-env/*
@reboot docker system prune -a

```

I'm on bionic xubuntu...
```

dara@dara-HP-Stream-Laptop-11-y0XX:~$ lsb_release -a 
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.5 LTS
Release:        18.04
Codename:       bionic

```
I've installed my last update. The latest one was 130MB. I'm assuming that's the compressed size. I'll probably be foregoing updates for the considerable future. At least until i can get my external hd working with the system...

[https://ubuntuforums.org/showthread.php?t=2457179]("https://ubuntuforums.org/showthread.php?t=2457179")

 I don't suppose you can install updates/upgrades on external hds by any chance?

Anyway, my question is this. I have a large journaled '/var/log' file that I'm not using. How can i remove it and cut back on the logging feature?

```
dara@dara-HP-Stream-Laptop-11-y0XX:/mnt/microsd$ sudo du -a /var | sort -n -r | head -n 20
[sudo] password for dara: 
6509192	/var
4876960	/var/lib
4282400	/var/lib/docker
4278968	/var/lib/docker/volumes
982748	/var/log
975224	/var/log/journal
975220	/var/log/journal/b5f917a4277b4e3abff26ee9bec75328
563980	/var/cache
536772	/var/cache/apt
418756	/var/cache/apt/archives
245592	/var/lib/apt
245548	/var/lib/apt/lists
214004	/var/lib/mysql
202812	/var/lib/docker/volumes/docker_git_db_data
202808	/var/lib/docker/volumes/docker_git_db_data/_data
195024	/var/lib/docker/volumes/7e251b17685b0524af4816aa6be650bf_mysql
195020	/var/lib/docker/volumes/7e251b17685b0524af4816aa6be650bf_mysql/_data
192928	/var/lib/docker/volumes/e91533e49a87525fc90602f1b304147f_mysql
192924	/var/lib/docker/volumes/e91533e49a87525fc90602f1b304147f_mysql/_data
188604	/var/lib/docker/volumes/46aa23b46728c741a1e26940f5dc7c9267fa2f4bb4b567ec74fe0b07e4839dbf

```

---

### Post by oldfred on 2021-01-27
RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

I delete older logs with this in my housecleaning script.
[FONT=monospace][COLOR=#000000]sudo find /var/log/ -name *.gz* -type f -atime +10 -print -exec rm -f {} +[/COLOR]

[FONT=arial]I also houseclean Firefox & Thunderbird cache2.[/FONT][/FONT]

---

### Post by dbee on 2021-01-28
Excellent thanks oldfred.

any idea on how i can store that command in my emacs/shell env?

So i can run it like ...
```

$ $my_command

```

---

### Post by oldfred on 2021-01-28
I have my own script which is something like this:
I check sizes, update & houseclean in one script.
[https://github.com/jabarihunt/Ubuntu-Cleanup-Script/blob/master/clean.sh](https://github.com/jabarihunt/Ubuntu-Cleanup-Script/blob/master/clean.sh)

If Ubuntu with Nautilus
Scripts here will appear in scripts menu
~/.local/share/nautilus/scripts/

[https://askubuntu.com/questions/471285/how-to-create-execute-a-script-file/471286#471286](https://askubuntu.com/questions/471285/how-to-create-execute-a-script-file/471286#471286)
Lots of links on scripting in this thread
[http://ubuntuforums.org/showthread.php?t=1893106](http://ubuntuforums.org/showthread.php?t=1893106)

---

