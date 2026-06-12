---
title: "Testing if graphics card or display server is broken"
date: 2016-12-03
forum: General Help
---

### Post by g3blv on 2016-12-03
I just did an upgrade to Ubuntu Gnome installation. I'm running it on an Intel NUC that is a few years old. After restart I don't get any output to the display. I'm not sure if anything went wrong in the upgrade with display server or if it is the graphics card that is broken. I have been able to log in via SSH to the computer. How can I check if it is an issue with the graphics card or the display server?

Some info about my system

    ~$ lsb_release -a
    No LSB modules are available.
    Distributor ID:	Ubuntu
    Description:	Ubuntu 16.04.1 LTS
    Release:	16.04
    Codename:	xenial

-

    ~$ sudo lshw -C display 
      *-display               
           description: VGA compatible controller
           product: Haswell-ULT Integrated Graphics Controller
           vendor: Intel Corporation
           physical id: 2
           bus info: pci@0000:00:02.0
           version: 09
           width: 64 bits
           clock: 33MHz
           capabilities: msi pm vga_controller bus_master cap_list rom
           configuration: driver=i915 latency=0
           resources: irq:45 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)

-

    ~$ lspci | grep VGA
    00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)

-

    ~$ ps -e | grep X
     1740 tty7     00:00:00 Xorg

-

    ~$ ps -e | grep tty7
     1738 tty7     00:00:00 gdm-x-session
     1740 tty7     00:00:00 Xorg
     1746 tty7     00:00:00 dbus-daemon
     1749 tty7     00:00:00 gnome-session-b
     1754 tty7     00:00:00 at-spi-bus-laun
     1759 tty7     00:00:00 dbus-daemon
     1761 tty7     00:00:00 at-spi2-registr
     1770 tty7     00:00:00 gnome-settings-
     1801 tty7     00:00:03 gnome-shell
     1841 tty7     00:00:00 ibus-daemon
     1846 tty7     00:00:00 ibus-dconf
     1850 tty7     00:00:00 ibus-x11
     1877 tty7     00:00:00 ibus-engine-sim

-

    ~$ ps afx | grep unity-system-compositor
     2749 pts/0    S+     0:00              \_ grep --color=auto unity-system-compositor

For instance when I try to start Vino I get:

    ~$ /usr/lib/vino/vino-server 
    Failed to connect to Mir: Failed to connect to server socket: No such file or directory
    Unable to init server: Could not connect: Connection refused
    Cannot open display: 
    Run 'vino-server --help' to see a full list of available command line options

Please let me know what other information that is needed.

---

### Post by mörgæs on 2016-12-04
How does it work in a live boot of 16.10?

---

