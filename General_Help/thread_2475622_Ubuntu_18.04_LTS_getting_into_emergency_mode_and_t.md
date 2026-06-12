---
title: "Ubuntu 18.04 LTS getting into emergency mode and then exiting I can use the system"
date: 2022-06-02
forum: General Help
---

### Post by j.gohel on 2022-06-02
I have a Dell Laptop on which I had factory-installed Ubuntu and at the time of writing this I am using **Ubuntu 18.04.6 LTS**. From past 2 days all of a sudden when I restart my laptop it takes quite an amount of time to boot and then goes into emergency mode. On the emergency mode screen when I hit **Enter** the **root** user prompt appears and when I type **exit**, **fortunately** I can see the login screen and can get into the system and start using it. 

I explored various resources I found related to this problem and most of them says that such thing happens when the file system is corrupted or caused by dual boot or a new partition is created or there is some problem in **/etc/fstab**. Dual boot and New partition creation definitely not is applicable in my case. If the file system is corrupted sorry to say that I have no idea on how to diagnose it. If there are issues in **/etc/fstab** then I have not touched it for years. 

I checked **journalctl -xb** and extracted logs which were referred to the in most of the related resources I found on web. Below is the output with different grep terms. Since the output of that command was very long I thought it wouldn't be useful to post it all here. *Also from the emergency mode terminal itself how to grab that whole output so that I can paste it here in code format I don't know as I am not an expert on using the terminal. The only way I could think of is taking a photo of the screen using my mobile camera.* Considering this I hope that what I have provided below will help anybody who can help me out in this matter. And if more information is needed then please let me know and I will try to furnish it.

Log-1:

    ```
jignesh@jignesh-Latitude-7290:~$ journalctl -xb | grep "Timed out"
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-bc558793\x2d243d\x2d4a5e\x2d9369\x2d5c7b3b339c6f.device.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-345e070f\x2d3d96\x2d40a9\x2d8774\x2df7eeb8d4a958.device.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-E2DD\x2d0AED.device.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-2b1375de\x2d666d\x2d48b3\x2d8a42\x2d154e214abf95.device.
```

Log-2:

    ```
jignesh@jignesh-Latitude-7290:~$ journalctl -xb | grep "timed out"
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: dev-disk-by\x2duuid-bc558793\x2d243d\x2d4a5e\x2d9369\x2d5c7b3b339c6f.device: Job dev-disk-by\x2duuid-bc558793\x2d243d\x2d4a5e\x2d9369\x2d5c7b3b339c6f.device/start timed out.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: dev-disk-by\x2duuid-345e070f\x2d3d96\x2d40a9\x2d8774\x2df7eeb8d4a958.device: Job dev-disk-by\x2duuid-345e070f\x2d3d96\x2d40a9\x2d8774\x2df7eeb8d4a958.device/start timed out.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: dev-disk-by\x2duuid-E2DD\x2d0AED.device: Job dev-disk-by\x2duuid-E2DD\x2d0AED.device/start timed out.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: dev-disk-by\x2duuid-2b1375de\x2d666d\x2d48b3\x2d8a42\x2d154e214abf95.device: Job dev-disk-by\x2duuid-2b1375de\x2d666d\x2d48b3\x2d8a42\x2d154e214abf95.device/start timed out.
```

Log-3:

    ```
jignesh@jignesh-Latitude-7290:~$ journalctl -xb | grep "dependency"
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: mnt-jchamber.mount: Job mnt-jchamber.mount/start failed with result 'dependency'.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: dns-clean.service: Job dns-clean.service/start failed with result 'dependency'.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: local-fs.target: Job local-fs.target/start failed with result 'dependency'.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: home.mount: Job home.mount/start failed with result 'dependency'.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: [EMAIL="systemd-fsck@dev-disk-by\x2duuid-345e070f\x2d3d96\x2d40a9\x2d8774\x2df7eeb8d4a958.servic"]systemd-fsck@dev-disk-by\x2duuid-345e070f\x2d3d96\x2d40a9\x2d8774\x2df7eeb8d4a958.servic[/EMAIL]e: Job [EMAIL="systemd-fsck@dev-disk-by\x2duuid-345e070f\x2d3d96\x2d40a9\x2d8774\x2df7eeb8d4a958.servic"]systemd-fsck@dev-disk-by\x2duuid-345e070f\x2d3d96\x2d40a9\x2d8774\x2df7eeb8d4a958.servic[/EMAIL]e/start failed with result 'dependency'.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: boot-efi.mount: Job boot-efi.mount/start failed with result 'dependency'.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: [EMAIL="systemd-fsck@dev-disk-by\x2duuid-E2DD\x2d0AED.servic"]systemd-fsck@dev-disk-by\x2duuid-E2DD\x2d0AED.servic[/EMAIL]e: Job [EMAIL="systemd-fsck@dev-disk-by\x2duuid-E2DD\x2d0AED.servic"]systemd-fsck@dev-disk-by\x2duuid-E2DD\x2d0AED.servic[/EMAIL]e/start failed with result 'dependency'.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: swap.target: Job swap.target/start failed with result 'dependency'.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: dev-disk-by\x2duuid-2b1375de\x2d666d\x2d48b3\x2d8a42\x2d154e214abf95.swap: Job dev-disk-by\x2duuid-2b1375de\x2d666d\x2d48b3\x2d8a42\x2d154e214abf95.swap/start failed with result 'dependency'.
```

