---
title: "Script Not being run at bootup"
date: 2022-11-08
forum: General Help
---

### Post by toml_12953 on 2022-11-08
I tried adding a script I want to run to the list of startup commands. I also tried putting the commands in /etc/rc.local. Neither method works. The commands aren't run.
I can run the script from the command line and it works fine.

Here's the script:
```
#!/bin/sh
sudo /usr/bin/stty -F /dev/ttyUSB0 iexten icanon lcase cols 72
sudo /usr/bin/stty -F /dev/ttyUSB1 iexten icanon lcase cols 72
sudo /usr/bin/stty -F /dev/ttyUSB2 iexten icanon lcase cols 72
sudo /usr/bin/stty -F /dev/ttyUSB3 iexten icanon lcase cols 72
sudo /usr/bin/stty -F /dev/ttyUSB4 iexten icanon lcase cols 72
sudo /usr/bin/stty -F /dev/ttyUSB5 iexten icanon lcase cols 72
sudo /usr/bin/stty -F /dev/ttyUSB6 iexten icanon lcase cols 72
sudo /usr/bin/stty -F /dev/ttyUSB7 iexten icanon lcase cols 72
```

I also tried removing sudo. The script still doesn't seem to work.

---

### Post by MAFoElffen on 2022-11-08
Try this:
```

#!/bin/sh
sudo /usr/bin/stty -F /dev/tty0 iexten icanon lcase cols 72
sudo /usr/bin/stty -F /dev/tty1 iexten icanon lcase cols 72
sudo /usr/bin/stty -F /dev/tty2 iexten icanon lcase cols 72
sudo /usr/bin/stty -F /dev/tty3 iexten icanon lcase cols 72
sudo /usr/bin/stty -F /dev/tty4 iexten icanon lcase cols 72
sudo /usr/bin/stty -F /dev/tty5 iexten icanon lcase cols 72
sudo /usr/bin/stty -F /dev/tty6 iexten icanon lcase cols 72
sudo /usr/bin/stty -F /dev/tty7 iexten icanon lcase cols 72
```

The device settings you had do not exist... /dev/ttyX are 0 through 31. There are no devices with *"usb"* in it's name...

---

### Post by MAFoElffen on 2022-11-08
Sorry. An edit to the above, remove "sudo..." It's called from /etc/rc.local so it executed by root already...

---

### Post by toml_12953 on 2022-11-09
Those devices DO exist in my copy of Ubuntu. When I plug in an eight port USB to serial port converter, ttyUSB0 - ttyUSB7 show up in /dev. As I said, the script works fine from the command line.

---

### Post by toml_12953 on 2022-11-09
Even without sudo, /etc/rc.local never gets executed. Is it possible the USB devices aren't initialized at that point? If that's the case, then where can I put my script so
that it executes during powerup but before any login?

---

### Post by btindie on 2022-11-09
As mentioned previously, it may be because when that script is executed the USB device might not be available.

On my version of Ubuntu, that script is started by the systemd service called [FONT=system]rc-local.service[/FONT], try running the below to check that it has been run.
```
sudo systemctl status rc-local.service
```
Next thing, edit /etc/rc.local to include
```
ls -l /dev/ttyUSB* >/tmp/rc-local.log 2>&1
```
make sure it comes before the line that reads "[FONT=system]exit 0[/FONT]" if you've still got that in there. That'll list all ttyUSB devices when the script runs to a text file.
Reboot and then look at the file [FONT=system]/tmp/rc-local.log[/FONT], it'll either list a load of devices or it'll contain the message:
```
ls: cannot access '/dev/ttyUSB*': No such file or directory
```
if it contains that message, then it's running too soon in the boot process.

Additionally, the script is run as *root*, so there's no need to prefix the commands with [FONT=system]sudo[/FONT].

Without the USB device it's hard to say what might be going on.

Another possibility may be due to another systemd service that runs after [FONT=system]rc-local.service[/FONT] which is then overriding the settings. In /lib/systemd/system there's 2 possible units that might be overriding the settings for your USB tty  -   serial-getty@.service & getty@.service that results in units such as [FONT=system]getty@tty1.service[/FONT]
Try running something like the below to see if there's a getty running on ttyUSB0
```
systemctl status getty@ttyUSB0.service
```

You may be better off creating your own systemd unit, you can then specify where in the boot up process it runs. And create your own script that the unit runs[B].
[/B]
You could also simplify the script to just
```
#!/bin/sh

for n in $(seq 0 7); do
  [ -c /dev/ttyUSB$n ] && /usr/bin/stty -F /dev/ttyUSB$n iexten icanon lcase cols 72
done

```
which checks that the device exists before running the stty command.

---

### Post by MAFoElffen on 2022-11-09
> **btindie said:**
> As mentioned previously, it may be because when that script is executed the USB device might not be available.

You could also simplify the script to just
```
#!/bin/sh

for n in $(seq 0 7); do
  [ -c /dev/ttyUSB$n ] && /usr/bin/stty -F /dev/ttyUSB$n iexten icanon lcase cols 72
done

```
which checks that the device exists before running the stty command.
In this case, in the if (which checks if it exists), in an "else", it could echo that it doesn't exist yet... Which would help to debug problems you are having now (not knowing the timing of).

---

### Post by toml_12953 on 2022-11-09
The log file is never created leading me to believe that rc.local is never run.
Here's an indication that there's an agetty on all the serial ports:

