---
title: "Network Settings Problem on Ubuntu 6.10"
date: 2007-03-18
forum: General Help
---

### Post by NoSalt on 2007-03-18
Hello All

I have a weird problem with Ubuntu 6.10 and I was hoping somebody can help.

I first installed Ubuntu 6.06 last night on my old iBook 500MHz. It worked GREAT and I loved it from the start. Everything "just worked" for me and I was very happy.

For some reason, today I decided to install Ubuntu 6.10. I didn't do an upgrade (I couldn't figure out how) so I just did an erase/install.

Under 6.06 when I went to the "Network Settings" control panel then the "Connections" tab, clicked on the "Wireless connection" option then clicked "Properties". In the properties there was a drop-down selection for "Network name (ESSID)" and it would let me pick any active wireless networks that were available. Also, under the main "Connections" tab I could edit different configurations, using a drop-down selection, like "Home", "Starbucks", etc. Like I said, under 6.06 all of these things worked great.

Now ... under 6.10 whenever I try the "Network name (ESSID0)" or the "Location" drop-down all I am presented with is a very thin, empty line. There are no options available and I cannot make any new ones.

Has anybody else experienced this and if so (or even if not) do you know of a way I can fix this? I was able to make a single wireless network connection at home because I know the network name but I cannot show any others. If anybody can help I would greatly appreciate it.

Thanks in advance for reading    :)

---

### Post by xopher on 2007-03-18
```
sudo apt-get install network-manager-gnome
```

network-manager will do exactly what you want to do, but better ;) Try it out.

---

### Post by NoSalt on 2007-03-18
Thanks for the suggestion but that didn't help. I thought I would post a couple of pictures so you can see what I am talking about. Notice the very thin line under "Network name (ESSID)" (first picture) and next to "Location" (second picture). Those thin lines should be drop down menus but aren't. They were under 6.06 but not 6.10.


[IMG]http://i148.photobucket.com/albums/s7/IrateSalt/eth1.png[/IMG]

[IMG]http://i148.photobucket.com/albums/s7/IrateSalt/NetworkSettings.png[/IMG]

---

