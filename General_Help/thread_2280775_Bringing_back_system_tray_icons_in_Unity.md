---
title: "Bringing back system tray icons in Unity"
date: 2015-06-02
forum: General Help
---

### Post by hojjat on 2015-06-02
I am using 14.04 and I have the libappindicator1 package installed too, but somehow I cannot see certain icons in the system tray (including DavMail and Pidgin, to name a few). I do see Dropbox icon there, so I'm not sure how this is happening.

I tried adding all icons to the whitelist using [COLOR="#800080"]gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"[/COLOR] as has been recommended in multiple forum posts online, but the setting com.canonical.Unity.Panel doesn't exist any more.

Please advise!

---

### Post by QDR06VV9 on 2015-06-02
**Update see post #5 for solution**
Just Maybe this will help [http://askubuntu.com/questions/449751/system-tray-icons-and-dconf-editor-in-14-04](http://askubuntu.com/questions/449751/system-tray-icons-and-dconf-editor-in-14-04)
Read the whole page.
Regards

---

### Post by hojjat on 2015-06-02
Unfortunately that was not helpful.

---

### Post by QDR06VV9 on 2015-06-02
_**See the Post Below for solution**_

Regards

---

### Post by CantankRus on 2015-06-02
If you still need a system tray in Ubuntu (Unity), you don't need the patched Unity any more. 
Instead, you can simply install `Indicator Systemtray Unity`, a new AppIndicator which adds a system tray to the Unity panel.
[http://www.webupd8.org/2015/05/on-demand-system-tray-for-ubuntu.html](http://www.webupd8.org/2015/05/on-demand-system-tray-for-ubuntu.html)

After installing, logout and log back in and if any application is running that uses the system tray
the icon shown in pic will be visible.

---

### Post by yetimon_64 on 2015-06-03
> **CantankRus said:**
> If you still need a system tray in Ubuntu (Unity), you don't need the patched Unity any more. 
Instead, you can simply install `Indicator Systemtray Unity`, a new AppIndicator which adds a system tray to the Unity panel.
[http://www.webupd8.org/2015/05/on-demand-system-tray-for-ubuntu.html](http://www.webupd8.org/2015/05/on-demand-system-tray-for-ubuntu.html)

After installing, logout and log back in and if any application is running that uses the system tray
the icon shown in pic will be visible.
Thanks CantankRus, that works nicely here to get back my easystroke tray icon in 14.04. I had tried a couple of other ppas without any luck, including "timekiller/unity-systrayfix".

 And thanks to          hojjat, I saw this question yesterday and subscribed. Indicator Systemtray Unity works nicely here with a bit of tweaking of the position with dconf-editor; as is noted in the webupd8 link CantankRus posted. Cheers.

---

### Post by QDR06VV9 on 2015-06-03
Good Job CantankRus! I just don't use Unity but I was kind of stunned to see the PPAs Associated for that very problem!
I will Amend my first post if it shows no success.

---

### Post by mc4man on 2015-06-03
As far as positioning one can also use scroll on the indicator itself

---

### Post by hojjat on 2015-06-05
timekiller/unity-systrayfix did not help. ppa:fixnix/indicator-systemtray-unity did help! I wish it had an option to make it static, but have it automatically appear to the left of the last icon in Unity's built-in indicator area.

---

