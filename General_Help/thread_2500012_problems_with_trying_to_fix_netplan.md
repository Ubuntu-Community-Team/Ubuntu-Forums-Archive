---
title: "problems with trying to fix netplan"
date: 2024-08-18
forum: General Help
---

### Post by jgw on 2024-08-18
I was using [https://linuxconfig.org/ubuntu-22-04-connect-to-wifi-from-command-line](https://linuxconfig.org/ubuntu-22-04-connect-to-wifi-from-command-line) to learn how  to see my wifi passwords.  Instead I have probably screwed up something.  Anyway, need to know how I can fix this and move on. 
 
I was trying to setup netplan and i got this far (step 4):

```

My yarml file

# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
wifis:
   wlan0:
       optional:  true
       access-points:
           greg:
           password: greg
       dhcp4: true

Results of netplan apply:

 sudo netplan apply
[sudo] password for greg: 

** (generate:15172): WARNING **: 12:46:56.307: Permissions for /etc/netplan/01-network-manager-all.yaml are too open. Netplan configuration should NOT be accessible by others.
/etc/netplan/01-network-manager-all.yaml:5:1: Error in network definition: unknown key 'wifis'
wifis:
^

```
Thoughts?

---

### Post by #&amp;thj^% on 2024-08-18
jgw, can you show us this:
```
sudo netplan --debug apply

```
It might show us the fix. (REMOVE YOUR PASSWORD)

---

### Post by Tadaen_Sylvermane on 2024-08-18
```
wifis:
   wlan0:
       optional:  true
       access-points:
           greg:
           password: greg
       dhcp4: true
```

Yaml requires indentation with spaces. In this case you have wifis and network on the same column. Move everything wifis and beyond to the right a space or 2 (match your previous indentation to keep it tidy).

---

### Post by jgw on 2024-08-20
I am now being told:
* (process:21967): WARNING **: 12:17:37.263: Permissions for /etc/netplan/01-network-manager-all.yaml are too open. Netplan configuration should NOT be accessible by others.
** (process:21967): DEBUG: 12:17:37.263: starting new processing pass

Not sure what to do with this one.  I changed the permissions;
I own it
I can do what I want
nobody get nuthin

Don't have a clue and I surrender.

---

### Post by #&amp;thj^% on 2024-08-20
> **jgw said:**
> I am now being told:
* (process:21967): WARNING **: 12:17:37.263: Permissions for /etc/netplan/01-network-manager-all.yaml are too open. Netplan configuration should NOT be accessible by others.

Don't have a clue and I surrender.
```
sudo chmod 600 /etc/netplan/01-network-manager-all.yaml 
```
check:
```
sudo stat  /etc/netplan/01-network-manager-all.yaml
  File: /etc/netplan/01-network-manager-all.yaml
  Size: 49        	Blocks: 2          IO Block: 512    regular file
Device: 0,28	Inode: 5726        Links: 1
Access: (0600/-rw-------)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2024-08-20 10:41:06.972767765 -0600
Modify: 2024-07-24 14:25:40.928874151 -0600
Change: 2024-08-18 17:21:40.843209086 -0600
 Birth: 2024-07-16 17:50:38.968662715 -0600

```
After the change:
```
sudo netplan --debug apply
** (generate:215526): DEBUG: 13:29:40.840: starting new processing pass
** (generate:215526): DEBUG: 13:29:40.840: starting new processing pass
** (generate:215526): DEBUG: 13:29:40.840: starting new processing pass
** (generate:215526): DEBUG: 13:29:40.840: starting new processing pass
** (generate:215526): DEBUG: 13:29:40.840: NM-889bf16b-de80-437d-baaf-f64fd2cdbd51: adding wifi AP 'Keep-Me-Up'
** (generate:215526): DEBUG: 13:29:40.840: starting new processing pass
** (generate:215526): DEBUG: 13:29:40.840: starting new processing pass
** (generate:215526): DEBUG: 13:29:40.840: We have some netdefs, pass them through a final round of validation
** (generate:215526): DEBUG: 13:29:40.840: Configuration is valid
** (generate:215526): DEBUG: 13:29:40.840: Configuration is valid
** (generate:215526): DEBUG: 13:29:40.840: eno1: setting default backend to 2
** (generate:215526): DEBUG: 13:29:40.840: Configuration is valid
** (generate:215526): DEBUG: 13:29:40.840: Configuration is valid
** (generate:215526): DEBUG: 13:29:40.840: Generating output files..
** (generate:215526): DEBUG: 13:29:40.840: networkd: definition eno1 is not for us (backend 2)
** (generate:215526): DEBUG: 13:29:40.840: Open vSwitch: definition eno1 is not for us (backend 2)
** (generate:215526): DEBUG: 13:29:40.841: networkd: definition enx70b3d55c01b3 is not for us (backend 2)
** (generate:215526): DEBUG: 13:29:40.841: Open vSwitch: definition enx70b3d55c01b3 is not for us (backend 2)
** (generate:215526): DEBUG: 13:29:40.841: NetworkManager: using keyfile passthrough mode
** (generate:215526): DEBUG: 13:29:40.841: NetworkManager: passing through fallback key: connection.timestamp=1722004654
** (generate:215526): DEBUG: 13:29:40.841: NetworkManager: passing through fallback key: ethernet.auto-negotiate=true
** (generate:215526): DEBUG: 13:29:40.841: NetworkManager: fallback override: ipv6.method=ignore
** (generate:215526): DEBUG: 13:29:40.841: networkd: definition NM-46c3b9af-1b89-40ea-9a3b-21c1e3c09a98 is not for us (backend 2)
** (generate:215526): DEBUG: 13:29:40.841: Open vSwitch: definition NM-46c3b9af-1b89-40ea-9a3b-21c1e3c09a98 is not for us (backend 2)
** (generate:215526): DEBUG: 13:29:40.841: NetworkManager: using keyfile passthrough mode
** (generate:215526): DEBUG: 13:29:40.841: NetworkManager: passing through fallback key: ethernet.auto-negotiate=true
** (generate:215526): DEBUG: 13:29:40.841: NetworkManager: default override: clearing ipv6.ip6-privacy
** (generate:215526): DEBUG: 13:29:40.841: networkd: definition NM-889bf16b-de80-437d-baaf-f64fd2cdbd51 is not for us (backend 2)
** (generate:215526): DEBUG: 13:29:40.841: Open vSwitch: definition NM-889bf16b-de80-437d-baaf-f64fd2cdbd51 is not for us (backend 2)
** (generate:215526): DEBUG: 13:29:40.841: NetworkManager: using AP keyfile passthrough mode
** (generate:215526): DEBUG: 13:29:40.841: NetworkManager: passing through fallback key: wifi-security.auth-alg=open
** (generate:215526): DEBUG: 13:29:40.841: NetworkManager: passing through fallback key: ipv6.addr-gen-mode=default
** (generate:215526): DEBUG: 13:29:40.841: NetworkManager: default override: clearing ipv6.ip6-privacy
DEBUG:no netplan generated networkd configuration exists
DEBUG:netplan generated NM configuration changed, restarting NM
** (process:215507): DEBUG: 13:29:41.330: starting new processing pass
** (process:215507): DEBUG: 13:29:41.330: starting new processing pass
** (process:215507): DEBUG: 13:29:41.331: starting new processing pass
** (process:215507): DEBUG: 13:29:41.331: starting new processing pass
** (process:215507): DEBUG: 13:29:41.331: NM-889bf16b-de80-437d-baaf-f64fd2cdbd51: adding wifi AP 'Keep-Me-Up'
** (process:215507): DEBUG: 13:29:41.331: starting new processing pass
** (process:215507): DEBUG: 13:29:41.331: starting new processing pass
** (process:215507): DEBUG: 13:29:41.331: We have some netdefs, pass them through a final round of validation
** (process:215507): DEBUG: 13:29:41.331: Configuration is valid
** (process:215507): DEBUG: 13:29:41.331: Configuration is valid
** (process:215507): DEBUG: 13:29:41.331: eno1: setting default backend to 2
** (process:215507): DEBUG: 13:29:41.331: Configuration is valid
** (process:215507): DEBUG: 13:29:41.331: Configuration is valid
DEBUG:Merged config:
b''
DEBUG:Link changes: {}
DEBUG:netplan triggering .link rules for lo
DEBUG:netplan triggering .link rules for eno1
DEBUG:netplan triggering .link rules for enx70b3d55c01b3
DEBUG:netplan triggering .link rules for wlp4s0
DEBUG:netplan triggering .link rules for surfshark_ipv6
DEBUG:netplan triggering .link rules for surfshark_wg
** (process:215507): DEBUG: 13:29:41.496: starting new processing pass
** (process:215507): DEBUG: 13:29:41.496: starting new processing pass
** (process:215507): DEBUG: 13:29:41.497: starting new processing pass
** (process:215507): DEBUG: 13:29:41.497: starting new processing pass
** (process:215507): DEBUG: 13:29:41.497: NM-889bf16b-de80-437d-baaf-f64fd2cdbd51: adding wifi AP 'Keep-Me-Up'
** (process:215507): DEBUG: 13:29:41.497: starting new processing pass
** (process:215507): DEBUG: 13:29:41.497: starting new processing pass
** (process:215507): DEBUG: 13:29:41.497: We have some netdefs, pass them through a final round of validation
** (process:215507): DEBUG: 13:29:41.497: Configuration is valid
** (process:215507): DEBUG: 13:29:41.497: Configuration is valid
** (process:215507): DEBUG: 13:29:41.497: eno1: setting default backend to 2
** (process:215507): DEBUG: 13:29:41.497: Configuration is valid
** (process:215507): DEBUG: 13:29:41.497: Configuration is valid
DEBUG:Merged config:
b''

```

---

