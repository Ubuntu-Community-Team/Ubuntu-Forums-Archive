---
title: "Suspend script stalls on &quot;modprobe ndiswrapper&quot;--why?"
date: 2008-05-25
forum: General Help
---

### Post by caljohnsmith on 2008-05-25
I'm troubleshooting suspend problems on my computer, so first I put a "set -x" at the beginning of the /etc/acpi/sleep.sh script, then I login as root using sudo su, and then I run the script using:
```
./sleep.sh force 2>&1 | tee /home/john/Desktop/sleep.txt
```
Which essentially records everything that happens into the sleep.txt file while the script runs, including stderr. So when I run it, my monitor goes into standby, but I can't resume and have to reboot. Here is the result found in the sleep.txt file:
```
+ . /etc/default/acpi-support
++ ACPI_SLEEP=true
++ ACPI_HIBERNATE=true
++ ACPI_SLEEP_MODE=standby
++ MODULES=ptyq4
++ MODULES_WHITELIST=
++ SAVE_VBE_STATE=false
++ VBESTATE=/var/lib/acpi-support/vbestate
++ POST_VIDEO=false
++ USE_DPMS=true
++ HIBERNATE_MODE=shutdown
++ LOCK_SCREEN=true
++ STOP_SERVICES=
++ RESTART_IRDA=false
++ ENABLE_LAPTOP_MODE=false
++ SPINDOWN_TIME=12
+ . /usr/share/acpi-support/power-funcs
++ umask 022
++ PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/bin/X11
++ POWERSTATE=/var/lib/acpi-support/powerstate
++ LAPTOP_MODE=/usr/sbin/laptop_mode
++ HDPARM='/sbin/hdparm -q'
++ LIDSTATE=/var/lib/acpi-support/lidstate
+ . /usr/share/acpi-support/device-funcs
+ . /usr/share/acpi-support/policy-funcs
+ DeviceConfig
++ cat /var/lib/acpi-support/system-manufacturer
+ manufacturer=Compaq
++ cat /var/lib/acpi-support/system-product-name
+ model='Compaq PC'
++ cat /var/lib/acpi-support/system-version
+ version=N/A
++ cat /var/lib/acpi-support/bios-version
+ bios_version=786K1
+ '[' -f /usr/share/acpi-support/Compaq.config ']'
+ . /usr/share/acpi-support/Compaq.config
++ case "$model" in
+ '[' xtrue '!=' xtrue ']'
+ '[' xforce '!=' xforce ']'
+ '[' xtrue = xtrue ']'
+ pidof xscreensaver
+ . /etc/acpi/prepare.sh
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/05-acpi-lock.sh ']'
++ . /etc/acpi/suspend.d/05-acpi-lock.sh
+++ touch /var/lock/acpisleep
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/10-thinkpad-standby-led.sh ']'
++ . /etc/acpi/suspend.d/10-thinkpad-standby-led.sh
+++ . /usr/share/acpi-support/state-funcs
+++ setLEDThinkpadSuspending 1
++++ test 1 -ne 0
++++ echo blink
+++ action=blink
+++ test -w /proc/acpi/ibm/led
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/15-anacron.sh ']'
++ . /etc/acpi/suspend.d/15-anacron.sh
+++ /usr/sbin/invoke-rc.d anacron stop
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/30-proc-sysfs-save-state.sh ']'
++ . /etc/acpi/suspend.d/30-proc-sysfs-save-state.sh
+++ '[' -d /var/run -a -w /var/run ']'
+++ for i in '/sys/class/net/*/device/rf_kill' '/sys/devices/system/cpu/cpu*/cpufreq/scaling_governor'
+++ '[' -r '/sys/class/net/*/device/rf_kill' ']'
+++ for i in '/sys/class/net/*/device/rf_kill' '/sys/devices/system/cpu/cpu*/cpufreq/scaling_governor'
+++ '[' -r '/sys/devices/system/cpu/cpu*/cpufreq/scaling_governor' ']'
+++ i=/proc/acpi/ibm/bluetooth
+++ '[' -r /proc/acpi/ibm/bluetooth ']'
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/50-irda-stop.sh ']'
++ . /etc/acpi/suspend.d/50-irda-stop.sh
+++ '[' -f /var/run/irattach.pid ']'
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/50-tosh-save-brightness.sh ']'
++ . /etc/acpi/suspend.d/50-tosh-save-brightness.sh
+++ TOSH_LCD=/proc/acpi/toshiba/lcd
+++ '[' -e /proc/acpi/toshiba/lcd ']'
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/55-down-interfaces.sh ']'
++ . /etc/acpi/suspend.d/55-down-interfaces.sh
+++ pccardctl eject
+++ killall dhclient dhclient3
++++ /sbin/ifconfig
++++ awk '/^[^ ]+/ {print $1}'
+++ INTERFACES='eth0
lo
wlan0'
+++ for x in '$INTERFACES'
+++ ifdown eth0
ifdown: interface eth0 not configured
+++ ifconfig eth0 down
+++ for x in '$INTERFACES'
+++ ifdown lo
+++ ifconfig lo down
+++ for x in '$INTERFACES'
+++ ifdown wlan0
+++ ifconfig wlan0 down
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/60-generate-modules-list.sh ']'
++ . /etc/acpi/suspend.d/60-generate-modules-list.sh
+++ for x in '/sys/module/*_ircc' '/sys/module/*_ircc2'
++++ basename '/sys/module/*_ircc'
+++ x='*_ircc'
+++ '[' '*_ircc' '!=' nsc_ircc ']'
+++ modprobe -r '*_ircc'
+++ for x in '/sys/module/*_ircc' '/sys/module/*_ircc2'
++++ basename '/sys/module/*_ircc2'
+++ x='*_ircc2'
+++ '[' '*_ircc2' '!=' nsc_ircc ']'
+++ modprobe -r '*_ircc2'
+++ '[' -d /sys/module/ndiswrapper ']'
+++ modprobe -r ndiswrapper
+++ MODULES='ptyq4 ndiswrapper'
+++ for x in '/sys/class/net/*'
+++ '[' -e /sys/class/net/eth0/device/driver ']'
+++++ readlink /sys/class/net/eth0/device/driver
++++ basename ../../../bus/pci/drivers/8139too
++++ tr '[:upper:]' '[:lower:]'
+++ MODULES='ptyq4 ndiswrapper 8139too'
+++ for x in '/sys/class/net/*'
+++ '[' -e /sys/class/net/lo/device/driver ']'
+++ '[' -d /sys/module/netconsole ']'
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/65-services-stop.sh ']'
++ . /etc/acpi/suspend.d/65-services-stop.sh
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/70-modules-unload.sh ']'
++ . /etc/acpi/suspend.d/70-modules-unload.sh
+++ for x in '$MODULES'
+++ modprobe -r ptyq4
+++ for x in '$MODULES'
+++ modprobe -r ndiswrapper
+++ for x in '$MODULES'
+++ modprobe -r 8139too
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/75-console-switch.sh ']'
++ . /etc/acpi/suspend.d/75-console-switch.sh
++++ fgconsole
+++ CONSOLE=7
+++ chvt 12
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/80-video-pci-state.sh ']'
++ . /etc/acpi/suspend.d/80-video-pci-state.sh
+++ '[' x = xtrue ']'
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/80-video-vesa-state.sh ']'
++ . /etc/acpi/suspend.d/80-video-vesa-state.sh
+++ '[' xfalse = xtrue ']'
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/85-alsa-state.sh ']'
++ . /etc/acpi/suspend.d/85-alsa-state.sh
+++ '[' -x /etc/init.d/alsa-utils ']'
+++ /etc/init.d/alsa-utils stop
 * Shutting down ALSA...       [80G 
[74G[ OK ]
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/88-time.sh ']'
++ . /etc/acpi/suspend.d/88-time.sh
+++ '[' -x /etc/init.d/hwclock.sh ']'
+++ /etc/init.d/hwclock.sh stop
 * Saving the system clock
++ for SCRIPT in '/etc/acpi/suspend.d/*.sh'
++ '[' -x /etc/acpi/suspend.d/90-framebuffer-stop.sh ']'
++ . /etc/acpi/suspend.d/90-framebuffer-stop.sh
+++ '[' xtrue = xtrue ']'
+++ vbetool dpms off
+++ for x in '/sys/class/graphics/*'
+++ '[' -f '/sys/class/graphics/*/state' ']'
+ '[' x = xtrue ']'
+ echo -n standby
./sleep_new.sh: line 40: echo: write error: Resource temporarily unavailable
+ '[' x = xtrue ']'
+ '[' x = xtrue ']'
+ . /etc/acpi/resume.sh
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/10-thinkpad-standby-led.sh ']'
++ . /etc/acpi/resume.d/10-thinkpad-standby-led.sh
+++ . /usr/share/acpi-support/state-funcs
+++ setLEDThinkpadSuspending 1
++++ test 1 -ne 0
++++ echo blink
+++ action=blink
+++ test -w /proc/acpi/ibm/led
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/13-855-resolution-set.sh ']'
++ . /etc/acpi/resume.d/13-855-resolution-set.sh
+++ '[' -x /usr/sbin/855resolution ']'
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/15-video-post.sh ']'
++ . /etc/acpi/resume.d/15-video-post.sh
+++ '[' xfalse = xtrue ']'
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/17-video-restore.sh ']'
++ . /etc/acpi/resume.d/17-video-restore.sh
+++ '[' xfalse = xtrue ']'
+++ '[' x = xtrue ']'
++ for SCRIPT in '/etc/acpi/resume.d/*.sh'
++ '[' -x /etc/acpi/resume.d/35-modules-load.sh ']'
++ . /etc/acpi/resume.d/35-modules-load.sh
+++ '[' -f /sys/class/firmware/timeout ']'
++++ cat /sys/class/firmware/timeout
+++ timeout=60
+++ echo 100
+++ for x in '$MODULES'
+++ modprobe ptyq4
FATAL: Module ptyq4 not found.
+++ for x in '$MODULES'
+++ modprobe ndiswrapper
```
So notice it seemed to hang on trying to "modprobe ndiswrapper" even though I ran the script as root. So I manually "sudo modprobe -r ndiswrapper" before running the script (after I had rebooted), and voila, my computer suspends fine and resumes fine. And after resuming I can do a "sudo modprobe ndiswrapper" to reload ndiswrapper no problem.

Why does the script hang when it tries to reload the ndiswrapper module? Any ideas?

---

