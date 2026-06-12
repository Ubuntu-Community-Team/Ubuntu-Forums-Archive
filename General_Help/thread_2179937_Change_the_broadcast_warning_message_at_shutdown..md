---
title: "Change the broadcast warning message at shutdown."
date: 2013-10-10
forum: General Help
---

### Post by jak-grueneberg-0 on 2013-10-10
Hello!  Thanks for taking the time to look at my post.  Here is the background:

   Issue: 
I would like to edit the message that prints to the terminal when it recieves a shutdown command, and also have an option to print that message to the screen. What I mean, is when I execute a command like: 

```
sudo shutdown 10 -P 
``` 

I get a message:

> The system is going down for power off in 10 minutes!

If I put in:

```
sudo shutdown 10 -P "Bring the System Down!"
```

I get a message:

> The system is going down for power off in 10 minutes!  
                Bring the System Down!

I would like to remove the first message in front of, at the least, shutdown, with and without -P, and replace it with a custom message.  Having a way to print it to the screen of all logged in users would be cool too.  

Thanks in advance!

   Hardware: 
VGA ASUS HD 7770-2GD5  2Gb Ram
8Gbx2-GSkill F3-1866c10D-16Gb Ram
128 GB Samsung SSD
HDD 3Tb Toshiba DT01ACA300
CPU-AMD-8Core-FX-8320-3.5G-8M-R
Gigabyte GA-990FXA-UD3 AM3+ AMD 990FX SATA 6Gb/s USB 3.0 ATX AMD Motherboard
 Asus PCE-N10 Wireless-N Network Adapter (150 Mbs Transmit/Recieve) PCI-E interface-WPS
ASUS Vs228-H-P 22-Inch Full-HD 2ms LED-Lit LCD Monitor



   OS:
Ubuntu 12.04 LTS (On the SSD)

---

### Post by tgalati4 on 2013-10-10
A quick google search brings up this 2008 post:  [http://ubuntuforums.org/showthread.php?t=721850](http://ubuntuforums.org/showthread.php?t=721850)

I'm going to guess that *shutdown* is still part of the *upstart* command suite.

The offending phrase is included in the binary:

tgalati4@tpad-Gloria7 ~ $ grep "The system is going down" /sbin/shutdown
Binary file /sbin/shutdown matches

But:


tgalati4@tpad-Gloria7 ~ $ grep "The system is going down for power off" /sbin/shutdown
tgalati4@tpad-Gloria7 ~ $ 

So the messages change (besides just the time countdown) depending on what is going to happen--shutdown, reboot, no-login, cancel, etc.

You would have to rewrite the source code and recompile it to modify to get rid of the message.  And hope that you don't break it.

So there is no easy way to disable that message.

As an alternative, you can use dbus commands to shut the system down and the *wall* command to send out messages.  Basically, write a script to shut the system down the way you want to.

```
man telinit
man wall
```

Finally, some other shutdown resources:

[http://linux.101hacks.com/unix/shutdown/](http://linux.101hacks.com/unix/shutdown/)

[http://unix.stackexchange.com/questions/48973/execute-a-command-before-shutdown](http://unix.stackexchange.com/questions/48973/execute-a-command-before-shutdown)

And to make this thread interesting, who can name 10 different ways to shut down a linux system?

I will start:

Echo "1" to the power button.  This will vary depending on the machine, but most laptops have a power button event that is intercepted by the ACPI system.  Locate that power button and send a 1 to it--instant shutdown.  It will also depend on how the power button is set up in user preferences.

On an IBM thinkpad:

tgalati4@tpad-Gloria7 /etc/acpi/events $ cat powerbtn
# /etc/acpi/events/powerbtn
# This is called when the user presses the power button and calls
# /etc/acpi/powerbtn.sh for further processing.

# Optionally you can specify the placeholder %e. It will pass
# through the whole kernel event message to the program you've
# specified.

# We need to react on "button power.*" and "button/power.*" because
# of kernel changes.

event=button[ /]power
action=/etc/acpi/powerbtn.sh

tgalati4@tpad-Gloria7 /etc/acpi $ cat powerbtn.sh 
#!/bin/sh
# /etc/acpi/powerbtn.sh
# Initiates a shutdown when the power putton has been
# pressed.

# Skip if we just in the middle of resuming.
test -f /var/lock/acpisleep && exit 0

# If gnome-power-manager or kded4 are running, let
# them handle policy This is effectively the same as 'acpi-support's
# '/usr/share/acpi-support/policy-funcs' file.

if pidof gnome-power-manager kded4 > /dev/null; then
    exit
fi

# If all else failed, just initiate a plain shutdown.
/sbin/shutdown -h now "Power button pressed"

This doesn't fix the OP's particular problem as it just calls *shutdown* at the very last step.

---

### Post by jak-grueneberg-0 on 2013-10-10
Wow!  That was a thorough and helpful answer!  Thanks!  I may leave it alone and just print my message separately when needed.  Thank you.

---

### Post by tgalati4 on 2013-10-10
You are welcome, and welcome to the forums.

---

