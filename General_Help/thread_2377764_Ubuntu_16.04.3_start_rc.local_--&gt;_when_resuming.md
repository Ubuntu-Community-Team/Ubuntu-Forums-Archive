---
title: "Ubuntu 16.04.3 start rc.local --&gt; when resuming from suspend."
date: 2017-11-16
forum: General Help
---

### Post by Janiporo on 2017-11-16
I need /etc/rc.local to run (as root) when resuming (waking up) from suspend. At this time it opens gnome-calculator, for letting me know when it has been executed. 

I have tried every guide I have found, but I can not get it to run :roll:

With 14.04 I can get it to work, but I updated my system, and now nothing seems to make it work. Something has changed. (Also destroyed my notes on how to get it to run on 14.04)

I would appreciate if someone could test their solution on Ubuntu 16.04.3, or newer, and then tell me what they did.

Links are also welcome, but most likely I will just tell that I have tried that...

---

### Post by ajgreeny on 2017-11-16
Let's start from looking at the 14.04 OS version; how did you get rc.local to run when coming out of suspend in that version?

I suspect that whatever you did in 14.04 will need to be changed to use systemd instead of init-upstart, but when we know what you did before we may have more ideas.

---

### Post by Janiporo on 2017-11-16
As I said, I destroyed the notes.

While seeking similar solution I had, it seems I got this to work. Here is the solution:

I found this one --> [https://askubuntu.com/questions/886620/how-can-i-execute-command-on-startup-rc-local-alternative-on-ubuntu-16-10](https://askubuntu.com/questions/886620/how-can-i-execute-command-on-startup-rc-local-alternative-on-ubuntu-16-10)
And this one --> [https://askubuntu.com/questions/661715/make-a-script-start-after-suspend-in-ubuntu-15-04-systemd](https://askubuntu.com/questions/661715/make-a-script-start-after-suspend-in-ubuntu-15-04-systemd)

And found enough info to morph them to the following solution:

So, I did the following:

```
sudo gedit /etc/systemd/system/rc-local.service
```
Contains of that file:
```
[Unit]
Description=Run rc.local
After=suspend.target
#After=hibernate.target
#After=hybrid-sleep.target

[Service]
ExecStart=/etc/rc.local start

[Install]
WantedBy=suspend.target
#WantedBy=hibernate.target
#WantedBy=hybrid-sleep.target
```

The gnome-calculator gave me display error something, so I ditched that one, and used the commands I was going to use anyway. At the end contains of /etc/rc.local was:
```
sudo gedit /etc/rc.local
```
```
#!/bin/sh
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

sleep 2

rmmod mt7601u

sleep 1

modprobe mt7601u

exit 0
```

To make it executable:
```
sudo chmod +x /etc/rc.local
```

Then:
```
sudo systemctl enable rc-local
```
Then started the service:
```
sudo systemctl start rc-local.service
```
And tested it:
```
sudo systemctl status rc-local.service
```

It gives me no errors at the end, AND everything works, even after multiple reboots and suspend-resumes.

---

