---
title: "Scripting problem: UPS to shutdown VirtualBox VM"
date: 2012-10-30
forum: General Help
---

### Post by Shawn67 on 2012-10-30
I am running 12.04 and recently added a CyberPower UPS to my system. At first I ran into a problem where the system was incorrectly saying the battery was critical when I plugged in the UPS. I was able to work around this with dconf-editor by setting the battery critical action to nothing.

Then I installed CyberPowers Powerpanel for Linux. I have that working and it correctly reports on the status of my UPS. Powerpanel will invoke a script when AC is disconnected as well as when the battery reaches a certain percentage.

The line in the script (/etc/pwrstatd-powerfail.sh) is:

gksu -u shawn -l -d -w vboxmanage controlvm "Windows XP" savestate

What I am stuck on is if I am in /etc and use
sudo ./pwrstatd-powerfail.sh

the script runs properly and saves the state of the virtual machine. 

However, when the script is invoked by the pwrstatd daemon the virtual machine is not being saved. I know the script itself is being run as it has an echo command that pops up a message in terminal. 

What am I doing wrong? 

Thank You,

Shawn

---

### Post by papibe on 2012-10-30
Hi Shawn67.

I'm not very familiar with Powerpanel, but I understand there's a log you can check:
```
/var/log/pwrstatd.log
```
Could you post the complete content of the file pwrstatd-powerfail.sh?

Regards.

---

### Post by CharlesA on 2012-10-30
> **Shawn67 said:**
> 
gksu -u shawn -l -d -w vboxmanage controlvm "Windows XP" savestate

Use sudo not gksu. Also the true test would be to see if it is being run by root or as a certain user, who might not have sudo rights.

*digs thru shutdown script*

```

VBOXUSER=shawn
SU="sudo -H -u $VBOXUSER"
VBOXMANAGE="/usr/bin/VBoxManage --nologo"
$SU $VBOXMANAGE controlvm "Windows XP" savestate

```

If you don't want to do it that way, you can combine it into one line:

```
sudo -H -u shawn /usr/bin/VBoxManage --nologo controlvm "Windows XP" savestate
```

You can find my startup and shutdown script for virtualbox here:
[http://charlesa.net/scripts/linux/virtualbox-script-ubuntu.php](http://charlesa.net/scripts/linux/virtualbox-script-ubuntu.php)

---

### Post by Shawn67 on 2012-10-30
Sure, the script is:

```
#!/bin/sh
echo "Warning: Utility power failure has occurred for a few seconds, system will be shutdown soon!" | wall

export RECEIPT_NAME
export RECEIPT_ADDRESS
export SENDER_ADDRESS
gksu -u shawn -l -d -w vboxmanage controlvm "Windows XP" savestate

#vboxmanage controlvm "Windows XP" savestate
#
# If you want to receive event notification by e-mail, you must change 'ENABLE_EMAIL' item to 'yes'.
# Note: After change 'ENABLE_EMAIL' item, you must asign 'RECEIPT_NAME', 'RECEIPT_ADDRESS', and 
# 'SENDER_ADDRESS' three items as below for the correct information.
#

# Enable to send e-mail
ENABLE_EMAIL=no

# Change your name at this itme.
RECEIPT_NAME="user name"

# Change mail receiver address at this itme.
RECEIPT_ADDRESS=user_name@company.com

# Change mail sender address at this itme.
SENDER_ADDRESS=user_name@company.com

# Execute the 'pwrstatd-email.sh' shell script
if [ $ENABLE_EMAIL = yes ]; then
   /etc/pwrstatd-email.sh
fi
```Thanks,

Shawn

---

### Post by Shawn67 on 2012-10-30
Charles,

Thank you! That seemed to do the trick.

Shawn

---

### Post by CharlesA on 2012-10-30
Outstanding. Don't forget to mark the thread as solved from thread tools at the top. :)

---

### Post by Shawn67 on 2012-10-30
Thanks again for the help. 

I just changed powerpanel to not run the script on loss of AC and instead run the script when battery capacity hits 35%. Now when I hit 35% the script runs and saves the VM state, then it waits about 25 seconds and shuts down Ubuntu. 2 minutes after the shutdown is issued the UPS turns its outlets off. 

When AC is restored the UPS waits 10 seconds and then turns on the AC outlets. The bios in the computer is set to Always turn on when AC is restored so this turns back on the server. So now the server (and the VMs) are automatically shutting down and turning back on when power changes. Perfect!

Thanks,

Shawn

---

