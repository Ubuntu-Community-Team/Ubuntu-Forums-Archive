---
title: "Mounting CIFS volumes through second NIC stops all network activity through main NIC"
date: 2022-12-29
forum: General Help
---

### Post by goldenretrogames on 2022-12-29
[COLOR=#D7DADC][FONT=&amp][COLOR=#000000]NEW POST:
After spending a couple hours trying to troubleshoot the problem in my original post, I found something that completely changes the issue. When the system boots, both NICs work perfectly ... for about 5 seconds. The moment the system mounts my CIFS shares, the main NIC no longer responds. Here's the general config:


[LIST]
[*]NIC1
[LIST]
[*]This is used to connect to the internet and the rest of my local network
[*]192.168.1 subnet, static IP
[/LIST]

[*]NIC2
[LIST]
[*]This is a direct ethernet connection to my NAS
[*]No switch, just a cable directly between the two systems
[*]192.168.200 subnet, static IPs on both systems
[/LIST]
[/LIST]

I added an entry to my HOSTS file that uses the 192.168.200 subnet to access my NAS. All mounts are using the hostname I've assigned. The mounts all work perfectly after boot.

If I comment out all the mounts in FSTAB, both NICs work as expected. The moment I mount anything, it's like NIC1 stops working. The server can no longer access the internet and no devices on the 192.168.1 subnet can connect to the server. If I use 'ip a', it still shows NIC1 as connected and having the assigned IP address.

Any idea what could possibly be going on here?


ORIGINAL POST:
I've added a second NIC to my Ubuntu Server (22.04.1 LTS) and I'm having trouble configuring them. Whenever I try to do so, I completely lose access through my main NIC, which I'm guessing is a misconfigured 00-installer-config.yaml file. Ultimately, I want ETH1 to be the primary NIC which will have access to the internet and the rest of my network. ETH2 will be a local network specifically between my server and NAS (manual IP on a different subnet).
[/COLOR][/FONT][/COLOR]
[COLOR=#D7DADC][FONT=&amp][COLOR=#000000]What would be the proper settings in my config file? This is generally what I think it should look like, but it's obviously wrong somehow:[/COLOR][/FONT][/COLOR]
[COLOR=#000000]
[/COLOR]```
[COLOR=#000000]
[/COLOR]network:
  ethernets:
    ETH1:
      addresses: [192.168.1.235/24]
      routes:
        - to: default
          via: 192.168.1.1
          on-link: True
      nameservers:
        addresses: [192.168.1.1]
      dhcp4: false
    ETH2:
      addresses: [192.168.200.235/24]
      dhcp4: false

```[COLOR=#000000]
[/COLOR][COLOR=#D7DADC][FONT=&amp][COLOR=#000000]
Do I need to add something to the routes of ETH1 to stop it from trying to access the 192.168.200 subnet or add a route to ETH2 to make sure it doesn't try to access IPs outside its subnet?


[/COLOR][/FONT][/COLOR]

---

### Post by TheFu on 2022-12-29
To get any help at all, you'll need to use forum 'code tags' so indentation is maintained in your posts.
Edit the original post and wrap the config in code tags.
[Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) explains code tags.

---

### Post by goldenretrogames on 2022-12-29
Edited to make it easier to read.

---

### Post by TheFu on 2022-12-29
ETH1 and ETH2 are unlikely to be valid device names, so those will never work.

I keep settings for different NICs in different YAML files.  Names like 
enp3s0-static-config.yaml         enp7s0f1-mgnt-static-config.yaml    enp7s0f0-SAN-static-config.yaml   
are useful with the device name and subnet it is for spelled out.  The only requirement is that the filename end with yaml.

I've never used route-to:, so that's new to me.
I specify the gateway4: address which sets the default route off the subnet.
All other subnets are controlled by the netmask.
I disable both DHCP methods too. Don't want IPv6 junk here:
```
      dhcp4: false
      dhcp6: false

```
For the route-to stuff, I'd suggest the netplan.io website, examples, and explanation. [https://netplan.io/examples](https://netplan.io/examples) has an example with multiple gateways.

---

### Post by goldenretrogames on 2022-12-29
I just replaced the device names with ETH1 and ETH2 to make it easier to discuss. I have the correct names in there. Using 'ip a' shows that that both NICs have their assigned IPs, but the system seems to be trying to use ETH2 for all outbound communication for some reason. I can't figure out why it's doing that.

---

### Post by HermanAB on 2022-12-30
Look at the routing table and default gateway setting.

When I set up a server, I disable the automatic network configuration utilities such as NetworkManager and set it up with a little script, to preserve my sanity.

---

### Post by TheFu on 2022-12-30
Probably want to create a new thread for CIFS issues.  It is a different skill than netplan configs.

---

