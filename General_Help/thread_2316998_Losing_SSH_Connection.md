---
title: "Losing SSH Connection"
date: 2016-03-12
forum: General Help
---

### Post by Geoff_Lane on 2016-03-12
Folks,

I manage remotely a relatives Raspberry Pi running Mate.

Twice now I have lost the ssh connection and am not sure if it is the wifi or some other problem.

If a power off then on does not resolve the problem I'll then have to wait until I visit so would just like some advice as to which log files to check so ascertain the cause.

Geffers

---

### Post by papibe on 2016-03-12
Hi Geoff_Lane.

A few thoughts about remote support for friend and family.

You have to consider their ISP would change their public IP. You could use dynamic DNS, or a 'call home' solution for that.

Normally, the Pi would be a LAN DHCP client, and that's doesn't work very well for remote support. Reserve an address on the router, or set an static IP on the Pi.

You may want to change the port that is entering the router from 22 to a higher value in the dynamic range (49152–65535). You can keep the default port internally, just map a higher port to 22 on the router.

Since most ISP connections are _VERY_ asymmetric, you may be fighting for the, limited, upstream bandwidth. You could set a a priority for the ssh traffic using QoS on the router.

You may be having problems with WiFi. There may be some interference, or a weak connection. I would set up a wired connection if possible.

The problem may in your end if you are using a mobile client from your phone or over a 3G 4Lte service.

There is a special ssh service for poor network conditions called mosh. It may help you if the problem comes from the latest 3 points.

Just some thoughts. Let us know how it goes.
Regards.

---

### Post by HermanAB on 2016-03-13
It may also be a good idea to set up a cron job that will restart the SSH daemon once a day. ( Put a script in /etc/cron.daily)

---

### Post by Geoff_Lane on 2016-03-16
> **papibe said:**
> Hi Geoff_Lane.

You could use dynamic DNS, or a 'call home' solution for that.

Reserve an address on the router, or set an static IP on the Pi.

You may want to change the port that is entering the router.

Since most ISP connections are _VERY_ asymmetric, you may be fighting for the, limited, upstream bandwidth. You could set a a priority for the ssh traffic using QoS on the router.

You may be having problems with WiFi. There may be some interference, or a weak connection. I would set up a wired connection if possible.

Just some thoughts. Let us know how it goes.
Regards.

Thank you papibe for reply,

All those areas are covered, I have an address with dtdns, local address is fixed and port is altered.

I might have to wait until I visit to resolve the issue.

Geffers

---

### Post by Geoff_Lane on 2016-03-16
> **HermanAB said:**
> It may also be a good idea to set up a cron job that will restart the SSH daemon once a day. ( Put a script in /etc/cron.daily)

I don't think it is the ssh daemon, suspect the wifi.

Geffers

---

### Post by papibe on 2016-03-16
> **Geoff_Lane said:**
> I don't think it is the ssh daemon, suspect the wifi.
If you can't improve the signal, use a long cable, or get a new router, I would consider powerline ethernet.

Just a thought.
Regards.

---

