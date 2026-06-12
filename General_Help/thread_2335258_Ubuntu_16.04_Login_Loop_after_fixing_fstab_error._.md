---
title: "Ubuntu 16.04 Login Loop after fixing fstab error. Posting this is my last resort. :("
date: 2016-08-26
forum: General Help
---

### Post by basilamo on 2016-08-26
[LIST]
[*]Hi guys. Yesterday I had a problem with my fstab file because I tried to create a /home partition cause I didn't have one(which I later figured is unnecessary). I searched through the net how to fix it, tried a lot and failed, until I found a way to edit the file on recovery mode. Then another problem happened, I can't login as admin but I can however login as guest and I can't connect to the internet(as guest).
[/LIST]

The login loop problem looks pretty much the same as others.
Except for if I try to login in tty1 it says incorrect login.

So tried troubleshooting through Recovery Mode running the root shell.

I also noticed while it's booting to recovery mode the last message along the "**[   OK   ]**" messages reads,
 " **/bin/sh: 0: Can't open while systemctl list-jobs | grep -v friendly-recovery | g rep -q running; do sleep 0.2; done** "

Also when I run **apt-get update **I get a lot of

[B]Err :7 [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) xenial-updates In Release
  Temporary failure resolving ' ph.archive.ubuntu.com'[/B]                         --with other similar yet varying messages

[B]W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://ph.archive.ubuntu.com/ubuntu/dists/xenial/InRelease)
  Temporary failure resolving ' ph.archive.ubuntu.com'[/B]                         --with other similar yet varying messages

Last line is..
**W: Some index files failed to download. They have been ignored, or old ones used instead.**


I tried most what other forums suggested and still no change...maybe other solutions didn't work cause of this error I'm thinking that I can't connect to the net.. I tried **.Xauthority**, I have no such file.. I tried **ls -ld /tmp**, nothing happens... I tried lightdm, still nothing... i tried **.xsession-errors** and it was blank.. checked my **.profile** and it was clean... changing the password does nothing.. This has literally wasted my day and I am totally in regret. Please help. If there are any of you guys who want me to check or run and post the results here I am more than willing. I am new to this so I might need a step-by-step solution if it is too complex.

---

### Post by deadflowr on 2016-08-26
When you created the /home partition, did you follow any guide to do so, or was is by ear?
Since I would like to think you did the former, could you post a link to which guide.

Sidenote: also recovery mode's root shell runs non-networking and read-only, but you can enable both by setting up the networking option in the recovery mode list first and then enter the root shell, which would then be set read/write. It's a nifty trick. Or else to run root read/write you need to remount the filesystem.

---

### Post by basilamo on 2016-08-27
Hi. I didn't get to create the /home partition since the error occurred when I restarted it. 
I can't remember the exact link to what guide I followed. But there was a part that I edited the fstab file with this format.. 
[FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif][COLOR=#111111]UUID=New-partition-UUID /home ext4 nodev,nosuid 0 2[/COLOR][/FONT]
 Something was wrong with the editing that's when the first problem occurred. I fixed it by simply opening my fstab file on recovery mode and deleting all the lines that I added.
Thanks for the note. I'll definitely do that and try again the other solutions.

---

### Post by basilamo on 2016-08-27
I tried enabling networking option and while loading this happened..

grep: /etc/resolv.conf : No such file or directory
like 16 lines of this, then...
[TIME] Timed out waiting for device dev-di...\x2daec9\x2d43879d3aece.device.
[DEPEND] Dependency failed for /dev/disk/by-...124-92d2-4979-aec9-438379d3aece.
[DEPEND] Dependency failed for Swap

---

### Post by deadflowr on 2016-08-27
If you don't need networking, if you're only going to be editing the fstab file then it's probably not needed, then you can just run the remounting command:
```
mount -o remount,rw /
```

I'm not about that networking hang, does it return you to the main recovery page?

---

### Post by basilamo on 2016-08-27
I'm done with editing the fstab. My problem now is that I can't login to desktop as admin(stuck in login loop), only as guest. When I try to ctrl+alt+F1 i can't login either, it says login incorrect. I can however access through root shell. Is there any way I can troubleshoot the problem in root shell?

---

### Post by deadflowr on 2016-08-27
In root shell check that you own all the files in the /home directory.

```
 ls -la /home/your-username
```
it should output a long list of folders and files.
If the username that is listed is not yours, run
```
chown -R your-username:your-username /home/your-username
```
and of course, replace the your-username entries with that of your username.

---

### Post by basilamo on 2016-09-02
I think I'm getting close. I just got in tty1. while trying to fix via lightdm process my lightdm got deleted and i was not able to reinstall. so when I log in to my pc. instead of the login screen gui, the tty1 opens. finally I got in tty1. What i'm trying to do now is install the lightdm back to get back the login gui. So I tried to run [B]sudo apt-get install lightdm

[/B]I got I got these three errors from the last part of the process:
[B]Err:1 [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 lightdm amd64 1.18.2-0ubuntu1
   404 Not Found [IP: 202.90.159.172 80]
E: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/pool/main/l/lightdm/lightdm_1.18.2-0ubuntu1_amd64.deb](http://ph.archive.ubuntu.com/ubuntu/pool/main/l/lightdm/lightdm_1.18.2-0ubuntu1_amd64.deb)   404 Not Found [IP: 202.90.159.172 80]

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

[/B]when I try --fix-missing it says command not found

when I try try apt-get update, I get this:

[B]W: chmod 0700 of directory /var/lib/apt/lists/partial failed - SetupAPTPartialDirectory (1: Operation not permitted)
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied)
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

[/B]When I also run **dpkg-reconfigure lightdm** it says **/usr/sbin/dpkg-reconfigure must be run as root**


All I want is to keep the files safe or if I can still make a backup. Any procedure to fix the problem would be great as long as my files are safe. all my files are save in /

Thank you so much for helping. :)

---

