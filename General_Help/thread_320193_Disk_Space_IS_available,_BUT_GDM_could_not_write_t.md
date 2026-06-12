---
title: "Disk Space IS available, BUT GDM could not write to your authorisation file."
date: 2006-12-16
forum: General Help
---

### Post by Kurt_Alan on 2006-12-16
Sorry to vent but this repeated problem is an UBUNTU KILLER equivalent to Windows BSOD that most respondents don't understand or have the answer for or are silent.  There are at least 100 threads on this site alone with others who have had this problem.  This suggests a problem with the OS. I love Ubuntu but this problem is making me hate it because the problem is re-occuring, does so much damage, and solutions are so elusive.  I can't keep using this distro if I have to re-format my hdd every three months.  

The following confirmed that I do have disk space:

Another thing to try to pin down the offending file(s) is to run du -h. Start with du -h /bin, du -h /home, etc. Then look in further subdirectories. What you're looking for is someting that seems unusually large.

I checked every sub-directory of every directory, which confirms that my disk usage is accurate as reported:

root@kurt-desktop:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              28G   21G  5.8G  78% /
varrun                126M   12K  126M   1% /var/run
varlock               126M  4.0K  126M   1% /var/lock
udev                  126M  164K  125M   1% /dev
devshm                126M     0  126M   0% /dev/shm
lrm                   126M   19M  107M  15% /lib/modules/2.6.15-27-38

I have also done the following which failed:

sudo updatedb && locate core | less
to check for coredumps. If you find any, delete them. They're only useful for debugging.

sudo apt-get update
sudo apt-get upgrade
/etc/init.d/gdm/ restart

