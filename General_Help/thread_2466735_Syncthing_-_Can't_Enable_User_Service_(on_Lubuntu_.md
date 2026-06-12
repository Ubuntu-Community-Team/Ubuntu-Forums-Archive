---
title: "Syncthing - Can't Enable User Service (on Lubuntu box) - already running?"
date: 2021-09-04
forum: General Help
---

### Post by steve234 on 2021-09-04
I've come here for (L)ubuntu specific advice on Syncthing.

I use Syncthing to keep my video editing ~/scratch directory available  across two devices. 

This morning Syncthing is not syncing, and it's my Lubuntu box that's causing me difficulty. It seems there is another instance of syncthing running, but I don't recall setting it up more than once, and in any event, if it was running would it not (1) sync; and (2) return active when status is checked? 

I'm clearly failing to understand something simple.

I believe that (except for OS differences) syncthing  on the PCs is setup identically. Setup is as follows:

**PC 1: desktop**

    
[LIST]
[*]Lubuntu 20.04 
[*]Syncthing v1.8.1 installed via apt 
[*]Syncthing user service throws errors and won't start (see further below). 
[/LIST]
 
**PC 2: laptop**

    
[LIST]
[*]Arch 
[*]Syncthing v1.18.1-1 installed via pacman 
[*]Syncthing user service appears to be running fine: 
[/LIST]
      
```
$ systemctl --user status syncthing.service
&#9679; syncthing.service - Syncthing - Open Source Continuous File Synchronization
     Loaded: loaded (/usr/lib/systemd/user/syncthing.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2021-09-04 14:29:05 BST; 23s ago

```

When I try to start the Syncthing user service on **my Lubuntu box** the errors and journal log are:

