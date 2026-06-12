---
title: "*Step by step* how to fix repeated “Authentication required by Wi-Fi network” please!"
date: 2015-05-30
forum: General Help
---

### Post by Shawn_Alan on 2015-05-30
[COLOR=#111111][FONT=Ubuntu]I am finding solutions all over the web, I have been searching for hours. However the people that are asking understand how to work the command line, so the steps how to get to and apply the solutions are never discussed. I can't get the USB wifi stick to work and it turns out this is definitely a confirmed glitch. I found a solution that sounds like it would fix the problem, I just need help with a "Linux for dummies" type approach:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]"I have the same issue here (UQAM), it should have a certificate but, it does not. When you connect for the first time, it wont set it properly so, you need to go to /etc/NetworkManager/system-connections and find your connection name, edit the file. You should see this line:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]system-ca-certs=true change it to[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]system-ca-certs=false"[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]This is the website I found that from:[https://help.ubuntu.com/community/NetworkManager#Editing_Network_Settings_in_nm-connection-editor](https://help.ubuntu.com/community/NetworkManager#Editing_Network_Settings_in_nm-connection-editor)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Now I know this shows as a solution for a certificate issue, however I've seen other people use that solution to fix the password glitch.

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]Bus 002 Device 003: ID 06a3:8021 Saitek PLC Eclipse II Keyboard Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 001 Device 004: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323] Bus 001 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]

---

