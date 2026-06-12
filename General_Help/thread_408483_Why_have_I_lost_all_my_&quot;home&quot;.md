---
title: "Why have I lost all my &quot;home&quot;?"
date: 2007-04-13
forum: General Help
---

### Post by pipepool on 2007-04-13
Hi all,

I was playing with the aircrack-ng suite, I saw my Desktop and it was empty. I know that it sounds crazy, but I'm serious. My home is "/home/pipepool", the filesystem is ext3. All my documents and directories inside were erased excepting a directory with only root permission and the hidden directories (.directory), i.e, it's like someone had executed a "rm -rf *" in my home. I don't want to be paranoic but the only one explanation that comes to my mind is a cracker. I guess that there is another explanations to this.

I don't know when I lost my files exactly but this fragment of "history" should be "the before and the after".

  380  cd aircrack-ng/
  381  ls
  382  cd airoscript/
  383  ls
  384  ./airoscript.sh 
  385  ls
  386  cd ..
  387  l
  388  ls
  389  rm -rf aircrack-ng/
  390  ls
  391  top
  392  clear
  393  ls
  394  aireplay-ng 
  395  iwconfig 
  396  ls
  397  cd
  398  ls
  399  cd exp
  400  ls
  401  cd ..
  402  ls
  403  rm dvd1.iso 
  404  sudo rm dvd1.iso 
  405  ls
  406  cd pipepool
  407  ls
  408  ls -all
  409  dmesg 

I don't find any anomaly in the logs. Any idea? How could i trace the "error"?

Moreover, if someone could recommend me a program to recover my files it would be great  :)


Thanks.

P.D.-Now, have appeared many files which was erased 1 month ago in the Trash...

---

### Post by nemarasu on 2007-04-13
out of curiosity, what does root history show?

---

### Post by TheWizzard on 2007-04-13
> **nemarasu said:**
> out of curiosity, what does root history show?

he seems to use sudo. so no root history...

---

### Post by nemarasu on 2007-04-13
what does the sudo log have in it?

---

### Post by TheWizzard on 2007-04-13
> **nemarasu said:**
> what does the sudo log have in it?

@ pipepool

please post:
```
history | grep sudo
```

---

