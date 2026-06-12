---
title: "Suspend does not work on XBMCbuntu"
date: 2013-02-25
forum: General Help
---

### Post by keyboarder2k on 2013-02-25
Hi,
I'm using XBMCbuntu (Frodo) which sets up on a Ubuntu 12.10. Unfortunately suspend does not work for me an the guide [here]("http://ubuntuforums.org/showthread.php?t=1978290") did not help.

My hardware is a "Zotac ID41" with Suspend S3 enabled in BIOS.

When I try a suspend from GUI the screen gets black for a second and then system show up again. When I enter "pm-suspend" on terminal just nothing happens.

Here are some log files:
- pm-suspend.log: [http://pastebin.com/Jdmt2K0n]("http://pastebin.com/Jdmt2K0n")
- syslog for PM: [http://pastebin.com/ZLkbg8Bx]("http://pastebin.com/ZLkbg8Bx")
- lspci VGA: [http://pastebin.com/dNx60ySj]("http://pastebin.com/dNx60ySj")
- cmdline: [http://pastebin.com/csjTEv7Y]("http://pastebin.com/csjTEv7Y")

Has anyone an idea what I could do to get suspend working?

Thanks 4 help,
Key2k

---

### Post by Toz on 2013-02-25
Hello and welcome to the forums.

Some things that I've noticed:
[LIST=1]
[*]According to /var/log/pm-suspend.log:
> Running hook /etc/pm/sleep.d/99lirc-resume suspend suspend:
Unloading lirc kernel modules
ERROR: Module ir_lirc_codec does not exist in /proc/modules
ERROR: Module lirc_dev does not exist in /proc/modules
 
/etc/pm/sleep.d/99lirc-resume suspend suspend: Returned exit code 1.
Mon Feb 25 19:11:24 CET 2013: [COLOR="Red"]**Inhibit found, will not perform suspend**[/COLOR]

What are the contents of /etc/pm/sleep.d/99lirc-resume and what were you trying to achieve by adding that file?
.
[*]> BOOT_IMAGE=/boot/vmlinuz-3.5.0-22-generic root=UUID=3f176034-5faf-4c8d-bdb0-ddf65284e392 ro quiet splash usbcore.autosuspend=-1 acpi_enforce_resources=lax vt.handoff=7
Why did you add, and what were you trying to accomplish, by adding **usbcore.autosuspend=-1 acpi_enforce_resources=lax** to your kernel boot command?
.
[*]And finally, are you using the proprietary nvidia drivers? This command might help display some more info:
```
sudo lspci -vnn | grep -A12 VGA
```
[/LIST]

---

### Post by keyboarder2k on 2013-02-25
Here is the content of "99lirc-resume": [http://pastebin.com/jsafYdLy]("http://pastebin.com/jsafYdLy")

And that's the output of
```
bmc@xbmcbuntu:~$ sudo lspci -vnn | grep -A12 VGAsudo] password for xbmc:
3:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218 [ION] [10de:064] (rev a2) (prog-if 00 [VGA controller])
       Subsystem: ZOTAC International (MCO) Ltd. Device [19da:3100]
       Physical Slot: 34
```

The resume file should load lirc upon resume to provide the functionality of lirc after suspend and resume for my remote.

The addition to the boot string should provide "wake-on-usb" or "wake-on-remote" functionality.

Both settings I found on the XBMC forum.

You think that one/some of these settings are now the problem?

---

### Post by Toz on 2013-02-25
> **keyboarder2k said:**
> Here is the content of "99lirc-resume": [http://pastebin.com/jsafYdLy]("http://pastebin.com/jsafYdLy")
It would appear that the modules **ir-lirc-codec** & **lirc_dev** don't exist after you **/etc/init.d/lirc stop** (perhaps this script automatically removes them). I would suggest deleting that file (99lirc-resume) and trying the following procedure:

- run "sudo /etc/init.d/lirc stop"
- run "sudo pm-suspend"
- do what you need to resume from suspend
- if it successfully resumes, run "sudo /etc/init.d/lirc start"
- test out the system

..and report back how far you made it and what the results of every step were. Another copy of /var/log/pm-suspend.log would also be helpful.

We can always re-create /etc/pm/sleep.d/99lirc-resume if needed.

---

### Post by keyboarder2k on 2013-02-26
I deleted 99.. an testet. The single commands didn't made some output. The system suspends as it shold an woke up on remote as well. Afterwards I restarted lirc, but in XBMC not all buttons were intepreted. I rebooted the system and everythinks works fine. So the state after suspend is not the same as after reboot.

Here is a new pm-suspend.log: [http://pastebin.com/X8tMvaa7](http://pastebin.com/X8tMvaa7)

---

### Post by keyboarder2k on 2013-02-26
After uninstalling Lirc and using the hama-mce-event-client everything works fine. Thanks for your support.

---

