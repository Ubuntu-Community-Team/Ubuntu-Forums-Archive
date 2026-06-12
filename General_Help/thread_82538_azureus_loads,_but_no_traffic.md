---
title: "azureus loads, but no traffic"
date: 2005-10-26
forum: General Help
---

### Post by Steve Quezadas on 2005-10-26
Hello,

I have looked all around on google and the ubuntu forums and I cannot find the solution to this one. I downloaded the latest version of azureus 2.3.0.4, on my "breezey badger 5.10" ubuntu, just freshly installed. Azureus did not seem to be in the repository. However, I downloaded the generic installer from the official site. It loads, but when I load the torrent, no traffic comes in and out. 

I suspect this has something to do with the java library not loading correctly. Has anyone ever experienced this problem?

---

### Post by PriceChild on 2005-10-26
Try searching further down this forum for instructions on how to update java to 1.5

Also... you may want to check it is Azureus and not just that torrent, by starting one of the ubuntu disk torrents.

---

### Post by Hallavej on 2005-10-26
[QUOTE=PriceChild]Try searching further down this forum for instructions on how to update java to 1.5

Also... you may want to check it is Azureus and not just that torrent, by starting one of the ubuntu disk torrents.[/QUOTE]

I am running it in Blackdown java 1.4. Works fine. You dont need java 1.5. Run it from the terninal and have a look at the messages. This is what mine says, and it works.

$ /usr/local/azureus/azureus
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2-02]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/usr/local/azureus/Azureus2.jar:/usr/local/azureus/sw t.jar:/usr/local/azureus/swt-mozilla.jar:/usr/local/azureus/swt-pi.jar" -Djava.l ibrary.path="/usr/local/azureus" -Dazureus.install.path="/usr/local/azureus" org .gudy.azureus2.ui.swt.Main ''
**** DHT: Anti-spoof currently disabled for old clients ****

---

### Post by Steve Quezadas on 2005-10-27
Actually, I figured out what went wrong. Apparently, Azureus does not like the java runtime that comes with Ubuntu Breezey. I manually installed the Sun java runtime . There is no ubuntu package for it, I had to install it manually from the sun site. I then linked /usr/bin/java to the java binary from sun.

Then Azureus worked fine.

---

