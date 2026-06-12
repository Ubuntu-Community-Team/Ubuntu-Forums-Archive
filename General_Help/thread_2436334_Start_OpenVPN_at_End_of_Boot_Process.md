---
title: "Start OpenVPN at End of Boot Process"
date: 2020-02-04
forum: General Help
---

### Post by databoy2k on 2020-02-04
Hey All:

I've got a weird issue in my ubuntu server 18.04. The net result is that I need OpenvPN Server to only bother to start long after the boot process, basically at (but without) login.

I use my server with pihole to do DNS and DHCP. My router is set up to refer DHCP requests over to the server. Unfortunately, when I reboot my server ends up hanging on "Raise Network Interfaces" for about 5 minutes, I assume because it's asking the router for an IP, the Router responds that it can look in a mirror, and the standoff apparently goes for 4 minutes and 40 seconds (I think). In the interim, OpenVPN attempts to start but, seeing that the network interface isn't raised, it terminates.

Once the timeout expires, the server goes to the login screen (all CLI) but at that point pi-hole is running so it gets its network interface up. I then have to log into the server (either locally by SSH or by hooking up to the box) and run "sudo systemctl start openvpn@server" to get my OpenVPN back to life.

I'm assuming that troubleshooting this issue is going to be an absolute nightmare; instead, is there a way to automatically run "sudo systemctl start openvpn@server" as the very last action the server does, preferrably after the network interface is up?

Alternatively, if anyone has tips for fixing the whole timeout issue, I'm all ears too.

Thanks.

---

### Post by TheFu on 2020-02-04
Make the openvpn startup "target" dependent on networking "target" in the systemd config file for it.
The networking target is in *networking.service* file.

The file I would change is  /etc/systemd/system/multi-user.target.wants/openvpn.service  A little quick reading on the config options should have the 1 line needed.  Google found this: [https://community.openvpn.net/openvpn/ticket/462](https://community.openvpn.net/openvpn/ticket/462) which has a specific solution.

---

### Post by SeijiSensei on 2020-02-05
Servers should be configured with static IP addresses. I can't tell if that's the case here, or if the server requests its IP from the router with DHCP.

---

### Post by TheFu on 2020-02-05
Why not just disable DHCP on the router and let the Pi-hole box answer any requests? Having multiple DHCP servers on a subnet is asking for trouble.
For the server, as SeijiSensei says, configure that with a static IP so DHCP isn't used at all.  There are 2 groups about this.
a) only use DHCP for portable devices and end-user desktops, use static IPs for servers
b) Use DHCP for everything, including where static IPs are needed for specific servers via DHCP-reservations.

I'm in the first group.  I use dhcp-reservations for all known network devices, so they can be remotely accessed easily.  For example, the wifi IP for my phones, phone system, tablets, laptops (when on wifi), network TV tuners, roku, and media player devices are all dhcp-reservations.  OTOH, all physical servers, desktops, virtual machines have static IPs configured on each of those systems.

I prefer a well-managed network.

Any guest devices are put onto a different subnet (10.x.x.x) outside my internal router controlled subnets.  All public IPs are managed by my router, not the ISP's router.

---

### Post by databoy2k on 2020-02-09
Sorry guys - I didn't realize that I wouldn't actually get notifications of replies. Apparently it's been a long time since I've been on here. 

@SeijiSensei: I... can't. I have some sort of a weird issue between networkmanager and netplan. I screwed something up at some point, got it just barely running again, and then haven't touched it since. I'd be lying if I could even tell you whether I'm running one or the other, let alone what effect changing between them would have on my pi-hole setup. So yeah - this is an issue of my own making, and I just live with the 5 minute boot times. I just wish OVPN would too.

@TheFu: I have. The server that I'm working on is the Pi-hole box, and it answers the requests via DHCP reservations. In theory (see my answer to @SeijiSensei) it should be static IP'ed but something is horrendously borked somewhere in something that I truly can't figure out. 

My plan is to one day nuke this server after copying all relevant data onto another system and re-start from scratch. We're not there, though. 

I did change the multi-user.target.wants file, though, to just "network.target". That still didn't work. It seems that openvpn fails if networking isn't up. I still just need something that will try again after the boot is complete.

---

