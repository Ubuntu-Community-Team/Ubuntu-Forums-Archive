---
title: "Server crashes very often"
date: 2019-06-18
forum: General Help
---

### Post by aradmey on 2019-06-18
Hey, I have a server from Hetzner. Installed Ubuntu 16.04 Xenial on it and some other packages I need, but not too many.
Since the beginning, I've had issues with this server, while it was crashing every 2-3 days. Today, it started crashing every few hours.
I'm quite a beginner in the whole Ubuntu OS, so I don't really know how to fix it myself. I tried looking into the logs, but I didn't see anything suspicious in there. Also, asked them to plug a KVM console to my server so I can see the output when the server crashes, and it looked stuck on a "daily apt upgrade" schedule, so I thought that's the cause of the issue, as it stops the sockets before and then gets stuck, and so I disabled the relevant timers and services so it won't happen again.
This is how it got stuck:

[IMG]https://i.imgur.com/bfckOfl.png[/IMG]


Today, when the server crashed again, I asked them to plug a KVM again, and the output wasn't the same. It was just stuck on this:

[IMG]https://i.imgur.com/wF51gH0.png[/IMG]


I would be glad if you could help me out with this, as I really want to solve it.
Please tell me if you need me to provide you with any logs or whatever you need.

Thanks!

---

### Post by TheFu on 2019-06-18
That login screen is normal.  It is where you login. Does that not work?
Have you tried switching to a different pty? 
Or using ssh to login?

There isn't anyway we can help with clear details, please.  Not every button pressed, but the choices made in the installation.  
You installed a few packages?  How? Via apt or some other method? Did you use any PPAs? Source? .deb packages? Which ones?

Usually it takes about a year of daily used of Unix/Linux just to get good at the shell and understanding Unix terms before trying to run a server.  Seldom does Windows Server skills translate to Unix Servers. Very different philosophies in the OSes. Very different.

I'm current running about (20) 16.04.6 servers.  NONE of them crash unless there is a hardware issue.  Those are pretty obvious and show up in the system logs.  Ubuntu Servers just work, provided we don't do funky things.  It takes time to learn what NOT to do.  Unix is extremely flexible, but there is price to be paid in using that flexibility or doing things too different from the expected, normal, ways.  The only way I know to learn that is through experience and finding a mentor. 

So ... about those details.  I'll check back tomorrow.

---

### Post by aradmey on 2019-06-19
> **TheFu said:**
> That login screen is normal.  It is where you login. Does that not work?
Have you tried switching to a different pty? 
Or using ssh to login?

There isn't anyway we can help with clear details, please.  Not every button pressed, but the choices made in the installation.  
You installed a few packages?  How? Via apt or some other method? Did you use any PPAs? Source? .deb packages? Which ones?

Usually it takes about a year of daily used of Unix/Linux just to get good at the shell and understanding Unix terms before trying to run a server.  Seldom does Windows Server skills translate to Unix Servers. Very different philosophies in the OSes. Very different.

I'm current running about (20) 16.04.6 servers.  NONE of them crash unless there is a hardware issue.  Those are pretty obvious and show up in the system logs.  Ubuntu Servers just work, provided we don't do funky things.  It takes time to learn what NOT to do.  Unix is extremely flexible, but there is price to be paid in using that flexibility or doing things too different from the expected, normal, ways.  The only way I know to learn that is through experience and finding a mentor. 

So ... about those details.  I'll check back tomorrow.

Hey, thanks for getting back to me. I appreciate it.

First, the screen I showed you is from the KVM console, which was accessed when the server was inaccessible from any other method (HTTP, FTP, SSH). Also, the keystrokes in the KVM weren't responsive, just stuck at what I showed above.
About those packages, I installed most through 'apt install', but I also used rtinst (rutorrent installer), which installed some .debs and I also manually installed a .deb file myself (mergerfs).
I have a .txt file that includes all my SSH commands to get the server running as it is right now from a clean installation, I better just show it to you.

