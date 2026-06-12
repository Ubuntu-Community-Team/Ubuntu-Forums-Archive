---
title: "Trying to run shell script automatically after flash drive mounts"
date: 2020-09-04
forum: General Help
---

### Post by KneadToKnow on 2020-09-04
I found [this very old thread]("https://askubuntu.com/questions/25071/how-to-run-a-script-when-a-specific-flash-drive-is-mounted") on askubuntu.com, and have tried to follow the systemd service solution given in it as closely as I can, but (a) I realize things may have changed significantly in 9 years and (b) I'm iffy on the details of how it works anyway, so I wanted to reach out for some help to try to get this working.

I have a script which runs very nicely to use rsync to back up my flash drive to my local hard drive, complete with a dialog box to ask me if I want to proceed before it does anything. What I want to accomplish is to make it run automatically when the drive is mounted so that I don't have to start it manually.

I got the device unit with **sudo systemctl list-units -t mount**, with the result **media-knead-8FF9\x2dC76D.mount**.

I created the service named /etc/systemd/system/flash-auto-backup.service following the model of the linked thread:

```

[Unit]
Description=My flashdrive script trigger
Requires=media-knead-8FF9\x2dC76D.mount
After=media-knead-8FF9\x2dC76D.mount

[Service]
ExecStart=/home/knead/flash-backup.sh

[Install]
WantedBy=media-knead-8FF9\x2dC76D.mount
```

From [this page]("https://linuxconfig.org/how-to-run-script-on-startup-on-ubuntu-20-04-focal-fossa-server-desktop"), I learned what permissions might be affecting things, so my service permissions are set to 664 and my script permissions are 744. I have enabled the service and done both **sudo systemctl daemon-reload** and a full reboot, but when I insert the flash drive, it automounts, but nothing else happens.

Even though I have invested a bit of time in my current method, I'm open to other suggestions on how to accomplish this as well. Another responder to the original thread I'm working from claimed Nautilus let you run scripts when given drives mounted, but I can't find the setting it uses, so I'm guessing it's deprecated? Again: automounting the flash drive works great, and the script works great. I'm just having no luck getting the system to automatically run it when the flash drive is automounted.

Can anyone help me out?

---

### Post by TheFu on 2020-09-04
Programs with GUIs shouldn't be run by systemd or cron.
As for why the script fails, that depends on many things which haven't been provided.

---

### Post by dragonfly41 on 2020-09-04
I can only suggest how I might approach this although I have not applied this.

I draw on an automation tool named Actiona which you will find in Ubuntu repo.

Then I would create an Actiona script which looks for the condition .. flash drive mounted.

Then you can run any command(s) you wish including rsync (or even Grsync gui can be navigated).
I find Actiona to be useful for automating workflows. But there might be easier solutions based on cronjob.

[https://serverfault.com/questions/50585/whats-the-best-way-to-check-if-a-volume-is-mounted-in-a-bash-script](https://serverfault.com/questions/50585/whats-the-best-way-to-check-if-a-volume-is-mounted-in-a-bash-script)

---

### Post by dinkidonk on 2020-09-04
I do not think a service is the right tool for the task, what you want is more like an Udev rule which allows you to perform actions when devices are added and/or removed. First of all you need the serial number for the drive from udev, so plug the drive into a USB port and run the command "udevadm info -a /dev/sd?" where "?" is the drive's device letter (get it with lsblk, no partitions like sda1). This command pops out a lot of info, look for a line like "ATTRS{serial}==some_quoted_number" (you may need to use other attrs as well or instead).

Now, create a file named "/etc/udev/rules.d/99-rsync-my-drive.rules" and add the content:

```
ACTION="add", ATTRS{serial}=="the_drives_serial_number", RUN+="some_command_to_run"
```

You can have multiple ATTRS{field}=="what" in order to narrow the match criteria. "some_command_to_run" is the command (full path required) you want to execute whenever the drive is inserted to a USB port, note the following things for the command:

1) You'll most likely need to mount the drive in the command in order to access the file system on it.
2) If you want to invoke a shell script, you must run it with "/usr/bin/sh /path/to/script.sh" for it to work.
3) The command is run at kernel/root level, user rights must be explicitly enforced or any files created/copied will belong to "root".

