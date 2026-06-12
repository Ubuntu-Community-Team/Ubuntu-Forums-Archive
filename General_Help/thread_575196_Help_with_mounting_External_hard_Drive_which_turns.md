---
title: "Help with mounting External hard Drive which turns on with delay"
date: 2007-10-13
forum: General Help
---

### Post by davidme on 2007-10-13
I have this problem:

2 external hard drives, one of them mounts fine the other has this annoying issue that when I turn on my laptop, external hard drive turns on with delay.

What is the correct way to write it in fstab so that it mounts ?

At the moment I have this in fstab:

# Entry for Media Drive
UUID=73a058ab-290d-420a-acb5-9be6cb232d9a /media/Media ext3 defaults

However with this setup I always have to manually run this command after I start my laptop: sudo mount -a and then it mounts.

Please help.

---

### Post by kidders on 2007-10-15
Hi there,

This is a nasty one ... there's no way to notate "wait a while" in /etc/fstab. :-(

In your shoes, the way I would handle this would be ...[LIST]
[*]Prevent the current boot-time mount attempt from failing, by adding "noauto" to the mount options for the device with the delay.
[*]Create a new udev ruleset (eg /etc/udev/rules.d/99-my-rules.rules) to have the specific device you're having a problem with symlinked to somewhere like /dev/delayed.
[*]Set up a new service (along the lines of your existing printer or file sharing services) capable of handling problematic devices.
[/LIST]

Another poster may well have a better idea ... I've never seen this problem before, personally ... but in the meantime, you might like to give my suggestion a try.

**Udev**
Udev handles device recognition. You could use it to provide a means for a new, more tolerant, filesystem mounting service to recognise the devices it should worry about. Use "udevinfo" to identify something about your problem device that uniquely identifies it on your system ... perhaps its device UUID, the USB port you intend to plug it into, its manufacturer name, etc. You could use that to construct a new udev rule with a SYMLINK directive in it, so what used to be /dev/sdb (for the sake of example) would also appear as /dev/delayed/device1, and /dev/sdb1 would also be called /dev/delayed/device1-1. It's important to do this by creating your own udev ruleset, not by modifying one of Ubuntu's.

To test a new rule, run "sudo udevcontrol reload_rules", and unplug & reconnect your device.

**A smarter mount script**
You could create a script called something like /usr/local/sbin/smart_mount that would...[LIST=1]
[*]Check for devices called /dev/delayed/deviceX-Y.
[*]Identify their "real" names & look for a mount point in /etc/fstab.
[*]Check that the device hasn't somehow already been successfully mounted.
[*]Wait a few seconds.
[*]Try to perform the mount.
[*]If unsuccessful, the script could go back to step 4 a couple of times, before giving up.
[/LIST]

The finished product would then be a matter of creating a system "service" that called the script at boot time. Your system's pre-existing shutdown procedures would handle clean unmounting for you, when you turn your computer off.

Just in case you've never tried shell scripting before, here's an example of something that might do the job for you. It's off the top of my head, so I can't claim it'd be perfect...```
#!/bin/bash
for f in `find /dev/delayed -type l -name "*[0-9]-[0-9]"`; do
        REAL_NAME="/dev/`stat -c "%N" $f | cut -d'\`' -f3 | sed "s/'//" | xargs basename`"
        MOUNT_POINT="`grep $REAL_NAME /etc/fstab | sed 's/ /\t/g' | cut -f2`"
        if [ -n "$MOUNT_POINT" ]; then
                if [ -z "`mount | grep $REAL_NAME`" ]; then
                        echo Attempting to mount $REAL_NAME
                        sleep 5
                        mount $REAL_NAME $MOUNT_POINT
                fi
        fi
done
```

Essentially, it does the following, line by line...[LIST=1]
[*]Searches /dev/delayed for symlinks of the format somethingX-Y.
[*]Calculates the place in /dev the symlink points to.
[*]Searches /etc/fstab for the place the filesystem was supposed to be mounted.
[*]Proceeds only if the /etc/fstab search turned something up. (first "if ...")
[*]Proceeds only if the filesystem in question hasn't already been mounted (second "if ...")
[*]Says something like "Attempting to mount /dev/sda1".
[*]Waits for 5 seconds.
[*]Tries to mount the filesystem.
[/LIST]

Once you were set up, any filesystem that gave you trouble could be mounted using your script, simply by adding a new udev rule that symlinked it to /dev/delayed.

What do you think?

---

### Post by davidme on 2007-10-17
Wow, that is a huge way to achieve something simple like that. 

Maybe I can just play around with bios or the enclosure itself. But thank you.

---

