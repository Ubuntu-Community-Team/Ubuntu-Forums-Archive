---
title: "Installing NVIDIA drivers on Ubuntu 12.04 AWS EC2 instance for Tesla M2050"
date: 2013-04-04
forum: General Help
---

### Post by spidercat on 2013-04-04
Hi all,

I hope someone can help me with this.  I have searched numerous forums and spent several days trying to solve this and still haven't been able to find a solution.

I am trying to install the NVIDIA drivers on an Amazon Cluster GPU instance (cg1) which has 2 x NVIDIA Tesla “Fermi” M2050 GPUs.  I launched a Ubuntu Server 12.04 for Clusters instance, connected to the instance using PuTTY SSH and carried out the following steps:

1. Install the NVIDIA driver:
```
sudo -s
apt-add-repository ppa:ubuntu-x-swat/x-updates
apt-get upgrade
reboot
```

log in again

```
sudo -s
apt-get update
apt-get purge nvidia*
apt-get install nvidia-current
apt-get install  nvidia-settings
```

2. Install ubuntu desktop and vncserver:

```
apt-get update
apt-get install ubuntu-desktop
apt-get install vnc4server
exit
```

3. Configure the VNC xstartup file:

```
vncserver
vncserver -kill :1
vim .vnc/xstartup
```

Deleted the pound (#) sign from the beginning of the two  lines under the line that says "Uncomment the following two lines for  normal desktop." And on the second line added "sh" so the line reads:

exec sh /etc/X11/xinit/xinitrc

Saved and closed the file

4. Start the VNC server again by entering:

```
vncserver
```

5. Connected to the AWS instance using TigerVNC

When connected I can see that the driver is installed under Additional Drivers:

[ATTACH=CONFIG]240933[/ATTACH]

But when I try to open the NVIDIA X Server Settings I get the following message telling me that I am not using the NVIDIA X driver:

[ATTACH=CONFIG]240934[/ATTACH]

I have tried the following but the message still comes up (after restarting the X server and rebooting):

```
sudo nvidia-xconfig
```
and
```
sudo nvidia-xconfig -a --use-display-device=None --virtual=1280x1024
```

Does anyone know what I need to do?

Ultimately I would like to install VirtualGL on the AWS instance but for now I'm not sure I have installed the NVIDIA drivers correctly.

Many thanks!

---

### Post by spidercat on 2013-04-04
I'm sure someone must have done this before?!

---

### Post by conradin on 2013-04-04
64 bit nvidia driver:
us.download.nvidia.com/XFree86/Linux-x86_64/310.44/NVIDIA-Linux-x86_64-310.44.run
not sure what youre doing with the vnc server, installing it remotely?
anyhow, if you use the script youll need to not be running X, or any graphical stuff. 
you might also have to mark that script as executable.

I try to use manufacturers drivers whenever possible, NVidia usually has decent support.

---

### Post by spidercat on 2013-04-05
Hi Conradin

Thanks very much for the response.

Based on your reply I tried the following procedure, this time on a new Ubuntu 12.04 64 bit, cg1 Cluster AWS instance.

1. Installed ubuntu desktop and vncserver:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo apt-get install vnc4server
```

2. Configured the VNC xstartup file:

```
vncserver
vncserver -kill :1
vim .vnc/xstartup
exit

```

Deleted the pound (#) sign from the beginning of the two lines under the line that says "Uncomment the following two lines for normal desktop." And on the second line added "sh" so the line reads:

exec sh /etc/X11/xinit/xinitrc

Saved and closed the file

3. Download and install the NVIDIA driver:

```
wget http://us.download.nvidia.com/XFree86/Linux-x86_64/310.44/NVIDIA-Linux-x86_64-310.44.run
sudo chmod 0755 *.run
sudo ./NVIDIA-Linux-x86_64-310.44.run
```

4. Created the xorg.conf file:

```
sudo nvidia-xconfig
sudo reboot
```

5. When machine had restarted, connected via PuTTY SSH and started the VNC server again by entering:

```
vncserver
```

6. Connected to the AWS instance using TigerVNC

Unfortunately I still get the error regarding not using the NVIDIA X driver..  Is this some kind or permissions problem?  I get the feeling I am missing something...



Many thanks

---

### Post by spidercat on 2013-04-05
I have also just noticed that the nvidia drivers are no longer listed in the Additional Drivers system settings:
[ATTACH=CONFIG]240977[/ATTACH]

---

