---
title: "Assist with command to confirm I've turned off daily unattended upgrades"
date: 2020-04-11
forum: General Help
---

### Post by greavette on 2020-04-11
Hello,

I'm using the following command to determine if Unattended Upgrades are enabled on my servers:

```
python -mplatform | grep -qi Ubuntu && OPT=0;RES=$(apt-config shell OPT APT::Periodic::Unattended-Upgrade);eval $RES;echo $OPT 2  / 2>&1 | grep -qi '1' ; case "$?" in "0") echo "unattended upgrades are enabled" ;; "1") echo "unattended upgrades are not enabled" ;; esac
```

And I'm using this command to determine if the apt-daily task  is enabled to download and install security updates daily:

```
systemctl status apt-daily{,-upgrade}.{timer,*********
```

My task is to turn off apt-daily so that unattended upgrades are not automatically installed daily.  I will issue a command for unattended upgrades to install security patches only during an agreed upon time with the server owners.  

The command I would use to turn off apt-daily is:

```
systemctl disable --now apt-daily{,-upgrade}.{timer,*********
```

Once apt-daily is turned off I will issue the command above to check the status of apt-daily.  This is to confirm that apt-daily has been disabled.  Here is the result of apt-daily status after it has been disabled:

```
apt-daily.timer - Daily apt download activities
Loaded: loaded (/lib/systemd/system/apt-daily.timer; disabled; vendor preset: enabled)
Active: inactive (dead)
```

What I'm looking to do is to run this "systemctl status apt-daily{,-upgrade}.{timer,*********" command and only look for the "Active: Inactive (dead)" reply back from the "Daily apt download activities" section of the reply.  My thought was to pipe the "systemctl status apt-daily{,-upgrade}.{timer,*********" results to /dev/null and then grep these results but I'm unsure how to do this correctly and return a reply that the status is Inactive and not Running.

Any pointers or assistance in how I would form this one-line command to get what I need would be greatly appreciated.  

Thank you.

---

### Post by TheFu on 2020-04-12
Not the answer you seek, but a different solution.

i usually just purge the packages responsible. Let me check my Ansible scripts.
```
- name: Purge Update Notify
  action: apt pkg=update-notifier state=absent purge=yes
```

That will remove the systemd-unit files, anacron stuff, and prevent being bothered on servers.

---

