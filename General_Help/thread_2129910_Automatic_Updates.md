---
title: "Automatic Updates"
date: 2013-03-27
forum: General Help
---

### Post by Rytron on 2013-03-27
Hi.

I want to setup Automatic Updates for a relatives laptop.

Are all of these steps proper and safe? Also, please answer my questions in bold below.

Thanks.

**-- What does "-plow" do?**
```
sudo apt-get install unattended-upgrades
sudo dpkg-reconfigure -plow unattended-upgrades
```

Select YES when prompted.

----------

```
gksudo gedit /etc/apt/apt.conf.d/10periodic
```
Change like so. 1 means it will update every day. 7 is weekly. **-- What would 0 signify?**
**-- What do these 4 lines mean exactly?**
```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "7";
APT::Periodic::Unattended-Upgrade "1";
```

----------

gksudo gedit /etc/apt/apt.conf.d/50unattended-upgrades
Then edit file and uncomment lines as shown.
**-- What do these 2 lines mean exactly?**
```
"${distro_id}:${distro_codename}-security";
"${distro_id}:${distro_codename}-updates";
```

To auto remove unneeded packages, edit line at file end like so:
**--Is this necessary?**
```
Unattended-Upgrade::Remove-Unused-Dependencies "true";
```

---

### Post by schragge on 2013-03-27
> **Rytron said:**
> 
**-- What does "-plow" do?** Also ask low-priority questions that usually don't get asked during install. See [dpkg-reconfigure(8)]("http://manpages.ubuntu.com/manpages/precise/en/man8/dpkg-reconfigure.8.html"). Usually not needed when running *dpkg-reconfigure* from command-line as it defaults to *--priority=low* in this case. Note that default priority may be changed in [debconf.conf]("http://manpages.ubuntu.com/manpages/precise/en/man5/debconf.conf.5.html").

> **Rytron said:**
> **-- What would 0 signify?** 0=disable. See [/usr/share/doc/apt/examples/configure-index.gz]("http://bazaar.launchpad.net/~ubuntu-core-dev/apt/ubuntu/view/head:/doc/examples/configure-index")

> **Rytron said:**
> **-- What do these 4 lines mean exactly?** Again, see [/usr/share/doc/apt/examples/configure-index.gz]("http://bazaar.launchpad.net/~ubuntu-core-dev/apt/ubuntu/view/head:/doc/examples/configure-index")

> **Rytron said:**
> **-- What do these 2 lines mean exactly?**See comments in [/etc/apt/apt.conf.d/50unattended-upgrades]("http://bazaar.launchpad.net/~ubuntu-core-dev/unattended-upgrades/ubuntu/view/head:/data/50unattended-upgrades.Ubuntu")

> **Rytron said:**
> **--Is this necessary?** It's optional, but it makes your system tidier as it removes unneeded cruft.

---

### Post by Slim Odds on 2013-03-27
man apt-get

You can use cron and the -y option

---

### Post by Rytron on 2013-03-29
> **Slim Odds said:**
> man apt-get

You can use cron and the -y option

Hi Slim Odds. Please elaborate.

---

### Post by Rytron on 2013-03-29
> **schragge said:**
> 

...

Again, see [/usr/share/doc/apt/examples/configure-index.gz]("http://bazaar.launchpad.net/~ubuntu-core-dev/apt/ubuntu/view/head:/doc/examples/configure-index")

See comments in [/etc/apt/apt.conf.d/50unattended-upgrades]("http://bazaar.launchpad.net/~ubuntu-core-dev/unattended-upgrades/ubuntu/view/head:/data/50unattended-upgrades.Ubuntu")

...



Hi schragge.

Could you explain the 6 lines in plain English? Those links are not very clear.

Thanks. ;)

---

### Post by btindie on 2013-03-29
> **Rytron said:**
> Hi Slim Odds. Please elaborate.
As he said, take a look at the man page for the apt-get command:
> -y, --yes, --assume-yesAutomatic yes to prompts; assume "yes" as answer to all prompts and
run non-interactively. If an undesirable situation, such as
changing a held package, trying to install a unauthenticated
package or removing an essential package occurs then apt-get will
abort. Configuration Item: APT::Get::Assume-Yes.
Which means it'll work non-interactively and can thus be scheduled via cron.

---

