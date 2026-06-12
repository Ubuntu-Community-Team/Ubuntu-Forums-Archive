---
title: "Zoom problem - &quot;Your internet connection is unstable&quot;"
date: 2023-08-26
forum: General Help
---

### Post by Tom_Carr on 2023-08-26
When using Zoom I often get a message saying "Your internet connection is unstable".  Sometimes the pictures on screen freeze.


I watch youtube and Netflix videos on this computer and have no problems.


I have a wired connection directly from my comcast modem to the desktop where I use Zoom.  I did an internet speed test and got speeds of 87.6 Mbps download,  11.7 Mbps upload.


I did an uninstall and install of zoom-client using the ubuntu software app.  I am running the latest stable version, 5.15.2.4260.


What is the next step in solving the problem?

---

### Post by wyattwhiteeagle on 2023-08-26
> **Tom_Carr said:**
> When using Zoom I often get a message saying "Your internet connection is unstable".
Sometimes the pictures on screen freeze.
Freezing screen picture's are most often a symptom.
> **Tom_Carr said:**
> I watch youtube and Netflix videos on this computer and have no problems.
Do you watch YouTube and Netflix through Zoom?
Zoom may be a snap. Snap's tend to cause problem's.
Are you using any snap's?
> **Tom_Carr said:**
> I have a wired connection directly from my comcast modem to the desktop where I use Zoom.
I did an internet speed test and got speeds of 87.6 Mbps download, 11.7 Mbps upload.
Direct wired connect...that can't be the problem unless the modem is actually a access point using antenna, no wire, to give you connection.
Comcast modem...you may need to check your ModemManager configurations.
Zoom or the modem may not be configured properly for best compatability.
> **Tom_Carr said:**
> I did an uninstall and install of zoom-client using the ubuntu software app.
I am running the latest stable version, 5.15.2.4260.


What is the next step in solving the problem?
Next step would be gathering fact's and info's.

---

### Post by Rubi1200 on 2023-08-27
I would try the following steps first:

Open Zoom and click on your profile picture. Go to "Settings" > "Advanced" > "Troubleshooting." Run the network diagnostic tool to identify issues.

Also try restarting the Network Manager:
```
sudo systemctl restart NetworkManager

```

If you are using VPN, temporarily disable it to see if that makes a difference.

Do any these steps resolve the issue?

---

