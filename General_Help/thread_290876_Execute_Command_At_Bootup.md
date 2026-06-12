---
title: "Execute Command At Bootup"
date: 2006-11-01
forum: General Help
---

### Post by OffHand on 2006-11-01
Hi guys,

I'm looking for a way to automatically execute this command at bootup:
```
sudo rm /etc/vmware/not_configured
```

Anyone?

---

### Post by sefs on 2006-11-01
One way is possible to put the command in a bash script (saved anywhere in your home dir would do i think.) and run it from with in the startup programs area of the sessions dialog box.

```

#!/bin/sh
sudo rm /etc/vmware/not_configured

```

you could save the above to "vmwarenotconfigured.sh" for instance.

One thing though is you will be prompted for a password, which you can probably get around by modifying your sudoes list to suit.  What I do not know is if that is a security risk or not to do that.

---

### Post by OffHand on 2006-11-02
Hey sef,
Thanks for your reply but I am looking for a way to do it automatically at
startup. So if anyone know how I could achieve this I would be happy to know.

---

### Post by Rumo on 2006-11-02
You can add it at the end of your /etc/profile file.

---

### Post by OffHand on 2006-11-02
> **Rumo said:**
> You can add it at the end of your /etc/profile file.

That didn't work unless I did it wrong. This is my /etc/profile file:
```

# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022

#!/bin/sh
sudo rm /etc/vmware/not_configured

```

---

### Post by epennings on 2006-11-02
you can add the command to /etc/rc.local :

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[COLOR="RoyalBlue"]sudo rm /etc/vmware/not_configured[/COLOR]
exit 0
```

edit : i think sudo isn't required. try removing it and see if it works.

---

### Post by OffHand on 2006-11-02
> **epennings said:**
> you can add the command to /etc/rc.local :

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[COLOR="RoyalBlue"]sudo rm /etc/vmware/not_configured[/COLOR]
exit 0
```

edit : i think sudo isn't required. try removing it and see if it works.
Unless I made a mistake this didn't work either:
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# start hddtemp daemon
echo "   --> Starting hddtemp daemon for /dev/hda ..."
/usr/sbin/hddtemp --daemon --listen="127.0.0.1" /dev/sda
exit 0
sudo rm /etc/vmware/not_configured
exit 0

```

EDIT: without sudo it didn't work either.

---

### Post by OffHand on 2006-11-02
Ok, I fixed the issue for which I need the startup command.

The issue was that /etc/vmware/not_configured was re-created after eacht reboot. 

I found the following solution:

VMware need to re-run vmware-config.pl every reboot on linux
I found using VMware server or workstation on udev based linux kernel (2.6.x) hosts, that I had to re-run the vmware-config.pl script after every reboot - which is quite annoying when you want the guest OS to run as the service starts.

The issue is that due to udev being a dynamic system, nodes are wiped and re-created in /dev each boot. So the simple solution is to get the VMware init script to check for and re-create the nodes as required:

Add the following just under the start) line in /etc/init.d/vmware

# Start insert
      if [ ! -e "/dev/vmmon" ]; then
         mknod /dev/vmmon c 10 165
         chmod 600 /dev/vmmon
      fi
      for a in `seq 0 9`; do
         if [ ! -e "/dev/vmnet$a" ]; then
            mknod /dev/vmnet$a c 119 $a
            chmod 600 /dev/vmnet$a
         fi
      done
# End insert
      if [ -e "$vmware_etc_dir"/not_configured ]; then

Which recreates the nodes that are required - just need VMware to pick that up for future versions. Remember, you'll still need to re-run vmware-config.pl after a kernel upgrade. 

Source: [http://jeremy.co-comp.co.uk/archives/6-VMware-need-to-re-run-vmware-config.pl-every-reboot-on-linux.html](http://jeremy.co-comp.co.uk/archives/6-VMware-need-to-re-run-vmware-config.pl-every-reboot-on-linux.html)

P.S. I had to log in as a root with sudo su and use nano instead of gedit before I was able to change the file mentioned.

---

