---
title: "Several apps not finding required resources after softwware center change to snap"
date: 2022-02-02
forum: General Help
---

### Post by proctorius on 2022-02-02
Hello,

I am having a recuring problem on Ubuntu 21.04.

Since the change in the software center certain apps have been unable to locate resources.  The one I am struggling with today is a Firefox extension called "Video DownloadHelper"  [https://www.downloadhelper.net](https://www.downloadhelper.net) 

For some videos, a companion app is required to be installed, net.downloadhelper.coapp-1.6.3-1_amd64.deb located at [https://www.downloadhelper.net/install-coapp?browser=firefox](https://www.downloadhelper.net/install-coapp?browser=firefox) being the relavent installer download page.

Once installed, the Video Downloadhelper is unable to locate the installed comanion app and just repeatedly tells me that I need to install the companion app, even though it is already installed.  When I do the check for the companion app within the plugin settings it returns: Checking companion app returned:  *No such native application net.downloadhelper.coapp*

----this is not the only app I have had this issue with---- I have had similiar issues with apps that have plugins (audio, image editing) that are installed through the software center (or the underlying program that actually does the installing).

I have tried: 
-Installing via the software center, and via apt.
-Restarting the computer.
-Logging out and loging back in
-restarting firefox.
-restarting the plugin
-uninstalling and reinstalling the companion app
-uninstalling an reinstalling the plugin
-doing the above in every concievable order.

I suspect that because there is a new install method through the software center, there is somethnig like 'sandboxing' or the folders have changed.  The companion app show as being isntalled in the software center 'installed' tab.  I do not know how to make an app  a 'natiove app' un linux.  I am pretty green when it comes to linux.  I am trying to only use linux (so to fully move over) and have been Linux only for about 4 months.  Any help would be appreciated.  I need to be able to download the videos for my foster child who needs them for school.

---

### Post by Impavidus on 2022-02-02
Welcome to the list of people who're not happy with snaps.

Ubuntu 21.04 is no longer supported. If that was no typo, get on a supported release. A move to 21.10 should be easy. Firefox is still available as a normal .deb on both 20.04 and 21.10. Maybe that works better.

---

### Post by proctorius on 2022-02-04
I have now tried several (re) installation methods to no avail.  I don't think the issue is specific to the snap isntal, I think it is specific to changes made due to/along with the change to snap being the new standard for the software center.  

It seems to me that the main app cannot find the expected directory fro the plugin/companion app in some cases.  

Anyone have any ideas?

---

### Post by Impavidus on 2022-02-04
Well, I use neither snaps nor the software centre. But I've understood that, over the years, the software centre has become more confusing due to hiding too many details in an attempt to become friendlier to less advanced users. Dealing with Firefox extensions and companion applications may be too advanced for it.

---

### Post by tea for one on 2022-02-04
> **proctorius said:**
> I have now tried several (re) installation methods to no avail.  I don't think the issue is specific to the snap isntal, I think it is specific to changes made due to/along with the change to snap being the new standard for the software center.  It seems to me that the main app cannot find the expected directory fro the plugin/companion app in some cases.  Anyone have any ideas?

You can still install the gnome-software package.
```
sudo apt install gnome-software
```
Also, there is synaptic.
```
sudo apt install synaptic
```

---

### Post by dragonfly41 on 2022-02-04
I will also suggest installing a Stacer dashboard to offer more visibility of resources, apps etc.

[https://oguzhaninan.github.io/Stacer-Web/#:~:text=Stacer%20is%20an%20open%20source,all%20in%20one%20system%20utility](https://oguzhaninan.github.io/Stacer-Web/#:~:text=Stacer%20is%20an%20open%20source,all%20in%20one%20system%20utility).

---

