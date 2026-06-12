---
title: "NetworkManager not restarting on Ubuntu 24.04"
date: 2024-08-12
forum: General Help
---

### Post by lads on 2024-08-12
I installed Ubuntu 24.04 about a week ago on a Asus Vivobook. Every now and then the NetworkManager stops working and all connections to the internet become idle. So far I am not certain the programme is actually crashing, this is what the Settings reports:

[IMG]https://pasteboard.co/WpP6m64VdMNI.png[/IMG]

*Follow [this link]("https://pasteboard.co/WpP6m64VdMNI.png") if the image does not show.*

The command line tools report "Network unreachable" during these events. So far I tried to restart the NetworkManager, but there is no response, the terminal just remains idle, no messages are shown:

```$ sudo systemctl restart NetworkManager

```

There are no error messages displayed by dmesg, although I am not fully awere what I should be searching for. The NetworkManager only comes back to life with a reboot.

Is there any way to force the NetworkManager to restart? Or any strategies to identify the cause?

Thank you for reading.

---

### Post by currentshaft on 2024-08-12
3821

---

### Post by lads on 2024-08-12
@currentshaft Once the Settings starts reporting "NetworkManager not running" neither wireless, not wired connections respond. "Network unreacheable" is what I get from the probing tools. 

Thank you.

---

### Post by currentshaft on 2024-08-12
1>2

---

### Post by lads on 2024-08-28
This problem did not manifest itself during the middle of August, but is back with a vengeance the past week or so. The NetworkManager crashes or becomes unresponsive once or twice per day. The only way to re-connect to the internet is by restarting the system. Below a few command line outputs during one of these episodes, following the comments above.


```
$ systemctl status NetworkManager
&#9679; NetworkManager.service - Network Manager
     Loaded: loaded (/usr/lib/systemd/system/NetworkManager.service; enabled>
     Active: active (running) since Sun 2024-08-27 18:21:44 WEST; 2h 18min a>
       Docs: man:NetworkManager(8)
   Main PID: 1149 (NetworkManager)
      Tasks: 4 (limit: 18646)
     Memory: 12.2M (peak: 28.6M)
        CPU: 836ms
     CGroup: /system.slice/NetworkManager.service
             &#9492;&#9472;1149 /usr/sbin/NetworkManager --no-daemon

ago 27 19:34:08 Symbolic NetworkManager[1149]: <info>  [1724006048.8961] man>
ago 27 19:34:08 Symbolic NetworkManager[1149]: <info>  [1724006048.8965] dev>
ago 27 19:34:09 Symbolic NetworkManager[1149]: <info>  [1724006049.1482] dev>
ago 27 19:34:09 Symbolic NetworkManager[1149]: <info>  [1724006049.1484] dev>
ago 27 19:34:09 Symbolic NetworkManager[1149]: <info>  [1724006049.1488] dhc>
ago 27 19:34:09 Symbolic NetworkManager[1149]: <info>  [1724006049.1488] dhc>
ago 27 19:34:09 Symbolic NetworkManager[1149]: <info>  [1724006049.1489] dhc>
ago 27 19:34:09 Symbolic NetworkManager[1149]: <info>  [1724006049.2049] dev>
ago 27 20:33:50 Symbolic NetworkManager[1149]: <info>  [1724009630.5340] man>
ago 27 20:33:50 Symbolic NetworkManager[1149]: <info>  [1724009630.5344] dev>

```