### Post by schragge on 2013-03-29
> **Rytron said:**
> Could you explain the 6 lines in plain English?
From [/usr/share/doc/apt/examples/configure-index.gz](http://bazaar.launchpad.net/~ubuntu-core-dev/apt/ubuntu/view/head:/doc/examples/configure-index):
> 
  // control parameters for cron jobs by /etc/cron.daily/apt
  Periodic
  {
...
    Update-Package-Lists "0";
    // - Do "apt-get update" automatically every n-days (0=disable)
    //
    Download-Upgradeable-Packages "0";
    // - Do "apt-get upgrade --download-only" every n-days (0=disable)
    //
    Unattended-Upgrade "0";
    // - Run the "unattended-upgrade" security upgrade script
    //   every n-days (0=disabled)
    //   Requires the package "unattended-upgrades" and will write
    //   a log in /var/log/unattended-upgrades
    //
    AutocleanInterval "0";
    // - Do "apt-get autoclean" every n-days (0=disable)
...
  };
 Sorry, I'm afraid I cannot explain it better. As to the meaning of *-security* and *-updates* in the second link, see [uhelp]community/Repositories#A_Quick.2C_Tongue-in-cheek_Description_of_the_Ubuntu_Repositories[/uhelp] and [uhelp]community/UbuntuUpdates[/uhelp].

---

### Post by Rytron on 2013-03-29
Cheers schragge.

I appreciate your help.

---

### Post by Rytron on 2013-04-11
Is this a good method?

From: [http://askubuntu.com/questions/45797/fully-automatic-updates-in-kubuntu](http://askubuntu.com/questions/45797/fully-automatic-updates-in-kubuntu)

[I]sudo dolphin

Create file named 'autoupdate' in /etc/cron.* (where * is hourly, daily, weekly, monthly depending on your preference).

Put following contents into file:

```
#!/bin/bash
apt-get update
apt-get upgrade -y
apt-get autoclean
```

Allow file to be executed via properties or by using this: sudo chmod 755 autoupdate[/I]

---

### Post by schragge on 2013-04-11
> **Rytron said:**
> Is this a good method?Different alternatives are discussed on [uhelp]community/AutoWeeklyUpdateHowTo[/uhelp]. Decide for yourself.

> sudo dolphinPlease don't do it. Instead, run```
kdesudo dolphin
```
See explanation at [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Rytron on 2013-04-14
Thanks schragge.

[http://www.psychocats.net](http://www.psychocats.net) is a great site.

Would this code as mentioned in the above setup eventually cause an automatic upgrade i.e. from Xubuntu 12.10 to 13.04? I'd rather it just kept 12.10 updated and let me manually upgrade (or more likely install from fresh) to 12.10.

```
#!/bin/bash
apt-get update
apt-get upgrade -y
apt-get autoclean
```

Here is my Software Sources - Updates tab:

---

### Post by schragge on 2013-04-14
No, this won't cause a release upgrade by itself. Moreover, even
```
apt-get dist-upgrade
``` won't, despite the name. But if you change the */etc/apt/sources.list* to point to another release, or just add lines for a newer release to this file then both *upgrade* and *dist-upgrade* will do a distribution upgrade. This is essentialy what command *do-release-upgrade* does: it changes */etc/apt/sources.list* to point to another release, then runs *apt-get* to do the actual upgrade.

---

### Post by Rytron on 2013-04-15
Thank you schragge for clarifying that.

---

### Post by Rytron on 2013-04-16
There is this directory that I can drop the below autoupdate script into: ***/etc/cron.daily***
What time of the day would that activate?

[I]```
#!/bin/bash
apt-get update
apt-get upgrade -y
apt-get autoclean
```[/I]

---

### Post by schragge on 2013-04-16
Depends on whether you have anacron installed (you usually have as part of ubuntu-desktop).
Without anacron: ```
awk '/daily/{print "at "$2":"$1}' /etc/crontab
```
With anacron: ```
awk '/daily/{print "at "$2" minutes after boot"}' /etc/anacrontab
```

---

### Post by Rytron on 2013-04-16
```
$ awk '/daily/{print "at "$2":"$1}' /etc/crontab
**at 6:25**

$ awk '/daily/{print "at "$2" minutes after boot"}' /etc/anacrontab
**at 5 minutes after boot**
```

So I just need to install anacron? I presume the "6:25" without anacron is in the morning and would be of no use.

---

### Post by schragge on 2013-04-16
You already have it installed. The file */etc/anacrontab* is installed by anacron.

---

### Post by Rytron on 2013-04-16
Thanks again schragge.  :)

---

### Post by Rytron on 2013-04-21
Would the bash script also update PPA's?

I setup the script on a secondary PC and put the script in the folder '/etc/cron.daily'. No updates are happening though. I rebooted a few times. It is running Xubuntu 12.04. Anacron is installed it should run 5 minutes after boot but it isn't. Anyone have any ideas on the problem/solution?

---

### Post by Slim Odds on 2013-04-21
> **Rytron said:**
> Would the bash script also update PPA's?

I setup the script on a secondary PC and put the script in the folder '/etc/cron.daily'. No updates are happening though. I rebooted a few times. It is running Xubuntu 12.04. Anacron is installed it should run 5 minutes after boot but it isn't. Anyone have any ideas on the problem/solution?
'apt-get update' updates from ALL repositories in /etc/apt/sources.list

How do you know what it's doing? Are you checking log files?

---

### Post by Rytron on 2013-04-22
I didn't check log files but notice that the Firefox version is v19* yet it is v20 since at least a week or 2 ago on my main updated PC. Would it make a difference if I added a .sh extension (as it is there is no extension)?

---

