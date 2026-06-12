---
title: "Broke x server when I installed IE6"
date: 2006-12-10
forum: General Help
---

### Post by HeavyEddie on 2006-12-10
I installed IE6 using [this tutororial]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Internet_Explorer_.2B_Flash_9_.28IEs4Linux.29") tonight.  I really wish the warning to not do this as root was at the beginning.

Now when I boot it says x server failed to start.   It also mentions that it can't configure the default locale for LC_ALL.  I've tried to reconfigure the xserver and locale using the following.  Both fail.

> sudo dpkg-reconfigure locales
dpkg-reconfigure xserver-xorg


---

### Post by riven0 on 2006-12-10
That what happens when you install IE6. :mrgreen: 

Try this instead:
> 
sudo apt-get install --reinstall xserver-xorg

---

### Post by HeavyEddie on 2006-12-10
Yeah, I didn't want to... but the wife uses OWA for work.

It doesn't work because it is failing to fetch anything.  Doesn't seem to want to connect to the network.  I was reconfiguring the network when I rebooted to give it a try.  Obviously I got the static settings wrong :)  Can I move that back to DHCP via the shell then give this a try?

---

### Post by riven0 on 2006-12-10
> **HeavyEddie said:**
> Yeah, I didn't want to... but the wife uses OWA for work.

It doesn't work because it is failing to fetch anything.  Doesn't seem to want to connect to the network.  I was reconfiguring the network when I rebooted to give it a try.  Obviously I got the static settings wrong :)  Can I move that back to DHCP via the shell then give this a try?

Hmm, not too knowledgeable about configuring the network, but can you bring up your network interface and copy the output here? 

> sudo nano /etc/network/interfaces

Maybe I can try comparing it to mine. I'm assuming your on a wired ethernet network, right?

---

### Post by HeavyEddie on 2006-12-10
Sorry, looks like I fell asleep at the keyboard this morning.  How fun in a strange ironic way.  Haven't done that since the days I was excited about computers and felt I was learning :)

Anyway, I ended up editing /etc/network/interfaces and changed the adapter to dhcp and I was back online.

I then performed the re-install and it appears that I'm up and running with a graphical interface again.  Thanks for the help.  I'm still getting that LC_All locale errors though.

---

