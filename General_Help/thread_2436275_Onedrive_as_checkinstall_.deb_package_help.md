---
title: "Onedrive as checkinstall .deb package help"
date: 2020-02-03
forum: General Help
---

### Post by yaminb on 2020-02-03
Hi all,

Old Setup:

I have a working setup of onedrive on my system.
I used this: [https://github.com/abraunegg/onedrive.git](https://github.com/abraunegg/onedrive.git)
It using make scripts, so I did make install...
I have it installed in ~/onedrive/onedrive
There is the executable (onedrive) and a configuration file (config) in that directory.
I had it autostart as a startup program as (onedrive --monitor)

New Setup:
As I've more about linux/Ubuntu, I had the bright idea that I did that 'wrong' and would have been better off using checkinstall to create a .deb file. So that the install is easy to install and remove.
It created this output
========================= Installation results ===========================
/usr/bin/install -c -D onedrive /usr/local/bin/onedrive
/usr/bin/install -c -D onedrive.1 /usr/local/share/man/man1/onedrive.1
/usr/bin/install -c -D -m 644 contrib/logrotate/onedrive.logrotate /usr/local/etc/logrotate.d/onedrive
mkdir -p /usr/local/share/doc/onedrive
/usr/bin/install -c -D -m 644 README.md config LICENSE CHANGELOG.md docs/Docker.md docs/INSTALL.md docs/Office365.md docs/USAGE.md /usr/local/share/doc/onedrive
/usr/bin/install -c -d -m 0755 /usr/lib/systemd/user /lib/systemd/system
/usr/bin/install -c -m 0644 contrib/systemd/onedrive@.service /lib/systemd/system
/usr/bin/install -c -m 0644 contrib/systemd/onedrive.service /usr/lib/systemd/user

======================== Installation successful ==========================

Things that I see that are interesting here:
1. It looks like checkinstall detected the config file (config) as a document and placed it in /usr/local/share/doc/onedrive. Best way to change this so it is a config file? I'm having issues understanding how it is going to locate the config file. In my original install, it was looking in where I did the make install ~/onedrive/onedrive/config
2. It looks like it has created this as a service as well, but I'm going stick with the manual startup entry for the user
3. There is some existing configuration (~/.config/onedrive) for things like the existing DB and refresh token. That should probably be fine to carry over.


I understand some of this is going to be very specific to this application.
What I'd like to do is make sure everything is installed via the deb and thus easily uninstallable.
rename the git report and it/s dir from ~/onedrive/onedrive to ~/local_apps/onedrive

---

### Post by yaminb on 2020-02-03
Nevermind, I am an idiot.

It was not looking for the config file in my original dir. It was using the defaults.
[https://github.com/abraunegg/onedrive/blob/master/docs/USAGE.md](https://github.com/abraunegg/onedrive/blob/master/docs/USAGE.md)

> Configuration is determined by three layers: the default values,  values set in the configuration file, and values passed in via the  command line. The default values provide a reasonable default, and  configuration is optional.
 Most command line options have a respective configuration file setting.
 If you want to change the defaults, you can copy and edit the included config file into your ~/.config/onedrive directory:



I'll try this out now.

---

### Post by yaminb on 2020-02-03
yep, everything works.

---

### Post by yaminb on 2020-02-03
doh. another lol.
Turns out I could have just installed this via apt.

---

### Post by CelticWarrior on 2020-02-03
> **yaminb said:**
> doh. another lol.
Turns out I could have just installed this via apt.

Yes :lolflag:

---

