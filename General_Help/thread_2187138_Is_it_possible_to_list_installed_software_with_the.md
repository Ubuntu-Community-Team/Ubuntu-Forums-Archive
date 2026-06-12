---
title: "Is it possible to list installed software with the date of installation?"
date: 2013-11-11
forum: General Help
---

### Post by vasa1 on 2013-11-11
**dpkg --get-selections** gives me a list of installed software. But how would I get a list that includes the date on which each software package was installed? I think the Ubuntu Software Center has such a facility. Is there a command-line equivalent that would work in the absence of Ubuntu Software Center? 

I didn't find the facility in Lubuntu Software Center. And Synaptic Package Manager has *File, History* but that doesn't seem to do anything possibly because I don't use SPM to install software.

(I know I can search /var/log/apt/history.log to find when a particular package was installed.)

---

### Post by oldfred on 2013-11-11
I am not sure if it is date last installed or not, but it shows date.

 All the data on what packages are installed is contained under the /var/lib/dpkg/ directory.
It's all in the status file - every installed package has the word "installed" on it's Status: line.
However, it's probably easiest to just get the directory listing of the /var/lib/dpkg/info/ directory. Just look at all the files named *.list:
cd /var/lib/dpkg/info
ls -l
Really long list may be better to redirect.

ls -l > paklist

---

### Post by vasa1 on 2013-11-12
@oldfred, thank you for replying. I looked various files in /var/lib/dpkg/ but didn't find mention of the date of installation. Meanwhile, I came across [Script to get the (short) installed app list similar to Ubuntu Software Center?]("http://askubuntu.com/q/33984/25656"). I found **zcat** (new to me) in [one of the answers]("http://askubuntu.com/a/33990/25656").

I then played around with things ...

First, I used zcat to get the full uncompressed contents of /var/log/apt/history.log*gz and history.log into one file, allhistory.log

```
cd /var/log/apt && cat history.log > ~/Desktop/allhistory.log && zcat history.log*gz >> ~/Desktop/allhistory.log && cd
```

Next, I used
```
sed -r -i.bak '/(^Upgrade: |^End-Date: |^Install: |^Purge: |^Error: |^Remove: |^Commandline: apt-get purge|^Commandline: apt-get --yes --no-install-recommends|^Commandline: apt-get autoremove|^Commandline: apt-get dist-upgrade)/d' allhistory.log
``` to clean up things.

Then, I ran 
```
sed -i.bak '/^Start-Date:/ {N; /\n$/d}' allhistory.log
``` to remove lines beginning with "Start-Date:" if they are followed by a blank line based on advice [here]("http://unix.stackexchange.com/a/100784/15760").
and
```
sed -r -i.bak '/Start-Date:/{N; s/\n/\t/}' allhistory.log
``` to merge lines.

The output now looks like this:
```

Start-Date: 2013-11-07  22:31:45	Commandline: apt-get install mousepad

Start-Date: 2013-11-09  18:26:02	Commandline: apt-get install lib32z1

Start-Date: 2013-11-09  18:27:38	Commandline: apt-get install lib32bz2-1.0

Start-Date: 2013-11-09  18:38:53	Commandline: apt-get install lib32ncurses5

Start-Date: 2013-11-10  08:12:50	Commandline: apt-get install lib32stdc++6

Start-Date: 2013-11-11  07:43:49	Commandline: apt-get install --no-install-recommends catfish

Start-Date: 2013-10-17  23:00:06	Commandline: apt-get install shimmer-themes

Start-Date: 2013-10-17  23:01:52	Commandline: apt-get install --no-install-recommends gedit

Start-Date: 2013-10-17  23:02:42	Commandline: apt-get install gedit-plugins

Start-Date: 2013-10-17  23:03:32	Commandline: apt-get install medit

Start-Date: 2013-10-18  00:13:39	Commandline: apt-get install xxxterm

``` I know I can clean things up a bit more and sort by date but that's how far I've got now. I'll see about not removing lines with "purge" in them.

I realize that this is quite limited because I'm using only apt-get and not Synaptic or the Lubuntu Software Center to manage software.

---

