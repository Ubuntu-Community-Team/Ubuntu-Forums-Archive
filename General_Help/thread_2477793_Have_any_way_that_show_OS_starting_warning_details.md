---
title: "Have any way that show OS starting warning details after the OS is totally started ?"
date: 2022-08-07
forum: General Help
---

### Post by aug7744 on 2022-08-07
Thanks for read that topic.
When OS starting if using in grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Not any messages about failed commands in OS startup, but the OS is totally started.
Is possible read the OS log and see if has anything line with "failed".

Ubuntu has any feature that open an window with any warning about the OS boot startup or even disabling the bootup screen changing to console showing any failed commands ?

Having to read the bootlogs all time that the OS is started not is the right choice.

Have an nice week.

---

### Post by &amp;KyT$0P# on 2022-08-07
Does
```
systemctl list-units --failed
```
show what you're looking for?

---

### Post by aug7744 on 2022-08-07
Thanks for your reply.

  UNIT                  LOAD   ACTIVE SUB    DESCRIPTION                           
&#9679; fwupd-refresh.service loaded failed failed Refresh fwupd metadata and update motd

LOAD   = Reflects whether the unit definition was properly loaded.
ACTIVE = The high-level unit activation state, i.e. generalization of SUB.
SUB    = The low-level unit activation state, values depend on unit type.

1 loaded units listed.





That happen randomly.

---

### Post by &amp;KyT$0P# on 2022-08-07
You might be able to see why it fails if you run this when it's failed -
```
systemctl status fwupd-refresh
```

---

### Post by arraybolt3 on 2022-08-07
Also:

```
 sudo dmesg | less 
```

This will show you output from the kernel, which may contain some interesting data that can aid in debugging things like audio or Wi-Fi driver issues.

---

### Post by oldos2er on 2022-08-08
So you want to see the kernel messages during boot? Change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="" then run ```
sudo update-grub
```

---

### Post by aug7744 on 2022-08-08
Thanks for all replies trying help me.
Here has good information shared.

I want known if Ubuntu has a way to warning the user after that the OS was totally loaded.
Example
OS started ... not problems ... not shown any warning
OS started ... try load components or failed commands in boot startup ... after OS totally started Ubuntu display an message about errors being in console or an window.

---

### Post by yancek on 2022-08-09
Check log files, specifically boot.log in /var/log directory.

---

### Post by oldfred on 2022-08-09
You can do this.
Errors/Warnings:
sudo journalctl -b -p err
sudo egrep -i 'warn|error' /var/log/*g

Its just I get multiple lines and none really are issues.
Some are from things I have turned off as I do not want them, so just a warning.

---

### Post by &amp;KyT$0P# on 2022-08-10
I think what they're seeking is if any systemd services failed during boot, show a generic notification of that when logging in.

I don't know a way to do this out-of-the-box, sorry.  If I wanted this I'd probably try to script it myself, figuring out an automatic way to check [FONT=Courier New]systemctl list-units --failed[/FONT] and if anything failed, send the notification using [FONT=Courier New]notify-send[/FONT] (from package [FONT=Courier New]libnotify-bin[/FONT]).  Once that's working you can set up to autostart it at login (if your desktop environment doesn't have a GUI way to control autostart at login, you can manually create a .desktop file for the script and place it in [FONT=Courier New]~/.config/autostart/[/FONT] folder).

---

### Post by mIk3_08 on 2022-08-11
> **aug7744 said:**
> Thanks for read that topic.
When OS starting if using in grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Not any messages about failed commands in OS startup, but the OS is totally started.
Is possible read the OS log and see if has anything line with "failed".

Ubuntu has any feature that open an window with any warning about the OS boot startup or even disabling the bootup screen changing to console showing any failed commands ?

Having to read the bootlogs all time that the OS is started not is the right choice.

Have an nice week.

You can also see the system logs here. Just run the command below in your terminal. Regards and cheers
```
cat /var/log/syslog
```

---

