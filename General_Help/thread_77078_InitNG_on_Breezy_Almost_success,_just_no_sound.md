---
title: "InitNG on Breezy: Almost success, just no sound"
date: 2005-10-16
forum: General Help
---

### Post by temcat on 2005-10-16
I hereby report 95-percent success with InitNG on Breezy. The only thing that doesn't work is sound: Volume Control says it couldn't find any devices to connect to or something to that effect. Automounting works fine. Boot time on my machine reduced by a half - from 65s to 35s!

1) Get InitNG version 0.3.3 from [http://alioth.debian.org/projects/pkg-initng/](http://alioth.debian.org/projects/pkg-initng/)

2) Change dbus.i file in /etc/initng/daemon directory as per [http://bugzilla.initng.thinktux.net/show_bug.cgi?id=220](http://bugzilla.initng.thinktux.net/show_bug.cgi?id=220)

3) Change hald.i file in /etc/initng/daemon directory as per [http://bugzilla.initng.thinktux.net/show_bug.cgi?id=221](http://bugzilla.initng.thinktux.net/show_bug.cgi?id=221)

4) Edit /boot/grub/menu.lst. Find an entry that looks like

title		Ubuntu, kernel 2.6.12-9-686 
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/sda9 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-686
savedefault
boot

Insert an identical entry below. Remove the word 'splash' from the 'kernel' line in the newly created entry and append 'init=/sbin/initng' to that line (without quotes). Replace 'Ubuntu' word in the 'title' line with something like 'Ubuntu (InitNG)'.

5) Reboot and choose 'Ubuntu (InitNG)' in Grub boot menu.

After that, the system should correctly boot all the way to gdm and then to Gnome, after you enter user name and password. Volume Control on the panel will be disabled.

BTW if anybody knows how to fix the volume thing - suggestions are welcome ;-)

---

### Post by mctavish on 2005-10-19
I've given it a go. It kind of worked, same as you.

I had the same problem with sound. It seems to be an alsa problem - ie alsa isn't running. There is a thread on the initnd forum on the subject but no real resolution.

I also had problems with the nvidia kernel modules. There is information on this in the gentoo wiki page on initng.

Early days I guess for the project. It seems to be a gentoo initiative. It would be nice to see debian/ubuntu collaboration on it, but would that happen?

---

### Post by temcat on 2005-10-20
Weird... I saw alsa start in syslog, it didn't spew any errors.

Early days may it be, but I think the visible troubles are already minor ;-)

---

### Post by Bitmastro on 2005-10-20
Hi! It's my first post :-). I've added coldplug in /etc/initng/system.runlevel
```

system/initial
system/mountroot
system/mountfs
system/bootmisc
system/clock
system/hostname
**system/coldplug**
system/modules
system/static-modules
system/hdparm
system/keymaps
system/urandom
system/consolefont
system/swap
net/lo
daemon/getty
system/makedev
system/discover

```
and now I have sound :-)... I don't know if adding the line at the end of the file or at the beginning can modify the startup time.
I also had to add "daemon/gdm" to /etc/initng/default.runlevel to start X.
Bye!

---

### Post by temcat on 2005-10-20
[QUOTE=Bitmastro]Hi! It's my first post :-). I've added coldplug in /etc/initng/system.runlevel
<skip>
and now I have sound :-)... I don't know if adding the line at the end of the file or at the beginning can modify the startup time.
I also had to add "daemon/gdm" to /etc/initng/default.runlevel to start X.
Bye![/QUOTE]

Maaaaan, you've made my day! Now I have working sound, too! Boot time inscreased by about 5 sec with adding coldplug.

---

### Post by Kyral on 2005-10-20
Wow! This sounds cool, can someone make a HOWTO? :D

---

### Post by temcat on 2005-10-20
[QUOTE=Kyral]Wow! This sounds cool, can someone make a HOWTO? :D[/QUOTE]

I'll try to do it, since this thread is effectively a HOWTO anyway :-)

---

### Post by mctavish on 2005-10-20
Coldplug! yeah!

I thought it must be alsa because oss was working and alsa not. I think the sound device weren't there without coldplug and ... whatever. Sound works now!

Has anyone using an nvidia card got that going? Regular init has a nvidia-glx script. I had a bit of a look but didn't see anything equivalent with initng.

---

### Post by maecenas on 2005-10-21
Wow this is really greate, I cut  boot time in half! On my thinkpad it's only about 30 s now!
This is really improving mobile use. Don't have to switch to Windows anymore :)

I hope they will implement initNG in one of the comming releases soon!
But I guess I'm dreaming here?!

Still I have problems with acpi.
I get this error:
```

FATAL: Error inserting asus_acpi (/lib/modules/2.6.12-9-386/kernel/drivers/acpi/asus_acpi.ko): No such device

FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.12-9-386/kernel/drivers/acpi/toshiba_acpi.ko): No such device

FATAL: Error inserting ibm_acpi (/lib/modules/2.6.12-9-386/kernel/drivers/acpi/ibm_acpi.ko): No such device

``` 
I think it's connected to system/speedstep.i.
I found something on bugzilla:

[http://bugzilla.initng.thinktux.net/show_bug.cgi?id=45](http://bugzilla.initng.thinktux.net/show_bug.cgi?id=45)

But it wasn't really working. So I loaded some additional modules the normal init always loads:
```

  service system/speedstep {
        depends = system/initial system/modules
        start {
                modprobe cpufreq-ondemand
		modprobe cpufreq_userspace       
		modprobe cpufreq_stats           
		modprobe cpufreq_powersave      
		modprobe cpufreq_conservative 

                modprobe speedstep-centrino
                cat  /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor > /tmp/origgovanor
                echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
        }

        stop {
                echo `cat /tmp/origgovanor` > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
        }
}

```

Well, the gnome-panel freq-app shows me different cpu-frequencys now but it only jumps from the lowet 600 to the highest 1700 and
```

enki@schleppi:~$ cat /proc/acpi/processor/CPU/throttling
state count:             8
active state:            T0
states:
   *T0:                  00%
    T1:                  12%
    T2:                  25%
    T3:                  37%
    T4:                  50%
    T5:                  62%
    T6:                  75%
    T7:                  87%

```
gives me always this output:
So I think it's not working...

Since I'm not so into the whole init process I have no idea what to do :(

I hope someone can help me with this! Cause the rest is really working fine!

---

### Post by temcat on 2005-10-22
See my HOWTO: [http://ubuntuforums.org/showthread.php?t=80423](http://ubuntuforums.org/showthread.php?t=80423)

---