Oh, and whenever a rule is added/modified, you need to reload udev rules with "sudo udevadm control --reload-rules && udevadm trigger". I would encourage you to research the topic and play with your udev rules before you let loose something important.

Good luck! :-)

---

### Post by amx23112 on 2020-09-05
I agree on the Udev advice. Udev checks for changes in power events. Since USB devices draw power, it allows for more accurate detection  exactly when the script should be run.

---

### Post by KneadToKnow on 2020-09-05
Thanks for the helpful responses! I will try to get the Udev solution configured and report back.

---

### Post by KneadToKnow on 2020-09-11
Running into some roadblocks.

I found a step-by-step guide ([https://www.tecmint.com/auto-backup-files-to-usb-media-in-linux/](https://www.tecmint.com/auto-backup-files-to-usb-media-in-linux/)), which I believe I followed correctly. I tweaked one thing based on advice in another article ([https://brokkr.net/2017/06/12/why-my-udev-backup-script-kept-failing-and-how-i-fixed-it/](https://brokkr.net/2017/06/12/why-my-udev-backup-script-kept-failing-and-how-i-fixed-it/)), but the script is not starting.

Here is the UDEV rule I made:

```
SUBSYSTEM=="block", ACTION=="add", ATTRS{serial}=="4C530000080913104140", ATTRS{partition}=="1"  SYMLINK+="external%n", RUN+="/home/knead/udevtest.sh"
```

The script, for testing, just touches a file in my home folder:
```
#! /bin/bash
muuid="$(uuidgen)"
mdate="$(date +%s)"
touch "/home/knead/udev-${mdate}-${muuid}"
exit 0
```

This script has been tested and works as intended. I have not tried the systemd service solution from the second linked article because I still hope to be able to make use of the zenity pop up messages from my actual backup script.

Happy to post any additional information that might be useful.

---

### Post by dinkidonk on 2020-09-11
As mentioned above, the "RUN" command is executed outside the shell, so a shell-script will only work if you add it as argument to the shell itself:

```
RUN+="/bin/sh /home/knead/udevtest.sh"
```

Inside your script, you also need to either specify the full path to any used program (eg. /bin/uuidgen) OR you need to set the PATH variable as the first thing:

```
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
```

It is exactly the same thing you would need to do when running a shell script as a cron job since the environment (as retreived with the "env" command) is undefined or very limited.

---

### Post by KneadToKnow on 2020-09-11
Good catches, sorry I missed that. Here are the modifications I've made:

```
SUBSYSTEM=="block", ACTION=="add", ATTRS{serial}=="4C530000080913104140", ATTRS{partition}=="1"  SYMLINK+="external%n", RUN+="/bin/bash /home/knead/udevtest.sh"
```

and

```
#! /bin/bash
muuid="$(/usr/bin/uuidgen)"
mdate="$(/bin/date +%s)"
/bin/touch "/home/knead/udev-${mdate}-${muuid}"
exit 0
```

After making the changes, I ran **sudo udevadm control --reload**. Still no results from the test script via the rule, script works as expected when executed from the command line.

---

### Post by Holger_Gehrke on 2020-09-11
"RUN" is really only meant for quick tasks. The whole udev event processing is suspended while it runs. That's why the systemd solution exists.

If you absolutely can not get the systemd unit to work, one approach is to have "RUN" 'touch' a file. A script autostarted with your session would watch that file for the change in timestamp using inotifywait and execute your actual task.

Holger

---

### Post by dinkidonk on 2020-09-11
You are missing a comma in your udev rule, right after ATTRS{partition}=="1"

---

