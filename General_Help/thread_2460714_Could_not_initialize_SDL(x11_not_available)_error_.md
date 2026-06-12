---
title: "Could not initialize SDL(x11 not available) error while I'm trying to start automatic"
date: 2021-04-16
forum: General Help
---

### Post by marietto2008 on 2021-04-16
Hello

I would like to run a shell script automatically every time my ubuntu 18.04 installation has landed and I see the desktop manager fully loaded. The script should be executed regarless of the desktop manager that I'm using. To do this I created these scripts :

Created executable file /opt/rasp/setup-rasp.sh:

```
#!/bin/bash
echo "Setting up rasp ...mounting I9"
touch /tmp/rasp-activated
echo mounting I9...wait 20s
sleep 20s

sudo mount -t nfs -o nolock,local_lock=all 192.168.1.6:/home/ziomario/Scrivania/Dati/Data/Nano/I9 /home/zi/Desktop/Work/I9

sleep 20s

qemu-system-aarch64 -M virt -m 2048 -smp 2 -cpu host,aarch64=off -enable-kvm \
-kernel /home/zi/Desktop/Work/I9/arm32/debian11-bullseye/vmlinuz-5.10.0-5-armmp-lpae \
-initrd /home/zi/Desktop/Work/I9/arm32/debian11-bullseye/initrd.img-5.10.0-5-armmp-lpae \
-append 'root=/dev/vda2' \
-device usb-ehci -device usb-kbd -device usb-mouse -usb -serial stdio \
-device virtio-gpu-pci,virgl=on,xres=1920,yres=1080 -display sdl,gl=on \
-drive if=none,file=/home/zi/Desktop/Work/I9/arm32/hda-bullseye2.qcow2,format=qcow2,id=hd \
-device virtio-blk-device,drive=hd -netdev user,id=mynet \
-device virtio-net-device,netdev=mynet \
-bios edk2-arm-code.fd \
-no-reboot

```
Created executable file /opt/rasp/teardown-rasp.sh:

```
#!/bin/bash
echo "Tearing down rasp ..."
if [ -f /tmp/rasp-activated ]; then
    rm /tmp/rasp-activated
else
    echo "Doesnt seem to be up: Skipping ..."
fi
```

Created systemd unit file : /etc/systemd/system/rasp.service

```
[Unit]
Description=Setup rasp
#After=network.target

[Service]
Type=oneshot
ExecStart=/opt/rasp/setup-rasp.sh
RemainAfterExit=true
ExecStop=/opt/foo/teardown-rasp.sh
StandardOutput=journal

[Install]
WantedBy=multi-user.target
```

and I have activated the service with :

**sudo systemctl enable rasp.service**

I have rebooted ubuntu and I saw that the nfs folder I9 has been mounted,but the raspberry qemu-system-aarch64 virtual machine didn't start because this error :

```
zi@zi-desktop:~$ sudo systemctl status raspberry.service

   raspberry.service - Setup rasp
   Loaded: loaded (/etc/systemd/system/raspberry.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2021-04-16 12:19:30 CEST; 524ms ago
  Process: 4060 ExecStart=/opt/rasp/setup-rasp.sh (code=exited, status=1/FAILURE)
 Main PID: 4060 (code=exited, status=1/FAILURE)
apr 16 12:18:39 zi-desktop setup-rasp.sh[4060]: Setting up rasp ...mounting I9
apr 16 12:18:39 zi-desktop setup-rasp.sh[4060]: mounting I9...wait 20s
apr 16 12:19:00 zi-desktop sudo[7326]:     root : TTY=unknown ; PWD=/ ; USER=root ; COMMAND=/bin/mount -t nfs -o nolock,local_lock=all 192.168.1.6:/home/zioma
apr 16 12:19:00 zi-desktop sudo[7326]: pam_unix(sudo:session): session opened for user root by (uid=0)
apr 16 12:19:00 zi-desktop sudo[7326]: pam_unix(sudo:session): session closed for user root
apr 16 12:19:00 zi-desktop setup-rasp.sh[4060]: Running raspbian. Wait 30s...
apr 16 12:19:30 zi-desktop setup-rasp.sh[4060]: Could not initialize SDL(x11 not available) - exiting
apr 16 12:19:30 zi-desktop systemd[1]: raspberry.service: Main process exited, code=exited, status=1/FAILURE
apr 16 12:19:30 zi-desktop systemd[1]: raspberry.service: Failed with result 'exit-code'.
apr 16 12:19:30 zi-desktop systemd[1]: Failed to start Setup rasp.

```
the vm starts correctly when I open a terminal and I run the qemu vm from there.

I have also tried this script : /opt/rasp/setup-rasp.sh:

```
#!/bin/bash
gnome-terminal
```

this time error is :

**Unable to init server: could not connect : connection refused failed to parse arguments: cannot open display:**

---

### Post by ActionParsnip on 2021-04-17
Make sure you use full paths to all commands and files. Also make sure that the accounts running the commands have sufficient access to the files being used. If your user can run the command OK then it may be an access/permission issue

---

### Post by Holger_Gehrke on 2021-04-17
You're trying to use SDL (Simple DirectMedia Layer) as a display. SDL expects X11 to be up and running. This is not yet the case at this point of the boot process. If this is a program which generally needs a graphical display, then a systemd service might not be the way to go ...
And by the way, systemd services run as root, so the 'sudo' in the script is not necessary.

Holger

---

### Post by marietto2008 on 2021-04-17
is there a method to launch also the X server with systemd ?

---

### Post by Holger_Gehrke on 2021-04-17
X is launched by the display manager which is launched by systemd but AFAIK at the end of the start process; '/lib/systemd/system/lightdm.service' on my system (XUbuntu 18.04) specifies 'After=systemd-user-sessions.service [email]getty@tty7.servic[/email]e plymouth-quit.service'; that looks very late indeed; you need the display manager in there because before starting your desktop it runs the greeter to log you in. As I said previously: a systemd service might not be the way to go. A simple .desktop file in '~/.config/autostart is probably a better choice.

Holger

---

