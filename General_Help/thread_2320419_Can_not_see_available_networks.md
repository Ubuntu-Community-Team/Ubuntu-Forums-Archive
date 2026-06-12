---
title: "Can not see available networks"
date: 2016-04-13
forum: General Help
---

### Post by nu2this2 on 2016-04-13
Recently installed Lubuntu 14.04 DT. I can access my own network but can not see other WIFI hotspots. For instance my local library and coffee shops networks aren't visible. Am planning a trip soon and would  like to browse the web and check email. Can anyone suggest a solution?

Thank you.

---

### Post by nothingspecial on 2016-04-13
Hi 

You need to provide more information

Which networks can you see?

What have you tried?

Are you getting any errors?

Do you have a screenshot of the issue?

---

### Post by grahammechanical on 2016-04-13
I am not using Lubuntu so I cannot give clear directions but some where there should be a utility that will list all the wireless access points that are in range. This command will also do it.

```
sudo iwlist scan
```

The names that appear after ESSID are the names of the wireless access points in range. How you connect to them in Lubuntu I cannot tell you. 

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections)

Regards

---

### Post by nu2this2 on 2016-04-14
Thanks for the command.
The screen say's.

  IE: Unknown 2A0104
  IE: Unknown 2F0104
  IE: IEE 802.11i/WPA2 Version 1
 
Then there are a lot of lines of numbers and letters and finally this,


Interface doesn't support scanning.

I will try to see if I can figure out the way to take and post a screen shot.

---

### Post by nu2this2 on 2016-04-14
Hi there,

After some searching I think the problem is solved. This was the procedure:


Menu, Preferences > Default applications for LXSession, then click on the Autostart tab and under "Manual autostarted applications" type "nm-applet", then click the "+ Add" button on the left.

It appears as though Network manager is appearing in the lower left of the screen panel now. It wasn't there before. I can now see networks other than my own.

Sorry but I don't know how to post a "SOLVED" reply. If anyone can please let me know how.

Thank you.

---