```

                                                                                                                      
> systemctl --user status syncthing.service
&#9679; syncthing.service - Syncthing - Open Source Continuous File Synchronization
     Loaded: loaded (/usr/lib/systemd/user/syncthing.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Sat 2021-09-04 13:18:58 BST; 5min ago
       Docs: man:syncthing(1)
    Process: 1638 ExecStart=/usr/bin/syncthing serve --no-browser --no-restart --logflags=0 (code=exited, status=1/FAILURE)
   Main PID: 1638 (code=exited, status=1/FAILURE)

Sep 04 13:18:58 [USER] systemd[1389]: syncthing.service: Scheduled restart job, restart counter is at 4.
Sep 04 13:18:58 [USER] systemd[1389]: Stopped Syncthing - Open Source Continuous File Synchronization.
Sep 04 13:18:58 [USER] systemd[1389]: syncthing.service: Start request repeated too quickly.
Sep 04 13:18:58 [USER] systemd[1389]: syncthing.service: Failed with result 'exit-code'.
Sep 04 13:18:58 [USER] systemd[1389]: Failed to start Syncthing - Open Source Continuous File Synchronization.

> systemctl --user start syncthing.service

> journalctl -e --user-unit=syncthing.service
Sep 04 13:24:13 [USER] systemd[1389]: syncthing.service: Main process exited, code=exited, status=1/FAILURE
Sep 04 13:24:13 [USER] systemd[1389]: syncthing.service: Failed with result 'exit-code'.
Sep 04 13:24:14 [USER] systemd[1389]: syncthing.service: Scheduled restart job, restart counter is at 3.
Sep 04 13:24:14 [USER] systemd[1389]: Stopped Syncthing - Open Source Continuous File Synchronization.
Sep 04 13:24:14 [USER] systemd[1389]: Started Syncthing - Open Source Continuous File Synchronization.
Sep 04 13:24:14 [USER] syncthing[4422]: [start] INFO: syncthing v1.18.1 "Fermium Flea" (go1.16.6 linux-amd64) deb@build.syncthing.net 2021-07-30 12:41:57 UTC [noupgrade]
Sep 04 13:24:14 [USER] syncthing[4422]: [start] WARNING: Error opening database: resource temporarily unavailable (is another instance of Syncthing running?)
Sep 04 13:24:14 [USER] systemd[1389]: syncthing.service: Main process exited, code=exited, status=1/FAILURE
Sep 04 13:24:14 [USER] systemd[1389]: syncthing.service: Failed with result 'exit-code'.
Sep 04 13:24:15 [USER] systemd[1389]: syncthing.service: Scheduled restart job, restart counter is at 4.
Sep 04 13:24:15 [USER] systemd[1389]: Stopped Syncthing - Open Source Continuous File Synchronization.
Sep 04 13:24:15 [USER] systemd[1389]: syncthing.service: Start request repeated too quickly.
Sep 04 13:24:15 [USER] systemd[1389]: syncthing.service: Failed with result 'exit-code'.
Sep 04 13:24:15 [USER] systemd[1389]: Failed to start Syncthing - Open Source Continuous File Synchronization.
Sep 04 13:24:13 [USER] systemd[1389]: syncthing.service: Main process exited, code=exited, status=1/FAILURE
Sep 04 13:24:13 [USER] systemd[1389]: syncthing.service: Failed with result 'exit-code'.
Sep 04 13:24:14 [USER] systemd[1389]: syncthing.service: Scheduled restart job, restart counter is at 3.
Sep 04 13:24:14 [USER] systemd[1389]: Stopped Syncthing - Open Source Continuous File Synchronization.
Sep 04 13:24:14 [USER] systemd[1389]: Started Syncthing - Open Source Continuous File Synchronization.
Sep 04 13:24:14 [USER] syncthing[4422]: [start] INFO: syncthing v1.18.1 "Fermium Flea" (go1.16.6 linux-amd64) deb@build.syncthing.net 2021-07-30 12:41:57 UTC [noupgrade]
Sep 04 13:24:14 [USER] syncthing[4422]: [start] WARNING: Error opening database: resource temporarily unavailable (is another instance of Syncthing running?)
Sep 04 13:24:14 [USER] systemd[1389]: syncthing.service: Main process exited, code=exited, status=1/FAILURE                                                                                                                                                                                                                                          
Sep 04 13:24:13 [USER] systemd[1389]: syncthing.service: Main process exited, code=exited, status=1/FAILURE
Sep 04 13:24:13 [USER] systemd[1389]: syncthing.service: Failed with result 'exit-code'.
Sep 04 13:24:14 [USER] systemd[1389]: syncthing.service: Scheduled restart job, restart counter is at 3.
Sep 04 13:24:14 [USER] systemd[1389]: Stopped Syncthing - Open Source Continuous File Synchronization.
Sep 04 13:24:14 [USER] systemd[1389]: Started Syncthing - Open Source Continuous File Synchronization.
Sep 04 13:24:14 [USER] syncthing[4422]: [start] INFO: syncthing v1.18.1 "Fermium Flea" (go1.16.6 linux-amd64) deb@build.syncthing.net 2021-07-30 12:41:57 UTC [noupgrade]
Sep 04 13:24:14 [USER] syncthing[4422]: [start] WARNING: Error opening database: resource temporarily unavailable (is another instance of Syncthing running?)
Sep 04 13:24:14 [USER] systemd[1389]: syncthing.service: Main process exited, code=exited, status=1/FAILURE
Sep 04 13:24:14 [USER] systemd[1389]: syncthing.service: Failed with result 'exit-code'.
Sep 04 13:24:15 [USER] systemd[1389]: syncthing.service: Scheduled restart job, restart counter is at 4.
Sep 04 13:24:15 [USER] systemd[1389]: Stopped Syncthing - Open Source Continuous File Synchronization.
Sep 04 13:24:15 [USER] systemd[1389]: syncthing.service: Start request repeated too quickly.
Sep 04 13:24:15 [USER] systemd[1389]: syncthing.service: Failed with result 'exit-code'.
Sep 04 13:24:15 [USER] systemd[1389]: Failed to start Syncthing - Open Source Continuous File Synchronization.
Sep 04 13:24:13 [USER] systemd[1389]: syncthing.service: Main process exited, code=exited, status=1/FAILURE
Sep 04 13:24:13 [USER] systemd[1389]: syncthing.service: Failed with result 'exit-code'.
Sep 04 13:24:14 [USER] systemd[1389]: syncthing.service: Scheduled restart job, restart counter is at 3.
Sep 04 13:24:14 [USER] systemd[1389]: Stopped Syncthing - Open Source Continuous File Synchronization.
Sep 04 13:24:14 [USER] systemd[1389]: Started Syncthing - Open Source Continuous File Synchronization.
Sep 04 13:24:14 [USER] syncthing[4422]: [start] INFO: syncthing v1.18.1 "Fermium Flea" (go1.16.6 linux-amd64) d>
Sep 04 13:24:14 [USER] syncthing[4422]: [start] WARNING: Error opening database: resource temporarily unavailab>
Sep 04 13:24:14 [USER] systemd[1389]: syncthing.service: Main process exited, code=exited, status=1/FAILURE
Sep 04 13:24:14 [USER] systemd[1389]: syncthing.service: Failed with result 'exit-code'.
Sep 04 13:24:15 [USER] systemd[1389]: syncthing.service: Scheduled restart job, restart counter is at 4.
Sep 04 13:24:15 [USER] systemd[1389]: Stopped Syncthing - Open Source Continuous File Synchronization.
Sep 04 13:24:15 [USER] systemd[1389]: syncthing.service: Start request repeated too quickly.
Sep 04 13:24:15 [USER] systemd[1389]: syncthing.service: Failed with result 'exit-code'.
Sep 04 13:24:15 [USER] systemd[1389]: Failed to start Syncthing - Open Source Continuous File Synchronization.
Sep 04 13:24:13 [USER] systemd[1389]: syncthing.service: Main process exited, code=exited, status=1/FAILURE
Sep 04 13:24:13 [USER] systemd[1389]: syncthing.service: Failed with result 'exit-code'.
Sep 04 13:24:14 [USER] systemd[1389]: syncthing.service: Scheduled restart job, restart counter is at 3.
Sep 04 13:24:14 [USER] systemd[1389]: Stopped Syncthing - Open Source Continuous File Synchronization.
Sep 04 13:24:14 [USER] systemd[1389]: Started Syncthing - Open Source Continuous File Synchronization.
Sep 04 13:24:14 [USER] syncthing[4422]: [start] INFO: syncthing v1.18.1 "Fermium Flea" (go1.16.6 linux-amd64) d>
Sep 04 13:24:14 [USER] syncthing[4422]: [start] WARNING: Error opening database: resource temporarily unavailab>
Sep 04 13:24:13 [USER] systemd[1389]: syncthing.service: Main process exited, code=exited, status=1/FAILURE
Sep 04 13:24:13 [USER] systemd[1389]: syncthing.service: Failed with result 'exit-code'.
Sep 04 13:24:14 [USER] systemd[1389]: syncthing.service: Scheduled restart job, restart counter is at 3.
Sep 04 13:24:14 [USER] systemd[1389]: Stopped Syncthing - Open Source Continuous File Synchronization.
Sep 04 13:24:14 [USER] systemd[1389]: Started Syncthing - Open Source Continuous File Synchronization.
Sep 04 13:24:14 [USER] syncthing[4422]: [start] INFO: syncthing v1.18.1 "Fermium Flea" (go1.16.6 linux-amd64) d>
Sep 04 13:24:14 [USER] syncthing[4422]: [start] WARNING: Error opening database: resource temporarily unavailab>
Sep 04 13:24:14 [USER] systemd[1389]: syncthing.service: Main process exited, code=exited, status=1/FAILURE
Sep 04 13:24:14 [USER] systemd[1389]: syncthing.service: Failed with result 'exit-code'.
Sep 04 13:24:15 [USER] systemd[1389]: syncthing.service: Scheduled restart job, restart counter is at 4.
Sep 04 13:24:15 [USER] systemd[1389]: Stopped Syncthing - Open Source Continuous File Synchronization.
Sep 04 13:24:15 [USER] systemd[1389]: syncthing.service: Start request repeated too quickly.
Sep 04 13:24:15 [USER] systemd[1389]: syncthing.service: Failed with result 'exit-code'.
Sep 04 13:24:15 [USER] systemd[1389]: Failed to start Syncthing - Open Source Continuous File Synchronization.

```