Log-4 (extract of more details for timed out entries)

    ```
Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-bc558793\x2d243d\x2d4a5e\x2d9369\x2d5c7b3b339c6f.de
    -- Subject: Unit dev-disk-by\x2duuid-bc558793\x2d243d\x2d4a5e\x2d9369\x2d5c7b3b339c6f.device has failed
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit dev-disk-by\x2duuid-bc558793\x2d243d\x2d4a5e\x2d9369\x2d5c7b3b339c6f.device has failed.
    -- 
    -- The result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Dependency failed for /mnt/jchamber.
    -- Subject: Unit mnt-jchamber.mount has failed
    -- Defined-By: systemd
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Dependency failed for /mnt/jchamber.
    -- Subject: Unit mnt-jchamber.mount has failed
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit mnt-jchamber.mount has failed.
    -- 
    -- The result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: mnt-jchamber.mount: Job mnt-jchamber.mount/start failed with result 'dependency'.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: dev-disk-by\x2duuid-bc558793\x2d243d\x2d4a5e\x2d9369\x2d5c7b3b339c6f.device: Job dev-disk-by\x2duuid
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: dev-disk-by\x2duuid-345e070f\x2d3d96\x2d40a9\x2d8774\x2df7eeb8d4a958.device: Job dev-disk-by\x2duuid
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-345e070f\x2d3d96\x2d40a9\x2d8774\x2df7eeb8d4a958.de
    -- Subject: Unit dev-disk-by\x2duuid-345e070f\x2d3d96\x2d40a9\x2d8774\x2df7eeb8d4a958.device has failed
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit dev-disk-by\x2duuid-345e070f\x2d3d96\x2d40a9\x2d8774\x2df7eeb8d4a958.device has failed.
    -- 
    -- The result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Dependency failed for File System Check on /dev/disk/by-uuid/345e070f-3d96-40a9-8774-f7eeb8d4a958.
    -- Subject: Unit [EMAIL="systemd-fsck@dev-disk-by\x2duuid-345e070f\x2d3d96\x2d40a9\x2d8774\x2df7eeb8d4a958.servic"]systemd-fsck@dev-disk-by\x2duuid-345e070f\x2d3d96\x2d40a9\x2d8774\x2df7eeb8d4a958.servic[/EMAIL]e has failed
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit [EMAIL="systemd-fsck@dev-disk-by\x2duuid-345e070f\x2d3d96\x2d40a9\x2d8774\x2df7eeb8d4a958.servic"]systemd-fsck@dev-disk-by\x2duuid-345e070f\x2d3d96\x2d40a9\x2d8774\x2df7eeb8d4a958.servic[/EMAIL]e has failed.
    -- 
    -- The result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Dependency failed for /home.
    -- Subject: Unit home.mount has failed
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit home.mount has failed.
    -- 
    -- The result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Dependency failed for Local File Systems.
    -- Subject: Unit local-fs.target has failed
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit local-fs.target has failed.
    -- 
    -- The result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Dependency failed for Clean up any mess left by 0dns-up.
    -- Subject: Unit dns-clean.service has failed
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit dns-clean.service has failed.
    -- 
    -- The result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: dns-clean.service: Job dns-clean.service/start failed with result 'dependency'.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: local-fs.target: Job local-fs.target/start failed with result 'dependency'.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: local-fs.target: Triggering OnFailure= dependencies.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: home.mount: Job home.mount/start failed with result 'dependency'.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: [EMAIL="systemd-fsck@dev-disk-by\x2duuid-345e070f\x2d3d96\x2d40a9\x2d8774\x2df7eeb8d4a958.servic"]systemd-fsck@dev-disk-by\x2duuid-345e070f\x2d3d96\x2d40a9\x2d8774\x2df7eeb8d4a958.servic[/EMAIL]e: Job syste
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: dev-disk-by\x2duuid-345e070f\x2d3d96\x2d40a9\x2d8774\x2df7eeb8d4a958.device: Job dev-disk-by\x2duuid
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: dev-disk-by\x2duuid-E2DD\x2d0AED.device: Job dev-disk-by\x2duuid-E2DD\x2d0AED.device/start timed out
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-E2DD\x2d0AED.device.
    -- Subject: Unit dev-disk-by\x2duuid-E2DD\x2d0AED.device has failed
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit dev-disk-by\x2duuid-E2DD\x2d0AED.device has failed.
    -- 
    -- The result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Dependency failed for /boot/efi.
    -- Subject: Unit boot-efi.mount has failed
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit boot-efi.mount has failed.
    -- 
    -- The result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: boot-efi.mount: Job boot-efi.mount/start failed with result 'dependency'.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Dependency failed for File System Check on /dev/disk/by-uuid/E2DD-0AED.
    -- Subject: Unit [EMAIL="systemd-fsck@dev-disk-by\x2duuid-E2DD\x2d0AED.servic"]systemd-fsck@dev-disk-by\x2duuid-E2DD\x2d0AED.servic[/EMAIL]e has failed
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit [EMAIL="systemd-fsck@dev-disk-by\x2duuid-E2DD\x2d0AED.servic"]systemd-fsck@dev-disk-by\x2duuid-E2DD\x2d0AED.servic[/EMAIL]e has failed.
    -- 
    -- The result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: [EMAIL="systemd-fsck@dev-disk-by\x2duuid-E2DD\x2d0AED.servic"]systemd-fsck@dev-disk-by\x2duuid-E2DD\x2d0AED.servic[/EMAIL]e: Job systemd-fsck@dev-disk-by\x2duuid-E2DD\x2d
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: dev-disk-by\x2duuid-E2DD\x2d0AED.device: Job dev-disk-by\x2duuid-E2DD\x2d0AED.device/start failed wi
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: dev-disk-by\x2duuid-2b1375de\x2d666d\x2d48b3\x2d8a42\x2d154e214abf95.device: Job dev-disk-by\x2duuid
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-2b1375de\x2d666d\x2d48b3\x2d8a42\x2d154e214abf95.de
    -- Subject: Unit dev-disk-by\x2duuid-2b1375de\x2d666d\x2d48b3\x2d8a42\x2d154e214abf95.device has failed
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit dev-disk-by\x2duuid-2b1375de\x2d666d\x2d48b3\x2d8a42\x2d154e214abf95.device has failed.
    -- 
    -- The result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Dependency failed for /dev/disk/by-uuid/2b1375de-666d-48b3-8a42-154e214abf95.
    -- Subject: Unit dev-disk-by\x2duuid-2b1375de\x2d666d\x2d48b3\x2d8a42\x2d154e214abf95.swap has failed
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit dev-disk-by\x2duuid-2b1375de\x2d666d\x2d48b3\x2d8a42\x2d154e214abf95.swap has failed.
    -- 
    -- The result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Dependency failed for Swap.
    -- Subject: Unit swap.target has failed
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit swap.target has failed.
    -- 
    -- The result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: swap.target: Job swap.target/start failed with result 'dependency'.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: dev-disk-by\x2duuid-2b1375de\x2d666d\x2d48b3\x2d8a42\x2d154e214abf95.swap: Job dev-disk-by\x2duuid-2
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: dev-disk-by\x2duuid-2b1375de\x2d666d\x2d48b3\x2d8a42\x2d154e214abf95.device: Job dev-disk-by\x2duuid
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Starting Create final runtime dir for shutdown pivot root...
    -- Subject: Unit finalrd.service has begun start-up
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit finalrd.service has begun starting up.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Starting Set console font and keymap...
    -- Subject: Unit console-setup.service has begun start-up
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit console-setup.service has begun starting up.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Started Stop ureadahead data collection 45s after completed startup.
    -- Subject: Unit ureadahead-stop.timer has finished start-up
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit ureadahead-stop.timer has finished starting up.
    -- 
    -- The start-up result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Reached target Login Prompts.
    -- Subject: Unit getty.target has finished start-up
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit getty.target has finished starting up.
    -- 
    -- The start-up result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 apparmor[638]:  * Starting AppArmor profiles
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Starting Set console scheme...
    -- Subject: Unit setvtrgb.service has begun start-up
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit setvtrgb.service has begun starting up.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Closed Syslog Socket.
    -- Subject: Unit syslog.socket has finished shutting down
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit syslog.socket has finished shutting down.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Reached target Timers.
    -- Subject: Unit timers.target has finished start-up
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit timers.target has finished starting up.
    -- 
    -- The start-up result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Reached target Sockets.
    -- Subject: Unit sockets.target has finished start-up
    -- Defined-By: systemd
    -- The result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Dependency failed for /boot/efi.
    -- Subject: Unit boot-efi.mount has failed
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit boot-efi.mount has failed.
    -- 
    -- The result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: boot-efi.mount: Job boot-efi.mount/start failed with result 'dependency'.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Dependency failed for File System Check on /dev/disk/by-uuid/E2DD-0AED.
    -- Subject: Unit [EMAIL="systemd-fsck@dev-disk-by\x2duuid-E2DD\x2d0AED.servic"]systemd-fsck@dev-disk-by\x2duuid-E2DD\x2d0AED.servic[/EMAIL]e has failed
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit [EMAIL="systemd-fsck@dev-disk-by\x2duuid-E2DD\x2d0AED.servic"]systemd-fsck@dev-disk-by\x2duuid-E2DD\x2d0AED.servic[/EMAIL]e has failed.
    -- 
    -- The result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: [EMAIL="systemd-fsck@dev-disk-by\x2duuid-E2DD\x2d0AED.servic"]systemd-fsck@dev-disk-by\x2duuid-E2DD\x2d0AED.servic[/EMAIL]e: Job systemd-fsck@dev-disk-by\x2duuid-E2DD\x2d
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: dev-disk-by\x2duuid-E2DD\x2d0AED.device: Job dev-disk-by\x2duuid-E2DD\x2d0AED.device/start failed wi
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: dev-disk-by\x2duuid-2b1375de\x2d666d\x2d48b3\x2d8a42\x2d154e214abf95.device: Job dev-disk-by\x2duuid
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-2b1375de\x2d666d\x2d48b3\x2d8a42\x2d154e214abf95.de
    -- Subject: Unit dev-disk-by\x2duuid-2b1375de\x2d666d\x2d48b3\x2d8a42\x2d154e214abf95.device has failed
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit dev-disk-by\x2duuid-2b1375de\x2d666d\x2d48b3\x2d8a42\x2d154e214abf95.device has failed.
    -- 
    -- The result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Dependency failed for /dev/disk/by-uuid/2b1375de-666d-48b3-8a42-154e214abf95.
    -- Subject: Unit dev-disk-by\x2duuid-2b1375de\x2d666d\x2d48b3\x2d8a42\x2d154e214abf95.swap has failed
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit dev-disk-by\x2duuid-2b1375de\x2d666d\x2d48b3\x2d8a42\x2d154e214abf95.swap has failed.
    -- 
    -- The result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Dependency failed for Swap.
    -- Subject: Unit swap.target has failed
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit swap.target has failed.
    -- 
    -- The result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: swap.target: Job swap.target/start failed with result 'dependency'.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: dev-disk-by\x2duuid-2b1375de\x2d666d\x2d48b3\x2d8a42\x2d154e214abf95.swap: Job dev-disk-by\x2duuid-2
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: dev-disk-by\x2duuid-2b1375de\x2d666d\x2d48b3\x2d8a42\x2d154e214abf95.device: Job dev-disk-by\x2duuid
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Starting Create final runtime dir for shutdown pivot root...
    -- Subject: Unit finalrd.service has begun start-up
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit finalrd.service has begun starting up.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Starting Set console font and keymap...
    -- Subject: Unit console-setup.service has begun start-up
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit console-setup.service has begun starting up.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Started Stop ureadahead data collection 45s after completed startup.
    -- Subject: Unit ureadahead-stop.timer has finished start-up
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit ureadahead-stop.timer has finished starting up.
    -- 
    -- The start-up result is RESULT.
    Jun 02 00:18:03 jignesh-Latitude-7290 systemd[1]: Reached target Login Prompts.
    -- Subject: Unit getty.target has finished start-up
    -- Defined-By: systemd
    -- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
    -- 
    -- Unit getty.target has finished starting up.
    -- 
    -- The start-up result is RESULT.
```


