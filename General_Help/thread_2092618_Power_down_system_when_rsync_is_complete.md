---
title: "Power down system when rsync is complete?"
date: 2012-12-08
forum: General Help
---

### Post by Roasted on 2012-12-08
(TL : DR @ bottom)

Hey everyone. I'm trying to figure out how I can set things up here. I have a server, which is a standard quad core 4GB RAM box. It has some disk space in it and has operated as my file server for quite some time. The more I look at the performance needs I have of a server (ssh, samba, things like that don't take much CPU usage) I started to wonder if I can utilize my Raspberry Pi for that. As a result, here are my ideas and goals...

The Raspberry Pi will be my primary server, with (eventually) a 3TB drive plugged in via USB. This will be my primary means of storage.

The server will be powered off all of the time except for one hour a day. At 3 AM or so I will have it automatically power on by setting the BIOS to "turn on when power is restored" (or whatever that option is) and have a surge strip timer kick on at 3 AM. So once the system recognizes power, it turns on.

I'd like to set it so the Raspberry Pi will rsync all of the data on the 3TB drive to the other server onto its matching 3TB internal drive. That way I have my data on two disks in two locations. 

The only thing is, I'm questioning if something absolutely massive changes on the Pi that takes a while to transfer that 1 hour may not be enough. On the flip side, I don't want to have to manually change the allotted times for specific events. I'd much rather have an automated setup here. As a result, I'm wondering if there's an easy way to remote shut off the big server once the Pi is done with rsyncing the data.

I currently have a script I run in a similar fashion, at least in regard to how I ran things before I set up the Pi. This is my desktop script. It rsync's my data to my server in the background without me knowing. In an effort to have some sort of a visual, I have it enter a date/time stamp into a text file. That way I can check the text file every week or so and just make sure it's backing up at some point.

```
#!/bin/bash
set -e
rsync -az --delete --exclude=.gvfs /home/jason jason@192.168.1.150:/media/NAS/jason/DesktopUbuntu
ssh jason@192.168.1.150 'date >> /media/NAS/backup_logs/DesktopUbuntu.txt'
exit
```

I understand that set -e enables the script to only complete if each step is successful. That way if the rsync command fails for whatever reason, it won't simply bypass it and enter the date to the text file. Instead, it flat out fails the entire script, so I know if there's no date, something didn't work out.

At any rate, I'm certainly open to ideas. Any info or thoughts you guys might have would be a tremendous help.

TL : DR - When Server A is done rsyncing data to Server B, I want Server A to trigger Server B to power off.

---

### Post by Cheesemill on 2012-12-08
How about just adding the line:
```
shutdown now -h
```
to the end of your script.

---

### Post by Herbon on 2012-12-08
Bump

Time issue, network speed + amount of data changed on source??

---

### Post by ibjsb4 on 2012-12-08
Found a few scripts here.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Power+down+system+when+rsync+is+complete&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Power+down+system+when+rsync+is+complete&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by TheFu on 2012-12-08
I'd do it completely differently.  I'd add this to the end of the script:
```
/sbin/shutdown -h now
```Of course, the user running the script will need authority to run the shutdown program.

If you need the shutdown to happen on a remote machine, just put ssh in front of it.```
ssh remote-user@remote-server /sbin/shutdown -h now
```

Simple.  No need to over think this.

---

### Post by Roasted on 2012-12-08
shutdown -h now requires root. I don't want to mix root and rsync... bad things can happen...

Not to mention, I would need some sort of user input to enter the PW for root to initiate the shutdown to begin with, no?

What I'm looking into now is a way to run shutdown -h now without the need for root, which looks entirely possible...

---

### Post by TheFu on 2012-12-08
> **Roasted said:**
> shutdown -h now requires root. I don't want to mix root and rsync... bad things can happen...

Not to mention, I would need some sort of user input to enter the PW for root to initiate the shutdown to begin with, no?

What I'm looking into now is a way to run shutdown -h now without the need for root, which looks entirely possible...

There are many ways to allow specific users access to specific commands using sudo without a password prompt for just that single command.  Or you could let all users run shutdown by making it setuid-root. The 2nd option is probably a bad idea.

Sudo is extremely flexible - well beyond what most people know. You can setup a single, exact command, to be available for 1 user only without a password. **man sudoers** explains how.  You can setup where the command happens on the client or the remote server - your choice. Just be sure to use key-based ssh logins.

None of this is hard.  I'd do the sudoers setup on the remote box myself. 1 line added to the sudoers file is all that is needed and you already have most of that line in the comments above.

---

### Post by Roasted on 2012-12-08
I know this "should" be easy, but the problem is, everything I tried hasn't worked. I'm just not sure if I'm using the wrong line of text or what. My user is a member of wheel. In sudoers I have added:

%wheel ALL= NOPASSWD: /sbin/shutdown

I've also tried:

%wheel ALL=(ALL) NOPASSWD: /sbin/shutdown

I've logged out, back in, no dice. It still requires a password to execute the command. Is this incorrect?

---

### Post by Cheesemill on 2012-12-08
Can you post your entire sudoers file please:
```
cat /etc/sudoers
```

---

### Post by Rebelli0us on 2012-12-08
Why not schedule a task to wake the machine at 3am, run rsync and then let the power management auto-suspend?

---

### Post by Roasted on 2012-12-08
Nah, I want it to explicitly shut down, not suspend, that way I can have my automated surge strip with a timer kick it on the way I'd like. Good thought though, I'm just not sure it fits what I'm after.

My current sudoers file:

```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults	env_reset
Defaults	secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL:ALL) ALL

# Wheel members can shut down via terminal without the need for root privileges
%wheel	ALL = NOPASSWD: /sbin/shutdown

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d
```

```
:~$ groups jason
jason : jason adm lp sudo dip plugdev lpadmin wheel

```

EDIT - Is it possible that the location of where that entry is in the sudoers file can impact how it works? I just added it to the end of the file, and now it works fine. So instead of having the %wheel line further up, I put it at the very end, and now it works great. Hmm?

---