### Post by pipepool on 2007-04-13
Apr 13 03:17:19 localhost gdm[5060]: (pam_unix) session opened for user pipepool by (uid=0)
Apr 13 03:30:37 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool ; USER=root ; COMMAND=/sbin/modprobe zd1211rw
Apr 13 03:31:50 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool ; USER=root ; COMMAND=/sbin/iwconfig eth1 NosaRede
Apr 13 03:31:58 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool ; USER=root ; COMMAND=/sbin/iwconfig eth1 essid NosaRede
Apr 13 03:32:00 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool ; USER=root ; COMMAND=/sbin/iwconfig eth1 NosaRede
Apr 13 03:32:18 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool ; USER=root ; COMMAND=/sbin/dhclient eth1
Apr 13 03:34:34 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool ; USER=root ; COMMAND=/sbin/iwconfig eth1 key s:t3n3m0sq+card
Apr 13 03:35:12 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool ; USER=root ; COMMAND=/sbin/iwconfig eth1 key s:t3n3m0sq+card
Apr 13 03:35:29 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool ; USER=root ; COMMAND=/sbin/dhclient eth1
Apr 13 03:36:16 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool ; USER=root ; COMMAND=/sbin/modprobe -r ndiswrapper
Apr 13 03:36:23 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool ; USER=root ; COMMAND=/sbin/modprobe bcm43xx
Apr 13 03:39:01 localhost CRON[12678]: (pam_unix) session opened for user root by (uid=0)
Apr 13 03:39:01 localhost CRON[12680]: (pam_unix) session opened for user root by (uid=0)
Apr 13 03:39:01 localhost CRON[12680]: (pam_unix) session closed for user root
Apr 13 03:39:01 localhost CRON[12678]: (pam_unix) session closed for user root
Apr 13 03:40:01 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool/exp ; USER=root ; COMMAND=/sbin/iwconfig
Apr 13 03:40:27 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool/exp ; USER=root ; COMMAND=/sbin/iwconfig eth2 mode monitor
Apr 13 03:40:29 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool/exp ; USER=root ; COMMAND=/sbin/iwconfig
Apr 13 03:42:34 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool/exp ; USER=root ; COMMAND=/usr/sbin/airodump-ng --ivs -w pepe --channel 5 eth2
Apr 13 03:43:58 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool/exp ; USER=root ; COMMAND=/usr/sbin/airodump-ng --ivs -w pepe --channel 5 eth2
Apr 13 03:44:29 localhost sudo: pipepool : TTY=pts/1 ; PWD=/home/pipepool/exp ; USER=root ; COMMAND=/usr/sbin/aireplay-ng
Apr 13 03:46:29 localhost sudo: pipepool : TTY=pts/1 ; PWD=/home/pipepool/exp ; USER=root ; COMMAND=/usr/sbin/aireplay-ng -b 00:11:F5:1B:79:94 eth2
Apr 13 03:46:48 localhost sudo: pipepool : TTY=pts/1 ; PWD=/home/pipepool/exp ; USER=root ; COMMAND=/usr/sbin/aireplay-ng -b 00:11:F5:1B:79:94 -3 eth2
Apr 13 03:48:48 localhost sudo: pipepool : TTY=pts/1 ; PWD=/home/pipepool/exp ; USER=root ; COMMAND=/usr/sbin/aireplay-ng -b 00:11:F5:1B:79:94 -h 00:02:72:51:8B:AE -3 eth2
Apr 13 04:09:01 localhost CRON[12935]: (pam_unix) session opened for user root by (uid=0)
Apr 13 04:09:01 localhost CRON[12937]: (pam_unix) session opened for user root by (uid=0)
Apr 13 04:09:01 localhost CRON[12937]: (pam_unix) session closed for user root
Apr 13 04:09:01 localhost CRON[12935]: (pam_unix) session closed for user root
Apr 13 04:09:58 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool/Desktop/aircrack-ng-0.7 ; USER=root ; COMMAND=/usr/bin/apt-get install build-essential
Apr 13 04:10:37 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool/Desktop/aircrack-ng-0.7 ; USER=root ; COMMAND=/usr/bin/aptitude remove aircrack-ng
Apr 13 04:12:08 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool/Desktop/aircrack-ng-0.7 ; USER=root ; COMMAND=/usr/bin/aptitude install linux-headers-2.6.20-14
Apr 13 04:12:22 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool/Desktop/aircrack-ng-0.7 ; USER=root ; COMMAND=/usr/bin/aptitude install linux-headers-2.6.20-14-386
Apr 13 04:14:21 localhost sudo: pipepool : TTY=pts/1 ; PWD=/home/pipepool/exp/aircrack-ng ; USER=root ; COMMAND=/usr/bin/checkinstall
Apr 13 04:16:28 localhost sudo: pipepool : TTY=pts/1 ; PWD=/home/pipepool/exp/aircrack-ng ; USER=root ; COMMAND=/usr/bin/dpkg -i aircrack_666-1_i386.deb
Apr 13 04:17:01 localhost CRON[14955]: (pam_unix) session opened for user root by (uid=0)
Apr 13 04:17:01 localhost CRON[14955]: (pam_unix) session closed for user root
Apr 13 04:17:37 localhost sudo: pipepool : TTY=unknown ; PWD=/home/pipepool ; USER=root ; COMMAND=/usr/sbin/synaptic
Apr 13 04:21:22 localhost sudo: pipepool : TTY=pts/1 ; PWD=/home/pipepool/exp/aircrack-ng ; USER=root ; COMMAND=./aireplay-ng -b 00:11:F5:1B:79:94 -h 00:02:72:51:8B:AE -3 eth2
Apr 13 04:21:50 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool/exp/aircrack-ng ; USER=root ; COMMAND=/usr/local/sbin/airodump-ng --ivs -w pepe --channel 5 eth2
Apr 13 04:24:43 localhost sudo: pipepool : TTY=pts/2 ; PWD=/home/pipepool ; USER=root ; COMMAND=/sbin/dhclient eth1
Apr 13 04:25:28 localhost sudo: pipepool : TTY=pts/2 ; PWD=/home/pipepool ; USER=root ; COMMAND=/bin/kill -9 amuled
Apr 13 04:25:48 localhost sudo: pipepool : TTY=pts/2 ; PWD=/home/pipepool ; USER=root ; COMMAND=/bin/kill -9 12820
Apr 13 04:39:01 localhost CRON[15108]: (pam_unix) session opened for user root by (uid=0)
Apr 13 04:39:01 localhost CRON[15110]: (pam_unix) session opened for user root by (uid=0)
Apr 13 04:39:01 localhost CRON[15110]: (pam_unix) session closed for user root
Apr 13 04:39:01 localhost CRON[15108]: (pam_unix) session closed for user root
Apr 13 04:45:25 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool ; USER=root ; COMMAND=/usr/bin/dpkg --purge aircrack
Apr 13 04:46:17 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool ; USER=root ; COMMAND=/usr/bin/aptitude install aircrack-ng
Apr 13 04:59:43 localhost sudo: pipepool : TTY=pts/1 ; PWD=/home ; USER=root ; COMMAND=/bin/rm dvd1.iso
Apr 13 05:09:01 localhost CRON[16099]: (pam_unix) session opened for user root by (uid=0)
Apr 13 05:09:01 localhost CRON[16101]: (pam_unix) session opened for user root by (uid=0)
Apr 13 05:09:01 localhost CRON[16101]: (pam_unix) session closed for user root
Apr 13 05:09:01 localhost CRON[16099]: (pam_unix) session closed for user root
Apr 13 05:13:34 localhost sudo: pipepool : TTY=pts/0 ; PWD=/home/pipepool ; USER=root ; COMMAND=/bin/su
Apr 13 05:13:34 localhost su[16192]: Successful su for root by root
Apr 13 05:13:34 localhost su[16192]: + pts/0 root:root
Apr 13 05:13:34 localhost su[16192]: (pam_unix) session opened for user root by (uid=0)
Apr 13 05:14:54 localhost su[16192]: (pam_unix) session closed for user root
Apr 13 05:15:08 localhost gdm[5060]: (pam_unix) session closed for user pipepool
Apr 13 05:15:16 localhost gdm[5060]: (pam_unix) session opened for user pipepool by (uid=0)
Apr 13 05:17:01 localhost CRON[16472]: (pam_unix) session opened for user root by (uid=0)
Apr 13 05:17:01 localhost CRON[16472]: (pam_unix) session closed for user root
Apr 13 05:22:45 localhost gdm[5060]: (pam_unix) session closed for user pipepool
Apr 13 05:22:57 localhost gdm[5060]: (pam_unix) session opened for user pipepool by (uid=0)
Apr 13 05:23:11 localhost gdm[5060]: (pam_unix) session closed for user pipepool
Apr 13 05:23:44 localhost gdm[5060]: (pam_unix) session opened for user pipepool by (uid=0)
Apr 13 05:25:14 localhost gdm[5060]: (pam_unix) session closed for user pipepool
Apr 13 05:25:22 localhost gdm[5060]: (pam_unix) session opened for user pipepool by (uid=0)
Apr 13 05:29:55 localhost sudo: pipepool : TTY=unknown ; PWD=/home/pipepool ; USER=root ; COMMAND=/usr/sbin/firestarter
Apr 13 05:33:05 localhost gdm[5060]: (pam_unix) session closed for user pipepool
Apr 13 05:34:23 localhost sshd[5432]: Server listening on :: port 22.
Apr 13 05:34:36 localhost gdm[5121]: (pam_unix) session opened for user pipepool by (uid=0)

