---
title: "Internet browsing stops working a few seconds after I log into Ubuntu. How to fix?"
date: 2023-10-19
forum: General Help
---

### Post by Advait on 2023-10-19
All the details are here: [https://docs.google.com/document/d/1jP4oTPWK3Z5I1R3NXgxcAU8IvPeoSZOJ_0XaDUSFKZo/edit?usp=sharing](https://docs.google.com/document/d/1jP4oTPWK3Z5I1R3NXgxcAU8IvPeoSZOJ_0XaDUSFKZo/edit?usp=sharing)

Internet browsing stops working a few seconds after I login. See google doc for the diagnostic commands I ran. How to fix this?

I have to do one or two or three reboots before it starts working again.

Please give me instructions on which logs you wanna look at. Then I'll copy and paste that data so you experts can review it.

I'm a noob and know nothing about the command line. But I can copy and paste.

---

### Post by MAFoElffen on 2023-10-19
Please post the output of this within CODE Tags:
```

sudo systemctl status systemd-resolved --no-pager
grep -Ei 'NetworkManager' /var/log/syslog | tail -n50

```
I'll wait for that before explaining...

---

### Post by Advait on 2023-10-19
> **MAFoElffen said:**
> Please post the output of this within CODE Tags:
```

sudo systemctl status systemd-resolved --no-pager
grep -Ei 'NetworkManager' /var/log/syslog | tail -n50

```
I'll wait for that before explaining...

See below:

```
advait@advait-Bravo-15-A4DDR:~$ sudo systemctl status systemd-resolved --no-pager
[sudo] password for advait: 
&#9675; systemd-resolved.service - Network Name Resolution
     Loaded: loaded (/lib/systemd/system/systemd-resolved.service; disabled; vendor preset: enabled)
     Active: inactive (dead)
       Docs: man:systemd-resolved.service(8)
             man:org.freedesktop.resolve1(5)
             https://www.freedesktop.org/wiki/Software/systemd/writing-network-configuration-managers
             https://www.freedesktop.org/wiki/Software/systemd/writing-resolver-clients
advait@advait-Bravo-15-A4DDR:~$ 
advait@advait-Bravo-15-A4DDR:~$ grep -Ei 'NetworkManager' /var/log/syslog | tail -n50
Oct 20 06:05:46 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762146.5275] device (virbr0): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'external')
Oct 20 06:05:46 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762146.5291] device (virbr0): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'external')
Oct 20 06:05:46 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762146.5293] device (virbr0): state change: secondaries -> activated (reason 'none', sys-iface-state: 'external')
Oct 20 06:05:46 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762146.5296] manager: NetworkManager state is now CONNECTED_LOCAL
Oct 20 06:05:46 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762146.5298] device (virbr0): Activation: successful, device activated.
Oct 20 06:05:48 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762148.0157] agent-manager: agent[494436dc43ea3932,:1.42/org.gnome.Shell.NetworkAgent/126]: agent registered
Oct 20 06:05:49 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762149.9685] policy: auto-activating connection 'Galaxy A71BD53 1' (2babcac3-5aa9-4d73-80b9-f3309489dc5d)
Oct 20 06:05:49 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762149.9692] device (wlp4s0): Activation: starting connection 'Galaxy A71BD53 1' (2babcac3-5aa9-4d73-80b9-f3309489dc5d)
Oct 20 06:05:49 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762149.9693] device (wlp4s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Oct 20 06:05:49 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762149.9696] manager: NetworkManager state is now CONNECTING
Oct 20 06:05:49 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762149.9699] device (wlp4s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Oct 20 06:05:49 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762149.9703] device (wlp4s0): Activation: (wifi) access point 'Galaxy A71BD53 1' has security, but secrets are required.
Oct 20 06:05:49 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762149.9703] device (wlp4s0): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
Oct 20 06:05:49 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762149.9717] device (wlp4s0): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
Oct 20 06:05:49 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762149.9721] device (wlp4s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Oct 20 06:05:49 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762149.9724] device (wlp4s0): Activation: (wifi) connection 'Galaxy A71BD53 1' has security, and secrets exist.  No new secrets needed.
Oct 20 06:05:49 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762149.9724] Config: added 'ssid' value 'Galaxy A71BD53'
Oct 20 06:05:49 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762149.9725] Config: added 'scan_ssid' value '1'
Oct 20 06:05:49 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762149.9725] Config: added 'bgscan' value 'simple:30:-70:86400'
Oct 20 06:05:49 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762149.9725] Config: added 'key_mgmt' value 'WPA-PSK WPA-PSK-SHA256 FT-PSK SAE FT-SAE'
Oct 20 06:05:49 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762149.9726] Config: added 'auth_alg' value 'OPEN'
Oct 20 06:05:49 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762149.9726] Config: added 'psk' value '<hidden>'
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.0092] device (wlp4s0): supplicant interface state: disconnected -> authenticating
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.0093] device (p2p-dev-wlp4s0): supplicant management interface state: disconnected -> authenticating
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.1045] device (wlp4s0): supplicant interface state: authenticating -> associating
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.1045] device (p2p-dev-wlp4s0): supplicant management interface state: authenticating -> associating
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.1337] device (wlp4s0): supplicant interface state: associating -> associated
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.1337] device (p2p-dev-wlp4s0): supplicant management interface state: associating -> associated
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.1510] device (wlp4s0): supplicant interface state: associated -> 4way_handshake
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.1510] device (p2p-dev-wlp4s0): supplicant management interface state: associated -> 4way_handshake
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.2677] device (wlp4s0): supplicant interface state: 4way_handshake -> completed
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.2678] device (wlp4s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful. Connected to wireless network "Galaxy A71BD53"
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.2678] device (p2p-dev-wlp4s0): supplicant management interface state: 4way_handshake -> completed
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.2680] device (wlp4s0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.2686] dhcp4 (wlp4s0): activation: beginning transaction (timeout in 45 seconds)
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.3705] dhcp4 (wlp4s0): state changed new lease, address=192.168.33.24
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.3768] device (wlp4s0): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'managed')
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.3792] device (wlp4s0): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'managed')
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.3793] device (wlp4s0): state change: secondaries -> activated (reason 'none', sys-iface-state: 'managed')
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.3795] manager: NetworkManager state is now CONNECTED_LOCAL
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.3818] manager: NetworkManager state is now CONNECTED_SITE
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.3819] policy: set 'Galaxy A71BD53 1' (wlp4s0) as default for IPv4 routing and DNS
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.3824] device (wlp4s0): Activation: successful, device activated.
Oct 20 06:05:50 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762150.3827] manager: NetworkManager state is now CONNECTED_GLOBAL
Oct 20 06:05:50 advait-Bravo-15-A4DDR dbus-daemon[869]: [system] Activating via systemd: service name='org.freedesktop.resolve1' unit='dbus-org.freedesktop.resolve1.service' requested by ':1.18' (uid=0 pid=1601 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Oct 20 06:05:51 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762151.8688] manager: startup complete
Oct 20 06:05:51 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762151.8786] policy: set 'Galaxy A71BD53 1' (wlp4s0) as default for IPv6 routing and DNS
Oct 20 06:06:00 advait-Bravo-15-A4DDR systemd[1]: NetworkManager-dispatcher.service: Deactivated successfully.
Oct 20 06:07:25 advait-Bravo-15-A4DDR NetworkManager[1601]: <info>  [1697762245.0517] agent-manager: agent[3dad32dde545ccd6,:1.92/org.gnome.Shell.NetworkAgent/1000]: agent registered
Oct 20 06:07:27 advait-Bravo-15-A4DDR kernel: [  107.215750] audit: type=1107 audit(1697762247.087:88): pid=869 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/NetworkManager" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.18" pid=3462 label="snap.snap-store.ubuntu-software" peer_pid=1601 peer_label="unconfined"
advait@advait-Bravo-15-A4DDR:~$ 
```

Anything helpful there?

---

### Post by ap10707 on 2023-10-19
New to the forums, but have been using Linux Operating systems (Ubuntu in particular) for a long time. Rollin through your log tail I see the following:

**_DNS Resolver (systemd-resolved) Status:_**

```
Active: inactive (dead)

```

**_Network Manager Logs:_**

```
dhcp4 (wlp4s0): state changed new lease, address=192.168.33.24

```
```
manager: NetworkManager state is now CONNECTED_GLOBAL

```
```

```

**_Agent Registration? (Someone will definitely be able to answer this better than I):_**

It appears that some sort of agent (possibly a NetworkManager plugin or GNOME Shell's network agent) is being registered a couple of times.

```
agent-manager: agent[3dad32dde545ccd6,:1.92/org.gnome.Shell.NetworkAgent/1000]: agent registered
```

**_AppArmor is MAD:_**

There is an AppArmor "DENIED" event related to snap.snap-store.ubuntu-software, which might not be directly related but could be indicative of some permission issues.

```
apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/NetworkManager" ...

```


Step 1 - Check DNS Settings:

```
sudo systemctl restart systemd-resolved

```

OR

```
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf

```

Step 2 - Check your AppArmor logs for any denied actions that could be affecting your network activities. Let us know what you see.

Step 3 - Other network agents that could be interfering.

Step 4 - Run your normal diagnostic tests like ping (IP & Hostname), Traceroute

Step 5 - Test your hardware. Your adapter might have an issue with your wireless network. Try connecting to a different one. If it connects fine, try connecting to your network with a physical cable and see if that makes a difference. If it runs no problems with a hard line connection, may have a wifi issue.

Don't hesitate to PM me if you have any questions. Good luck.

---

### Post by Advait on 2023-10-20
> **ap10707 said:**
> New to the forums, but have been using Linux Operating systems (Ubuntu in particular) for a long time. Rollin through your log tail I see the following:

**_DNS Resolver (systemd-resolved) Status:_**

```
Active: inactive (dead)

```

**_Network Manager Logs:_**

```
dhcp4 (wlp4s0): state changed new lease, address=192.168.33.24

```
```
manager: NetworkManager state is now CONNECTED_GLOBAL

```
```

```

**_Agent Registration? (Someone will definitely be able to answer this better than I):_**

It appears that some sort of agent (possibly a NetworkManager plugin or GNOME Shell's network agent) is being registered a couple of times.

```
agent-manager: agent[3dad32dde545ccd6,:1.92/org.gnome.Shell.NetworkAgent/1000]: agent registered
```

**_AppArmor is MAD:_**

There is an AppArmor "DENIED" event related to snap.snap-store.ubuntu-software, which might not be directly related but could be indicative of some permission issues.

Any commands I can copy and paste to diagnose this deeper?

> **ap10707 said:**
> ```
apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/NetworkManager" ...

```

Step 1 - Check DNS Settings:

```
sudo systemctl restart systemd-resolved

```

OR

```
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf

``` 

Here's the results:

advait@advait-Bravo-15-A4DDR:~$ sudo systemctl restart systemd-resolved
[sudo] password for advait: 

advait@advait-Bravo-15-A4DDR:~$ echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf
nameserver 8.8.8.8
advait@advait-Bravo-15-A4DDR:~$ 

> **ap10707 said:**
> Step 2 - Check your AppArmor logs for any denied actions that could be affecting your network activities. Let us know what you see. 

How to do this? What commands should I run?

> **ap10707 said:**
> Step 3 - Other network agents that could be interfering. 

How to check this? What commands should I run?

> **ap10707 said:**
> Step 4 - Run your normal diagnostic tests like ping (IP & Hostname), Traceroute 

When the problem arises I'll ping an IP4 address and it'll work. Then I ping a name (like [www.google.com](www.google.com)) and it doesn't work. You saw that on the earlier post.

> **ap10707 said:**
> Step 5 - Test your hardware. Your adapter might have an issue with your wireless network. Try connecting to a different one. If it connects fine, try connecting to your network with a physical cable and see if that makes a difference. If it runs no problems with a hard line connection, may have a wifi issue.
 

OK, I'll try this when the problem happens again.

Any other diagnostics you want me to run?

> **ap10707 said:**
> Don't hesitate to PM me if you have any questions. Good luck. 

Will do. Thanks!

---

### Post by #&amp;thj^% on 2023-10-20
For errors or denied on apparmor:
```
tat /var/log/syslog | grep apparmor
```

---

### Post by Advait on 2023-10-20
> **ap10707 said:**
> [QUOTE=1fallen;14161963]For errors or denied on apparmor:
```
tat /var/log/syslog | grep apparmor
```

Looks like an error...?

advait@advait-Bravo-15-A4DDR:~$ tat /var/log/syslog | grep apparmor
Command 'tat' not found, but there are 16 similar ones.
advait@advait-Bravo-15-A4DDR:~$

---

### Post by #&amp;thj^% on 2023-10-20
> **Advait said:**
> [QUOTE=ap10707;14161900]

Looks like an error...?

advait@advait-Bravo-15-A4DDR:~$ tat /var/log/syslog | grep apparmor
Command 'tat' not found, but there are 16 similar ones.
advait@advait-Bravo-15-A4DDR:~$

Yep my bad, more coffee please
```
tac /var/log/syslog | grep apparmor
```

---

### Post by Advait on 2023-10-20
> **1fallen said:**
> [QUOTE=Advait;14161970]

Yep my bad, more coffee please
```
tac /var/log/syslog | grep apparmor
```

The error will cost you one bean. :P :D

Here it is: [https://docs.google.com/document/d/1lNWnIC1S8jdQPLTEzpTO6q_uLfMVzeG8O5v7SvNtRBk/edit?usp=sharing](https://docs.google.com/document/d/1lNWnIC1S8jdQPLTEzpTO6q_uLfMVzeG8O5v7SvNtRBk/edit?usp=sharing) 

Anything helpful?

---

