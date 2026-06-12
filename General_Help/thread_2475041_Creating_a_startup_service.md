---
title: "Creating a startup service?"
date: 2022-05-14
forum: General Help
---

### Post by josullivan.c on 2022-05-14
I have an issue with my X1 Nano being unable to wake from suspend, which is resolved when I do the following:

```
sudo sh -c "echo RP01 > /proc/acpi/wakeup"
```

This disables RP01, which I believe is the issue (from Googling, think it has something to do with WWAN / LTE module)?

However, every time I reboot the machine, RP01 is enabled again. Is there a way for me to run the aforementioned at startup?

Thanks in advance.

---

### Post by TheFu on 2022-05-14
Yes, there is. There must be 50 different ways.

Which release of Ubuntu are you running? It matters.  

The easiest way, which may not work on newer Ubuntu releases is to sudoedit /etc/rc.local and add this exact line:
```
echo RP01 > /proc/acpi/wakeup
```
I'm assuming you 100% know this does what you want.

If it doesn't work when you test it, then rc.local isn't enabled and you'll want to use [https://www.linuxbabe.com/linux-server/how-to-enable-etcrc-local-with-systemd](https://www.linuxbabe.com/linux-server/how-to-enable-etcrc-local-with-systemd) to enable it.

See if it is working or not.
```
$ sudo systemctl status rc-local
```
Enable it
```
sudo systemctl enable rc-local
```

If that doesn't work, LinuxBabe has more troubleshooting and an option to use cron @reboot method.  I wouldn't use the crontab she uses. There are multiple places for crontabs and the one she's using in the example is located in a place that most people forget to backup.  I'd **sudoedit /etc/crontab** which has a slightly different format with different fields/columns.  Just be certain to include /etc/ in your backups. Get the whole thing, though you shouldn't restore it. It is small, but having the files in there for reference at restore time is very helpful, especially if you have to restore to completely new hardware.

---

### Post by psychohermit on 2022-05-14
How to run a script at startup. [https://linuxconfig.org/how-to-run-script-on-startup-on-ubuntu-20-04-focal-fossa-server-desktop](https://linuxconfig.org/how-to-run-script-on-startup-on-ubuntu-20-04-focal-fossa-server-desktop)

I've used it on three things so far it works great.

--glenn

---

### Post by josullivan.c on 2022-05-16
Have just installed Jammy Jellyfish: first time back in 20 years or so.

When I enter

```
sudo systemctl status rc-local
```

I get 

```
&#9675; rc-local.service - /etc/rc.local Compatibility     Loaded: loaded (/lib/systemd/system/rc-local.service; static)
    Drop-In: /usr/lib/systemd/system/rc-local.service.d
             &#9492;&#9472;debian.conf
     Active: inactive (dead)
       Docs: man:systemd-rc-local-generator(8)

```

Thanks for the advice.

---

### Post by norobro on 2022-05-16
systemd can do what you want by using /etc/tmpfiles.d. 

Simply create a file in /etc/tmpfiles.d with a ".conf" suffix and put the following line in it:```
w /proc/acpi/wakeup - - - - RP01
```
Or a one liner:```
sudo bash -c "echo w /proc/acpi/wakeup - - - - RP01 > /etc/tmpfiles.d/rp01.conf"
```See "man tmpflles.d"

---

### Post by TheFu on 2022-05-16
> **josullivan.c said:**
>  
I get 

```
&#9675; rc-local.service - /etc/rc.local Compatibility     Loaded: loaded (/lib/systemd/system/rc-local.service; static)
    Drop-In: /usr/lib/systemd/system/rc-local.service.d
             &#9492;&#9472;debian.conf
     Active: inactive (dead)
       Docs: man:systemd-rc-local-generator(8)

```

Thanks for the advice.

The link provided above answers exactly that question with the detailed steps.  Click it.  It is fairly clear.  

We should have said that using rc.local is the old-school way. I think systemd actually didn't ship with it for a few years. New ways of doing things sometimes break the old ways we have been doing thing. That isn't always bad, unless it has been 40 yrs of the old way like rc.local was. rc.local is/was how we'd run local stuff at the very end of the multi-user boot process.  Change, because they can.

As for /etc/tempfiles.d/, the manpage is 11 pgs. Clearly powerful, but with a new file format. Didn't know about it before.

---

