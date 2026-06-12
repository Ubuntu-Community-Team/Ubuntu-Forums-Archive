---
title: "Disabling IPV6 does not hold after reboot"
date: 2015-08-30
forum: General Help
---

### Post by feartheterrapin on 2015-08-30
I want to disable IPV6 for VPN connections.  I modified /etc/sysctl.conf to include the following lines:
 ```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
``` 

I then run:
```
sudo sysctl -p
``` 
 Test my IPV6 using:
```
http://ipv6leak.com 
```

 No IPV6 leaks are detected.   
 
 I reboot and re-check at "[http://ipv6leak.com"]("http://ipv6leak.com/") and leaks are detected.  I need to run “sudo sysctl -p” again and no leaks are detected.

  Is there a better way to disable IPV6 that holds after reboot?

---

### Post by JKyleOKC on 2015-08-30
If you add your "sysctl -p" command to the "/etc/rc.local" file, just above the line that reads "exit 0" near the end of the file, that will run automagically at the end of the boot process. Since rc.local runs with full root privilege at that point, the "sudo" is not only not needed but actually would prevent the command from running.

---

### Post by feartheterrapin on 2015-08-30
> **JKyleOKC said:**
> If you add your "sysctl -p" command to the "/etc/rc.local" file, just above the line that reads "exit 0" near the end of the file, that will run automagically at the end of the boot process. Since rc.local runs with full root privilege at that point, the "sudo" is not only not needed but actually would prevent the command from running.

That did not work.

My rc.local looks like:
```
sysctl -p
exit 0
```
Everything else is commented out.

My sysctl looks like:
```
#disable ipv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```

I just noticed the comment in the rc.local file:  "In order to enable or disable this script just change the execution bits."  Is there something else I need to do?

---

### Post by JKyleOKC on 2015-08-30
It's possible that /etc/local's permissions do not include the execution bit. Normally, its properties on the permissions tab should include toward the bottom of the dialog a checkbox saying "allow this file to run as a program" and it should be checked.

However, at the time rc.local is executed, the PATH environment variable will not be set to the same one used after you log in; it's best practice to use full absolute paths to commands such as "sysctl" in this file, to assure that they are found at boot time. At a command prompt, use "which sysctl" to get the full absolute path and add it to your command. Here, that would be "/sbin/sysctl" but it might be different on your system.

---

### Post by pqwoerituytrueiwoq on 2015-08-30
you can disable it from grub also in [FONT=courier new]/etc/default/grub[/FONT]
[FONT=courier new]ipv6.disable=1[/FONT]
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ipv6.disable=1"
```
just be sure to run update-grub after making the change

---

### Post by feartheterrapin on 2015-08-31
> **JKyleOKC said:**
> It's possible that /etc/local's permissions do not include the execution bit. Normally, its properties on the permissions tab should include toward the bottom of the dialog a checkbox saying "allow this file to run as a program" and it should be checked.

However, at the time rc.local is executed, the PATH environment variable will not be set to the same one used after you log in; it's best practice to use full absolute paths to commands such as "sysctl" in this file, to assure that they are found at boot time. At a command prompt, use "which sysctl" to get the full absolute path and add it to your command. Here, that would be "/sbin/sysctl" but it might be different on your system.

Still no success.

"allow this file to run as a program" is checked.

Complete rc.local listed below:

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
/sbin/sysctl -p
exit 0
```

---

### Post by feartheterrapin on 2015-08-31
> **pqwoerituytrueiwoq said:**
> you can disable it from grub also in [FONT=courier new]/etc/default/grub[/FONT]
[FONT=courier new]ipv6.disable=1[/FONT]
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ipv6.disable=1"
```
just be sure to run update-grub after making the change

I will try this later today after exhausting my efforts with rc.local and reverting rc.local & sysctl.conf to original state.

---

### Post by feartheterrapin on 2015-08-31
> **pqwoerituytrueiwoq said:**
> you can disable it from grub also in [FONT=courier new]/etc/default/grub[/FONT]
[FONT=courier new]ipv6.disable=1[/FONT]
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ipv6.disable=1"
```
just be sure to run update-grub after making the change

That worked.

---