```
tom@Ubuntu-22:~$ ps -aux | grep agetty
root        1661  0.0  0.0  16900  1080 ttyUSB0  Ss+  23:45   0:00 /sbin/agetty -L -U ttyUSB0 9600 1200 110 tty
root        1662  0.0  0.0  16900  1084 ttyUSB1  Ss+  23:45   0:00 /sbin/agetty -L -U ttyUSB1 9600 1200 110 tty
root        1663  0.0  0.0  16900  1052 ttyUSB2  Ss+  23:45   0:00 /sbin/agetty -L -U ttyUSB2 9600 1200 110 tty
root        1664  0.0  0.0  16900  1076 ttyUSB3  Ss+  23:45   0:00 /sbin/agetty -L -U ttyUSB3 9600 1200 110 tty
root        1665  0.0  0.0  16900  1084 ttyUSB4  Ss+  23:45   0:00 /sbin/agetty -L -U ttyUSB4 9600 1200 110 tty
root        1666  0.0  0.0  16900  1084 ttyUSB5  Ss+  23:45   0:00 /sbin/agetty -L -U ttyUSB5 9600 1200 110 tty
root        1667  0.0  0.0  16900  1080 ttyUSB6  Ss+  23:45   0:00 /sbin/agetty -L -U ttyUSB6 9600 1200 110 tty
root        1668  0.0  0.0  16900  1084 ttyUSB7  Ss+  23:45   0:00 /sbin/agetty -L -U ttyUSB7 9600 1200 110 tty
tom         2622  0.0  0.0  17712  2288 pts/0    S+   23:50   0:00 grep --color=auto agetty
```

---

### Post by toml_12953 on 2022-11-10
> **btindie said:**
> On my version of Ubuntu, that script is started by the systemd service called [FONT=system]rc-local.service[/FONT], try running the below to check that it has been run.
```
sudo systemctl status rc-local.service
```


Here's the output from that:
```
tom@Ubuntu-22:~$ sudo systemctl status rc-local.service
&#9679; rc-local.service - /etc/rc.local Compatibility
     Loaded: loaded (/lib/systemd/system/rc-local.service; enabled-runtime; preset: enabled)
    Drop-In: /usr/lib/systemd/system/rc-local.service.d
             &#9492;&#9472;debian.conf
     Active: active (exited) since Thu 2022-11-10 00:19:46 EST; 1min 49s ago
       Docs: man:systemd-rc-local-generator(8)
    Process: 887 ExecStart=/etc/rc.local start (code=exited, status=0/SUCCESS)
        CPU: 23ms


Nov 10 00:19:40 Ubuntu-22 systemd[1]: Starting /etc/rc.local Compatibility...
Nov 10 00:19:46 Ubuntu-22 systemd[1]: Started /etc/rc.local Compatibility.

```

---

### Post by toml_12953 on 2022-11-10
> **btindie said:**
> A
Next thing, edit /etc/rc.local to include
```
ls -l /dev/ttyUSB* >/tmp/rc-local.log 2>&1
```
make sure it comes before the line that reads "[FONT=system]exit 0[/FONT]" if you've still got that in there. That'll list all ttyUSB devices when the script runs to a text file.
Reboot and then look at the file [FONT=system]/tmp/rc-local.log[/FONT], it'll either list a load of devices or it'll contain the message:
```
ls: cannot access '/dev/ttyUSB*': No such file or directory
```
if it contains that message, then it's running too soon in the boot process.


The rc-local.log file contains this:

```
crw-rw---- 1 root dialout 188, 0 Nov 10 00:26 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 Nov 10 00:26 /dev/ttyUSB1
crw-rw---- 1 root dialout 188, 2 Nov 10 00:26 /dev/ttyUSB2
crw-rw---- 1 root dialout 188, 3 Nov 10 00:26 /dev/ttyUSB3
crw-rw---- 1 root dialout 188, 4 Nov 10 00:26 /dev/ttyUSB4
crw-rw---- 1 root dialout 188, 5 Nov 10 00:26 /dev/ttyUSB5
crw-rw---- 1 root dialout 188, 6 Nov 10 00:26 /dev/ttyUSB6
crw-rw---- 1 root dialout 188, 7 Nov 10 00:26 /dev/ttyUSB7
```

but when I check any ttyUSB port, they all still have icanon and iexten turned off. If I run /etc/rc.local from the command line, they all get turned on properly.

---

### Post by btindie on 2022-11-10
OK, so the ttyUSB's are available at that stage in the boot.

If you run
```
sudo systemd-analyze plot > /tmp/systemd.svg
```
and open the image, you'll need to zoom in towards the bottom. You'll see that the rc-local service is being started before the getty service, thereby overriding any settings you may have given earlier.

Can you run the below, it'll show which unit file is responsible for starting the agetty on the ttyUSB devices.
```
sudo systemctl list-units '*getty*'
```

If it's [FONT=system]getty@.service[/FONT] (which would appear as [FONT=system]getty@ttyUSB0.service[/FONT] in the output) then you can extend that unit to initialise your ttyUSB devices. 

Create a new file called [FONT=system]/usr/local/sbin/setup-tty-usb[/FONT] and make it executable.
```
sudoedit /usr/local/sbin/setup-tty-usb
sudo chmod +x /usr/local/sbin/setup-tty-usb

```
contents:
```
#!/bin/sh

if case $1 in ttyUSB[0-9]) ;; *) false;; esac; then
  /usr/bin/stty -F /dev/$1 iexten icanon lcase cols 72
fi

```

Then create a systemd drop-in for the [FONT=system]getty@.service[/FONT]
```
sudo systemctl edit getty@.service
```
contents:
```
[Service]ExecStartPost=-/usr/local/sbin/setup-tty-usb %I

```

Once done you'll need to reboot. You can check with
```
stty -F /dev/ttyUSB0 -a
```
which will print the current settings in human-readable form.

---

