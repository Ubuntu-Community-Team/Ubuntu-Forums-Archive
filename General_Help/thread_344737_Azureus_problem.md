---
title: "Azureus problem"
date: 2007-01-23
forum: General Help
---

### Post by lemmy999 on 2007-01-23
When I open Azureus and try and start a download the app just shuts itself down. From terminal the output is as follows

> chris@chris-desktop:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  Internal Error (53484152454432554E54494D450E43505001A3), pid=5941, tid=3085379248
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid5941.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)
chris@chris-desktop:~$ 


Any thoughts?

---

### Post by highneko on 2007-01-23
How did you install java? How did you install azureus?
[http://www.google.com/search?hl=en&q=53484152454432554E54494D450E43505001A3](http://www.google.com/search?hl=en&q=53484152454432554E54494D450E43505001A3)
[http://www.ubuntuforums.org/showthread.php?t=288004](http://www.ubuntuforums.org/showthread.php?t=288004)

---

### Post by lemmy999 on 2007-01-23
Came as part of the ubuntu christmas package!

---

### Post by stealth17 on 2007-01-28
I'm having the exact same problem.

To fix it goto ~/.azureus and delete the files inside that directory.

That worked for me for a few hours and it started crashing again.


I'm on 6.10, upgraded from 6.06. I can't remember how I installed java. I think I'm going to reinstall ubuntu since I just got a new 500g HDD and hopefully it will clear the issue up.

---

### Post by etank on 2007-01-28
Try out qBittorrent. [http://qbittorrent.org](http://qbittorrent.org)

---

### Post by stealth17 on 2007-01-29
Here is the solution.

Open up Gnome Terminal or similar. Type:

```
sudo apt-get remove --purge azureus
```Then:

```
cd ~/.azureus
rm -r *
```Now we will install azureus via the "[alternative method]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#.28Alternative_Method.29")." The rest has been taken directly from the UbuntuGuide.org

```
wget [http://kent.dl.sourceforge.net/sourceforge/azureus/Azureus_2.5.0.2_linux.tar.bz2](http://kent.dl.sourceforge.net/sourceforge/azureus/Azureus_2.5.0.2_linux.tar.bz2)
sudo tar jxvf Azureus_2.5.0.2_linux.tar.bz2 -C /opt/
sudo gedit /usr/share/applications/azureus.desktop
```Add the following to the new file:
```
[Desktop Entry] 
Name=Azureus
Comment=Java BitTorrent Client
Exec=/opt/azureus/azureus
Icon=/opt/azureus/Azureus.png
Terminal=false
Type=Application
Categories=Application;Network;
```[LIST]
[*]Save the edited file
[*]Applications -> Internet -> Azureus
[*]or /opt/azureus/azureus[/LIST]*note- you will have to chown the /opt/azureus to install updates.

```
sudo chown -R youruser:youruser /opt/azureus
```It has worked great for me so far, hope it does for the rest of you!

---

### Post by Denn1s on 2007-01-29
wath do you have selected under:
```
update-alternatives --config java
```
if it is not sun`s latest java maybe changing it may help

---

### Post by janko33 on 2007-02-08
Hi!

A typo in the line 

```
cd ~./.azureus
```

it should be 

```
cd ~/.azureus
```

---

### Post by stealth17 on 2007-02-08
> **janko33 said:**
> Hi!

A typo in the line 

```
cd ~./.azureus
```it should be 

```
cd ~/.azureus
```

woops, my bad. fixed. thanks.

---

### Post by bionnaki on 2007-02-08
try ktorrent. 

sudo apt-get install ktorrent

---

### Post by fabiodasoghe on 2007-02-08
I had exactly same problem. Reinstalling azureus resolved only for some time.

I also tried to use Automatix, but it seems broken (at least in my case): the menu icon started with a pop up error.

I was going to erase my ~/.azureus directory (loosing all partial download), but first I tried another thing.

I removed azureus from automatix, then reistalled it (again from automatix), then I tried to launch it from the shell.. it wasn't in the path. I edited the menu item and put into it the complete path (/opt/azureus/azureus), then it started!

I updated azureus with its integrated update system, and it complained about user rights...
To fix this, I exited azureus, then in a shell:
```
cd /opt/azureus
sudo chown -R fabio azureus/

```
where fabio is my username. Then restared azureus, updated and now it's working again.

I was scared about it eventually stop working again, then I found this thread:

[http://www.ubuntuforums.org/showthread.php?t=354922]("http://www.ubuntuforums.org/showthread.php?t=354922")

In few words, It seems the version in the repository was broken: I hope the fast update I did was enough to resolve it (it seems so: now I have the latest versione, 2.5.0.4).

Hope this helps.

Cheers,

Fabio

---

