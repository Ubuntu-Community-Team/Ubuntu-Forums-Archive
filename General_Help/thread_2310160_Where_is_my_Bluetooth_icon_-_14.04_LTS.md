---
title: "Where is my Bluetooth icon - 14.04 LTS"
date: 2016-01-16
forum: General Help
---

### Post by Xinghao_Chen on 2016-01-16
After upgraded to 14.xx LTS from 12.yy I lost the Bluetooth icon on the top-right. I thought that maybe the 14.xx release doesn't support the specific Bluetooth device as my ThinkPad X61 Tablet is an old PC. This afternoon I did an Install Updates in the System Settings and the Bluetooth icon magically appeared in the top-right row of icons! I tried and the Bluetooth icon works as it used to be. But to my disappointment after a Restart (after the Install Updates) the Bluetooth icon is nowhere to be found.

Can anyone please advise how to reload the (disappeared) Bluetooth icon (as I know now that 14.04 LTS supports it)?

---

### Post by Hadaka on 2016-01-17
Hi, please open a terminal ctrl/alt/t and do..
```
bluetooth-applet
```
*If that does not ativate your bluetooth icon then
click,system settings >>bluetooth ,verify it is ON
You may also click the system settings in the upper right corner
then Startup Applications at the startup applications prefrences screen
click ADD and enter bluetooth-applet. This will force the bluetooth to
start and display the icon each time you start your computer.
good luck.

---

### Post by deadflowr on 2016-01-17
Is Bluetooth a Section in System Settings for you?
If so, if you open the Bluetooth Section, is there a check box in the bottom left corner that says: 
Show Bluetooth Status in the Menu Bar
?

---

### Post by Xinghao_Chen on 2016-01-17
The Bluetooth icon is back in the System Settings/All Settings page after I clicked on the Install Updates and ran the updates a few times. In the All Settings/Bluetooth page there is this little check box at the bottom "Show Bluetooth Status in the menu bar" and the the check was not "memorized" until I check the box + reboot a couple of times. Now it appears to work fine that the little Bluetooth icon appears in the top-right menu bar after system is up.

To Hadaka: I don't fine a Startup Application in System Settings/All Settings. Perhaps it is located somewhere else?

---

### Post by deadflowr on 2016-01-18
> **Xinghao_Chen said:**
> The Bluetooth icon is back in the System Settings/All Settings page after I clicked on the Install Updates and ran the updates a few times. In the All Settings/Bluetooth page there is this little check box at the bottom "Show Bluetooth Status in the menu bar" and the the check was not "memorized" until I check the box + reboot a couple of times. Now it appears to work fine that the little Bluetooth icon appears in the top-right menu bar after system is up.

To Hadaka: I don't fine a Startup Application in System Settings/All Settings. Perhaps it is located somewhere else?

Point 1 would be it's possible that the bluetooth wasn't being initially recognized on start.
But that is more of an anything is possible possible, more in the unlikely than likely category.

Point 2 Startup Applications hasn't been in the system settings for a long time, if ever.
You need to search for it in the dash.

---

### Post by Xinghao_Chen on 2016-01-18
Thank you all for the feedback and advice.

---

### Post by Hadaka on 2016-01-18
Hi, click the "sun/star" shaped icon..top far right .. the same one you use to shutdown
you should see 'Startup Aplications...'      see attached:
[ATTACH=CONFIG]266818[/ATTACH]

---

### Post by Xinghao_Chen on 2016-01-18
I don't see a Startup Applications. When I click on the gear wheel symbol, the menu entries are: 
About This Computer
Ubuntu Hep
System Settings ...
Lock
Guest Session
<<My Session>>
Logout ...
Suspend
Shut Down ...

---

### Post by deadflowr on 2016-01-18
The startup applications was removed from the dropdown cog area well before 14.04 came out.
(I think it was remove in 12.10, around the same time the username disappeared in the panel)

It does exist in 12.04, though...

---

