---
title: "who needs cups-browsed? (xubuntu 16.04 slow reboot/shutdown)"
date: 2017-02-08
forum: General Help
---

### Post by r.stiltskin on 2017-02-08
After doing a system upgrade from 14.04 to 16.04 (and switching from Kubuntu to Xubuntu) my laptop was taking a long time to shut down or reboot.  I assume that there are various possible causes for a symptom like this but in this case it turned out to be related to cups-browsed (1.8.3-2ubuntu3.1), possibly due to cups shutting down before cups-browsed, or possibly something involving cups-filters (both discussed in [this thread]("https://bugs.launchpad.net/ubuntu/+source/cups-filters/+bug/1579905")).  The shutdown sequence would get through "Stopped D-Bus System Message Bus" and then hang for 90 seconds before continuing.

First I tried solving it by reducing the timeout to 10 seconds as suggested by [COLOR="#FF8C00"]unhammer[/COLOR] in [this thread]("http://askubuntu.com/questions/760952/slow-shutdown-on-ubuntu-16-04-lts-stopping-thermal-daemon-running-fit-make-remo") but then decided that even waiting 10 sec was annoying so I decided to try uninstalling cups-browsed.  This completely solved the problem -- rebooting or shutting down now proceeds as fast as it should.  Also, even after uninstalling cups-browsed I had no problem locating, installing, and using my 3 network printers.

So the question is -- what exactly is cups-browsed needed for?  The package description talks about browsing Bonjour broadcasts to make the printers available locally.  But I'm able to find a Canon Pixma IP7200, an Epson WF3520 and an HP Laserjet P1606dn on my LAN without that package so what kind of printers depend on Bonjour?


[Note: to see if your slow shutdown is caused by this package, you can comment out the line in /etc/default/grub that says:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
(just place a # at the beginning of that line)
and then run
sudo update-grub
so that you can see the messages produced during the shutdown process.  When it hangs, press the Meta (Windows) key to show what is happening during the pause.  If your problem is related to cups-browsed you should see:
"A stop job is running for Make remote CUPS printers available locally".]

---

### Post by Morbius1 on 2017-02-08
> So the question is -- what exactly is cups-browsed needed for?  The  package description talks about browsing Bonjour broadcasts to make the  printers available locally.  But I'm able to find a Canon Pixma IP7200,  an Epson WF3520 and an HP Laserjet P1606dn on my LAN without that  package so what kind of printers depend on Bonjour?

I hate to make absolute statements because I'm sure there is an exception out there but I think all relatively current printers are Bonjour ( Avahi in Linux ) enabled. cups-browsed not only searches for printers but also automatically creates local print queues for these printers. If you can find them without it then disable the service.

---

