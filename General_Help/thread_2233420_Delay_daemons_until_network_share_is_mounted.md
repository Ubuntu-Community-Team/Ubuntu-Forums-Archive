---
title: "Delay daemons until network share is mounted?"
date: 2014-07-08
forum: General Help
---

### Post by Tim_Graffam on 2014-07-08
I use mounted Windows shares for storage of Transmission (daemon) and SABnzbd and Im trying to figure out the best way to delay these services from starting until the file shares are mounted. I came up with the following code that Im thinking I can insert someplace to wait until the share is mounted to continue, but I havent figured out the best way to implement it.

```
DIR=/WindowsShare


while [ ! -d "$DIR" ]; do
        sleep 30
done

```
My original attempt was to disable both services from automatically starting, create a script that includes the above code followed by the start command for each of these services and finally, calling this script in the rc.local script. Unfortunately I cant get this to work. The first problem is I cant figure out how to keep the transmission daemon from starting. The other issue is rc.local doesnt seem to launch the script during startup.

Any thoughts on how to best handle this?

Thanks!

---

### Post by ian-weisser on 2014-07-08
The best way is to edit the Upstart job that starts Transmission.
Add those services as a requirement for Transmission to start.

---

### Post by Tim_Graffam on 2014-07-08
Honestly, Im super new at this stuff. Ive checked out the upstart cookbook and I thought by changing the start on to "started mountall" it would wait to start until everything in fstab is mounted, but thats not happening.

Any suggestions on what I need to update to ensure transmission doesnt start until my cifs shares are mounted?

Thanks!

---

### Post by papibe on 2014-07-08
Hi Tim_Graffam.

I don't have all the answers, but you can disable transmission-daemon from starting at startup by editing its default file.

To edit the file, on a GUI desktop:
```
gksudo gedit /etc/default/transmission-daemon
```
or in the command line:
```
sudo nano /etc/default/transmission-daemon
```
Look for a line that looks like this:
```
ENABLE_DAEMON=1
```
then edit it so it looks like this:
```
ENABLE_DAEMON=0
```
Save the file. Next time you reboot your system, transmission-daemon** won't** start by default.

Hope it helps. Let us know how it goes.
Regards.

---

