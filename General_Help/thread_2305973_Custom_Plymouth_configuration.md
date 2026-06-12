---
title: "Custom Plymouth configuration"
date: 2015-12-11
forum: General Help
---

### Post by corneliuz2 on 2015-12-11
Hey guys,

I am working for a company that produces an appliance that uses Ubuntu 12.04 with no desktop environment (but the X server runs). It only has one application (with GUI) which starts automatically at boot. I am trying to show a custom splash screen while the OS is loading. I took care of GRUB by setting the wait time to zero, so it doesn't show up. I know I can show a splash screen with Plymouth. I have created a theme like this:
simple.script:
```
wallpaper_image=Image("7.png");
screen_width=1024
screen_height=768
resized_wallpaper_image=
wallpaper_image.Scale(1024, 768);
wallpaper_sprite=Sprite(resized_wallpaper_image);
wallpaper_sprite.SetZ(-100)
```
simple.plymouth:
```
[Plymouth Theme]
Name=Simple
Description=Wallpaper only
ModuleName=script

[script]
ImageDir=/lib/plymouth/themes/simple
ScriptFile=/lib/plymouth/themes/simple/simple.script
```
I followed this tutorial when I created this theme: [http://www.ubunturoot.com/2010/05/how-to-create-simple-plymouth-theme.html](http://www.ubunturoot.com/2010/05/how-to-create-simple-plymouth-theme.html)
After I put these two files and the png in a folder named simple in /lib/plymouth/themes
I execute the commands:
```
*sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/simple/simple.plymouth 100*
[I]sudo update-alternatives --config default.plymouth
*sudo update-initramfs -u*[/I]

```
And it doesn't show my splash screen. Does anyone see anything wrong with this stuff?
Thank you in advance,
Corneliu

---

### Post by Portaro on 2015-12-11
I think you need also put here the content of the script file of plymouth directory theme maybe the problem is on the script.

Edit: Teh script that you have on first quote is similar to others I see on Web.

I dont understand what is the problem with your config, maybe you can try to test show plymouth theme to see if works.

I think that the command to test Plymouth themes is this:

> sudo plymouth --show-splash && sleep 5s && sudo plymouth --quit &

---

### Post by corneliuz2 on 2015-12-11
Thank you for helping. The command that you posted does not show anything. It just produces this:
```
me@myself:~$sudo plymouth --show-splash && sleep 5s && sudo plymouth --quit &
[1] 1776
me@myself:~$
```

---

### Post by corneliuz2 on 2015-12-11
I took a look at the plymouth files in /etc/init because this version uses upstart. Here they are (minus commented stuff and empty lines for concision):
pymuth.conf
```
description    "Userspace bootsplash utility"
start on (starting mountall
          or (runlevel [016]
              and (desktop-shutdown
                   or stopped xdm
                   or stopped uxlaunch)))
expect fork
kill timeout 60
script
    if [ "$RUNLEVEL" = "0" -o "$RUNLEVEL" = "1" -o "$RUNLEVEL" = "6" ]; then
        exec /sbin/plymouthd --mode=shutdown
    else
        exec /sbin/plymouthd --mode=boot --attach-to-session
    fi
end script
post-start script
    if [ "$RUNLEVEL" = "0" -o "$RUNLEVEL" = "1" -o "$RUNLEVEL" = "6" ]; then
    exec /bin/plymouth show-splash
    fi
end script
pre-stop exec /bin/plymouth quit
```
plymouth-log.conf
```
description    "Flush boot log to disk"start on filesystem
task
exec /bin/plymouth update-root-fs --read-write
```
plymouth-ready.conf
```
description "Send an event to indicate plymouth is up"task
start on startup or started plymouth-splash
instance $UPSTART_EVENTS
emits plymouth-ready
script
  if [ "$UPSTART_EVENTS" = started ] || \
     status plymouth-splash | grep -q "start/started" || \
     plymouth --ping
  then
    initctl emit plymouth-ready
  fi
end script
```
plymouth-splash.conf
```
description "Send an event to indicate plymouth is up"task
start on startup or started plymouth-splash
instance $UPSTART_EVENTS
emits plymouth-ready
script
  if [ "$UPSTART_EVENTS" = started ] || \
     status plymouth-splash | grep -q "start/started" || \
     plymouth --ping
  then
    initctl emit plymouth-ready
  fi
end script
```
plymouth-stop.conf
```
start on (starting gdm
          or starting kdm
          or starting xdm
          or starting lxdm
          or starting lightdm
          or starting uxlaunch
          or starting ubiquity
          or starting oem-config
          or stopped rc RUNLEVEL=[2345]
          or starting rcS
          or starting mountall-shell)
stop on stopped plymouth
pre-start script
    case "$JOB" in
    gdm|kdm|lightdm|ubiquity|oem-config)
    exit 0
    ;;
    *)
    exec /bin/plymouth quit
    ;;
    esac
end script
```
plymouth-upstart-bridge.conf
```
description    "Bridge Upstart state changes into Plymouth"
start on (started dbus
          or runlevel [06])
stop on stopping plymouth
console output
exec plymouth-upstart-bridge
```
And I noticed that the file plymouth-shutdown.conf is not there.

---

### Post by corneliuz2 on 2015-12-11
I changed plymouth.conf to
```
[COLOR=#000000][FONT=Ubuntu Mono]description    "Userspace bootsplash utility"
[/FONT][/COLOR]start on starting mountall
expect fork
kill timeout 60
exec /sbin/plymouthd --mode=boot --attach-to-session
pre-stop exec /bin/plymouth quit
```[COLOR=#222222][FONT=Verdana]
and plymouth-upstart-bridge.conf to
[/FONT][/COLOR]```
description    "Bridge Upstart state changes into Plymouth"
respawn
start on startup
          or runlevel [06])
stop on stopping plymouth
console output
exec plymouth-upstart-bridge
```
Still, no splash screen.

---

### Post by corneliuz2 on 2015-12-11
I read somewhere that there should be a file named [B]/etc/initramfs-tools/conf.d/splash
[/B]But I don't have it. Can anyone confirm that you still see the splash screen even if you don't have this file? And if you have the file, please post the content here. Thank you.

---

### Post by corneliuz2 on 2015-12-11
I think the x server is not started when I try to start plymouth. Can anyone tell me which upstart script should start the x server? I would like to check that, maybe the x server start command has been removed.

---

### Post by Dennis N on 2015-12-11
> **corneliuz2 said:**
> I read somewhere that there should be a file named [B]/etc/initramfs-tools/conf.d/splash
[/B]But I don't have it. Can anyone confirm that you still see the splash screen even if you don't have this file? And if you have the file, please post the content here. Thank you.

That file was part of a solution to get the splash screen to appear more quickly. Otherwise, it appeared for only a second or two or perhaps not at all. I have a note about it in Feb 2014 used in Xubuntu 13.04. You have to create it yourself. All it contained was the single line:
 Here is the whole note:

```
Use the terminal and change working directory to
/etc/initramfs-tools/conf.d

Create a new file named splash with nano
sudo nano splash

Place this line in the file:
FRAMEBUFFER=y

Save and exit nano

Update the initramfs
sudo update-initramfs -u

Reboot
The splash screen now will display normally.


```

And it did work. Nvidia cards especially had a problem.

---

### Post by corneliuz2 on 2015-12-11
Thank you, Dennis. In my case your stuff didn't work. The problem seems to be elsewhere.

---