The file is auth.log.
The problem is in the the interval 4:30-5:13, when I realize and I logged like root.

I have readed the logs in /var/log, I don't know other places where looking for.

 EDITED: history  |grep sudo
 
   47  sudo dhclient eth1
   48  sudo kill -9 amuled
   50  sudo kill -9 12820
   54  sudo aireplay-ng 
   55  sudo aireplay-ng -b 00:11:F5:1B:79:94   eth2
   56  sudo aireplay-ng -b 00:11:F5:1B:79:94 -3  eth2
   57  sudo aireplay-ng -b 00:11:F5:1B:79:94 -h 00:02:72:51:8B:AE  -3  eth2
   66  sudo checkinstall 
   70  sudo dpkg -i aircrack_666-1_i386.deb 
   88  sudo ./aireplay-ng -b 00:11:F5:1B:79:94 -h 00:02:72:51:8B:AE  -3  eth2
   96  sudo modprobe zd1211rw
  101  sudo iwconfig eth1 NosaRede
  102  sudo iwconfig eth1 essid NosaRede
  103  sudo iwconfig eth1 NosaRede
  105  sudo dhclient eth1
  110  sudo iwconfig eth1 key s:t3n3m0sq+card
  112  sudo iwconfig eth1 key s:t3n3m0sq+card
  114  sudo dhclient eth1
  115  sudo modprobe -r ndiswrapper 
  116  sudo modprobe bcm43xx
  125  sudo iwconfig 
  126  sudo iwconfig eth2 mode monitor
  127  sudo iwconfig 
  135  sudo airodump-ng --ivs -w pepe --channel 5 eth2
  137  sudo airodump-ng --ivs -w pepe --channel 5 eth2
  157  sudo apt-get install build-essential
  159  sudo aptitude remove aircrack-ng 
  161  sudo aptitude install linux-headers-2.6.20-14
  162  sudo aptitude install linux-headers-2.6.20-14-386 
  170  sudo airodump-ng --ivs -w pepe --channel 5 eth2
  179  sudo dpkg --purge aircrack 
  180  airsnort sudo aptitude install aircrack-ng
  181   sudo aptitude install aircrack-ng
  211  sudo rm dvd1.iso 
  251  sudo su
  254  sudo aptitude search stelar
  255  sudo su
  264  sudo su
  266  sudo iwconfig 
  267  sudo iwconfig wlan1 essid NosaRede
  277  sudo su
  280  sudo su
  320  sudo clamscan -r
  321  sudo clamscan
  322  sudo clamscan 
  363  sudo chmod -w a
  374  sudo mv /home/pipepool/folding@home/ .
  504  history |grep sudo

As I explained before, a directory with only root permission was not deleted, so I think that the action was done like user and not superuser.

Thanks for the interest  :)

---

### Post by TheWizzard on 2007-04-14
> **pipepool said:**
> All my documents and directories inside were erased excepting a directory with only root permission and the hidden directories (.directory), i.e, it's like someone had executed a "rm -rf *" in my home. I don't want to be paranoic but the only one explanation that comes to my mind is a cracker. 

did you install software that is not in the ubuntu repo's? is your box running a ssh server? 

maybe it's time to be paranoid. install and run both chkrootkit and rkhunter.

---

### Post by pipepool on 2007-04-14
The repo's were from official servers, the ssh port was closed. Both, chkrootkit and rkhunter, didn't find any rootkit. 

I formatted and, from now on, I'm gonna backup oftenly ...

Thanks for all.

---

