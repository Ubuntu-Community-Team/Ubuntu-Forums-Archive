---
title: "Sync Palm to Evolution or Thunderbird with Bluetooth"
date: 2008-02-05
forum: General Help
---

### Post by pullinsb on 2008-02-05
After about 12 hours this past week, I have still not been able to get my Evolution to sync with my Palm Treo 700p.

I followed this HOW TO:

[http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html](http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html)

and got my Palm to sync PERFECTLY with J-Pilot.

I got my Palm a few weeks ago, but I use Thunderbird+Lightning on my Windows partition, and of course, I can't get that to sync. So, I'm on my linux partition trying to get Evolution to sync.  If I don't get Evolution or Thunderbird to sync to my Treo, I will be forced to install Outlook (*shudder*)

I've exhausted google and the ubuntu forums searching for a way to get the gnome-pilot to recognize my bluetooth connection (net:any) for my phone. 

Gnome-pilot apparently doesn't work with bluetooth?
Evolution doesn't use anything other than gnome-pilot to sync?

Is there maybe a way to mount my bluetooth-serial connection to a locale that gnome-pilot will accept??


.....please don't let me install outlook!!!

---

### Post by pullinsb on 2008-02-05
boo outlook!

---

### Post by pullinsb on 2008-02-06
nothing?

---

### Post by randyclark on 2008-03-09
After following the HOWTO you used, I also couldn't get it to work. 

But yesterday, I found the following suggestion (and now I can't find where) and it worked for me.

(1) Pair the phone with your computer
(2) If you used the same script names as the HOWTO, open a terminal and enter:

sudo dund -s call treo

I then hit Hotsync and it synced perfectly!

I would add the caveat that others have noted that the Evolution ToDo conduit hangs on undated To Do's. 

I am not very technically savvy on Linux but this worked for me.

Randy

---

### Post by ALittleSlow on 2008-03-19
> **pullinsb said:**
> 
I followed this HOW TO:

[http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html](http://elijah.pinoguin.com/blog/blog-view/article/sync-treo-650-on-ubuntu-linux.html)
[snip]

I've exhausted google and the ubuntu forums searching for a way to get the gnome-pilot to recognize my bluetooth connection (net:any) for my phone. 

Gnome-pilot apparently doesn't work with bluetooth?
Evolution doesn't use anything other than gnome-pilot to sync?

Is there maybe a way to mount my bluetooth-serial connection to a locale that gnome-pilot will accept??

I got this to work using Elijah's instructions, gnome-pilot, and Evolution under gutsy (7.10) with a Sprint Treo 755p and a Dell D600 laptop and a TBW-105UB USB Bluetooth adapter.

1. Follow Elijah's instructions until you get to the Test Hotsync section. (If you get a Error:Serial:0x030B on the Treo when you try to connect to the new network, see the footnote below.)
2. From the Gnome menu, choose System->Preferences->Palm OS Devices.
3. (If this is the first time you've run this, you'll get a wizard. In this case, follow the prompts, and tell it you want to sync over the network. Re-open the dialog and check the settings as follows.) At the gnome-pilot settings dialog, choose the Devices tab. 
4. If you don't see a device of type "Network", Choose Add..., give it a name, set the type to Network.Choose OK. 
5. Close the gnome-pilot-settings dialog.
6. Hot sync from your Palm using the modem sync.

That should do it. 

Notes: 
a. If you get a Error:Serial:0x030B on the Treo when you try to connect to the new network, do the following (may only apply to Ubuntu gutsy; thanks to  [Greg963]("http://ubuntuforums.org/archive/index.php/t-328880.html")):
   1) As the superuser, edit /etc/default/bluetooth.
   2) After these two lines (which occurs in two places),
     ```
start-stop-daemon --start --quiet --exec $HCID -- $HCID_OPTIONS || true
log_progress_msg "$HCID_NAME"
```

      add this line:
     ```
 sleep 1
```
   3) restart the bluetooth services (e.g.by typing "sudo /etc/init.d/bluetooth restart" from a shell prompt).
b. I don't think you need to change the LANSync Prefs. You can leave this set up to do a cradle/cable direct sync, for instance.
c. Under Hotsync settings->Primary PC setup, it works better if you do in fact leave the PC name and/or netmask blank.
d. You need to make sure you choose IP addresses that are not in use on your LAN. From a shell prompt, type "netstat -i". If you see a destination or gateway starting with 192.168.1, you shouldn't use 192.168.1.1 or 192.168.1.2 for your ppp connection. Try using 192.168.2.1 and 192.168.2.2 instead. 

-Brian

---

