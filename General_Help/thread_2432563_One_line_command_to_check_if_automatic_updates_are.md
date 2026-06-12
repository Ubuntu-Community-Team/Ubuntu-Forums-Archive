---
title: "One line command to check if automatic updates are enabled"
date: 2019-12-04
forum: General Help
---

### Post by greavette on 2019-12-04
Hello,

I'm hoping I can use a one line command to confirm that automatic updates are enabled on ubuntu servers.  

I'm considering using this command to look for the contents of the unattended updates file:

```
cat /etc/apt/apt.conff.d/20auto-upgrades | paste -sd \; || echo "Unattended Upgrades not installed"
```

Or perhaps this command is better to confirm the file exists (meaning if it doesn't exist then unattended upgrades is not installed):

```
[[ -f /etc/apt/apt.conf.d/20auto-upgrades ]] && echo "unattended updates are enabled" || echo "unattended updates are not enabled";
```

But are automatic updates on Ubuntu only through unattended upgrades?   Are the above commands good ways to confirm (using a one line command) to check if my Ubuntu Servers will receive updates/upgrades automatically?

Thank you in advance for any advice you can provide me.

---

### Post by #&amp;thj^% on 2019-12-04
I myself like to handle these things myself, but I get the reason your wanting it this way.
The only thing that come to mind, is to check "sudo dpkg-reconfigure -plow unattended-upgrades"
edit the files:
```

/etc/apt/apt.conf.d/10periodic
/etc/apt/apt.conf.d/20auto-upgrades
```

In that file you can set how often you want the server to update.
```

APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "7";
APT::Periodic::Unattended-Upgrade "1";
```

The file should look like the above. The 1 means it will update every day. 7 is weekly.
Another way to check if automatic updates work is waiting a few days and checking the unattended upgrades logs:
```

cat /var/log/unattended-upgrades/unattended-upgrades.log
```
But I can't think of just a one liner for your needs, hope this helps.

---

### Post by Holger_Gehrke on 2019-12-04
The existence of this configuration file isn't enough to come to any conclusion since it might contain directives to switch updates OFF. There is a program for querying apt configuration named apt-config.
```

OPT=0;RES=$(apt-config shell OPT APT::Periodic::Update-Package-Lists);eval $RES;echo $OPT

```
will print "1" if apt is set to automatically update the package lists while
```

OPT=0;RES=$(apt-config shell OPT APT::Periodic::Unattended-Upgrade);eval $RES;echo $OPT

```
should give "1" if unattended upgrades are active.

Holger

---

### Post by greavette on 2019-12-04
Thanks very much 1fallen and Holger for your replies to my post.  Very much appreciate your input.  

I think the command Holger has provided will do me well.  I've modified it a bit to provide some context for me:

```
python -mplatform | grep -qi Ubuntu && OPT=0;RES=$(apt-config shell OPT APT::Periodic::Unattended-Upgrade);eval $RES;echo $OPT 2  / 2>&1 | grep -qi '1' ; case "$?" in "0") echo "unattended upgrades are enabled" ;; "1") echo "unattended upgrades are not enabled" ;; esac
```

I scan both RHEL and Ubuntu servers in my environment so I had to add a check for if the server I'm on is Ubuntu or not.  i don't think I have it quite right yet though as it seems to try and execute on my RHEL machines the apt-config code still... but it does provide for me human readable context on if a '1' is found then a message is printed to say unattended-upgrades are enabled on my Ubuntu servers.

Thanks!

---

### Post by Holger_Gehrke on 2019-12-04
```

if [ $(lsb_release -si)x=='Ubuntu'x ] ; then O=0;R=$(apt-config shell O APT::Periodic::Unattended-Upgrade);eval $R; echo -n unattended upgrades are" " ; if [ x$O==x1 ] ; then echo enabled; else echo disabled;fi;fi

```

The command lsb_release should be available on Ubuntu and RHEL both. The Option -i outputs the id of the distribution, the -s suppresses the output of headers.

Holger

---

### Post by #&amp;thj^% on 2019-12-04
@Holger here is what I get on Arch:
```

if [ $(lsb_release -si)x=='Ubuntu'x ] ; then O=0;R=$(apt-config shell O APT::Periodic::Unattended-Upgrade);eval $R; echo -n unattended upgrades are" " ; if [ x$O==x1 ] ; then echo enabled; else echo disabled;fi;fi
bash: apt-config: command not found
unattended upgrades are enabled
```
I have disabled Auto-Upgrades.

---

### Post by Holger_Gehrke on 2019-12-04
Thank you, 1fallen. Missing spaces around the comparison operators, I think. So second try:
```

if [ 'Ubuntu'x == $(lsb_release -si)x ] ; then O=0;R=$(apt-config shell O APT::Periodic::Unattended-Upgrade);eval $R; echo -n unattended upgrades are" " ; if [ x$O == x1 ] ; then echo enabled; else echo disabled;fi;fi

```
Gives me the correct output on Ubuntu; if I replace 'Ubuntu' with something else (to simulate running on a different system), I get no output; if I replace lsb_release with lsbx_release in that command (to simulate a system without that command) I get a 'command not found' error and no output; if I replace apt_config with apt_configx to simulate a strange situation (Ubuntu without apt-config ? I don't think so) I get "command not found" for apt_configx and  "unattended upgrades are disabled" (which might be right or wrong, but the error before that should clue in the clueless ...).

Holger

---

### Post by #&amp;thj^% on 2019-12-04
That works better:
```
if [ 'Ubuntu'x == $(lsb_release -si)x ] ; then O=0;R=$(apt-config shell O APT::Periodic::Unattended-Upgrade);eval $R; echo -n unattended upgrades are" " ; 
if [ x$O == x1 ] ; then echo enabled; else echo disabled;fi;fi

```
Now the OP should be somewhat satisfied.
Thanks Holger,  we value your contributions here in UF. :)

---

### Post by Dennis N on 2019-12-04
> One line command to check if automatic updates are enabled

Wow. Amazing constructs. How about looking in systemd journal?

```
dmn@Sydney-vm:~$ journalctl | grep unattended-upgrades.service | grep -i dec
Dec 02 05:46:56 Sydney-vm systemd[1]: unattended-upgrades.service: Succeeded.
Dec 04 12:09:23 Sydney-vm systemd[1]: unattended-upgrades.service: Succeeded.

```

Would this suffice?

---

### Post by Holger_Gehrke on 2019-12-04
That service is part of the back end for unattended upgrades and gets started whether unattended upgrades are active or not. It's mostly concerned with postponing a shutdown until the package system is in a defined state (the name of the python script started by the service is unattended-upgrade-shutdown ...). The work of updating and upgrading is done by apt-daily.service and apt-daily-upgrade.service (Both are one-shot services that get started by timers). Checking the journal just tells you that it's been started in the past not whether it's currently running - that would be 'systemctl status unattended-upgrades' - nor whether the other two services are configured to actually do something - that would be the commands given above.

Holger

Edit:
What version of Ubuntu is that, Dennis N ? On my XUbuntu 18.04 -- which I only reboot when an upgrade makes it necessary, so I've got several months worth of journal -- your journalctl|grep combo sits there for 2½ minutes and produces no output. The official way of filtering journal messages for a unit is the '-u' option followed by a unit name - 'journalctl -u unattended-upgrades' -- and that returns after about 4 seconds giving a screenful of messages...

---

