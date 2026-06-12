---
title: "Minimising an app to system tray"
date: 2021-03-23
forum: General Help
---

### Post by abinav-shankar on 2021-03-23
Hi,

Is there a way to force applications to run silently in the system tray? Thunderbird needs to be running all the time to receive new mails. I found a plugin [Minimize on Close]("https://addons.thunderbird.net/en-US/thunderbird/addon/minimize-on-close/?src=ss") to keep it running but it remains on the application bar and keeps getting in the way. I want to push it to the system tray when minimised. I found an app [AllTray]("https://github.com/mbt/alltray") to do this. But it doesn't work. It opens up in an empty app window that cannot be closed until restart in Ubuntu 20.10. Is there any other way of doing this?

Thanks.

---

### Post by blackbird34 on 2021-03-23
I googled a bit. Is this what you're looking for? 

Edit: I didn't find the option mentioned below in my own Thunderbird preferences (Kubuntu 20.10 / Thunderbird 78.7.1)

However there's a project on github that seem to have solved this issue and set up an Ubuntu PPA: [https://github.com/Ximi1970/systray-x](https://github.com/Ximi1970/systray-x)

--------------

[Windows Tip] Use Minimize to System Tray Feature in Mozilla Thunderbird
- Last updated on July 18, 2020 by VG

> Now the good news is that finally **the newer versions of Mozilla Thunderbird (version 78 and later) come with &#8220;Minimize to System Tray&#8221; functionality built-in**.  If you are using a new version of Thunderbird, you don&#8217;t need to use  any extra extension to add this feature. You can activate and enable  &#8220;Minimize to System Tray&#8221; feature using Thunderbird settings.
 If you also want to enable minimize to system tray functionality in Mozilla Thunderbird, following steps will help you:
 **1.** Open Mozilla Thunderbird and press **ALT** key on your keyboard to temporarily show Menu bar. Now select **Tools -> Options**.

 Alternatively, you can click on 3-lines Hamburger menu present at the end of the toolbar and select **Options**.

 It&#8217;ll open Thunderbird Options page.
 **2.** In **General** tab, look for following option in right-side pane:[INDENT]When Thunderbird is minimized, move it to the tray
[/INDENT]
Enable the option and it&#8217;ll activate minimize to system tray functionality in Thunderbird.



[https://www.askvg.com/tip-use-minimize-to-system-tray-feature-in-mozilla-thunderbird/](https://www.askvg.com/tip-use-minimize-to-system-tray-feature-in-mozilla-thunderbird/)

---

### Post by CatKiller on 2021-03-23
You don't have a system tray.

Some desktop environments have a notification area for notifications. 

> **abinav-shankar said:**
> Is there any other way of doing this?

It sounds like you haven't yet discovered workspaces/virtual desktops.

---

