---
title: "Lightdm hangs on start?"
date: 2014-05-02
forum: General Help
---

### Post by HiRez_L on 2014-05-02
About a year ago, my system started booting to terminal instead of gui.  If I did a ps -ef|grep lightdm, I see it running, but I don't get gui mode until I enter: 'sudo service lightdm restart' . After that, it works fine.  I am tring to determine why lightdm is hanging on startup.  I have reinstalled lightdm, no change.


[COLOR=#000000]System: Dell Optiplex 320 (Don't laugh)[/COLOR]
[COLOR=#000000]CPU: Single physical core, 2 logical core Pentium 4 3.2GHz[/COLOR]
[COLOR=#000000]GPU: NVidia GT520, 2 monitors attached[/COLOR]
[COLOR=#000000]OS: Lubuntu 13.04 x86_64[/COLOR]
[COLOR=#000000]Kernel: 3.8.0.30-generic[/COLOR]
[COLOR=#000000]RAM: 4gb, 2 2GB sticks, 4GB Swap[/COLOR]


Here is my boot line from grub:  BOOT_IMAGE=/boot/vmlinuz-3.8.0-30-generic root=UUID=22eead58-1567-457a-b245-2042bafbbe4a ro splash quiet 5

Where would I start to look to diagnose the problem?

dmesg|grep -i lightdm gets this:

rfelty@REZ:~$ dmesg|grep -i lightdm
[   24.302817] type=1400 audit(1399049804.350:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1336 comm="apparmor_parser"
[   24.303202] type=1400 audit(1399049804.350:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=1336 comm="apparmor_parser"
[   24.303643] type=1400 audit(1399049804.350:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1335 comm="apparmor_parser"
[   24.304062] type=1400 audit(1399049804.354:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1335 comm="apparmor_parser"
[   24.312319] type=1400 audit(1399049804.362:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=1337 comm="apparmor_parser"
[   24.312730] type=1400 audit(1399049804.362:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser" pid=1337 comm="apparmor_parser"

I don't see any errors in there.

---

### Post by HiRez_L on 2014-05-03
I wen and rebooted and checked again, ps does not find lightdm when it is booted in a terminal with no gui, so lightdm is not starting at all!  Any ideas?

---

### Post by bapoumba on 2014-05-03
Had you changed anything to the LightDM configuration ?

[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

---

### Post by ibjsb4 on 2014-05-03
You can try:

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg-reconfigure lightdm[/FONT][/COLOR]
```

---

### Post by HiRez_L on 2014-05-05
> **bapoumba said:**
> Had you changed anything to the LightDM configuration ?

[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

I don't think I have, my lightdm.conf contains only three lines:

```
[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter

```

---

### Post by HiRez_L on 2014-05-05
> **ibjsb4 said:**
> You can try:

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg-reconfigure lightdm[/FONT][/COLOR]
```

Is this the expected output?

```
rfelty@REZ:~$ sudo dpkg-reconfigure lightdm
rfelty@REZ:~$ 



```

---

### Post by bapoumba on 2014-05-05
Should be normal, meaning exit without error.

Now I had a look the other day, and again today, the only lightdm.conf file I have is very different from yours. Are we talking about the same file ?
```
locate lightdm.conf
**/etc/init/lightdm.conf**
/etc/lightdm/lightdm.conf.d
/etc/lightdm/lightdm.conf.d/20-lubuntu.conf
/home/bapoumba/Desktop/lightdm.conf
/home/bapoumba/Desktop/lightdm.conf.gz
/usr/share/doc/lightdm/lightdm.conf.gz
/usr/share/lightdm/lightdm.conf.d
/usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
/usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
/usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
/usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
/var/lib/dpkg/info/lightdm.conffiles
/var/lib/dpkg/info/lightdm.config
```

The ones on my /Desktop I added myself.

```
# LightDM - light Display Manager
#
# The display manager service manages the X servers running on the
# system, providing login and auto-login services
#
# based on gdm upstart script

description	"LightDM Display Manager"
author		"Robert Ancell <robert.ancell@canonical.com>"

start on ((filesystem
           and runlevel [!06]
           and started dbus
           and plymouth-ready)
          or runlevel PREVLEVEL=S)

stop on runlevel [016]

emits login-session-start
emits desktop-session-start
emits desktop-shutdown

script
    if [ -n "$UPSTART_EVENTS" ]
    then
        # Check kernel command-line for inhibitors, unless we are being called
        # manually
        for ARG in $(cat /proc/cmdline); do
            if [ "$ARG" = "text" ]; then
		plymouth quit || : 
                stop
		exit 0
            fi
        done


```

From the wiki page :
> LighDM configuration is governed by the lightdm.conf file, however it's not suppose to be directly edited, instead use:
lightdm-set-defaults
Before you start configuring LighDM create a backup file:
sudo cp /etc/lightdm/lightdm.conf /etc/lightdm/lightdm.conf.old

---

### Post by HiRez_L on 2014-05-06
I was looking at the one under /etc/lightdm:

```
rfelty@REZ:~$ locate lightdm.conf
/etc/init/lightdm.conf
/etc/lightdm/lightdm.conf
/etc/lightdm/lightdm.conf.d
/etc/lightdm/lightdm.conf.d/10-ubuntu.conf
/etc/lightdm/lightdm.conf.d/20-gnome.conf
/etc/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
/etc/lightdm/lightdm.conf.d/50-guest-wrapper.conf
/etc/lightdm/lightdm.conf.d/50-xserver-command.conf
/usr/share/doc/lightdm/lightdm.conf.gz
/var/lib/dpkg/info/lightdm.conffiles
/var/lib/dpkg/info/lightdm.config
```

/etc/init/lightdm.conf is this:
```

# LightDM - light Display Manager
#
# The display manager service manages the X servers running on the
# system, providing login and auto-login services
#
# based on gdm upstart script


description     "LightDM Display Manager"
author          "Robert Ancell <robert.ancell@canonical.com>"


start on ((filesystem
           and runlevel [!06]
           and started dbus
           and plymouth-ready)
          or runlevel PREVLEVEL=S)


stop on runlevel [016]


emits login-session-start
emits desktop-session-start
emits desktop-shutdown


script
    if [ -n "$UPSTART_EVENTS" ]
    then
        # Check kernel command-line for inhibitors, unless we are being called
        # manually
        for ARG in $(cat /proc/cmdline); do
            if [ "$ARG" = "text" ]; then
                plymouth quit || :
                stop
                exit 0
            fi
        done


        [ ! -f /etc/X11/default-display-manager -o "$(cat /etc/X11/default-display-manager 2>/dev/null)" = "/usr/bin/lightdm" -o "$(cat /etc/X11/default-display-manager 2>/dev/null)" = "/usr/sbin/lightdm" ] || { stop; exit 0; }


        if [ "$RUNLEVEL" = S -o "$RUNLEVEL" = 1 ]
        then
            # Single-user mode
            plymouth quit || :
            exit 0
        fi
    fi


    exec lightdm
end script


post-start script
    sleep 5
    clear > /dev/tty7
end script


post-stop script
        if [ "$UPSTART_STOP_EVENTS" = runlevel ]; then
                initctl emit desktop-shutdown
        fi
end script

```

---

### Post by bapoumba on 2014-05-06
have you edited the file yourself ? Do you have a backup ?

---

### Post by HiRez_L on 2014-05-06
I have not edited it.  Could a problem with plymouth be the underlying cause?

---

### Post by bapoumba on 2014-05-06
I asked if you had changed it because of the diff between you file and mine, but that could be the ubuntu flavor you are using (I truly do not know). That said, I read over your OP.

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1283826](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1283826) ?

Are you doing some remote login ?
I had bookmarked this the other day, not sure it can help you : [http://www.mattfischer.com/blog/?p=343](http://www.mattfischer.com/blog/?p=343)

---

### Post by HiRez_L on 2014-09-15
I gave up and reinstalled, no solution found :(

---

