---
title: "USG CIS compliance blocks all internet when still connected."
date: 2023-10-14
forum: General Help
---

### Post by richard378 on 2023-10-14
Hi I am following the Ubuntu, guide here:

[https://ubuntu.com/security/certifications/docs/usg/cis/compliance](https://ubuntu.com/security/certifications/docs/usg/cis/compliance)

But when I apply usg fix for level 1 workstation or server I am connected to the network, but can't access internet.  What does this tool do to block all internet access.  How do I allow basic internet access after running the tool and I am blocked from the internet?

---

### Post by MAFoElffen on 2023-10-14
I have been waiting on this for 22.04 and been actively bugging the Canonical Ubuntu Pro Support Staff for a while on this.

I am in the middle of some installs and tests right now for something else. 

I will get to this late tonight or tomorrow and see what it does, and to see it I can replicate that problem.

---

### Post by MAFoElffen on 2023-10-16
Okay, I'm spinning up a 22.04 test instance to add to my Ubuntu Pro subscription so I can reproduce and test this... 

Sorry -- My other tests took a bit longer than I thought because ZFS 2.2 released on the 13th along with some 'other things' that same day, which had to be worked out.

Just letting you know I'm working on this and trying to find out. 

I am just a volunteer, and I am just one person. LOL

I saw where you said for both workstation and server... [COLOR=#ff0000]But was that for cis level 1 or 2?[/COLOR]

---

### Post by MAFoElffen on 2023-10-17
Yes. I reproduced the problem.

It breaks DNS resolve. Here is how I fixed it.

I created a netplan yaml file. It doesn't matter if it is static or is dhcp, just so it has the interface name and other details for either. I set the renderer for networkd, instead of NetworkManager. So this will work for both the workstation profile and for the server profile...

I disabled and masked the Network Manager Service
```

sudo su
systemctl stop network-manager
systemctl disable network-manager
systemctl mask network-manager

```
Then I enabled an started systemd-networkd
```

systemctl enable and started systemd-networkd
systemctl start systemd-networkd
systemctl status networkd

```
Then I enabled and started systemd-resolved
```

systemctl enable systemd-resolved
systemctl start systemd-resolved
systemctl status systemd-resolved

```
Then I changed the resolv.conf symlink to point to systemd-resolved
```

unlink /etc/resolv.conf
ln -s /run/systemd/resolve/resolv.conf /etc/resolv.conf

```
Both workstation and server profiles then had DNS resolve and connectivity to named services.

---

### Post by richard378 on 2023-10-21
I have figured it out too. I needed to create a ntables rule to allow firewall. I fixed it buy settinga firewall policy for ntables. The default policy disabled ufw and iptables and enables ntables. But does not configure ntables firewall to work.

---

### Post by MAFoElffen on 2023-10-21
LOL. That would also be a problem. Glad you found that. Very good catch!

If fixed now, please select the "Thread Tools" link to mark your thread as "Solved". As this was a very unique find to a specific issue, marking this as solved will help others find your solution to help them fix their similar problem during their search.

---