Below is the output of various commands which were asked for by the community in the forums  on which I found questions and answers related to problems similar to I am seeking help about.

**$cat /etc/fstab**

    ```
# /etc/fstab: static file system information.
    #
    # Use 'blkid' to print the universally unique identifier for a
    # device; this may be used with UUID= as a more robust way to name devices
    # that works even if disks are added and removed. See fstab(5).
    #
    # <file system> <mount point>   <type>  <options>       <dump>  <pass>
    # / was on /dev/nvme0n1p3 during installation
    UUID=6fe8763a-c5a8-4057-ba4e-a81669304fbf /               ext4    errors=remount-ro 0       1
    # /boot/efi was on /dev/nvme0n1p1 during installation
    UUID=E2DD-0AED  /boot/efi       vfat    umask=0077      0       1
    # swap was on /dev/nvme0n1p4 during installation
    UUID=2b1375de-666d-48b3-8a42-154e214abf95 none            swap    sw              0       0
    
    UUID=345e070f-3d96-40a9-8774-f7eeb8d4a958   /home   ext4     nodev,nosuid   0    2 
    
    UUID=bc558793-243d-4a5e-9369-5c7b3b339c6f /mnt/jchamber auto nosuid,nodev,nofail,x-gvfs-show 0 0
```

** $ blkid**

    ```
jignesh@jignesh-Latitude-7290:~$ blkid 
    /dev/loop0: TYPE="squashfs"
    /dev/loop1: TYPE="squashfs"
    /dev/loop2: TYPE="squashfs"
    /dev/loop3: TYPE="squashfs"
    /dev/loop4: TYPE="squashfs"
    /dev/loop5: TYPE="squashfs"
    /dev/loop6: TYPE="squashfs"
    /dev/loop7: TYPE="squashfs"
    /dev/nvme0n1p1: LABEL="ESP" UUID="E2DD-0AED" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="6108d280-31cf-4306-8eb0-0d581ffc507e"
    /dev/nvme0n1p2: LABEL="OS" UUID="FCFB-790C" TYPE="vfat" PARTLABEL="Basic data partition" PARTUUID="6986226f-14b8-4e3f-8728-ee7b279a0222"
    /dev/nvme0n1p3: LABEL="UBUNTU" UUID="6fe8763a-c5a8-4057-ba4e-a81669304fbf" TYPE="ext4" PARTUUID="ec2d94d2-82e7-44c9-b178-04e5a705854b"
    /dev/nvme0n1p4: UUID="2b1375de-666d-48b3-8a42-154e214abf95" TYPE="swap" PARTUUID="554b71d5-8c3e-4254-9f13-b36b0fa8a70c"
    /dev/nvme0n1p5: LABEL="home" UUID="345e070f-3d96-40a9-8774-f7eeb8d4a958" TYPE="ext4" PARTUUID="92a4ea18-5588-4e49-857e-bde780988581"
    /dev/nvme0n1p6: LABEL="jchamber" UUID="bc558793-243d-4a5e-9369-5c7b3b339c6f" TYPE="ext4" PARTUUID="8a181965-8f20-4764-83b3-4a94b90acf82"
    /dev/loop8: TYPE="squashfs"
    /dev/loop9: TYPE="squashfs"
    /dev/loop10: TYPE="squashfs"
    /dev/loop11: TYPE="squashfs"
    /dev/loop12: TYPE="squashfs"
    /dev/loop13: TYPE="squashfs"
    /dev/loop14: TYPE="squashfs"
    /dev/loop15: TYPE="squashfs"
    /dev/loop16: TYPE="squashfs"
    /dev/loop17: TYPE="squashfs"
    /dev/loop18: TYPE="squashfs"
    /dev/loop19: TYPE="squashfs"
    /dev/loop20: TYPE="squashfs"
    /dev/loop21: TYPE="squashfs"
    /dev/loop22: TYPE="squashfs"
    /dev/loop23: TYPE="squashfs"
    /dev/loop24: TYPE="squashfs"
    /dev/loop25: TYPE="squashfs"
    /dev/loop26: TYPE="squashfs"

```

