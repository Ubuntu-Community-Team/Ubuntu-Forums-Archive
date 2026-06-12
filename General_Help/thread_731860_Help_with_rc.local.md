---
title: "Help with rc.local"
date: 2008-03-22
forum: General Help
---

### Post by keninem on 2008-03-22
Hi, 
I am running a headless machine and have VNC server set up so that I can access it(also have SSH)

I added my line "vncserver :2" to my /etc/rc.local file, above the line "exit 0", but when I reboot, the vnc server doesn't start up..

If i run "sudo /etc/rc.local", however, it does start up..

Is there something I need to do to tell rc.local to run on startup, or am I missing something else?

Thanks!

---

### Post by banewman on 2008-03-22
I would have gone to 
system - preferences - session - startup 
and added an entry
server  - with the command - vncserver :2
to get that running after startup.

---

### Post by keninem on 2008-03-22
> **banewman said:**
> I would have gone to 
system - preferences - session - startup 
and added an entry
server  - with the command - vncserver :2
to get that running after startup.

Unfortunately that doesn't do anything either..

---

### Post by ryanhaigh on 2008-03-22
I believe that by default rc.local doesn't have executable permissions and therefore nothing in it will be run. To make the file executable:
```
sudo chmod +x /etc/rc.local
```
The only problem that I see with this is that the vnc server will be running with root priveliges, to correct this you could try using something like:
```
su - yourusername -c vncserver :2
```
instead of just vncserver :2

---

### Post by pointone on 2008-03-22
Depending on your system, the network might not be fully configured by the time rc.local runs. You could try delaying the command with "sleep 15" before running "vncserver".

Also, check /etc/rc2.d and make sure a symlink exists to rc.local.

---

### Post by keninem on 2008-03-22
Ok I tried the following:

I know rc.local is written right, and is executable, because if i run 

```
sudo /etc/rc.local
```

It starts the vnc server up and running..

I tried adding the sleep 15 to the rc.local file, to no avail..it just takes longer when i try to run it manually!

I'll change it so it doesn't vnc as root after I get it to work at all, no need to add extra confusion into it now, but thanks for the suggestion, I didn't realize i could specify the username to run as!

Lastly, I made sure that rc.local is symlinked in /etc/rc2.d/, and it is..

My only thought is that it isn't processing rc.local on startup..is this possible?

---

### Post by ryanhaigh on 2008-03-22
If you restart your computer and when the grub menu comes up edit the kernel line and delete splash from the end then boot you should see a bunch of text, the last of which will be about executing rc.local and hopefully any related error information.

When you run rc.local using sudo can you check who the process is runnning as?

---

### Post by keninem on 2008-03-22
I probably won't be able to check the rc.local on boot until I can grab a monitor from somewhere..but I checked the vnc process after I ran the sudo /etc/rc.local command, and it's owned by root.  The full line in ps is:

```
root      6344  0.1  0.4   8884  4968 pts/0    S    22:48   0:00 Xvnc :2 -desktop linux-fs:2 (root) -auth /home/ken/.Xauthority -geometry 1024x768 -depth 16 -rfbwait 30000 -rfbauth /home/ken/.vnc/passwd -rfbport 5902 -pn -extension XFIXES
```

---

### Post by dcstar on 2008-03-23
> **keninem said:**
> Hi, 
I am running a headless machine and have VNC server set up so that I can access it(also have SSH)

I added my line "vncserver :2" to my /etc/rc.local file, above the line "exit 0", but when I reboot, the vnc server doesn't start up..

If i run "sudo /etc/rc.local", however, it does start up..

Is there something I need to do to tell rc.local to run on startup, or am I missing something else?

Thanks!

Put the full path to all binaries in things that are **not** run in user shells.

What runs in a user shell is not the same as what the system runs on start up.

---

### Post by keninem on 2008-03-23
dc, I changed my line in /etc/rc.local to read:

```
/usr/bin/vncserver :2
```

and rebooted, it still didn't come up unfortunately..

---

### Post by pointone on 2008-03-23
Change the command to read "/usr/bin/vncserver :2 &>/home/log.rc.local" and check /home/log.rc.local after the next boot for clues.

---

### Post by keninem on 2008-03-23
> **pointone said:**
> Change the command to read "/usr/bin/vncserver :2 &>/home/log.rc.local" and check /home/log.rc.local after the next boot for clues.

I tried that and rebooting, it leaves a 0 byte file in my home directory..

---

### Post by pointone on 2008-03-24
Whoops! Sorry, that should've been >&, not &>.

```
/usr/bin/vncserver :2 >&/home/log.rc.local
```

---

### Post by dcstar on 2008-03-24
> **pointone said:**
> Whoops! Sorry, that should've been >&, not <&.

```
/usr/bin/vncserver :2 >&/home/log.rc.local
```

Or
```
/usr/bin/vncserver :2 >/home/log.rc.local &
```

Anyway, vncserver is a user X session based process and requires various files in $HOME, running it in rc.local means it is run by root, does the root home directory have these files?

Look here for more info:

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by pointone on 2008-03-24
> **dcstar said:**
> Or
```
/usr/bin/vncserver :2 >/home/log.rc.local &
```

Not exactly...

">&/path/to/file" redirects both stdout and stderr to the file.

">/path/to/file &" redirects stdout only and backgrounds the process. Quite a different effect, if one wants to log errors.

">&/dev/null" is equivalent to ">/dev/null 2>&1", which most people are more familiar with.

---

