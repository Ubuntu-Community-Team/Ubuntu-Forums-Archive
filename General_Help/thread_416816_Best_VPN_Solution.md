---
title: "Best VPN Solution?"
date: 2007-04-21
forum: General Help
---

### Post by Orbit45244 on 2007-04-21
I'm upgrading my Ubuntu webserver this weekend to Feisty, and I need to set up a VPN connection to the new Feisty server so some of my friends can commit data to the SVN repository. I need to know which VPN solution is best. There are so many options, such as PPTP and OpenVPN, that I can't say which is the best one. My friends will be accessing the VPN from Windows XP. I also would like the VPN to be encrypted, so we can securely commit data to the SVN server.

---

### Post by Orbit45244 on 2007-04-21
Please, I really need this question answered.

---

### Post by nrwilk on 2007-04-21
I use vpnc almost everyday with no problems.

```
sudo aptitude install vpnc
```

There's also a GUI front-end which plugs-in to NetworkManager to add VPN capabilities using vpnc:

```
sudo aptitude install network-manager network-manager-vpnc
```

Hope this helps!

---

### Post by tschneiter on 2007-04-21
Ive tried a few VPN clients (vpnc, networkmanager-vpnc, kvpnc, etc) and have found that vpnc works best. It is command-line based, so youll have to deal with that a bit, but it works more reliably than any of the other options. 

You can set up a custom config file for vpnc so the only thing you need to write wold be:

```
vpnc configname
```

Hope this helps!

---

### Post by nrwilk on 2007-04-21
> **tschneiter said:**
> Ive tried a few VPN clients (vpnc, networkmanager-vpnc, kvpnc, etc)

Those are all just frontends for vpnc.  But, yes, you are correct that using vpnc directly via the command line is noticably more stable than using one of these frontends.

---

### Post by dabbner on 2007-04-30
Since installing 7.04, I have tried both kvpnc and network-manager-vpnc, and both error out.  network-manager says my .pcf doesn't contain valid data, so it can't be imported.  kvpnc imports the pcf fine, but just can't connect.  The same pcf works under windows and 6.10.  This issue is happening on multiple machines.  

anyone ever seen a similar issue?

---