```
lads@Symbolic:~$ journalctl -u NetworkManager
ago 26 09:55:18 Symbolic NetworkManager[1265]: <info>  [1723884918.3561] dev>
ago 26 09:55:18 Symbolic NetworkManager[1265]: <info>  [1723884918.3565] man>
ago 26 09:55:18 Symbolic NetworkManager[1265]: <info>  [1723884918.3566] man>
ago 26 09:55:18 Symbolic NetworkManager[1265]: <info>  [1723884918.3567] dev>
ago 26 09:55:18 Symbolic NetworkManager[1265]: <info>  [1723884918.3958] dev>
ago 26 09:55:18 Symbolic NetworkManager[1265]: <info>  [1723884918.3959] man>
ago 26 09:55:38 Symbolic NetworkManager[1265]: <info>  [1723884938.6188] man>
ago 26 09:55:38 Symbolic NetworkManager[1265]: <info>  [1723884938.6190] dev>
ago 26 09:55:58 Symbolic NetworkManager[1265]: <info>  [1723884958.6810] dev>
ago 26 09:55:58 Symbolic NetworkManager[1265]: <info>  [1723884958.6812] man>
ago 26 09:55:58 Symbolic NetworkManager[1265]: <info>  [1723884958.6814] man>
ago 26 09:55:58 Symbolic NetworkManager[1265]: <info>  [1723884958.6814] dev>
ago 26 09:55:58 Symbolic NetworkManager[1265]: <info>  [1723884958.7263] dev>
ago 26 09:55:58 Symbolic NetworkManager[1265]: <info>  [1723884958.7265] man>
ago 26 09:56:18 Symbolic NetworkManager[1265]: <info>  [1723884978.9571] man>
ago 26 09:56:18 Symbolic NetworkManager[1265]: <info>  [1723884978.9572] dev>
ago 26 09:56:39 Symbolic NetworkManager[1265]: <info>  [1723884999.0380] dev>
ago 26 09:56:39 Symbolic NetworkManager[1265]: <info>  [1723884999.0383] man>
ago 26 09:56:39 Symbolic NetworkManager[1265]: <info>  [1723884999.0388] man>
ago 26 09:56:39 Symbolic NetworkManager[1265]: <info>  [1723884999.0389] dev>
ago 26 09:56:39 Symbolic NetworkManager[1265]: <info>  [1723884999.0759] dev>
ago 26 09:56:39 Symbolic NetworkManager[1265]: <info>  [1723884999.0761] man>
ago 26 09:56:59 Symbolic NetworkManager[1265]: <info>  [1723885019.3372] man>
ago 26 09:56:59 Symbolic NetworkManager[1265]: <info>  [1723885019.3374] dev>
ago 26 09:57:19 Symbolic NetworkManager[1265]: <info>  [1723885039.4108] dev>
ago 26 09:57:19 Symbolic NetworkManager[1265]: <info>  [1723885039.4116] man>
ago 26 09:57:19 Symbolic NetworkManager[1265]: <info>  [1723885039.4127] man>
ago 26 09:57:19 Symbolic NetworkManager[1265]: <info>  [1723885039.4128] dev>
ago 26 09:57:19 Symbolic NetworkManager[1265]: <info>  [1723885039.4593] dev>
ago 26 09:57:19 Symbolic NetworkManager[1265]: <info>  [1723885039.4595] man>
ago 26 09:57:39 Symbolic NetworkManager[1265]: <info>  [1723885059.7008] man>
ago 26 09:57:39 Symbolic NetworkManager[1265]: <info>  [1723885059.7010] dev>
ago 26 09:57:59 Symbolic NetworkManager[1265]: <info>  [1723885079.7631] dev>
ago 26 09:57:59 Symbolic NetworkManager[1265]: <info>  [1723885079.7634] man>
ago 26 09:57:59 Symbolic NetworkManager[1265]: <info>  [1723885079.7636] man>
ago 26 09:57:59 Symbolic NetworkManager[1265]: <info>  [1723885079.7636] dev>
ago 26 09:57:59 Symbolic NetworkManager[1265]: <info>  [1723885079.8101] dev>
ago 26 09:57:59 Symbolic NetworkManager[1265]: <info>  [1723885079.8102] man>
ago 26 09:58:20 Symbolic NetworkManager[1265]: <info>  [1723885100.0482] man>
ago 26 09:58:20 Symbolic NetworkManager[1265]: <info>  [1723885100.0484] dev>
ago 26 09:58:40 Symbolic NetworkManager[1265]: <info>  [1723885120.1255] dev>
ago 26 09:58:40 Symbolic NetworkManager[1265]: <info>  [1723885120.1257] man>
ago 26 09:58:40 Symbolic NetworkManager[1265]: <info>  [1723885120.1260] man>
ago 26 09:58:40 Symbolic NetworkManager[1265]: <info>  [1723885120.1261] dev>
ago 26 09:58:40 Symbolic NetworkManager[1265]: <info>  [1723885120.1703] dev>
ago 26 09:58:40 Symbolic NetworkManager[1265]: <info>  [1723885120.1705] man>

```

```
$ ping 1.1.1.1
ping: connect: Network is unreachable

$ sudo systemctl restart NetworkManager

[hangs up]

```

---

### Post by lads on 2024-09-09
I am not sure this how relevant this information is, during these episodes there are more tools unresponsive, namely `ifconfig`. They all hang up without reporting errors.

---

### Post by lads on 2024-09-12
I just reported this issue as a bug: 
[https://bugs.launchpad.net/launchpad/+bug/2080489](https://bugs.launchpad.net/launchpad/+bug/2080489)

I will keep investigating the cause, but this behaviour looks way off.

---

### Post by speartip on 2024-09-12
I had a similar issue with the network freezing. What solved it for me was editing the file /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf, and changing the value from 3 to 2 then rebooting. At worst it won't do any harm trying it.

---

### Post by lads on 2024-09-20
Thank you for the suggestion speartip. Unfortunately, the NetworkManager keeps freezing after that change.

---

