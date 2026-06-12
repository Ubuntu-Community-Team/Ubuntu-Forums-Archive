---
title: "Audible feedback shutting down a headless server"
date: 2008-01-27
forum: General Help
---

### Post by Oceanwatcher on 2008-01-27
I have a headless Ubuntu Server 7.10 running and would like to be able to have some control of the shut down of it.

My problem is that I have no idea about programming. I am pretty good at following instructions when it comes to setting up the server, but planning and programming something myself is not possible :-)

This is what I am looking for:

I have heard that a short press on the power button whould start a shut-down sequence. This is exactly what I need, but I would like some kind of audio confirmation that the shutdown process has started. Maybe two short beeps?

Also, if it is possible to set somewhere how long the power button should be pressed for the shutdown sequence to be started, I would like to set it to half a second.

How do I achieve this?

---

### Post by .nedberg on 2008-01-27
You kan make your machine beep by putting

```

echo -en "\007"

```

in a shutdown script ( /etc/rc1.d/K00scriptname I believe)

---

### Post by doug1212 on 2008-01-27
Hi,
To configure the power button to do a polite shutdown on my headless box I followed the example in the man page "acpid".
```
man acpid
```
Doug.

---

### Post by Oceanwatcher on 2008-01-27
Thank you. I will check this. Do you think it is possible to make the server beep twice as a confirmation of pressing the button long enough?

---

### Post by .nedberg on 2008-01-28
Just a small question:

Why don't you shut it down from a ssh session? That is what I do with my headless servers.

```

ssh machinename
<enter ssh password>
sudo poweroff
<enter root password>

```

And the machine powers off. You can also restart with 'sudo reboot'.

---

### Post by Oceanwatcher on 2008-01-28
Exactly what I need to avoid. I have absolutely no problem shutting it down remotely. But sometimes there are no computers running and to boot a computer just to shut down the server is such a waste of time and energy :-)

Another very good point is that this need to be wife-friendly. Would you like to try to explain to my wife that she needs to open a terminal window and issue some commands to turn off the server? She would rather just pull the power plug.....

We have some nasty lightning storms here and when something lke that come in, we run around to shut everything down. So it is better to set things up so the server shuts down in a controlled matter by pressing the power button. And it is nice to get a couple of beeps to signal that it is starting the shut-down sequence.

So far, I have been trying to understand the man pages. It would have been more easy with a few examples, so I guess I should try a different search on Google.

---

### Post by Oceanwatcher on 2008-01-28
Could not understand why I could not find any of the folders that was mentioned in the man pages. So I did a search and found that ACPID was not installed. Installing it now to see if I can get this to work.

---

### Post by doug1212 on 2008-01-28
Hi,
Create a file "power":
```
sudo nano /etc/acpi/events/power
```
paste in these lines an save. 
```
# power down nice on button.
event=button/power.*
action=/usr/local/sbin/power.sh "%e"

```
After reboot the box should power down on the button.
Doug.

---

### Post by PinkFloyd102489 on 2008-01-28
My server automatically issues a beep when I give the shutdown command

```

sudo shutdown -hP now

```

---

### Post by Oceanwatcher on 2008-01-28
> **doug1212 said:**
> 
```
# power down nice on button.
event=button/power.*
action=/usr/local/sbin/power.sh "%e"

```


Thanks for the example Doug. I have made the file, but this file then points to another file, power.sh . What should be in this file?

---

### Post by doug1212 on 2008-01-29
:oops: my bad,
I had another look and this is what I have on my box:
```
 /etc/acpi/events/powerbtn
```
looks like this:
```

event=button[ /]power
action=/etc/acpi/powerbtn.sh

```
this should run powerbtn.sh script on button press.

---

