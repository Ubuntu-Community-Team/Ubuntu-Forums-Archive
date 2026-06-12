---
title: "Azureus-CLI and webui"
date: 2007-08-09
forum: General Help
---

### Post by jdarias on 2007-08-09
Hello.
I've read a lot of azureus wiki pages, about how to set the azureus CLI interface, using it as a daemon and controlling it via a webui (either the html one or the swing one).
The problem here is that when i start azureus in a console, the webui won't work at all. The browser refuses the connection. 
Firewall/port forwarding problems? No, i've already forwarded it :( Also, no matter if the port is forwarded or not, when i start azureus in graphic mode (the normal way) the webui works flawlessly.
What i'm doing wrong?
i got Azureus 2.3.0.4, java 1.6.

---

### Post by swoskow on 2007-08-10
i see you are not getting much response on this so i will try to help.  i do not claim to be an expert but i have spent a lot of time setting up azurues and i do have the web interface working.  the first thing i would recommend is updating azureus to the latest version (2.6.2).  You should be able to do this right from the help menu or uninstall the current version and reinstall via synaptic (or whatever you use).  once you do that come back to the forum and let me know and i can walk you through setting it up.  it should not be very difficult - i was able to set them up and now i am working on azsrmc which you may also be interested in.

---

### Post by swoskow on 2007-08-10
> **swoskow said:**
> uninstall the current version and reinstall via synaptic (or whatever you use).  once you do that come back to the forum and let me know and i can walk you through setting it up. 

FYI - if you do it through the repository (synaptic) it does have a bug but the fix is easy - follow these instructions [http://ubuntuforums.org/showthread.php?t=144546](http://ubuntuforums.org/showthread.php?t=144546)

---

### Post by bond711 on 2007-08-21
Hey all, new here

currently I'm just logging in through my kvm and running

```
java -jar /opt/azureus/azureus.jar --ui=console
```

i found this to damonize it:[http://www.azureuswiki.com/index.php/DaemonizedAzureus](http://www.azureuswiki.com/index.php/DaemonizedAzureus)

```
java -jar /opt/azureus/azureus.jar --ui=console >/dev/null 2>&1 </dev/null &
```

how can i have this execute at startup?


cheers

---

### Post by Aetherius on 2007-08-21
@bond 711

open terminal and type

```
sudo nano /etc/init.d/azureus-daemon.sh
```

(substitute "sudo nano" with "gksudo gedit" if you're not comfortable with using a command line editor)

paste in

```
#!/bin/bash
java -jar /opt/azureus/azureus.jar --ui=console >/dev/null 2>&1 </dev/null &
```

hit ctrl+x and then hit Y to save (or just click save if you are using gedit)

//----------
*EDIT*

You should probably at this point make the script executable, to do this type......

```
sudo chmod a+x /etc/init.d/azureus-daemon.sh
```

*END-EDIT*
----------//

now type in the following

```
sudo update-rc.d azureus-daemon.sh defaults 99
```

This will getting it running right from boot by creating the appropriate links in the /etc/rcX.d directories using default run levels. The number 99 means that the script is called after most of the other startup commands. I use this as I presume other system startup things are more of a priority.

Hope this helps ;)

@jdarias

I had problems getting the webui working via command-line for a couple of reasons.

First I'd recommed you make sure you have the latest version with the default Azureus2.jar file (some of the modified ones like BitTyrant seem to mess with the webui). Second you should make sure you are using the Sun JRE as in my experience Azureus is just happier that way. Third and final, if you are using the Swing webui, try the HTML webui (i much prefer it to be honest) or vice versa.

Failing that have a look at AzSMRC as swoskow mentioned. It allows Azureus to operate in a client-server fashion. Very poweful and very interesting.

Later.

---

### Post by swoskow on 2007-08-25
> **Aetherius said:**
> @bond 711

Failing that have a look at AzSMRC as swoskow mentioned. It allows Azureus to operate in a client-server fashion. Very poweful and very interesting.

Later.

Just to update - I tried the web ui and swing ui but found AZSMRC to work best for me.  I was able to get it up and running on both my Ubuntu and Windows computers and it works great as an interface for both.  I use my Ubunutu box as a server and through AZSMRC I download from all my home computers (Windows, Ubuntu and even my wifes MAc) to the Ubuntu box and store all my music on the Raid 5 I have on that box.  Then use Samba (or other file share I also have a Lamp server set up) and you have a very powerful music server you can access from both Ubuntu and Windows.

As Aetherius stated - "very powerful and interesting"

---

