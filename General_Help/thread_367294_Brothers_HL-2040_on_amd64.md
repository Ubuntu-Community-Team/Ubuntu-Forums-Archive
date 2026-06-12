---
title: "Brothers HL-2040 on amd64"
date: 2007-02-22
forum: General Help
---

### Post by pay on 2007-02-22
Hey,
        I've been trying to set up my Brothers HL-2040 on an amd64 installation of Feisty Fawn. What I did was ```
sudo ln -s /etc/init.d/cupsys /etc/init.d/cups
sudo aptitude install gimp-print
sudo aptitude install cupsys-driver-gimpprint
sudo aptitude install cups
sudo aptitude install cupsomatic-ppd
sudo mkdir -p /usr/lib/cups/filter
sudo dpkg -i --force-architecture brhl2040lpr-2.0.0-1.i386.deb
sudo dpkg -i --force-architecture cupswrapperHL2040-2.0.0-1.i386.deb
```Some of those drivers were already installed but I put them there since I can't remember which ones were already installed or not.

I then changed the port to LPT #1 since that's the one. Everything looks like it is working fine but when I click print it just spits out every page in the tray and jams. What am I doing wrong?

Thanks in advance, pay.

---

### Post by pay on 2007-02-26
Okay this is what I'm getting in [http://localhost:631/printers](http://localhost:631/printers)
> [HL2040]("http://localhost:631/printers/HL2040") "Filter "brlpdwrapperHL2040" for printer "HL2040" not available: No such file or directory"

---

### Post by jamesnewell on 2007-06-03
Hi,
I'm quite new to linux. On Xubuntu 7.04 AMD64 I had the same problem, of endless blank pages being printed to a shared networked printer on a WinXP machine.

I installed the drivers and still couldn't get it working. Then i uninstalled the drivers, removed the printer from the web admin and reinstalled the drivers and the printer using the "Brother HL-2060 Foomatic/hl1250 (recommended)" driver.

It now works beautifully.

---

