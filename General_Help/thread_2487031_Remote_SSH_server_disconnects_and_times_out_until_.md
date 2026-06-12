---
title: "Remote SSH server disconnects and times out until the server is restarted"
date: 2023-05-20
forum: General Help
---

### Post by jessebar on 2023-05-20
Hey guys,

I've run into an ssh connection issue and it's been driving me crazy.

**Background:**
I set up ubuntu server (22.04) on an old PC, and set up SSH server. It's set up for private key authentication and google 2fa.

It's currently in a remote location (7 hours drive away), so I can't access it physically except for someone (non-technical) that can restart the machine.

It was running just fine and allowing ssh connections for a three weeks or so until today when it started experiencing the following:

**Issue:**
1. It'll disconnect the active ssh session with the following message: ```
client_loop: send disconnect: Connection reset
```
2. The ssh server doesn't allow any subsequent connections with the following error: ```
ssh: connect to host <host> port <port>: Connection timed out
```
3. Restarting the server (or even sleeping it and un-sleeping it) will allow connections again, but after about 10-20 minutes, the issue starts again from #1

**Troubleshooting:**
1. I tried connecting via another PC and get the same "connection timed out" error
2. noticed a lot of traffic (chinese ip's) probing ssh default port in auth.log, so I changed ssh port from 22 to another open one, thinking it might be some kind of DOS issue
3. added following to sshd_config and restarted the ssh service:
    ```
ClientAliveInterval 600
TCPKeepAlive yes
ClientAliveCountMax 10
```
4. add the following rules via iptables
    ```
sudo iptables -A INPUT -p tcp --dport <port> -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
sudo iptables -A OUTPUT -p tcp --sport <port> -m conntrack --ctstate ESTABLISHED -j ACCEPT
```
    
**Note:**
Further troubleshooting can only be done when someone is available to restart the machine which gives me a ~10-20 minute interval to troubleshoot remotely via ssh.

---

### Post by TheFu on 2023-05-21
a) Install **fail2ban** to get the brute force attempts under control.
b) Move the inbound port from 22/tcp to some very high port, perhaps 61022/tcp, to avoid tourists. I do this at the WAN router, keeping the computer on 22/tcp for LAN-to-LAN connections.
c) My ssh troubleshooting guide - it doesn't touch 2FA and I'd never use Google for that, but you do you.  [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

---

### Post by jessebar on 2023-05-21
> **TheFu said:**
> a) Install **fail2ban** to get the brute force attempts under control.
b) Move the inbound port from 22/tcp to some very high port, perhaps 61022/tcp, to avoid tourists. I do this at the WAN router, keeping the computer on 22/tcp for LAN-to-LAN connections.
c) My ssh troubleshooting guide - it doesn't touch 2FA and I'd never use Google for that, but you do you.  [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

Hey, thanks for the reply. I've ruled out brute force attempts as the cause. Once I changed the ssh port, the logs showed no more attempts, but it still locked up. To my knowledge the 2FA auth shouldn't be the problem because it was working fine for several weeks.

Looking through the troubleshooting guide, I've completed most of those checks already. Some I'm unable to do since I don't have physical access to the machine such as checking if the ssh service is running when it's locked up or checking ssh localhost. Guiding anyone with access is also out of the question.

I suspect that the server is somehow the issue since restarting seems to resolve the issue for about 15 minutes. However, I won't rule out local connection being at fault just yet. I'm connecting via powershell's ssh implementation, though I've tried other clients and machines and got the same result. Running with the verbose flag -vvv, I got the following:

```
debug1: Authenticator provider $SSH_SK_PROVIDER did not resolve; disabling
debug2: resolving "<host>" port <port>
debug3: ssh_connect_direct: entering
debug1: Connecting to <host> [<ip>] port <port>.
debug3: finish_connect - ERROR: async io completed with error: 10060, io:0000013FC8A2C820
debug1: connect to address <ip> port <port>: Connection timed out
ssh: connect to host <host> port <port>: Connection timed out
```

---

### Post by jessebar on 2023-05-21
The issue was resolved. If anyone experienced these odd set of circumstances, I'm leaving the solution here.

TLDR: gnome settings daemon power plugin was suspending the system erroneously after "inactivity"

**Cause/Description:**
I'm not sure if it's a bug or why this issue arose after weeks of the server running, but gsd was suspending the server after apparent "inactivity" even though there were active ssh sessions. I didn't realize it was suspended as I didn't have access to the machine physically. What I thought was a system restart to fix the issue was in fact pulling the system out of suspended state. Then after 20 minutes, gsd would trigger a suspend again and ssh connections would time out obviously.

[B]Resolution:
[/B]1. Masked suspend, sleep, hibernate entirely
2. Disabled sleep-inactive-type gsd setting
3. For good measure, I disabled the power button from doing anything

```
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type nothing
gsettings set org.gnome.settings-daemon.plugins.power power-button-action nothing
```

---

### Post by TheFu on 2023-05-21
The real lesson should be NOT to put any desktop/DE onto a server.

---

### Post by MAFoElffen on 2023-05-22
+1 when I saw the first post, I first thought, he said "server"... so it wouldn't be a sleep/hibernation issue... "Servers" do not have gnome-settings installed. LOL.

I guess I should not assume what people might do. But I am guilty of that also. I have (also) made that mistake before... And caused a different outcome.

Yes, if you install a Desktop onto Ubuntu Server, and if it installs the dconf database, then one of the things you need to disable is "all" the power settings. Because of this (this happened to me), even on a minimal-X install on a server, where I ran into a problem where the screen was staying up, but the storage controllers were going to sleep. You might think, okay, that is saving power... But on ZFS based systems, the status of the storage pools go into a "suspend mode" and the drop off the system, which is bad juju. Not good at all. With that kind of thing, It doesn't forget that on a reboot, and fix itself.

So not just the screen timeout setting. For gnome type desktops, if used on a system providing server services, set to "performance mode", no screen timeouts, etc. Be thorough.

---