**$ lsblk -l**

    ```
jignesh@jignesh-Latitude-7290:~$ lsblk -l
    NAME      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
    loop0       7:0    0   704K  1 loop /snap/gnome-characters/741
    loop1       7:1    0 140.7M  1 loop /snap/gnome-3-26-1604/104
    loop2       7:2    0 162.9M  1 loop /snap/gnome-3-28-1804/145
    loop3       7:3    0   2.6M  1 loop /snap/gnome-calculator/920
    loop4       7:4    0   704K  1 loop /snap/gnome-characters/761
    loop5       7:5    0 140.7M  1 loop /snap/gnome-3-26-1604/102
    loop6       7:6    0  61.9M  1 loop /snap/core20/1494
    loop7       7:7    0 248.8M  1 loop /snap/gnome-3-38-2004/99
    loop8       7:8    0 164.8M  1 loop /snap/gnome-3-28-1804/161
    loop9       7:9    0 111.7M  1 loop /snap/core/13250
    loop10      7:10   0  55.5M  1 loop /snap/core18/2409
    loop11      7:11   0  65.2M  1 loop /snap/gtk-common-themes/1519
    loop12      7:12   0   548K  1 loop /snap/gnome-logs/106
    loop13      7:13   0 110.6M  1 loop /snap/core/12834
    loop14      7:14   0   2.5M  1 loop /snap/gnome-calculator/884
    loop15      7:15   0   556K  1 loop /snap/gnome-logs/112
    loop16      7:16   0   2.5M  1 loop /snap/gnome-system-monitor/174
    loop17      7:17   0     4K  1 loop /snap/bare/5
    loop18      7:18   0 260.7M  1 loop /snap/kde-frameworks-5-core18/32
    loop19      7:19   0   219M  1 loop /snap/gnome-3-34-1804/72
    loop20      7:20   0  55.5M  1 loop /snap/core18/2344
    loop21      7:21   0   219M  1 loop /snap/gnome-3-34-1804/77
    loop22      7:22   0   2.5M  1 loop /snap/gnome-system-monitor/169
    loop23      7:23   0  61.9M  1 loop /snap/core20/1434
    loop24      7:24   0  81.3M  1 loop /snap/gtk-common-themes/1534
    loop25      7:25   0 242.4M  1 loop /snap/gnome-3-38-2004/76
    loop26      7:26   0 290.5M  1 loop /snap/photogimp/141
    nvme0n1   259:0    0   477G  0 disk 
    nvme0n1p1 259:1    0   750M  0 part /boot/efi
    nvme0n1p2 259:2    0     5G  0 part 
    nvme0n1p3 259:3    0   100G  0 part /
    nvme0n1p4 259:4    0  31.8G  0 part [SWAP]
    nvme0n1p5 259:5    0   100G  0 part /home
    nvme0n1p6 259:6    0 239.5G  0 part /mnt/jchamber

```

**$ lsblk -d -o name,rota**

    ```
NAME    ROTA
    loop0      1
    loop1      1
    loop2      1
    loop3      1
    loop4      1
    loop5      1
    loop6      1
    loop7      1
    loop8      1
    loop9      1
    loop10     1
    loop11     1
    loop12     1
    loop13     1
    loop14     1
    loop15     1
    loop16     1
    loop17     1
    loop18     1
    loop19     1
    loop20     1
    loop21     1
    loop22     1
    loop23     1
    loop24     1
    loop25     1
    loop26     1
    nvme0n1    0
```


If there is any more information needed please let me know and please help me understand the cause behind this problem and how to fix this permanently.

Thanks.

---

### Post by yancek on 2022-06-02
>  If the file system is corrupted sorry to say that I have no idea on how to diagnose it.