rm -rf /home/username/.Trash/*
aptitude clean

   sudo aptitude clean
   sudo /etc/init.d/gdm stop
   sudo /etc/init.d/gdm start

Any solutions?

---

### Post by majoridiot on 2006-12-18
you outline the things you tried, but have not clearly defined your problem.  please describe
in detail what is happening, when, and also attach logs so we can hopefully help you track
this down.

---

### Post by Kurt_Alan on 2006-12-20
> **majoridiot said:**
> you outline the things you tried, but have not clearly defined your problem.  please describe
in detail what is happening, when, and also attach logs so we can hopefully help you track
this down.

My functioning is limited to tty1, maintenance mode, accessed from GRUB plus Escape.  My default is root.  In a normal boot, I am stuck in a log-on loop with error message.

There are logs that I can access? Where and how?

---

### Post by K.Mandla on 2006-12-21
I'm a little confused too. Your error message is "GDM could not write to your authorisation file"?

---

### Post by Kurt_Alan on 2006-12-21
> **K.Mandla said:**
> I'm a little confused too. Your error message is "GDM could not write to your authorisation file"?

Yes, the message Is: "GDM could not write to your authorization file . . . Your Home Directory could not be opened for writing."  Based on my search of Google and ubuntuforums, this is a very common error message.  The usual reason for it is that the disk is full.  After checking df -h and  du -h /usr and all my directories, I have a few GB of extra space, so I must have some other problem.

I'm just learning about logs.  This is my latest log from /var/log/gdm:


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux kurt-desktop 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec 16 18:59:38 2006
(==) Using config file: "/etc/X11/xorg.conf"
FATAL: Module mach64 not found.
[drm] failed to load kernel module "mach64"
(EE) ATI(0): [dri] DRIScreenInit Failed
error opening security policy file /etc/X11/xserver/SecurityPolicy
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory

And this is my latest info from dmesg | less

[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000cc000 - 00000000000d2000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[4294667.296000]  BIOS-e820: 000000000fff0000 - 000000000fff8000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000000fff8000 - 0000000010000000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 255MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000fb690
[4294667.296000] On node 0 totalpages: 65520
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 61424 pages, LIFO batch:15
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 AMI

---

### Post by scrooge_74 on 2006-12-21
I used to get that message when one of my PCs did not recognize the hardrive where the /home directories where.  

Also that happened if I somehow screw up the home folder of the user.  If I took out the user or moved the folder and then put it back where it should but created a user with the same name I had that message.

Maybe you did something like this?

---

### Post by Kurt_Alan on 2006-12-21
> **scrooge_74 said:**
> I used to get that message when one of my PCs did not recognize the hardrive where the /home directories where.  

Also that happened if I somehow screw up the home folder of the user.  If I took out the user or moved the folder and then put it back where it should but created a user with the same name I had that message.

Maybe you did something like this?

I'm not sure.  Before my GDM crash I had to "force quit" a couple of frozen apps -- don't remeber which; force quit failed and I had a system freeze.  I think I just re-booted from tty1.

This is my first time looking at my logs (above). What do they tell you?  I see errors but I don't know what they mean.

I tried this too:

root@kurt-desktop:~# sudo dpkg-reconfigure gdm
 * Reloading GNOME Display Manager configuration...  * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

---

### Post by Kurt_Alan on 2006-12-21
Here is syslog:

Dec 16 18:50:33 kurt-desktop syslogd 1.4.1#17ubuntu7: restart.
Dec 16 18:50:33 kurt-desktop anacron[4831]: Job `cron.daily' terminated
Dec 16 18:54:36 kurt-desktop anacron[4831]: Job `cron.weekly' started
Dec 16 18:54:36 kurt-desktop anacron[5226]: Updated timestamp for job `cron.weekly' to 2006-12-16
Dec 16 18:54:38 kurt-desktop exiting on signal 15
Dec 16 18:54:39 kurt-desktop syslogd 1.4.1#17ubuntu7: restart.
Dec 16 18:54:39 kurt-desktop anacron[4831]: Job `cron.weekly' terminated
Dec 16 18:54:39 kurt-desktop anacron[4831]: Normal exit (2 jobs run)
Dec 16 18:59:34 kurt-desktop gdm[4333]: gdm_auth_user_add: /home/kurt/.Xauthority is not owned by uid 1000.
Dec 16 18:59:34 kurt-desktop gdm[4333]: gdm_auth_user_add: Could not open cookie file /tmp/.gdmh8wtuA
Dec 16 18:59:47 kurt-desktop gdm[4325]: Restarting computer...
Dec 16 18:59:48 kurt-desktop shutdown[4325]: shutting down for system reboot
Dec 16 18:59:48 kurt-desktop init: Switching to runlevel: 6
Dec 16 18:59:50 kurt-desktop kernel: [17180528.172000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Dec 16 18:59:50 kurt-desktop kernel: [17180528.172000] apm: disabled on user request.
Dec 16 18:59:57 kurt-desktop sdpd[4782]: terminating...   
Dec 16 18:59:57 kurt-desktop hcid[4778]: Exit.
Dec 16 18:59:57 kurt-desktop kernel: Kernel logging (proc) stopped.
Dec 16 18:59:57 kurt-desktop kernel: Kernel log daemon terminating.
Dec 16 18:59:58 kurt-desktop exiting on signal 15


THERE are some references here to gdm which might be useful, but I don't understand them.

---

### Post by scrooge_74 on 2006-12-21
probably something is messed up in the hidden files for the user config,but that is beyond me.

Try adding a user from the command line and then try to log into that user.  If you can log in that way then you will know your user config files are the ones giving trouble.

This is the only thing that comes to my mind beyond uninstalling and reinstalling gnome again

---

### Post by mssever on 2006-12-25
> **Kurt_Alan said:**
> Here is syslog:

Dec 16 18:50:33 kurt-desktop syslogd 1.4.1#17ubuntu7: restart.
Dec 16 18:50:33 kurt-desktop anacron[4831]: Job `cron.daily' terminated
Dec 16 18:54:36 kurt-desktop anacron[4831]: Job `cron.weekly' started
Dec 16 18:54:36 kurt-desktop anacron[5226]: Updated timestamp for job `cron.weekly' to 2006-12-16
Dec 16 18:54:38 kurt-desktop exiting on signal 15
Dec 16 18:54:39 kurt-desktop syslogd 1.4.1#17ubuntu7: restart.
Dec 16 18:54:39 kurt-desktop anacron[4831]: Job `cron.weekly' terminated
Dec 16 18:54:39 kurt-desktop anacron[4831]: Normal exit (2 jobs run)
[COLOR="Red"]Dec 16 18:59:34 kurt-desktop gdm[4333]: gdm_auth_user_add: /home/kurt/.Xauthority is not owned by uid 1000.[/COLOR]
Dec 16 18:59:34 kurt-desktop gdm[4333]: gdm_auth_user_add: Could not open cookie file /tmp/.gdmh8wtuA
Dec 16 18:59:47 kurt-desktop gdm[4325]: Restarting computer...
Dec 16 18:59:48 kurt-desktop shutdown[4325]: shutting down for system reboot
Dec 16 18:59:48 kurt-desktop init: Switching to runlevel: 6
Dec 16 18:59:50 kurt-desktop kernel: [17180528.172000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Dec 16 18:59:50 kurt-desktop kernel: [17180528.172000] apm: disabled on user request.
Dec 16 18:59:57 kurt-desktop sdpd[4782]: terminating...   
Dec 16 18:59:57 kurt-desktop hcid[4778]: Exit.
Dec 16 18:59:57 kurt-desktop kernel: Kernel logging (proc) stopped.
Dec 16 18:59:57 kurt-desktop kernel: Kernel log daemon terminating.
Dec 16 18:59:58 kurt-desktop exiting on signal 15


THERE are some references here to gdm which might be useful, but I don't understand them.
Here's one possible problem: The file ~/.Xauthority has very specific permissions requirements. That explains the log message I colored red. If .Xauthority is set wrong, that could explain your error message--though it's difficut to say how the permissions became incorrect without more information. You can fix them thus:
```
sudo chown 1000: ~/.Xauthority
chmod 600 ~/.Xauthority
```

---

### Post by solderhead on 2007-01-13
> **mssever said:**
> Here's one possible problem: The file ~/.Xauthority has very specific permissions requirements. That explains the log message I colored red. If .Xauthority is set wrong, that could explain your error message--though it's difficut to say how the permissions became incorrect without more information. You can fix them thus:
```
sudo chown 1000: ~/.Xauthority
chmod 600 ~/.Xauthority
```

interesting.  i'm having exactly the same problem.  i am stuck in a loop where the user is placed at the GDM logon screen.  when X attempts to start, it dumps the user back at the logon screen.

i've grep'd the syslog and messages file for "gdm" and i've found nothing.  i don't have an ~/.Xauthority file.

this situation came along after a system lockup just like the one described above.  my only option was to reboot the system, and now i can't even get a tty console.

---

### Post by Alf77 on 2008-01-20
I have the same problem, just afetr the system updates of some days ago.

I solved deleting .Xauthority file and then re-installing NVIDIA drivers. 

A reboot was needed too.

Alf

---

### Post by julian67 on 2008-01-20
I used to have a similar problem when I used opensuse, sometime the Xauthority file's permissions would be changed so it was owned by root....no log in possible as user. Deleting the file was the quick fix. The cause of the problem turned out to be  using certain KDE apps as root in the Gnome environment, particularly if they were started from terminal using su. In theory using gksu or kdesu (according to DE) should have prevented the problem but in practise it didn't.  The apps I was using that caused this were (if I recall correctly) Kdar, a back up tool I used to back up certain system files as well as user files hence the need for root privileges, and K3b which has some components which need root acess to the optical drives or block devices.  I think this is the only real problem I had mixing elements of different desktop environments but it's a biggie for a new user! I remember  trying re-installing and also creating a new user and transferring ownership of my files to the new user  because I couldn't figure it out at first...of course it kept happening until I worked out what had actually caused the problem.  Your situation may be different but clearly something is changing ownership on the .Xauthority file, hopefully you can see what it is in the logs or work it out somehow and perhaps change the way you perform certain tasks and also submit a bug report so this can be fixed for others.

---

### Post by chrisccoulson on 2008-01-20
> **Kurt_Alan said:**
> Here is syslog:

Dec 16 18:50:33 kurt-desktop syslogd 1.4.1#17ubuntu7: restart.
Dec 16 18:50:33 kurt-desktop anacron[4831]: Job `cron.daily' terminated
Dec 16 18:54:36 kurt-desktop anacron[4831]: Job `cron.weekly' started
Dec 16 18:54:36 kurt-desktop anacron[5226]: Updated timestamp for job `cron.weekly' to 2006-12-16
Dec 16 18:54:38 kurt-desktop exiting on signal 15
Dec 16 18:54:39 kurt-desktop syslogd 1.4.1#17ubuntu7: restart.
Dec 16 18:54:39 kurt-desktop anacron[4831]: Job `cron.weekly' terminated
Dec 16 18:54:39 kurt-desktop anacron[4831]: Normal exit (2 jobs run)
Dec 16 18:59:34 kurt-desktop gdm[4333]: gdm_auth_user_add: /home/kurt/.Xauthority is not owned by uid 1000.
[COLOR="Red"]Dec 16 18:59:34 kurt-desktop gdm[4333]: gdm_auth_user_add: Could not open cookie file /tmp/.gdmh8wtuA[/COLOR]
Dec 16 18:59:47 kurt-desktop gdm[4325]: Restarting computer...
Dec 16 18:59:48 kurt-desktop shutdown[4325]: shutting down for system reboot
Dec 16 18:59:48 kurt-desktop init: Switching to runlevel: 6
Dec 16 18:59:50 kurt-desktop kernel: [17180528.172000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Dec 16 18:59:50 kurt-desktop kernel: [17180528.172000] apm: disabled on user request.
Dec 16 18:59:57 kurt-desktop sdpd[4782]: terminating...   
Dec 16 18:59:57 kurt-desktop hcid[4778]: Exit.
Dec 16 18:59:57 kurt-desktop kernel: Kernel logging (proc) stopped.
Dec 16 18:59:57 kurt-desktop kernel: Kernel log daemon terminating.
Dec 16 18:59:58 kurt-desktop exiting on signal 15


THERE are some references here to gdm which might be useful, but I don't understand them.

One of your problems definately looks like incorrect ownership / permissions on ~/.Xauthority, as mssever stated above. But the line that I have also highlighted in red may indicate a second problem. Do you have read / write access to /tmp?

---

