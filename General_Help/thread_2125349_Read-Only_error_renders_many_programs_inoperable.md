---
title: "Read-Only error renders many programs inoperable"
date: 2013-03-13
forum: General Help
---

### Post by ChaoticMarin on 2013-03-13
This error seems to appear when I try to load memory intensive programs, such as World of Warcraft under wine. It is not present when Ubuntu starts and is gone after a restart, but is extremely easy to trigger. (I literally cannot play WoW right now because trying to load it alone triggers this.)

Here are some of the affected programs and their errors returned.

[LIST]
[*]Skype 4.1 will crash to the login screen with a "Disk I/O error" 
[*]Audacious starts telling me "Cannot open /home/marin/.config/audacious/playlists/1000.audpl: Read-only file system." periodically 
[*]Launching WoW through the gui yields no results. Launching it through the terminal yields this: 
[/LIST]
```
marin@marin-Studio-1535:~/.wine/drive_c/Program Files/World of Warcraft$ wine "World of Warcraft Launcher.exe"

fixme:heap:HeapSetInformation (nil) 1 (nil) 0
Could not open log file at 'C:\users\Public\Application   Data\Battle.net\Setup\wow_enus\Log\Setup-20130313-174552969.log'.   Disabling logging.
```

[LIST]
[*]Launching Teamviewer through the gui yields no results. Launching it through the terminal yields this: 
[/LIST]
```
marin@marin-Studio-1535:~$ teamviewer

Init...
/opt/teamviewer8/tv_bin/script/tvw_main: line 14: /home/marin/.config/teamviewer8/logfiles/startup.log: Read-only file system

Error: Init failed. Please check '/home/marin/.config/teamviewer8/logfiles/startup.log'

```


