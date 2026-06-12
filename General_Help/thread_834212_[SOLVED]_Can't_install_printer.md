---
title: "[SOLVED] Can't install printer"
date: 2008-06-19
forum: General Help
---

### Post by editrix on 2008-06-19
Back in Dapper, I installed my HP Deskjet 3847 in Gnome and it was also installed in KDE. Now I'm in Hardy and tried the same thing.

The printer installed in Gnome, but it won't print--the Print button is greyed out.

Now in KDE 3.5.9 the printer wizard won't even work--at least, it looks nothing like what the help file says it should look like. The Add Printer Class menu option is greyed out.

I have read a number of bug reports, understanding little. But I am in the lp, scanner, and lpadmin groups. 

I found one suggestion to add myself to the usb group, but I don't see a usb group in the list of secondary groups. I also found a suggestion to install cupsys-driver-gutenprint, but it's already installed.

2.6.24-18-generic kernel, if that makes a difference.

Please help!

EDIT: Oh, this is too strange. I found a wiki that said:

Right click, KDE panel -> Configure Panel... -> Menus -> check Print System -> OK. This will put a Print System folder in the Main menu.

so I did, and the networkmanager icon went into offline mode. Since I'm on dialup it didn't affect my connection to the internet, but what has this got to do with printing?

(And I still can't install the printer!)

---

### Post by cmnorton on 2008-06-19
You are in the right groups to try [http://localhost:631](http://localhost:631). See what CUPS' interface thinks about your printer. Other than that, you can go right into the config files and look, under /etc/cups.

---

### Post by kool_kat_os on 2008-06-19
ya...try what cmnorton said... [http://localhost:631](http://localhost:631) you can configure alot of stuff there.

---

### Post by editrix on 2008-06-19
Thanks, guys, but ...

When I'm not on the internet via my hardware dialup modem, I get this message:

Could not connect to host localhost ... (can't recall the exact wording, but it was definitely port 631).

Now that I'm online with my hardware dialup modem, I don't even get that message. Both Konqueror and Firefox just keep trying to find the page--the spinners rotate, but nothing happens.

I also get the same Cannot connect message when I try to install a web proxy (both wwwoffle and polipo use localhost and a port).

FWIW, here is the entirety of my localhosts file:

127.0.0.1 localhost
127.0.1.1 darren

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by cmnorton on 2008-06-19
What does /etc/network/interfaces look like (its contents)?

What's the output of ps -ef | grep cups ?

What about ping localhost ?

---

### Post by editrix on 2008-06-19
> **cmnorton said:**
> What does /etc/network/interfaces look like (its contents)?

#The loopback network interface (for no ethernet devices)
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.130
netmask 255.255.255.0
gateway 192.168.0.2

auto eth0
iface eth0 inet static
192.168.0.130
netmask 255.255.255.0
gateway 192.168.0.2

iface ppp0 inet ppp
provider ppp0

auto ppp0

I've got a static IP because I'll eventually be connecting this box to another via crossover cable.

> What's the output of ps -ef | grep cups ?

root      4920     1  0 16:35 ?        00:00:00 /usr/sbin/cupsd
wolfgang  6035  5589  0 18:46 pts/0    00:00:00 grep cups

> What about ping localhost ?

I found another post someplace that said my /hosts file was incorrect. The first line read only 127.0.0.1 localhost instead of 127.0.0.1 localhost name_of_computer.

I've updated it since my last post here, but still no joy.

PING localhost (127.0.0.1) 56(84) bytes of data

And it's hanging. Don't know if that's as it should be.

Thanks for trying to tackle this. I'm getting desperate.

---

### Post by cmnorton on 2008-06-20
You should be able to network to localhost

This is the head of my /etc/hosts

127.0.0.1    localhost
127.0.1.1    my_host_name

---

### Post by Pjotr123 on 2008-06-20
You can try this:

- give yourself low-level authority over USB hardware: grant yourself full user rights in System - Administration - Users and Groups (make sure that every category is ticked, including scanners).
- turn on the printer
- remove the printer in System - Administration - Printers
- install HPLIP Toolbox (hplip-gui)
- start HPLIP Toolbox and let that take care of printing for you.

---

### Post by editrix on 2008-06-20
Thanks, Pjotr123--there's good news and bad news.

I got into Gnome and removed the printer. The only 2 groups I wasn't already a member of were Send & receive faxes and Use tape drives, so I ticked those. 

But, although I had HPLIP on my menu in KDE, I couldn't find it in Gnome. So, back to KDE, where I clicked on it in the menu, but it wouldn't work. hplip-gui is already installed.

(BTW, back in KDE I see that my knetworkmanager icon is now in offline mode. It was online before.)

tried /usr/bin/hp-toolbox with and without sudo and it just hung. Then, when I shut the printer **off**, a printer icon showed up in my sytem tray. But I have no idea if it's there as root's or mine :-(

However, it still won't print. The print button is greyed out. The Control Centre says there's no printer installed, and won't give me the option to install one.

There is no HPLIP documentation, no man page, nada. Finally found something that said install the documentation "hplip-doc" which is **4.2MB**, for those of us on dialup!

Now that it's installed, I don't see anything about how to install a printer. Grrr!

Sorry for all the details, but someone else searching this problem may need them.

PS: I can't get rid of the printer icon, so I suspect it's root's.

PPS: Firefox seems to be broken. I'm here only because Konqueror still works.

---

### Post by Pjotr123 on 2008-06-20
In Gnome, HPLIP Toolbox places itself in System - Preferences.  :-)

I wish that the Ubuntu installer would mention where it places the menu item, after installation of an application. You always have to look for it yourself...

Your system seems pretty messed up to me. Consider a clean reinstallation and then apply this to-do list:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)

---

### Post by editrix on 2008-06-20
> **Pjotr123 said:**
> In Gnome, HPLIP Toolbox places itself in System - Preferences.  :-)

Ack! I'm sure there's logic behind that, but not to my mind.

> Your system seems pretty messed up to me. Consider a clean reinstallation ...

For reasons I won't go into, that's a drastic step. But it was a clean install on a new (second-hand) machine so I don't know what could improve by doing it all again.

---

### Post by avtolle on 2008-06-20
What about totally removing the printer, and reinstalling it under Add Printer?

---

### Post by editrix on 2008-06-20
> **avtolle said:**
> What about totally removing the printer, and reinstalling it under Add Printer?

If you mean Add in Kubuntu, that's what I've tried but it won't work.

If you mean in Gnome, it installed but the print button was greyed out.

---

### Post by editrix on 2008-06-20
In my efforts to get an important print job done, I decided to haul out an old Win98 box and print from that. This meant moving the printer, and in the process I dropped it.

So, thanks to all those who tried to help, but I won't be pursuing this until I get another printer.

---

### Post by editrix on 2008-06-24
I don't know if my problem is 100% solved, since the printer is broken, but I can now run hp-setup and connect to localhost.

It appears my /etc/hosts was incorrect. It should have read:
127.0.0.1 localhost.localdomain localhost computername

---