Any help would be appreciated

---

### Post by steve234 on 2021-09-06
Purged and reinstalled - now it's happy. Solved.

---

### Post by steve234 on 2021-09-07
Noooooooooooooooooooooo,

Logged back in after a shutdown and Syncthing is broken again. Only works if I fire up the browser.

```
&#9679; syncthing.service - Syncthing - Open Source Continuous File Synchronization
     Loaded: loaded (/usr/lib/systemd/user/syncthing.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Tue 2021-09-07 10:51:40 BST; 5min ago
       Docs: man:syncthing(1)
    Process: 12873 ExecStart=/usr/bin/syncthing serve --no-browser --no-restart --logflags=0 (code=exited, status=1/FAILURE)
   Main PID: 12873 (code=exited, status=1/FAILURE)

Sep 07 10:51:40 <user>  systemd[1573]: syncthing.service: Scheduled restart job, restart counter is at 4.
Sep 07 10:51:40 <user>  systemd[1573]: Stopped Syncthing - Open Source Continuous File Synchronization.
Sep 07 10:51:40 <user> systemd[1573]: syncthing.service: Start request repeated too quickly.
Sep 07 10:51:40 <user> systemd[1573]: syncthing.service: Failed with result 'exit-code'.
Sep 07 10:51:40 <user> systemd[1573]: Failed to start Syncthing - Open Source Continuous File Synchronization.


```

Any ideas?

---