[LIST]
[*]Launching Chromium through the gui yields no results. (I'm using Firefox, which was already open.) Launching it throuh the terminal yields this: 
[/LIST]
```
marin@marin-Studio-1535:~$ chromium-browser
[5160:5185:0313/175737:ERROR:nss_util.cc(490)] Error initializing NSS with a persistent database (sql:/home/marin/.pki/nssdb): NSS error code: -8187
[5160:5160:0313/175737:ERROR:process_singleton_linux.cc(263)] Failed to create /home/marin/.config/chromium/SingletonLock: Read-only file system
[5160:5160:0313/175737:ERROR:chrome_browser_main.cc(1066)] Failed to create a ProcessSingleton for your profile directory. This means that running multiple instances would start multiple browser processes rather than opening a new window in the existing process. Aborting now to avoid profile corruption.
```

 These errors seem to be a theme with all programs that were not already open before the error started. (Note: The Audacious error occurs even though Audacious was open beforehand. Terminal opens without issue.) There are little grey locks next to all my folders and documents. Attempting sudo apt-get update resulted in a read only file system error after I entered my password (That is unfortunately flooded off-screen rather quickly by normal update procedure.) There is a second set of errors at the bottom, reading as such (Along with an example of some of the stuff that flooded my screen:
```
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.201 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
W: Not using locking for read only lock file /var/lib/dpkg/lock
```



Google has been entirely unhelpful troubleshooting this problem. I'm running Ubuntu 12.10 on a Dell Studio 1535 as the only operatin system. df -h returns the following:
```
marin@marin-Studio-1535:~$ df -h
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu-root  290G   38G  237G  14% /
udev                     2.0G  4.0K  2.0G   1% /dev
tmpfs                    807M  956K  806M   1% /run
none                     5.0M     0  5.0M   0% /run/lock
none                     2.0G  2.1M  2.0G   1% /run/shm
none                     100M   32K  100M   1% /run/user
/dev/sda1                228M   64M  153M  30% /boot
```

I will not be restarting my computer in order to preserve the current bug. Restarting has proven a temporary solution, and I want a permanent one. Please let me know if I can provide more information.

Edit: I forgot to mention that Windows has had no trouble on this computer, leading me to believe that this is a software issue.

---

### Post by josamen on 2013-03-13
Hey marin!

from what I've been seeing, the read-only error you should be able to fix by running the chmod command

*chmod -R u+rwx /home/ *should give you, the user (and presumably sole operator of the Ubuntu machine) read, write, and execute permissions on the files and directories recursively, meaning on the /home/ directory and all its subdirectories

this is also presuming, of course, that Ubuntu is in any way similar to UNIX

this should get rid of the read-only error

as for the error in executing WoW resulting in the disabling of logging, the program still executed, correct?

---

### Post by ChaoticMarin on 2013-03-14
After forcing it to run in openGL mode, I was able to actually get WoW fully running (Admittedly at like... 9 FPS. Entirely different problem. I suppose it had a hard enough time running on Windows.)

/However/ running it still reliably triggers the bug that causes every file on my system to become read-only. I don't believe this is a permissions error, as if it were I'd probably be able to bypass the restrictions by running things as root. Regardless, I tried the command you suggested with no luck. It ran fine, but... didn't fix the bug. Here's an example of the output from it trying to chage the permissions of one of my files. 

```
chmod: changing permissions of `/home/marin/SeleneApp.txt': Read-only file system
```

Here is me attempting to run Teamviewer as root for example.

```
marin@marin-Studio-1535:~$ sudo teamviewer
[sudo] password for marin: 
sudo: unable to open /var/lib/sudo/marin/0: Read-only file system

Init...
/opt/teamviewer8/tv_bin/script/tvw_main: line 14: /home/marin/.config/teamviewer8/logfiles/startup.log: Read-only file system

Error: Init failed. Please check '/home/marin/.config/teamviewer8/logfiles/startup.log'
```

Please note that I have not taken any step to restrict root's ability to do anything. (Unless encrypting my hard drive during Ubuntu's installation counts...)

---

### Post by Impavidus on 2013-03-14
Sounds like your hard drive is remounted read only. This happens after an I/O error. I don't know whether this can happen when your system is running short on RAM and using an encrypted disk, but it may be.

---

### Post by 3rdalbum on 2013-03-14
When your disk gets remounted as read-only, it's usually because the system has detected filesystem damage, and wants to make sure it doesn't add to the damage.

When the problem occurs, look at the "dmesg" command and the last few lines might give you information about why the disk was remounted read-only.

You will probably need to run fsck - "filesystem check" - while the disk is unmounted. In other words, boot an Ubuntu live CD or live USB, make sure the disk is unmounted, and then run fsck in the terminal.

---

### Post by josamen on 2013-03-14
yeah that's what I was thinking as well since my sister's iBook has the same problem, which is a disk I/O error which in this case prevents the iBook from booting into MacOS at all .  Unfortunately I have no bootable MacOS CD that I could use to run disk utilities from but Marin insists that everything else runs fine.  It very well could be the game doing something to her file system and not the result of any physical damage to the sectors of the hard disk *shrug*

---

### Post by ChaoticMarin on 2013-03-14
A simple reboot wold result in it detecting some errors and fixing them on boot successfully.

Here's  the thing though--I went to try and replicate the bug to try out all of  your guys' new suggestions, but... I couldn't do it! I can no longer  replicate the bug.

The only thing I really did was run a small update and install linux-headers specifically. which was ironically an attempt at improving my FPS and not at solving this specific bug.

As much as it leaves me uneasy to simply assume this fixed itself or that I fixed it on accident, I can't exactly test these new issues without the bug being active.

---

### Post by efflandt on 2013-03-14
It is not that certain files are read only.  In 64-bit Ubuntu 12.04 occasionally my whole file system ended up read-only at times (which can happen automatically if the system is having trouble with a drive). My Linux partition is at the far end of a 1 TB drive (sda), so I figured maybe it was having trouble working with the physically narrower bits and sectors towards the center of the drive.

I also have 64-bit 11.10 on SSD (sdb).  So from that I did **e2fsck -fpc /dev/sda4** and have not had any problems since then.

I did buy a new drive and eSata caddy, but have not had a chance to clone the other drive yet since the problems seemingly disappeared once I got rid of the badblocks.

---