```
apt updateapt -y upgrade
apt remove -y unattended-upgrades
systemctl disable apt-daily.service
systemctl disable apt-daily.timer
systemctl disable apt-daily-upgrade.timer
systemctl disable apt-daily-upgrade.service
systemctl daemon-reload
--for ubuntu 16.04
wget https://github.com/trapexit/mergerfs/releases/download/2.27.1/mergerfs_2.27.1.ubuntu-xenial_amd64.deb
dpkg -i mergerfs_2.27.1.ubuntu-xenial_amd64.deb
--
apt install -y openbox obconf lxpanel tightvncserver gparted mergerfs


vncpasswd
vncserver :1
vncserver -kill :1
nano $HOME/.vnc/xstartup
	openbox-session & lxpanel
nano /etc/systemd/system/vncserver@.service
-- COPY TO SERVICE FILE (16.04)
[Unit]
Description=Start TightVNC server at startup
After=syslog.target network.target


[Service]
Type=forking
User=root
PAMName=login
PIDFile=/home/root/.vnc/%H:%i.pid
ExecStartPre=-/usr/bin/vncserver -kill :%i > /dev/null 2>&1
ExecStart=/usr/bin/vncserver -depth 24 -geometry 1280x800 :%i
ExecStop=/usr/bin/vncserver -kill :%i


[Install]
WantedBy=multi-user.target
--
systemctl daemon-reload
systemctl enable vncserver@1.service
systemctl start vncserver@1
systemctl status vncserver@1


// BEFORE CONTINUING - MOUNT ALL DISKS AND MERGE WITH MERGERFS!!!
// THEN - INSTALL RTINST (RUTORRENT)
wget --no-check-certificate https://raw.githubusercontent.com/arakasi72/rtinst/master/rtsetup
sudo bash rtsetup
rtinst -t
cd /var/www/rutorrent/plugins/
git clone https://github.com/Ardakilic/rutorrent-pausewebui.git pausewebui


wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
echo 'deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main' | sudo tee /etc/apt/sources.list.d/google-chrome.list
apt update
apt install -y pcmanfm deluge mkvtoolnix mkvtoolnix-gui mediainfo-gui wine-stable google-chrome-stable software-properties-common git
```

Also, I forgot to mention that I asked my server provider to run an hardware test which took more than 12 hours and showed no errors. After it kept crashing, I asked them to replace the servers, but keep the drives, though it did not help as well.

---

### Post by TheFu on 2019-06-19
You are doing lots of things I would never do. 

```
apt updateapt -y upgrade
```
is wrong.  
```
sudo apt update && sudo apt dist-upgrade 
```
are correct.

I would not use mergefs.  I would use LVM.  Actually, I wouldn't cross physical disk boundaries with a single file system. I've been burned. Experience matters. LVM is what the professionals use when ZFS isn't a good solution. Both are extremely stable and provide advanced capabilities.

I would not install a GUI nor any VNC on a "server"   That's asking to be hacked. Both compromise the security and stability of the server. Use the shell/CLI interfaces. If you must use a GUI, use something that includes strong encryption, like x2go.  In general, RDP and VNC security is a joke.

I wouldn't touch rutorrent and definitely wouldn't install .deb files from unknown, untrusted, sources through a script. I don't know where to start with this. I wouldn't touch it or rtinst.

I wouldn't setup plain FTP, ever, anywhere.  Plain FTP has ZERO security and transmits credentials without any encryption. Use secure, encrypted, key-based alternatives.

So, I think the issue is the software you've loaded from unknown/untrusted sources.  I wouldn't download anything using root. I wouldn't run any commands using the root account that weren't absolutely required to have root privilege.  I would NEVER remotely connect as root beyond the 1st connect.  If you didn't setup a userid, do that immediately. Make it sudo'able.  Ubuntu doesn't allow use of the root account directly by default, so if you are using that, it isn't a normal install.

Wipe the server.  Do a fresh server install with just **openssh-server** and **fail2ban**. Nothing else.  
Patch the box immediately (dist-upgrade), but leave it alone for 24 hrs. Bet it stays up and you can access it all that time.  If true, we've figured out the issue. Oh, and don't use passwords for ssh authentication.  Use ssh-keys. From your local Unix machine, generate the keys, then push the public key to the remote server, in the correct way.  That's just 2 commands:
```
ssh-keygen -t ed25519
ssh-copy-id -i ~/.ssh/id_ed25519.pub userid@remote
```
Test that the ssh connection works.  If it does, change the sshd_config to not allow root or any outside direct access using passwords.  It would be smart to make another userid on the remote system, also with sudo capabilities as a backup user. Give it a crazy long - 55 character password. It will be what you use via the console if networking fails. Obviously, store these things in a password manager that requires use of some hardware token to access - like a u2f device.

