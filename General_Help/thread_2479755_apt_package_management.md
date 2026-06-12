---
title: "apt package management"
date: 2022-10-05
forum: General Help
---

### Post by ejkeebler2 on 2022-10-05
I was testing out an application and it required some prereqs of 8 or 9 things, so I ran apt and installed them all in a list.  All is well, a few days later, and I've now decided not to use that application, and I want to remove the prereqs, but to be honest, I dont know which I still need.  Is there an apt log, I can look in to see maybe which ones were already installed and in use prior to me installing the whole list.  I know, I know terrible process to not pay complete attention to what I was doing.  For example I know I want to keep curl and wget installed, but I dont know if other packages were like jq, dbus, libglib2, etc.  I was hoping I could see a log and see, oh yeah it skipped that one and that one and that one, etc and remove the others.

It's just for cleanup purposes, everything is working as expected, from what I can tell.

---

### Post by Holger_Gehrke on 2022-10-05
/var/log/apt/history for the latest installations, /var/log/apt/history.*some_number*.gz for older installations (replace *some_number* with a number, on my system there's only 6 old log files kept but I did a fresh install for 22.04).

Holger

---

### Post by ejkeebler2 on 2022-10-05
thanks actually just came across this answer myself, good to know i'm headed in the right direction!  Do you know if it shows the command and then what action was taken, or does it just show one or the other?

---

### Post by &amp;KyT$0P# on 2022-10-05
It shows both, though the command line may not necessarily be particularly informative if the operation was done through something like Synaptic or Software Updater.

---

### Post by ajgreeny on 2022-10-05
A useful command to get information on packages installed is ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
``` which will list all installed packages in order of the dates installed.

By looking at the dates shown you should be able to see what was installed at the same time.
You can use a similar command to show dates of upgrades or removal of packages simply by changing the search term ***install*** to ***upgrade*** or ***remove***.  It's best keep the space each side of the search word in the quotation marks for a nice clean output, particularly for the install search.

PS:
These commands show everything installed, upgraded or removed using the systems package management system, ie, software-updater, synaptic or command line using apt or apt-get as all those use ***dpkg*** in the background.

---

### Post by Dennis N on 2022-10-05
> All is well, a few days later, and I've now decided not to use that application, and I want to remove the prereqs, but to be honest, I dont know which I still need.
prereqs = dependencies?
Assumed that when you say you decided "not to use" the application, you have removed it:
```
sudo apt autoremove
``` 
will remove the dependencies that were automatically installed for the package and no longer needed.

See: **man apt** > **autoremove** option

---

### Post by ejkeebler2 on 2022-10-05
> **Dennis N said:**
> prereqs = dependencies?
Assumed that when you say you decided "not to use" the application, you have removed it:
```
sudo apt autoremove
``` 
will remove the dependencies that were automatically installed for the package and no longer needed.

See: **man apt** > **autoremove** option

unfortunately no, I wish it was dependancies, it was a list of " before you install, make sure you have these"

So, now that I am at home, would it be safe to say that from the log below, after running my command, whatever was missing was already on there?  i.e dbus? Or if I had an older version is it possible it installed it as an update to what I already had?

Commandline: apt install apparmor jq wget curl udisks2 libglib2.0-bin network-manager dbus systemd-journal-remote -y


Install: libonig5:amd64 (6.9.7.1-2build1, automatic)
libmicrohttpd12:amd64 (0.9.75-3ubuntu1, automatic)
wpasupplicant:amd64 (2:2.10-6ubuntu2, automatic)
ppp:amd64 (2.4.9-1+1ubuntu3, automatic)
libnl-route-3-200:amd64 (3.5.0-0.1, automatic)
pptp-linux:amd64 (1.10.0-1build3, automatic)
ystemd-journal-remote:amd64 (249.11-0ubuntu3.6)
dnsmasq-base:amd64 (2.86-1.1ubuntu0.1, automatic)
libndp0:amd64 (1.8-0ubuntu3, automatic)
libpcsclite1:amd64 (1.9.5-3, automatic)
libteamdctl0:amd64 (1.31-1build2, automatic)
network-manager:amd64 (1.36.6-0ubuntu2)
network-manager-pptp:amd64 (1.2.10-1, automatic)
libbluetooth3:amd64 (5.64-0ubuntu1, automatic)
jq:amd64 (1.6-2.1ubuntu3)
libjq1:amd64 (1.6-2.1ubuntu3, automatic)
libnm0:amd64 (1.36.6-0ubuntu2, automatic)
dns-root-data:amd64 (2021011101, automatic)

---

### Post by raleigh3 on 2022-10-05
Thanks very much for the useful command.

---

### Post by &amp;KyT$0P# on 2022-10-05
> **ejkeebler2 said:**
> would it be safe to say that from the log below, after running my command, whatever was missing was already on there?  i.e dbus? Or if I had an older version is it possible it installed it as an update to what I already had?

If you already had an older version of the package installed, it would update it to the latest version.  If you already had the latest version, it would just mark it as manually installed.  In the latter case it would not be listed in the log.  In the former case I think it would be listed on an [FONT=Courier New]Upgrade:[/FONT] line.

Based on the log you posted, start with this -
```
sudo apt-get --autoremove purge jq systemd-journal-remote
```

But oddly, your logs also say that [FONT=Courier New]network-manager[/FONT] was installed by that command?  Are you sure you don't need that?  Is this machine a server that has networking set up some other way?

---

