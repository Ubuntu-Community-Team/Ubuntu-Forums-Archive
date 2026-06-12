---
title: "Can't Get ssh Working Between My MacAir and Linux Box"
date: 2020-04-12
forum: General Help
---

### Post by o2b on 2020-04-12
Hi,

I have spent a lot of time trying to get ssh working between my MacAir and Ubuntu server (18.04.4 LTS) and i think the issue is an address is changing.  Here is some information:

[COLOR=#000000][FONT=&amp][FONT=&amp]Mac User@hostame &#8211; [EMAIL="mirkwood@luthien.local"]mirkwood@luthien.local[/EMAIL][/FONT][/FONT][/COLOR]

[COLOR=#000000][FONT=&amp][FONT=&amp]Mac &#8211; known_hosts[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]radagast,**23.202.231.171** ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBMFolSO2zM712VJgxheswDiNc7g/NuOQ7eNpHwR4yOR5kfMaT3HBKx/RvZncr3pHI1IzDvMWmnGbvhOIvK+/cYo=[/COLOR][/FONT][/COLOR]

[COLOR=#000000][FONT=&amp][COLOR=windowtext]Note especially the 23.202.231.171[/COLOR][/FONT][/COLOR]

[COLOR=#000000][FONT=&amp][COLOR=windowtext]Linux User@hostname &#8211; tony@radagast[/COLOR][/FONT][/COLOR]

[COLOR=#000000][FONT=&amp][COLOR=windowtext]Linux &#8211; known_hosts[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]radagast,**23.202.231.171** ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBMFolSO2zM712VJgxheswDiNc7g/NuOQ7eNpHwR4yOR5kfMaT3HBKx/RvZncr3pHI1IzDvMWmnGbvhOIvK+/cYo=[/COLOR][/FONT][/COLOR]

[COLOR=#000000][FONT=&amp][COLOR=windowtext](same as what Mac has for Linux box).

Mac known_hosts also has 23.202.231.171[/COLOR][/FONT][/COLOR]

[COLOR=#000000][FONT=&amp][COLOR=windowtext]Mac Attempted ssh Into Linux[/COLOR][/FONT][/COLOR]

[COLOR=#000000][FONT=&amp][COLOR=windowtext]bash-3.2$ ssh tony@radagast[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]@       WARNING: POSSIBLE DNS SPOOFING DETECTED!          @[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]The ECDSA host key for radagast has changed,[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]and the key for the corresponding IP address **23.195.69.110**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]is unknown. This could either mean that[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]DNS SPOOFING is happening or the IP address for the host[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]and its host key have changed at the same time.[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY![/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]Someone could be eavesdropping on you right now (man-in-the-middle attack)![/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]It is also possible that a host key has just been changed.[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]The fingerprint for the ECDSA key sent by the remote host is[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]SHA256:N6nq+xrVIcIOXvSbLuHe6eTXIKPMpbTEJ16Rj3OrDTk.[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]Please contact your system administrator.[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]Add correct host key in /Users/mirkwood/.ssh/known_hosts to get rid of this message.[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]Offending ECDSA key in /Users/mirkwood/.ssh/known_hosts:1[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]ECDSA host key for radagast has changed and you have requested strict checking.[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]Host key verification failed.[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]bash-3.2$[/COLOR][/FONT][/COLOR]

[COLOR=#000000][FONT=&amp][COLOR=windowtext]Especially:[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]The ECDSA host key for radagast has changed,[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]and the key for the corresponding IP address **23.195.69.110**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][COLOR=windowtext]is unknown.[/COLOR][/FONT][/COLOR]

[COLOR=#000000][FONT=&amp][COLOR=windowtext]1. Where did 23.202.231.171 come from?[/COLOR][/FONT][/COLOR]

[COLOR=#000000][FONT=&amp][COLOR=windowtext]2. Where did 23.195.69.110 come from?[/COLOR][/FONT][/COLOR]

[COLOR=#000000][FONT=&amp][COLOR=windowtext]3. Why did Mac ssh command return 23.195.69.110 rather than 23.202.231.171?


If anyone can lend a hand, I'd sure appreciate it!


o2b[/COLOR][/FONT][/COLOR]

---

### Post by o2b on 2020-04-12
Oh, I can ssh in from Ubuntu to Mac, just not from Mac to Ubuntu.

---

### Post by o2b on 2020-04-19
I have a friend who is a Senior Linux Administrator help me.  It turns out Ubuntu 18.04 LTE is not ready for ssh as is.

He figured it out, but I could have done a simple search - "How to set up ssh on Ubuntu 18.04."

[https://linuxize.com/post/how-to-enable-ssh-on-ubuntu-18-04/](https://linuxize.com/post/how-to-enable-ssh-on-ubuntu-18-04/)

**Enabling SSH on Ubuntu**

[COLOR=#2D3748][FONT=Roboto]The SSH server is not installed by default on Ubuntu desktop systems but it can be easily installed from the standard Ubuntu repositories.[/FONT][/COLOR]
[COLOR=#2D3748][FONT=Roboto]To install and enable SSH on your Ubuntu system complete the following steps

[/FONT][/COLOR]1. Open your terminal either by using the Ctrl+Alt+T keyboard shortcut or by clicking on the terminal icon and install the openssh-server package by typing:

sudo apt install openssh-server
Enter the password when prompted and enter Y to continue with the installation.

2. Once the installation is completed, the SSH service will start automatically. To verify that the installation was successful and SSH service is running type the following command which will print the SSH server status:

sudo systemctl status ssh

You should see something like Active: active (running) :

3. Ubuntu comes with a firewall configuration [COLOR=#1A75FF]tool[/COLOR] called UFW. If the firewall is enabled on your system, [COLOR=#1A75FF]make sure[/COLOR] to open the SSH port.

sudo ufw allow ssh

That's it!

o2b

---