There are a number of critical remote attacks for Linux this week.  Some are important enough that I touched my production servers immediately.  An unpatched Linux system on the internet is asking to be hacked.  If the commands you posted are exactly correct, then your box isn't even patched. It takes less than 8 minutes for an unpatched Linux to be hacked on the internet.  Some of those attacks don't have patches yet for ubuntu - or they didn't 12 hrs ago.  There were sysctl updates to mitigate them, for now.  Running a server on the internet is a responsibility. The issues this week are the first in about 8 months that require immediate mitigation efforts.  IMMEDIATE.

I don't know if I've actually helped or not. You had a plan.  That plan was slightly sketchy and led to instability. I'm not providing a solution to your end goal, but to a stable server that doesn't do what you need. I don't do the things you seem to be attempting. 
* don't use plain FTP. Use sftp or scp or sshfs or rsync instead.
* don't use RDP/VNC without a full VPN connection. Use x2go or any of the NX protocol solutions.  x2go uses the same ssh credentials and port.
* setup a firewall that blocks all inbound connections except the ones you specifically need.  I think ssh would be the only one you need open, if you follow what I've suggested.
* BTW, with ssh running on that server, you can use it as a SOCKS proxy for all web traffic. This would mean you don't need a web browser on the remote box.  I would never load Chrome, but that is more about google tracking everything, everyone does, everywhere, than bad code.
* I cannot help with BT in any way. Sorry.

As for what are good replacements to the things you need, I'd use tools in the Canonical repos.  At least then they've been vetted *in some way*.

My 1st Five Minutes on a server: [https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)
System Maintenance For Ubuntu Desktops: [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)
ssh is amazing. Once you see what it can do; [https://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](https://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)
To learn more shell - [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  Do a chapter a week to get out of that beginner mode.

---

### Post by aradmey on 2019-06-19
Thanks for the thorough reply.
The problem is that I'm not that good with Linux systems, and it took me a few days until I managed to configure everything right so ruTorrent works (as I was unable to install it myself without the script) and all the other packages I need are installed and the system is bootable.
Until I managed to do so, every time I installed what I needed, the server just didn't boot when I restarted it, so had to go through it all from the beginning.

I use the server for torrent seeding, so I gotta have ruTorrent, and also some kind of a GUI as VNC (I don't know x2go, but will look into it), and a few applications as I installed which you can see in my commands above.
About the root access, the rtinst script actually blocked root access and configured another sudo account which I currently use, and allowed only my local IP to connect to SSH via the port.

I don't really want to format the system now, as I have about 12TB of data on the drives. What can I do in that situation?

---

### Post by TheFu on 2019-06-19
> **aradmey said:**
>  I don't really want to format the system now, as I have about 12TB of data on the drives. What can I do in that situation?

That's what backups are for. Use them.  All the other issues are due to lack of knowledge. There is no solution for that except education.  I've provided suggestions that will lead to a stable system. Whether you can follow those is completely your call.

GUIs aren't good for server directly on the internet. They open all sorts of hackable attack vectors.

There are BT seeding servers in the Ubuntu repos. Use those.  Using a script that you don't understand for BT is too dangerous to consider. I wouldn't.

Locking device access down to a single IP might not be the best idea if you don't have a static IP.  At the next router reboot - or if you are like many people near me - within the next 24 hrs, your IP will be force-changed by the ISP, just because.

For what is causing issues, check the log files and dmesg.  Setup journalctl to keep logs longer, at least through 5 reboots.  **sudo egrep -i 'error|warn' /var/log/*g** will search the current logs.  Some services might have dedicated logs that are placed in subdirectories.

Anyways, good luck.  Hopefully, someone with different experience and ideas will post.

---

