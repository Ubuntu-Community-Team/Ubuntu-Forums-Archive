---
title: "listing install packages in order installed"
date: 2020-09-28
forum: General Help
---

### Post by Skaperen on 2020-09-28
is there a way to list which packages are installed in the order that they were installed?

---

### Post by ajgreeny on 2020-09-28
How far back do you want to go?

Command ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
``` will list a fair way back with all packages installed listed in those two non-archive log files mentioned in the command.

If you need to go back further you will need to use the zgrep command on the numbered archived logs, eg ```
zgrep -i " install " /var/log/dpkg.log.5.gz
```
You will get a very long list of every package that has been installed in date order, irrespective of the method you used to install, ie, apt install, apt-get install, any of the GUI package managers such as synaptic, software-centre, etc, etc.

I don't think it will show any snaps or compiled applications you have installed.

---

### Post by Skaperen on 2020-09-28
i want to list *every* package.  those that come with the OS install should have the date of the OS install.  i want the date of original install, not upgrades (the kernel could be an issue due to package name changes).

---

### Post by ajgreeny on 2020-09-29
Every package that has been installed and is within the time frame of al&#314; those dpkg.log files will be shown if you use the command i showed using zgrep instead of grep and list the log files to be searched in backwards order,  ie start with numbered log file 5.gz if you have, then 4.gz etc etc.

You can send the output to .csv file and then open it in a spreadsheet to get everything in date order and much easier to  view by adding** > install.csv** to the end of command

---

### Post by Skaperen on 2020-09-29
so the logs are the only place the date is stored?  the database of what is installed doesn't have a date field?

---

### Post by dragonfly41 on 2020-09-29
Synaptic Package Manager GUI
File > History

---

### Post by ajgreeny on 2020-09-30
> **dragonfly41 said:**
> Synaptic Package Manager GUI
File > History
This is no use unless you have always used synaptic as it does not show any "apt install" packages and I can't  find any easy way to get that info from synaptic in the form of a txt file or similar.

---

### Post by dragonfly41 on 2020-09-30
> [COLOR=#000000]and I can't find any easy way to get that info from synaptic in the form of a txt file or similar[/COLOR]

It is true that history is difficult to dump. But I have just experimented with writing an automation script which can dump data to an external file.
Not ideal.

---

### Post by Skaperen on 2020-10-01
my log files don't go all the way back to the OS install.  they go back about one year but the OS install was before that.  i think i need to write a weekly script that collects this data from the logs and saves it in a package name indexed file more permanently.  that shouldn't be hard in Python.

---

