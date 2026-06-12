---
title: "Server New Install - Ethernet connection down"
date: 2024-11-26
forum: General Help
---

### Post by bigchuck2 on 2024-11-26
enp1s0 is down. After I use:
ip link set dev eno1s0 up
It still doesn’t have IP address. Then when I restart it goes back down.

Fresh install. I’m assuming I need to set something up. I tried messing with the Netplan yaml. But it seems to reset when I restart.

Sorry, new to this. I looked at several questions but not quite understanding. Any help is appreciated.

Thanks!

---

### Post by Irihapeti on 2024-11-27
Can you tell us which version of Ubuntu you are using.

Also, can you post the contents of your netplan .yaml file in between [code] tags? Netplan is quite fussy about the spacing/indentation in the config file, and there could be something there that needs a tweak.

---

### Post by bigchuck2 on 2024-11-27
24.04.1
Yaml is blank

---

### Post by Irihapeti on 2024-11-27
Then we need to create a new .yaml configuration.

We need to know where you would be getting the IP address for the server. Is it in a data centre and connected directly to the internet? Or is it on a home or work network? How do you get the IP address (DHCP or assigned to you)?

---

### Post by bigchuck2 on 2024-11-28
Assuming I set the .yaml file to this?


network:
  version: 2
  renderer: networkd
  ethernets:
    eth0:    # name of your ethernet adapter here
      addresses:
        - 192.168.1.5/24  # Updated to match the gateway subnet
      nameservers:
        addresses: [1.1.1.1, 8.8.8.8]
      routes:
        - to: default
          via: 192.168.1.1

---

### Post by Irihapeti on 2024-11-28
That should work, if it matches your setup.

Make sure, though, that you use spaces, not tabs, in the .yaml file, and that they exactly match what's in the example (it looks like something from the netplan.io site). Netplan is *extremely* fussy about the spacing.

---

