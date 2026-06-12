---
title: "Need to access ubuntu remotely - installed but no access to display"
date: 2021-05-27
forum: General Help
---

### Post by robert71 on 2021-05-27
Hi Guys, 

           I need some help setting up Ubuntu so that when it boots up it automatically enables SSH, RDP and VNC. 

I have a raspberry Pi 4 that I installed Ubuntu on and cant access it over the network because upon install remote protocols seem disabled. 

I flashed the install to a SD Card reader and then put it n my Pi. after installation my Micro HDMI adapter to HDMI started failing and now i cant access it via display. 

Thing is on the Pi there is only micro HDMI. Because of Covid restrictions in my country all electronic stores are closed and i cannot purchase a Micro HDMI to HDMI adapter or order online (Couriers are shut down as well) 

I can put the SD card in a SD Card reader and access it on my laptop. 

Can someone help me to make the necessary changes to config files etc so that when i put it back in my raspberry Pi i can access it remotely? 

i know the ip address it will have when it boots up

thanks

---

### Post by HermanAB on 2021-05-27
You probably only need one of SSH, RDP or VNC and can do anything with SSH, so get that to work first.  

RDP and VNC are MS Windows compatibility things which are not needed when working with RaspPis from a Linux machine.

---

### Post by robert71 on 2021-05-27
[COLOR=#000000]"You probably only need one of SSH, RDP or VNC and can do anything with SSH, so get that to work first."[/COLOR]

Sure thing but how do i get access to SSH. is there a config file i can edit ???

---

### Post by ActionParsnip on 2021-05-28
Just run
```

sudo apt install openssh-server

```
You will now be able to access the system using your favourite SSH client.
Why do you want to access the full desktop on the remote system? What will you be doing on the desktop that needs the full desktop once you connect via VNC or RDP? There may be a sleeker solution to what you want to achieve

---

### Post by ajgreeny on 2021-05-28
> **robert71 said:**
> [COLOR=#000000]"You probably only need one of SSH, RDP or VNC and can do anything with SSH, so get that to work first."[/COLOR]

Sure thing but how do i get access to SSH. is there a config file i can edit ???
To answer your specific question, yes, there is a config file for the ssh server; it's at ***/etc/ssh/sshd_config***.
It is a plain text file, like many linux config files, and there are several changes you can, and perhaps should, make to it.

All the details are at [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring) which is definitely worth reading carefully.

---

### Post by ActionParsnip on 2021-05-28
The defaults in the sshd_config file are fairly sane and OK

---

### Post by ajgreeny on 2021-05-29
> **ActionParsnip said:**
> The defaults in the sshd_config file are fairly sane and OK
But not as secure as they could be.

For example, it is a great deal better to disable passwords to connect and always use the private/public key authentication that makes things a lot more secure.

---

### Post by robert71 on 2021-05-30
> [COLOR=#000000][INDENT]All the details are at [https://help.ubuntu.com/community/SS...SH/Configuring]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring") which is definitely worth reading. [COLOR=#222222][/COLOR][/INDENT]
[/COLOR]


So i read through this documentation and what i gather is that i need to edit  

/etc/ssh/sshd_config

problem is that i dont have this file. in my /etc/ssh directory there is a folder called sshd_config

Any ideas what to do here ?

---

### Post by HermanAB on 2021-05-30
On most UNIXes:
$ sudo vi /etc/ssh/sshd_config

If you have a directory there, see what is in it:
$ sudo ls /etc/ssh/sshd_config

then edit whatever you found:
$ sudo vi /etc/ssh/sshd_config/whatever

---

### Post by robert71 on 2021-05-30
Hi HermanAB,

 Thanks for your response but the directory is empty there are no files there. 

Should I just create a file called sshd_config ?

---

### Post by TheFu on 2021-05-30
If the file doesn't exist, something failed during the installation of that package.

Run 
```
sudo apt install ssh fail2ban
```

ssh is a meta-package that includes both an ssh client and the ssh-server.  That also includes scp, sftp, ssh-keygen and ssh-copy-id - these are all helpful.

fail2ban will block brute force attempts after 3 or 5 failures. The blocking is for port 22/tcp which is the default for ssh. A failed source IP will be blocked for an hour, I think. This is a reasonable initial stance for ssh security.

That should be enough for a LAN client to connect to a LAN server over ssh.  Best if the LAN server has a static IP.  On a r-pi, I use DHCP reservations to keep my r-pi at the same IP, always.  But you can learn netplan YAML if you like.

Obviously, if you've enabled any firewall rules to block all inbound connections, then those will need to be relaxed for ssh.

Obviously, if you want to connect to this system over the internet, then the WAN router will need a port opened. Best for it NOT to be port 22, since that will be hit 100,000x a day by attackers.  I use port translation to listen on a non-standard port on the WAN, forward those connections to the static IP port 22 on your r-pi where ssh listens.

And lastly, setup ssh to only allow ssh-keys for logins from the internet.  This can happen later, assuming you have a strong, random, 20 character passphrase for ssh.  ssh-keys are both more secure and much more convenient, however.   I need to post a how-to with exact commands with real-time typing for how to do these things.

---

### Post by robert71 on 2021-05-30
Unfortunately I cannot run any commands through the terminal. 

All i can do is edit files on the SD card with the the ubuntu installation. 

Which is attached to another computer using an SD card reader. 

Currently doing some research on ssh,  right now when the system boots it  gets an ip but if i try to ssh into the system it gives the error 

"SSH connection refused" 

Therefore if anyone can help me resolve this by editing config files it would be really appreciated. 

thanks

---

### Post by TheFu on 2021-05-30
You cannot enable ssh, without installing the package.  To install the package, the system needs to be running.  That means for the very first boot on the Pi (any pi of the same model can be used), you'll want to have a HDMI connection to a monitor/TV, a USB connection to both a keyboard and mouse.

I haven't had my pis connected to a physical keyboard or mouse in years.  All management is performed over ssh from other systems.  That will work for r-pi v2, v3, and v4.  I don't know about the tiny r-pi versions like a pi-zero or pi-zero-wifi. Sorry.

After the first boot and storage reconfiguration, the first commands to be run are the ones already posted in #11 above.  That will make ssh run and it will run at every reboot, automatically.

There is no way for a neophyte method to edit config files that will do what you seek. The ssh software is NOT installed in any distro automatically. Someone better at scripting could put some commands into a script, call that script via the crontab that got run at every reboot to check whether ssh it installed or not. If not, install it.  While this isn't hard, the hill is too high for all the little details to be just right for this script to work.  If you'd like to try that, go for it.  The effort in learning a little scripting will be good for anyone not trying to be in the point-n-click world. At least 2 files need to be edited/created, permissions on the script set correctly and the commands inside the script need to be specified correctly.
Hint:
**/usr/bin/apt-get install ssh fail2ban**
is the main line to be put into the script file.  The other file(s) are about the crontab and getting that script file run at each reboot.  Don't forget to check whether ssh is already installed or not.  I'd use the dpkg and egrep commands for that.

Usually, when a r-pi is first booted, it will reconfigure the storage, create partitions, and get a network address using DHCP.  I've never attempted to run Ubuntu on a Pi, but that is how Raspian works.  I wouldn't know where to begin to put a script that installs ssh and fail2ban on first boot. That is beyond my knowledge, since I don't know what the pre-boot storage looks like.

Connecting the pi at first boot to video, keyboard, and mouse - makes this all easy.  If you will be cloning the SDcard for other r-pis, then this only needs to be done once, then clone the SD card and mail them out.

But none of this will open router ports or setup static IPs on all the different subnets involved.

---

### Post by robert71 on 2021-05-30
ok im going to try to do a crontab script to install ssh and work from there cuz i dont have a mini hdmi adapter to plug the pi in to my monitor. 

Will update the thread

---

