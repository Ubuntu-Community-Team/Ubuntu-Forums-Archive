---
title: "Apt-Get Growing Log"
date: 2024-10-19
forum: General Help
---

### Post by wyattwhiteeagle on 2024-10-19
Does apt-get have a growing log somewhere?

---

### Post by deadflowr on 2024-10-19
apt is logged in /var/log/apt.
usually 2 files, 1 is a history.log that shows what was installed, removed or upgraded.
the other is a term.log that shows the general output of what and how it was done.

For even more nuanced there is a dpkg.log usually just in /var/log.


These logs do rotate so there may also be several compressed archive tar.gz files as well.

---

### Post by 1fallen on 2024-10-19
+1 with deadflowr, and don't forget
```
/var/log/apt&#55357;&#56594; 
&#9492;&#9472;> less term.log
```

---

### Post by wyattwhiteeagle on 2024-11-01
I just took a closer look in this directory.
I'm goin fishin for these "catfish"...goin for sourthern fried...yummy

/var/log contents...
```
auth.logboot.log
btmp
cups
dmesg
dmesg.0
dmesg.1.gz
gpu-manager.log
kern.log
lastlog
monitorix
monitorix-httpd
private
syslog
unattended-upgrades
wtmp
Xorg.0.log
Xorg.0.log.old
```

---

### Post by wyattwhiteeagle on 2024-11-01
Already got one big catfish...
apt-get manpage lists' most or all of it's files and their locations.
None of them are in /var/log.
I believe I may still be looking for where the log file is and its configurations files.

```


FILES
       /etc/apt/sources.list
           Locations to fetch packages from. Configuration Item: Dir::Etc::SourceList.


       /etc/apt/sources.list.d/
           File fragments for locations to fetch packages from. Configuration Item: Dir::Etc::SourceParts.


       /etc/apt/apt.conf
           APT configuration file. Configuration Item: Dir::Etc::Main.


       /etc/apt/apt.conf.d/
           APT configuration file fragments. Configuration Item: Dir::Etc::Parts.


       /etc/apt/preferences
           Version preferences file. This is where you would specify "pinning", i.e. a preference to get
           certain packages from a separate source or from a different version of a distribution.
           Configuration Item: Dir::Etc::Preferences.


       /etc/apt/preferences.d/
           File fragments for the version preferences. Configuration Item: Dir::Etc::PreferencesParts.


       /var/cache/apt/archives/
           Storage area for retrieved package files. Configuration Item: Dir::Cache::Archives.


       /var/cache/apt/archives/partial/
           Storage area for package files in transit. Configuration Item: Dir::Cache::Archives (partial will
           be implicitly appended)


       /var/lib/apt/lists/
           Storage area for state information for each package resource specified in sources.list(5)
           Configuration Item: Dir::State::Lists.


       /var/lib/apt/lists/partial/
           Storage area for state information in transit. Configuration Item: Dir::State::Lists (partial
           will be implicitly appended)


SEE ALSO
       apt-cache(8), apt-cdrom(8), dpkg(1), sources.list(5), apt.conf(5), apt-config(8), apt-secure(8), The
       APT User's guide in /usr/share/doc/apt-doc/, apt_preferences(5), the APT Howto.
```

---

### Post by deadflowr on 2024-11-01
The logs are generated through logrotate.
Look at /etc/logrotate.d/apt

---

