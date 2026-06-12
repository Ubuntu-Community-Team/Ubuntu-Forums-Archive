---
title: "i want to run my own script at splash page time"
date: 2021-08-02
forum: General Help
---

### Post by Skaperen on 2021-08-02
i want to run my own script at splash page time.  this script does not open any windows and outputs nothing (to stdout or stderr)  it does not access the display or the network.  it does need to read files in [FONT=courier new]/etc[/FONT] and [FONT=courier new]/root[/FONT] and also needs to append a small amount of data to its own file(s) in those directories.  it also needs to read [FONT=courier new]/proc/partitions[/FONT] and on some occasions do a reboot (it can just run the [FONT=courier new]reboot[/FONT] command if directly signalling init is not a good idea).  does anyone know how to achieve this?  is rebooting safe at that point of time?

---

### Post by scorp123 on 2021-08-03
> **Skaperen said:**
>  i want to run my own script at splash page time.  this script does not open any windows and outputs nothing (to stdout or stderr)  it does not access the display or the network.  it does need to read files in [FONT=courier new]/etc[/FONT] and [FONT=courier new]/root[/FONT] and also needs to append a small amount of data to its own file(s) in those directories.  it also needs to read [FONT=courier new]/proc/partitions[/FONT] and on some occasions do a reboot (it can just run the [FONT=courier new]reboot[/FONT] command if directly signalling init is not a good idea).  does anyone know how to achieve this? 

Create a systemd service?

As root or by using **"sudo"**: Create a file with the name **"/etc/systemd/system/nameofyourservice.service"**
Content could be:
```

[Unit]
Description=NameOfYourService
Requires=network.target
After=systemd-user-sessions.service

[Service]
Type=simple
ExecStart=/path/to/your/shell-script/that/does/the/stuff/you/want.sh
# Please test your script first before you auto-hose your system at boot time!!
User=root

[Install]
WantedBy=multi-user.target

```

Once that file exists you can run these commands:
```
sudo systemctl daemon-reload
sudo systemctl enable nameofyourservice
```

If everything has been done correctly then your service should auto-run at the next reboot and do all the things you programmed it to do.

> **Skaperen said:**
>   is rebooting safe at that point of time?

I don't think so. And I don't think it's even possible at that very moment because the system would still be in the process of booting up. But you could create a file that informs you of the need to reboot, so you could reboot manually once the system is up and running. It would not feel much different than after a normal system update.

Your script could create this empty file, e.g with a simple "touch" command:
```
touch /var/run/reboot-required
```

Once the file exists your system will constantly nag you that it needs to reboot.

---

### Post by dragonfly41 on 2021-08-03
Another experiment.
If you install rEFIND to sit in /boot/efi/EFI/refind/
you will find a [ton of options in the refind.conf file]("http://www.rodsbooks.com/refind/configfile.html")
including selecting your own splash theme and running scripts.

---

### Post by Skaperen on 2021-08-04
> **scorp123 said:**
> Once the file exists your system will constantly nag you that it needs to reboot.

i want the reboot for this to be automatic and be done ASAP.  this script is detecting a condition that is unsafe for the system to run.  doing this before systemd even starts might be needed.  making my own init in C (BTDT) that does the check and maybe reboots the kernel or execve()'s the systemd init is not off table.

one aspect of the condition involves a possible USB hard drive left plugged in with the same UUID as the system root.  left running this way, one or more hard drives could end up with tangled or lost files.  i'd recognize the reboot and unplug the drive before BIOS runs, again.  or maybe some kernel argument can detect this.

---

### Post by scorp123 on 2021-08-05
> **Skaperen said:**
>  one aspect of the condition involves a possible USB hard drive left plugged in with the same UUID as the system root.

Then change the UUID?

```

sudo tune2fs -U $(uuidgen) /dev/sdXwhatever

```

Replace "/dev/sdX" with the actual value for the USB device.

---

### Post by Skaperen on 2021-08-05
changing the UUID is not an option for this setup.  it is a sector backup.  the UUID was just copied.

---

### Post by scorp123 on 2021-08-05
> **Skaperen said:**
>  it is a sector backup.

Why a sector backup? What for??

---

### Post by Skaperen on 2021-08-06
now we are getting off topic for this thread.

---

### Post by scorp123 on 2021-08-11
You expect solutions for self-inflicted problems. You could help yourself by not being so stubborn about doing these nonsensical things "your way" and be more open for suggestions by people who obviously know better.

---

### Post by Skaperen on 2021-08-11
if there were any "obviously know better" people around, i'd ask them my original question.  hopefully they know not to tread off topic.

---