A corrupt filesystem is a fairly common problem on any OS and their are many sites that explain how to do it on Linux.  The link below gives a detailed explanation of using fsck, the Linux software to use to do a filesystem check.  Review it and the various options for your needs.

 [https://phoenixnap.com/kb/fsck-command-linux](https://phoenixnap.com/kb/fsck-command-linux)

>  UUID=bc558793-243d-4a5e-9369-5c7b3b339c6f /mnt/jchamber auto nosuid,nodev,nofail,x-gvfs-show 0 0 

The timed out errors refer to that UUID which would indicate that might be the problem so I would run fsck on that partition to start and see what the results are, partition  nvme0n1p6.
A very common reason for a timeout error is if you have an entry in fstab for an external device partition and that device is not attached.  This is not the case with your problem as the UUID shows as a partition on your primary drive.

---

### Post by j.gohel on 2022-06-02
Thanks [**[COLOR=#000000]yancek[/COLOR]**]("https://ubuntuforums.org/member.php?u=1928724")for your response. I will definitely try fsck check and share the results here. At this moment I am not in a position to do that as I am on my job. Meanwhile I was just curious to know that how come after getting into emergency mode and typing-in exit from the root terminal the system is able to come up properly. Can you throw light on this? Thanks.

---

### Post by yancek on 2022-06-02
Some info at the link below on emergency mode and exiting it.

[https://explorelinux.com/how-to-exit-from-emergency-mode-in-linux/](https://explorelinux.com/how-to-exit-from-emergency-mode-in-linux/)

Since the problem seems to be with partition 6, I would try commenting out the line in /etc/fstab for that partition by placing a # at the beginning of the line and saving the change and rebooting.  If it boos normally, you will know there is something wrong with that entry in fstab so try changing the options one at a time and reboot.

> #UUID=bc558793-243d-4a5e-9369-5c7b3b339c6f /mnt/jchamber auto nosuid,nodev,nofail,x-gvfs-show 0 0 			 		 

---

### Post by j.gohel on 2022-06-02
I tried running fsck on all file systems except / (root) because on that it didn't allowed me. Following is the a snap of the screen 



[https://ubuntuforums.org/attachment.php?attachmentid=290558&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=290558&stc=1)

As can be seen an error like **Dirty bit is set** was found which I fixed but after that restarting the same the problem  of system getting into emergency mode and again running fsck same problem **Dirby bit is set** is found to the same partition I fixed it.

I will try the suggestion of commenting out the partition in **/etc/fstab **and share the results. Thanks.

---

### Post by j.gohel on 2022-06-02
[COLOR=#000000]I commented out the last two partitions and rebooted from emergency mode but no luck. 
[/COLOR]
```
# /etc/fstab: static file system information.
    #
    # Use 'blkid' to print the universally unique identifier for a
    # device; this may be used with UUID= as a more robust way to name devices
    # that works even if disks are added and removed. See fstab(5).
    #
    # <file system> <mount point>   <type>  <options>       <dump>  <pass>
    # / was on /dev/nvme0n1p3 during installation
    UUID=6fe8763a-c5a8-4057-ba4e-a81669304fbf /               ext4    errors=remount-ro 0       1
    # /boot/efi was on /dev/nvme0n1p1 during installation
    UUID=E2DD-0AED  /boot/efi       vfat    umask=0077      0       1
    # swap was on /dev/nvme0n1p4 during installation
    UUID=2b1375de-666d-48b3-8a42-154e214abf95 none            swap    sw              0       0
    
    #UUID=345e070f-3d96-40a9-8774-f7eeb8d4a958   /home   ext4     nodev,nosuid   0    2 
    
    #UUID=bc558793-243d-4a5e-9369-5c7b3b339c6f /mnt/jchamber auto nosuid,nodev,nofail,x-gvfs-show 0 0
```


[COLOR=#000000]The system still gets into emergency mode and in the **journalctl -xb **logs now the timeout appears for **boot/efi** and **swap** partitions.

Please let me know what next should I try to get to the root of this problem and fix this. Thanks.
[/COLOR]

---

### Post by j.gohel on 2022-06-02
Based on the instructions in a link  [https://medium.com/@nehamuthiyan/getting-out-of-the-emergency-mode-in-ubuntu-818180ce3940](https://medium.com/@nehamuthiyan/getting-out-of-the-emergency-mode-in-ubuntu-818180ce3940) I found, I booted with a live USB and tried following:

```
ubuntu@ubuntu:~$ blkid
/dev/nvme0n1p1: LABEL="ESP" UUID="E2DD-0AED" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="6108d280-31cf-4306-8eb0-0d581ffc507e"
/dev/nvme0n1p2: LABEL="OS" UUID="FCFB-790C" TYPE="vfat" PARTLABEL="Basic data partition" PARTUUID="6986226f-14b8-4e3f-8728-ee7b279a0222"
/dev/nvme0n1p3: LABEL="UBUNTU" UUID="6fe8763a-c5a8-4057-ba4e-a81669304fbf" TYPE="ext4" PARTUUID="ec2d94d2-82e7-44c9-b178-04e5a705854b"
/dev/nvme0n1p5: LABEL="home" UUID="345e070f-3d96-40a9-8774-f7eeb8d4a958" TYPE="ext4" PARTUUID="92a4ea18-5588-4e49-857e-bde780988581"
/dev/nvme0n1p6: LABEL="jchamber" UUID="bc558793-243d-4a5e-9369-5c7b3b339c6f" TYPE="ext4" PARTUUID="8a181965-8f20-4764-83b3-4a94b90acf82"
ubuntu@ubuntu:~$ sudo e2fsck -y /dev/nvme0n1p1
e2fsck 1.44.1 (24-Mar-2018)
ext2fs_open2: Bad magic number in super-block
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/nvme0n1p1

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

/dev/nvme0n1p1 contains a vfat file system labelled 'ESP'

ubuntu@ubuntu:~$ sudo e2fsck -y /dev/nvme0n1p6
e2fsck 1.44.1 (24-Mar-2018)
jchamber: clean, 3826/15695872 files, 13688285/62767616 blocks

ubuntu@ubuntu:~$ sudo e2fsck -y /dev/nvme0n1p5
e2fsck 1.44.1 (24-Mar-2018)
home: clean, 267357/6553600 files, 3434531/26214400 blocks

ubuntu@ubuntu:~$ sudo e2fsck -y /dev/nvme0n1p3
e2fsck 1.44.1 (24-Mar-2018)
UBUNTU: clean, 352536/6553600 files, 5025769/26214400 blocks

ubuntu@ubuntu:~$ sudo e2fsck -y /dev/nvme0n1p2
e2fsck 1.44.1 (24-Mar-2018)
ext2fs_open2: Bad magic number in super-block
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/nvme0n1p2

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

/dev/nvme0n1p2 contains a vfat file system labelled 'OS'

ubuntu@ubuntu:~$ sudo fsck /dev/nvme0n1p1
fsck from util-linux 2.31.1
fsck.fat 4.1 (2017-01-24)
/dev/nvme0n1p1: 42 files, 9545/190976 clusters

ubuntu@ubuntu:~$ sudo fsck /dev/nvme0n1p2
fsck from util-linux 2.31.1
fsck.fat 4.1 (2017-01-24)
/dev/nvme0n1p2: 1012 files, 538685/1307648 clusters

ubuntu@ubuntu:~$ sudo fsck /dev/nvme0n1p3
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
UBUNTU: clean, 352536/6553600 files, 5025769/26214400 blocks

ubuntu@ubuntu:~$ sudo fsck /dev/nvme0n1p4
fsck from util-linux 2.31.1

ubuntu@ubuntu:~$ sudo fsck /dev/nvme0n1p5
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
home: clean, 267357/6553600 files, 3434531/26214400 blocks

ubuntu@ubuntu:~$ sudo fsck /dev/nvme0n1p6
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
jchamber: clean, 3826/15695872 files, 13688285/62767616 blocks

ubuntu@ubuntu:~$ 



 
```

Is there anything problematic in this? If no then what can be the problem? Thanks.

---

### Post by j.gohel on 2022-06-04
Hello,

Is there no one who can help me out resolve my problem? For getting any concrete inputs if I need to post my problem to any other forum then please guide me to do so. 

I originally posted this same problem on [https://askubuntu.com/q/1411800](https://askubuntu.com/q/1411800) but I didn&#8217;t received any replies and thus I posted to this forum with a hope that this being the official community for any problems with Ubuntu I would definitely get assistance and I did received initial guidance but after sharing the results of whatever I could try I am clueless on what to try next. So please guide me. Thanks.

---

### Post by dragonfly41 on 2022-06-04
As one Dell user to another I will try to suggest a way forward.

Reading your report ..

> The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

So .. you should try running e2fsck (again) "with an alternate superblock".


[P.S.]

If you follow this guide, 

[https://phoenixnap.com/kb/fsck-command-linux](https://phoenixnap.com/kb/fsck-command-linux)

you read ..

Before you can run a disk check with fsck, you need to unmount a disk or partition. If you try to run fsck on a mounted disk or partition, you will get a warning:
Make sure to run the unmount command:


Thus if you are attempting to repair the partition containing Ubuntu, you must close down your laptop, and reboot using bootable LiveUSB &#8220;Try Ubuntu&#8221; (not Install Ubuntu).

Then from within LiveUSB session you can apply fsck to the unmounted partition.

It can be helpful to install Gparted into the LiveUSB since it shows all partitions in multiple drives.


[P.S.] again

I have just noticed that the report refers to superblock 8193 .. I am fairly sure that all alternative superblocks should be powers of 2 .. in this case 8192 .. that must be an error in documentation.

So 8192, 16384, .. , takes me back to octal coding days.

---

### Post by j.gohel on 2022-06-11
[**[COLOR=#000000]dragonfly41[/COLOR]**]("https://ubuntuforums.org/member.php?u=1261878") Thanks for your response and sorry for being late in replying.

Regarding

> 
Thus if you are attempting to repair the partition containing Ubuntu,   you must close down your laptop, and reboot using bootable LiveUSB “Try   Ubuntu” (not Install Ubuntu).

Then from within LiveUSB session you can apply fsck to the unmounted partition.


The results I shared in my previous post [https://ubuntuforums.org/showthread.php?t=2475622&p=14098433#post14098433](https://ubuntuforums.org/showthread.php?t=2475622&p=14098433#post14098433) were based on that approach.


Regarding 

> It can be helpful to install Gparted into the LiveUSB since it shows all partitions in multiple drives.

I have attached herewith the screenshot of gparted if it can help to figure anything which can help in resolving the problem under discussion.

Regarding

> 
[QUOTE]
                             The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>                            So .. you should try running e2fsck (again) "with an alternate superblock".

I have just noticed that the report refers to superblock 8193 .. I am  fairly sure that all alternative superblocks should be powers of 2 .. in  this case 8192 .. that must be an error in documentation.

So 8192, 16384, .. , takes me back to octal coding days.         
[/QUOTE]

Before following your recommendation of **running e2fsck (again) "with an alternate superblock" **I have a question to ask based on the error message related to superblock. It says that

[I]The superblock could not be read or does not describe a valid ext2/ext3/ext4 filesystem.  If the device is valid and it really contains an ext2/ext3/ext4 filesystem

[/I]If you check gparted screenshot it can be seen that **/dev/nvme0n1p1 **and **/dev/nvme0n1p2 **both are of type **fat32 **file system. Considering this will it be correct to follow your recommendation on those two partitions? And running e2fsck and fsck on remaining partitions reported they are clean (please refer my referenced post in this reply)

That makes me ask can any problem in **/dev/nvme0n1p1 **and **/dev/nvme0n1p2 **cause the problems under discussion? If yes is there any way it can be fixed without reinstalling Ubuntu?

Also I noticed that even though I am able to use the system after exiting from emergency mode but trying to run any music, videos I cannot hear any sound. It used to work without any problems and I did tried reinstalling pulse-audio and other related things recommended for any sound related issue in Ubuntu. Can this be caused because of the problem making the system end up in emergency mode?

Thanks.

---

### Post by j.gohel on 2022-06-11
After my last post I also tried boot-repair from live USB and rebooted but no luck. I still end-up in emergency mode and then exiting from it I can login to the system. This is really annoying. Can any expert please share their views and help me out fixing the issue? Below I am sharing the boot repair summary created:


```
boot-repair-4ppa200                                              [20220611_1228]

============================= Boot Repair Summary ==============================





grub-probe: error: cannot find a GRUB drive for /dev/sda1.  Check your device.map.
grub-probe: error: cannot find a GRUB drive for /dev/sda1.  Check your device.map.

Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi-amd64-signed of
nvme0n1p3,
using the following options:  nvme0n1p1/boot/efi
Additional repair will be performed:  unhide-bootmenu-10s use-standard-efi-file


Mount nvme0n1p1 on /mnt/boot-sav/nvme0n1p3/boot/efi

Unhide GRUB boot menu in nvme0n1p3/etc/default/grub

=============== Reinstall the grub-efi-amd64-signed of nvme0n1p3 ===============

chroot /mnt/boot-sav/nvme0n1p3 grub-install --version
grub-install (GRUB) 2.02-2ubuntu8.23
modprobe: FATAL: Module efivars not found in directory /lib/modules/4.15.0-29-generic
chroot /mnt/boot-sav/nvme0n1p3 modprobe efivars

chroot /mnt/boot-sav/nvme0n1p3 efibootmgr -v before grub install
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0001,0002,0003
Boot0000* Windows Boot Manager    HD(2,GPT,2d4577d5-eb6c-4fee-a555-8b38cb13c178,0xfa000,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...M................
Boot0001* ubuntu    HD(1,GPT,6108d280-31cf-4306-8eb0-0d581ffc507e,0x800,0x177000)/File(EFIubuntushimx64.efi)
Boot0002* Linux Firmware Updater    HD(1,GPT,6108d280-31cf-4306-8eb0-0d581ffc507e,0x800,0x177000)/File(EFIubuntushimx64.efi).f.w.u.p.d.x.6.4...e.f.i...
Boot0003* UEFI: SanDisk Cruzer Blade 1.26, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(1,0)/HD(1,MBR,0x663eb4c4,0x3906b4,0x1240)..BO
Boot0004* Diskette Drive    BBS(Floppy,Diskette Drive,0x0)..BO
Boot0005* USB Storage Device    BBS(USB,USB Storage Device,0x0)..BO
Boot0006* CD/DVD/CD-RW Drive    BBS(CDROM,CD/DVD/CD-RW Drive,0x0)..BO
Boot0007* Onboard NIC    BBS(Network,IBA CL Slot 00FE v0112,0x0)..BO
Boot0008* UEFI: KXG50ZNV512G NVMe TOSHIBA 512GB, Partition 1    HD(1,GPT,6108d280-31cf-4306-8eb0-0d581ffc507e,0x800,0x177000)/File(EFIbootbootx64.efi)..BO

chroot /mnt/boot-sav/nvme0n1p3 uname -r
4.15.0-29-generic

chroot /mnt/boot-sav/nvme0n1p3 grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
Installation finished. No error reported.
df /dev/nvme0n1p1
mv /mnt/boot-sav/nvme0n1p3/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/nvme0n1p3/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/nvme0n1p3/boot/efi/efi/ubuntu/shimx64.efi /mnt/boot-sav/nvme0n1p3/boot/efi/EFI/Boot/bootx64.efi
cp /mnt/boot-sav/nvme0n1p3/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/nvme0n1p3/boot/efi/EFI/Boot/

chroot /mnt/boot-sav/nvme0n1p3 grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
Installation finished. No error reported.

chroot /mnt/boot-sav/nvme0n1p3 efibootmgr -v after grub install
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0001,0002,0003
Boot0000* Windows Boot Manager    HD(2,GPT,2d4577d5-eb6c-4fee-a555-8b38cb13c178,0xfa000,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...M................
Boot0001* ubuntu    HD(1,GPT,6108d280-31cf-4306-8eb0-0d581ffc507e,0x800,0x177000)/File(EFIubuntushimx64.efi)
Boot0002* Linux Firmware Updater    HD(1,GPT,6108d280-31cf-4306-8eb0-0d581ffc507e,0x800,0x177000)/File(EFIubuntushimx64.efi).f.w.u.p.d.x.6.4...e.f.i...
Boot0003* UEFI: SanDisk Cruzer Blade 1.26, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(1,0)/HD(1,MBR,0x663eb4c4,0x3906b4,0x1240)..BO
Boot0004* Diskette Drive    BBS(Floppy,Diskette Drive,0x0)..BO
Boot0005* USB Storage Device    BBS(USB,USB Storage Device,0x0)..BO
Boot0006* CD/DVD/CD-RW Drive    BBS(CDROM,CD/DVD/CD-RW Drive,0x0)..BO
Boot0007* Onboard NIC    BBS(Network,IBA CL Slot 00FE v0112,0x0)..BO
Boot0008* UEFI: KXG50ZNV512G NVMe TOSHIBA 512GB, Partition 1    HD(1,GPT,6108d280-31cf-4306-8eb0-0d581ffc507e,0x800,0x177000)/File(EFIbootbootx64.efi)..BO
Warning: NVram was not modified.

chroot /mnt/boot-sav/nvme0n1p3 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/i915_bpo_enable_rc6.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-180-generic
Found initrd image: /boot/initrd.img-4.15.0-180-generic
Found linux image: /boot/vmlinuz-4.15.0-176-generic
Found initrd image: /boot/initrd.img-4.15.0-176-generic
Found linux image: /boot/vmlinuz-4.15.0-161-generic
Found initrd image: /boot/initrd.img-4.15.0-161-generic
grub-probe: error: cannot find a GRUB drive for /dev/sda1.  Check your device.map.
Adding boot menu entry for EFI firmware configuration

Unhide GRUB boot menu in nvme0n1p2/boot/grub/grub.cfg

Unhide GRUB boot menu in nvme0n1p3/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your UEFI firmware boot on the Ubuntu 18.04.6 LTS entry (nvme0n1p1/efi/ubuntu/shimx64.efi file) !


============================ Boot Info After Repair ============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/grubx64.efi 
                       /efi/Boot/shimx64.efi /efi/ubuntu/fwupdx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

nvme0n1p2: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg

nvme0n1p3: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 18.04.6 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

nvme0n1p4: _____________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

nvme0n1p5: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

nvme0n1p6: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/grub.cfg


================================ 1 OS detected =================================

OS#1:   Ubuntu 18.04.6 LTS on nvme0n1p3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: Intel Corporation from Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 18.04.1 LTS, bionic, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 1.25.0 from Dell Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot enabled but mokutil says: SecureBoot enabled - Please report this message to boot.repair@gmail.com.
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0001,0002,0003
Boot0000* Windows Boot Manager    HD(2,GPT,2d4577d5-eb6c-4fee-a555-8b38cb13c178,0xfa000,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...M................
Boot0001* ubuntu    HD(1,GPT,6108d280-31cf-4306-8eb0-0d581ffc507e,0x800,0x177000)/File(\EFI\ubuntu\shimx64.efi)
Boot0002* Linux Firmware Updater    HD(1,GPT,6108d280-31cf-4306-8eb0-0d581ffc507e,0x800,0x177000)/File(\EFI\ubuntu\shimx64.efi)\.f.w.u.p.d.x.6.4...e.f.i...
Boot0003* UEFI: SanDisk Cruzer Blade 1.26, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(1,0)/HD(1,MBR,0x663eb4c4,0x3906b4,0x1240)..BO
Boot0004* Diskette Drive    BBS(Floppy,Diskette Drive,0x0)..BO
Boot0005* USB Storage Device    BBS(USB,USB Storage Device,0x0)..BO
Boot0006* CD/DVD/CD-RW Drive    BBS(CDROM,CD/DVD/CD-RW Drive,0x0)..BO
Boot0007* Onboard NIC    BBS(Network,IBA CL Slot 00FE v0112,0x0)..BO
Boot0008* UEFI: KXG50ZNV512G NVMe TOSHIBA 512GB, Partition 1    HD(1,GPT,6108d280-31cf-4306-8eb0-0d581ffc507e,0x800,0x177000)/File(EFI\boot\bootx64.efi)..BO

728124f6ec8e22fbdbe7034812c81b95   nvme0n1p1/Boot/bkpbootx64.efi
728124f6ec8e22fbdbe7034812c81b95   nvme0n1p1/Boot/bootx64.efi
5dabe049a4dad758d975dc2e60a7f00e   nvme0n1p1/Boot/fbx64.efi
621356d82b109cd860ad92cdf241c58b   nvme0n1p1/Boot/grubx64.efi
ded965934506efb38a6dcb9ac5b2b79e   nvme0n1p1/Boot/shimx64.efi
1a689ed0360a33d1cc04ec47dc232437   nvme0n1p1/ubuntu/fwupdx64.efi
621356d82b109cd860ad92cdf241c58b   nvme0n1p1/ubuntu/grubx64.efi
f243a42f3bd3164872e792dbc2610270   nvme0n1p1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   nvme0n1p1/ubuntu/shimx64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p2    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p3    : is-os,    64, apt-get,    signed grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
nvme0n1p5    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p6    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios

Partitions info (2/3): _________________________________________________________

nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p3    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p6    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p2    : not--sepboot,    no-kernel,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p3    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme0n1
nvme0n1p5    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p6    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 477 GiB, 512110190592 bytes, 1000215216 sectors
Disk identifier: C9F216A5-53CA-49BA-8E33-A8FBC226511E
              Start        End   Sectors   Size Type
nvme0n1p1      2048    1538047   1536000   750M EFI System
nvme0n1p2   1538048   12023807  10485760     5G Microsoft basic data
nvme0n1p3  12023808  221739007 209715200   100G Linux filesystem
nvme0n1p4 933595136 1000214527  66619392  31.8G Linux swap
nvme0n1p5 221739008  431454207 209715200   100G Linux filesystem
nvme0n1p6 431454208  933595135 502140928 239.5G Linux filesystem
Partition table entries are not in disk order.
Disk sda: 3.7 GiB, 4004511744 bytes, 7821312 sectors
Disk identifier: 0x663eb4c4
      Boot   Start     End Sectors  Size Id Type
sda1  *          0 3815135 3815136  1.8G  0 Empty
sda2       3737268 3741939    4672  2.3M ef EFI (FAT-12/16/32)

parted -lm (filtered): _________________________________________________________

sda:4005MB:scsi:512:512:unknown:SanDisk Cruzer Blade:;
nvme0n1:512GB:nvme:512:512:gpt:NVMe Device:;
1:1049kB:787MB:786MB:fat32:EFI system partition:boot, esp;
2:787MB:6156MB:5369MB:fat32:Basic data partition:msftdata;
3:6156MB:114GB:107GB:ext4::;
5:114GB:221GB:107GB:ext4::;
6:221GB:478GB:257GB:ext4::;
4:478GB:512GB:34.1GB:linux-swap(v1)::;

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda         iso9660  2018-07-25-03-21-56-00                                                    Ubuntu 18.04.1 LTS amd64 
&#9500;&#9472;sda1      iso9660  2018-07-25-03-21-56-00               663eb4c4-01                          Ubuntu 18.04.1 LTS amd64 
&#9492;&#9472;sda2      vfat     0D5F-1DB6                            663eb4c4-02                          Ubuntu 18.04.1 LTS amd64 
nvme0n1                                                                                                                 
&#9500;&#9472;nvme0n1p1 vfat     E2DD-0AED                            6108d280-31cf-4306-8eb0-0d581ffc507e ESP                      EFI system partition
&#9500;&#9472;nvme0n1p2 vfat     FCFB-790C                            6986226f-14b8-4e3f-8728-ee7b279a0222 OS                       Basic data partition
&#9500;&#9472;nvme0n1p3 ext4     6fe8763a-c5a8-4057-ba4e-a81669304fbf ec2d94d2-82e7-44c9-b178-04e5a705854b UBUNTU                   
&#9500;&#9472;nvme0n1p4 swap     2b1375de-666d-48b3-8a42-154e214abf95 554b71d5-8c3e-4254-9f13-b36b0fa8a70c                          
&#9500;&#9472;nvme0n1p5 ext4     345e070f-3d96-40a9-8774-f7eeb8d4a958 92a4ea18-5588-4e49-857e-bde780988581 home                     
&#9492;&#9472;nvme0n1p6 ext4     bc558793-243d-4a5e-9369-5c7b3b339c6f 8a181965-8f20-4764-83b3-4a94b90acf82 jchamber                 

Mount points (filtered): _______________________________________________________

                Avail Use% Mounted on
/dev/nvme0n1p1 706.2M   5% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p2     3G  41% /mnt/boot-sav/nvme0n1p2
/dev/nvme0n1p3  75.8G  18% /mnt/boot-sav/nvme0n1p3
/dev/nvme0n1p5  81.9G  11% /mnt/boot-sav/nvme0n1p5
/dev/nvme0n1p6 175.2G  20% /mnt/boot-sav/nvme0n1p6
/dev/sda            0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/nvme0n1p1 vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/nvme0n1p2 vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/nvme0n1p3 ext4            rw,relatime,data=ordered
/dev/nvme0n1p5 ext4            rw,relatime,data=ordered
/dev/nvme0n1p6 ext4            rw,relatime,data=ordered
/dev/sda       iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048

=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid 6fe8763a-c5a8-4057-ba4e-a81669304fbf root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

=================== nvme0n1p2/boot/grub/grub.cfg (filtered) ====================

Install Complete, remove media and reboot.
Dell Recovery
Dell Recovery (safe graphics mode)

================= nvme0n1p2: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

=================== nvme0n1p3/boot/grub/grub.cfg (filtered) ====================

Ubuntu   6fe8763a-c5a8-4057-ba4e-a81669304fbf
Ubuntu, with Linux 4.15.0-180-generic   6fe8763a-c5a8-4057-ba4e-a81669304fbf
Ubuntu, with Linux 4.15.0-176-generic   6fe8763a-c5a8-4057-ba4e-a81669304fbf
Ubuntu, with Linux 4.15.0-161-generic   6fe8763a-c5a8-4057-ba4e-a81669304fbf
### END /etc/grub.d/30_os-prober ###
System setup   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###
Restore Ubuntu 16.04 to factory state

======================== nvme0n1p3/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p3 during installation
UUID=6fe8763a-c5a8-4057-ba4e-a81669304fbf /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=E2DD-0AED  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/nvme0n1p4 during installation
UUID=2b1375de-666d-48b3-8a42-154e214abf95 none            swap    sw              0       0
UUID=345e070f-3d96-40a9-8774-f7eeb8d4a958   /home   ext4     nodev,nosuid   0    2
UUID=bc558793-243d-4a5e-9369-5c7b3b339c6f /mnt/jchamber auto nosuid,nodev,nofail,x-gvfs-show 0 0

==================== nvme0n1p3/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="i915_bpo.enable_rc6=0 i915_bpo.enable_rc6=0 i915_bpo.enable_rc6=0 i915_bpo.enable_rc6=0 i915_bpo.enable_rc6=0"
GRUB_DISABLE_OS_PROBER=false

================= nvme0n1p3: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
   5.733406067 = 6.156197888    boot/grub/grub.cfg                             1
  34.678768158 = 37.236043776   boot/vmlinuz-4.15.0-161-generic                1
  28.858470917 = 30.986547200   boot/vmlinuz-4.15.0-176-generic                2
  20.538162231 = 22.052683776   boot/vmlinuz-4.15.0-180-generic                2
  20.538162231 = 22.052683776   vmlinuz                                        2
  28.858470917 = 30.986547200   vmlinuz.old                                    2
  25.767520905 = 27.667664896   boot/initrd.img-4.15.0-161-generic             6
  27.008728027 = 29.000400896   boot/initrd.img-4.15.0-176-generic             4
  22.834640503 = 24.518508544   boot/initrd.img-4.15.0-180-generic             6
  22.834640503 = 24.518508544   initrd.img                                     6
  27.008728027 = 29.000400896   initrd.img.old                                 4

=================== nvme0n1p3: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 12808 Aug 24  2020 10_linux
-rwxr-xr-x 1 root root 11298 Aug 23  2018 20_linux_xen
-rwxr-xr-x 1 root root 12059 Aug 23  2018 30_os-prober
-rwxr-xr-x 1 root root  1418 Apr 15  2016 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr 15  2016 40_custom
-rwxr-xr-x 1 root root   216 Apr 15  2016 41_custom
-rwxr-xr-x 1 root root  1255 Sep  6  2018 99_dell_recovery

==================== nvme0n1p3/etc/grub.d/99_dell_recovery =====================

#!/bin/bash -e
source /usr/lib/grub/grub-mkconfig_lib
cat << EOF
menuentry "Restore Ubuntu 16.04 to factory state" {
        search --no-floppy --hint '(hd0,gpt2)' --set --fs-uuid FCFB-790C
        set uuid_options="uuid=FCFB-790C"
        if [ -s /factory/common.cfg ]; then
            source /factory/common.cfg
        else
            set options="boot=casper automatic-ubiquity noprompt quiet splash nomodeset"
        fi
        if [ -s /factory/post-rts-gfx.cfg ]; then
            source /factory/post-rts-gfx.cfg
        fi
        if [ -s /factory/post-rts-wlan.cfg ]; then
            source /factory/post-rts-wlan.cfg
        fi
        #Support starting from a loopback mount (Only support ubuntu.iso for filename)
        if [ -f /ubuntu.iso ]; then
            loopback loop /ubuntu.iso
            set root=(loop)
            set options="\$options iso-scan/filename=/ubuntu.iso"
        fi
        if [ -n "\${lang}" ]; then
            set options="\$options locale=\$lang"
        fi
        if [ -s /factory/dual_enable ]; then
            set options="\$options dell-recovery/dual_boot=true"
        fi 
        linux   /casper/vmlinuz.efi dell-recovery/recovery_type=hdd \$uuid_options \$options
    initrd    /casper/initrd.lz
}
EOF

====================== sda/boot/grub/grub.cfg (filtered) =======================

Try Ubuntu without installing
Install Ubuntu
OEM install (for manufacturers)
Check disc for defects

==================== sda: Location of files loaded by Grub =====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
```

What is really wierd is that the system gets into emergency mode and then exiting from it I can see login screen and then use the system and everytime I am viewing **journalctl -xb** from emergency mode I can see only timeout entries in red like I have shown in my first post [https://ubuntuforums.org/showthread.php?t=2475622&p=14098344#post14098344](https://ubuntuforums.org/showthread.php?t=2475622&p=14098344#post14098344) (see Log 4). 

Can this problem be caused by any hardware issues? If yes, then one question raises in my mind that then how come I am able to come out of emergency mode and then use the system?

As can be seen I have tried every recommendation given and tried most of the possible solutions I found on web related but I no progress at all. 

**Note**: If there is another forum from which I can get some concrete solution then please guide me to that forum so that I can see help from that forum as well.

Thanks.

---

### Post by Yellow Pasque on 2022-06-11
The superblock error is due to running 'e2fsck' on a FAT partition. In general, just use 'fsck' and it should automatically detect partition type.

---

### Post by j.gohel on 2022-06-11
[**[COLOR=#000000]Yellow Pasque[/COLOR]**]("https://ubuntuforums.org/member.php?u=327594")

I also ran fsck on partitions from live USB whose results were shared in post [https://ubuntuforums.org/showthread.php?t=2475622&p=14098433#post14098433](https://ubuntuforums.org/showthread.php?t=2475622&p=14098433#post14098433). 
For quick view quoting those results below:

> 
ubuntu@ubuntu:~$ sudo fsck /dev/nvme0n1p1
fsck from util-linux 2.31.1
fsck.fat 4.1 (2017-01-24)
/dev/nvme0n1p1: 42 files, 9545/190976 clusters

ubuntu@ubuntu:~$ sudo fsck /dev/nvme0n1p2
fsck from util-linux 2.31.1
fsck.fat 4.1 (2017-01-24)
/dev/nvme0n1p2: 1012 files, 538685/1307648 clusters

ubuntu@ubuntu:~$ sudo fsck /dev/nvme0n1p3
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
UBUNTU: clean, 352536/6553600 files, 5025769/26214400 blocks

ubuntu@ubuntu:~$ sudo fsck /dev/nvme0n1p4
fsck from util-linux 2.31.1

ubuntu@ubuntu:~$ sudo fsck /dev/nvme0n1p5
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
home: clean, 267357/6553600 files, 3434531/26214400 blocks

ubuntu@ubuntu:~$ sudo fsck /dev/nvme0n1p6
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
jchamber: clean, 3826/15695872 files, 13688285/62767616 blocks



Thanks.

---

