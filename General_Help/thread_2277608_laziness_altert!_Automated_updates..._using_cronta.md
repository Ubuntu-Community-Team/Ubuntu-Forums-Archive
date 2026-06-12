---
title: "laziness altert! Automated updates... using crontab"
date: 2015-05-10
forum: General Help
---

### Post by Old Jimma on 2015-05-10
Hi Community:

:idea:

I've gotten extraordinarily lazy in my old age and decided the automatic updater required too much work for me to be happy with it, so I wrote a shell script in the file [COLOR="#FF0000"]**update.sh**[/COLOR]:

> 
#!/bin/sh 
# 
apt-get  update
#


I made [COLOR="#FF0000"]**update.sh**[/COLOR] executable:

> 
sudo chmod 777 [COLOR="#FF0000"]**update.sh**[/COLOR]


and then I added the following line to my superuser crontab:

> 
30 15 * * 0,1,2,3,4,6 /PATH/[COLOR="#FF0000"]**update.sh**[/COLOR] > /PATH/[COLOR="#FF0000"]**update.log**[/COLOR] > /dev/null 2>&1


I thought this would do automatic updates, but the automatic updater is still doing its thing, and requires my intervention to make it work.

:-({|=

How do I get my shell script to work so that my system is updated everyday?

Thanks!
Old Jimma

---

### Post by mcduck on 2015-05-10
*"apt-get update"* will only check the information about available packages and versions from the repositories. So it'll allow the package manager to know what updates might be available, but not actually update any packages. You also need to run *"apt-get upgrade"* or *"apt-get dist-upgrade"* to actually install the updates.

edit: Also might be worth mentioning that there is already a mechanism for automatic updates: [https://help.ubuntu.com/lts/serverguide/automatic-updates.html]("https://help.ubuntu.com/lts/serverguide/automatic-updates.html")

---

### Post by Lars Noodén on 2015-05-10
A good place to keep the script would be /usr/local/sbin

Then the permissions ought to be set so that it is not writable by others.  755 would be good.

In the crontab entry you seem to have two redirects > where only one at a time works.  

As mentioned by mcduck, update just refreshes the database of available packages.  If you really want it to install then use 'upgrade' and since it's to be run unattended, use the [-y option](http://manpages.ubuntu.com/manpages/trusty/en/man8/apt-get.8.html) to answer 'yes' to most questions.

```

apt-get update && apt-get -y upgrade

```

That will still leave the kernels and a few other things requiring manual intervention with 'apt-get dist-upgrade', but that is probably good since those need a reboot for the time being.

---

### Post by Old Jimma on 2015-05-11
I'm gratful for mcduck and Lars reply!

I used the automatic update feature and will monitor it to see how it works!

Many Thanks!
Old Jimma

---

### Post by ian-weisser on 2015-05-11
apt *already* has it's own daily update/upgrade job. No need to duplicate it.

The daily cron job is at /etc/cron.daily/apt. Don't edit it unless you know what you are doing.
Instead, edit the apt config files at /etc/apt/apt.conf.d/

Example: Here's a part of /etc/apt/apt.conf.d/50unattended-upgrades:
```
// Automatically upgrade packages from these (origin:archive) pairs
Unattended-Upgrade::Allowed-Origins {
        "${distro_id}:${distro_codename}-security";
//      "${distro_id}:${distro_codename}-updates";
//      "${distro_id}:${distro_codename}-proposed";
//      "${distro_id}:${distro_codename}-backports";
};

```
You can see that -security is enabled (not commented out). That's how Ubuntu can run security updates in the background without prompting you.
To do other updates the same way, simply uncomment the -updates line.
To to backports the same way, simply uncomment the  -backports line.
You can add PPA and other Non-Ubuntu lines to the section, too...but that may not be a great idea.

---

