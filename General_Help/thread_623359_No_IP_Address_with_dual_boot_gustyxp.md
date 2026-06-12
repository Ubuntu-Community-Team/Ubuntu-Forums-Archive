---
title: "No IP Address with dual boot gusty/xp"
date: 2007-11-25
forum: General Help
---

### Post by BandD on 2007-11-25
Hello all,

I'm a totally noob to the linux world.  I just finished a setting up a dual boot with gusty and xp.  Everything went fine.  After the Gusty set up, Ubuntu had no problem connecting to the internet (lan connection).  However, when I booted into XP, I was unable to obtain an IP Address.  So I messed around a bit, disabled my network card and then re-enabled it and I was able to get the IP Address.  BUT, when I booted back into Gusty, Gusty was unable to obtain an IP Address and I'm not familiar enough with the environment to really try much.

My network card is an Intel Pro/100 VE in a Sony Vaio VGN-FS620.  

Can you think of any reason why they seem to override each other?  It happened when I ran the Live CD for Gusty a couple of weeks ago as well.  I accessed the net through the live CD and when I booted back into Windows, no IP address.  Strange.

Thanks,

Dustin

---

### Post by bkraptor on 2007-11-26
You probably have different MAC addresses set on the LAN interface in Windows and Ubuntu, and your ISP only has a limited number of IP addresses it can lease.

Either that or it's just that your ISP has problems handing out leases.

In Windows you can try clicking Start -> Run -> cmd. In cmd run these 2 commands:
ipconfig /release
ipconfig /renew
Either that, or simply click the Repair button in the support tab in your LAN interface window (in network connections).

In Ubuntu, open up a Applications -> Terminal and type:
sudo dhclient eth0
then type in your password. This is assuming eth0 is your LAN interface.

---

### Post by BandD on 2007-11-26
Thanks for the reply.  

I tried the 'repair connection' option in Windows, but it tries to repair it simply by acquiring an IP address which it can't do to begin with.  It tries for several minutes and then tells me that it was unable to do so.  The only way I got it to work, was to disable the wired connection and the re-enable it.  

But now that I have it working in Windows, Gusty won't retrieve an IP and I have been unable to make it do so.  Mostly due to my lack of experience with Linux...I just don't even know where to begin.  Though, I'm pretty sure if I get it working in Gusty it will stop working in Windows.

I tried the 'sudo dhclient eth0' command in the terminal but it just kept cycling through the same operations without any resolution. 

I have a Terayon Terapro cable modem, no router--just straight from the modem port to my laptop.  The modem came with the apartment so I don't have any documentation on it, and it seems that Terayon has since been bought by Motorola and the documentation online seems to be non-existent.

Anyway, kind of strange.   Any other ideas, or info I can give you?

---

### Post by BandD on 2007-11-29
I can get an IP address in Ubuntu (or XP, which wasn't able to get one) by unplugging my modem for a few minutes and resetting it.  

If there is a better way I'd be happy to know.

---

