---
title: "Firefox in Hardy defaults &quot;Offline&quot;"
date: 2008-05-19
forum: General Help
---

### Post by paddyboy on 2008-05-19
Hi, I Just upgraded from Feisty to Hardy and got most things running OK. However, one really annoying thing I found is that Firefox opens up with the default of "work offline" enabled. How do I get firefox to always fire up with this not enabled ? Thanks.

---

### Post by desertboy on 2008-05-22
Snap I have the same problem, I found trawling on the net that it's a bug in NM and setting your network card to DHCP instead of roaming fixes it, but alas in my case it makes no difference I was already running on DHCP.

I can handle but it's screwing up my mother who also uses this machine.

---

### Post by chrisccoulson on 2008-05-22
> **desertboy said:**
> Snap I have the same problem, I found trawling on the net that it's a bug in NM and setting your network card to DHCP instead of roaming fixes it, but alas in my case it makes no difference I was already running on DHCP.

I can handle but it's screwing up my mother who also uses this machine.

Are you sure it's not the other way around? (ie, setting it from DHCP to roaming fixes it). Roaming is the default network configuration

---

### Post by anaconda on 2008-05-22
I had the same problem with NetworkManager.. It doesn't recognise my 3G internet connection, and that is why Firefox used to start in offline mode..

There are atleast 2 unmentioned easy solution for that problem.
First one is to remove firefox3 and install firefox-2, which doesnt ask NM about internet connection..
Or install some another alternative browser.. eg Opera

And another easy solution is to get rid of that annoying NetworkManager !!  It is only really useful in laptops when your internet connection is wireless..

---

### Post by parkus on 2008-05-23
im running on a laptop, and this keeps happening. its kind of a pain since i use a verizon usb modem to connect to the net.

---

### Post by Nikitas350 on 2008-05-28
Open the terminal (Apllication-->accesories--->terminal) and type "gksudo gedit /etc/dbus-1/system.d/NetworkManager.conf". Then you replace the 
<allow send_interface="org.freedesktop.NetworkManager"/> with <deny send_interface="org.freedesktop.NetworkManager"/> (there are three it the text). Then save the changes and reboot. This will not permit firefox (or pidgin) to communicate with network manager and the state will be always online in firefox...

---

### Post by Clark_ElMaSrY on 2008-05-29
Nikitas350    I follow the way u mentioned and it works greatly 

thanks very much

---

### Post by Nikitas350 on 2008-06-04
Always glad to help... :)

---

### Post by arrancaru on 2008-06-21
Thank you very much

---

### Post by SnarkyTech on 2008-06-21
> **Nikitas350 said:**
> Open the terminal (Apllication-->accesories--->terminal) and type "gksudo gedit /etc/dbus-1/system.d/NetworkManager.conf". Then you replace the 
<allow send_interface="org.freedesktop.NetworkManager"/> with <deny send_interface="org.freedesktop.NetworkManager"/> (there are three it the text). Then save the changes and reboot. This will not permit firefox (or pidgin) to communicate with network manager and the state will be always online in firefox...

Thank you!  :)

---

### Post by sunshine12 on 2008-06-22
Thanks a lot.

---

### Post by Shazaam on 2008-06-23
Add me to the thanks list Nikitas350 as you have helped this old dialup dinosaur. Good work.

---

### Post by antmenj on 2008-06-29
:guitar:

Thanks

For others info I had a box working fine with ethernet network internet then when changeing to a dialup modem this happens.

---

### Post by ucciucci on 2008-07-01
Thank you very much! I solved a problem that was driving me mad! :-) Nicola

---

### Post by rmrfstar on 2008-07-03
Following this advice crippled my network-manager. 

Long story short, I was no longer able to freely roam via wlan0. I could setup a location with the older network-admin application though, specifying the ESSID etc.

Removing network-manager and reinstalling network-manager/network-manager-gnome/nm-applet fixed the issue.

---

### Post by Paul86fxr on 2008-07-04
Worked great! Thankyou!

---

### Post by iloveannie on 2008-07-07
Thanks!!!

---

### Post by tdubois65 on 2008-07-07
Thank you so much!

---

### Post by rmrfstar on 2008-07-08
To follow up (although no one will likely read this), I believe the correct way to disable offline mode in Firefox is:

1) Start Firefox
2) In the address bar, type about:config
3) Search for "offline"
4) Toggle (double-click) browser.cache.offline.enable to "false"

---

### Post by khermans on 2008-07-10
Here is the fix I developed...

[http://kristian-hermansen.com/code/disable.offline.mode/disable.offline.mode.html]("http://kristian-hermansen.com/code/disable.offline.mode/disable.offline.mode.html")

---

### Post by Paul86fxr on 2008-07-12
Good fix but I dont want to stare @ Kristian erik Hermansen at the bottom of my browser page for all eternity, dont install this if you dont want his name on your browser page

---

### Post by Bat on 2008-08-01
rmrfstar's solution is wrong: [the browser.cache.offline.enable option switches the caching on and off]("http://kb.mozillazine.org/Browser.cache.offline.enable"), as the name suggests; it has no effect on whether the browser goes into offline mode.

Nikitas350's solution is also wrong: it prevents NetworkManager on wifi-enabled laptops from automatically connecting when it detects a wireless access point.

khermans's solution may or may not be wrong, but the link is down and he offers no explanation on the comments here, so it may as well be wrong for all the good it does.

The error is known: it's [Bug 339814 in Bugzilla]("https://bugzilla.mozilla.org/show_bug.cgi?id=339814").  As of today, nobody is assigned to fix it, and I can confirm it's present in Firefox 3.0.1 from the Ubuntu repositories.

Another solution mentions disabling network manager and/or editing the /etc/network/interfaces file.  This will of course mess up laptops that sometimes connect by wifi and sometimes by wire, so Don't Do That either.

It seems to me the only "solution" is to have a quick button that switches the offline mode back on.  It doesn't stop the bug, but it saves a click or two in dealing with it.  There's [an extension to do that]("https://addons.mozilla.org/en-US/firefox/addon/493") which works with FF3.

Here's hoping the Mozilla people fix this one and don't decide to leave it a few years to age like good wine and bad bugs.

---

### Post by Paul86fxr on 2008-08-01
for some reason mine stopped going into offline mode, I updated firefox from synaptic and everything worked fine, dont know why but it did.

---

### Post by igray78756 on 2008-08-04
If you like how NetworkManager works, but you simply want to be able to use FireFox while not connected to a network (i.e. for web development, etc.), you can edit the following special configuration in FireFox (use about:config-- click on link for more info):

[toolkit.networkmanager.disable]("http://kb.mozillazine.org/Toolkit.networkmanager.disable")

This will leave NetworkManager alone and let it do it's thing, but FireFox will still function in offline mode.

---

### Post by jemmrich on 2008-08-08
> **Nikitas350 said:**
> Open the terminal (Apllication-->accesories--->terminal) and type "gksudo gedit /etc/dbus-1/system.d/NetworkManager.conf". Then you replace the 
<allow send_interface="org.freedesktop.NetworkManager"/> with <deny send_interface="org.freedesktop.NetworkManager"/> (there are three it the text). Then save the changes and reboot. This will not permit firefox (or pidgin) to communicate with network manager and the state will be always online in firefox...



Thanks works great!

---

### Post by mcandre on 2008-08-15
******** that! I finally decided to make a Firefox extension to fix it. Now you'll never be in offline mode.

Always Online
[http://yellosoft.us/index.php?id=88]("http://yellosoft.us/index.php?id=88")

---

### Post by wpshooter on 2008-08-17
Is this problem ever going to be **_fixed_** (as in "it just works") ?

I ran into this problem a while back when trying to setup a computer for someone to use on a dialup connection and NOW I am finding out that it is a problem with a wired DSL connected computer also !!!

With problems like this, is there any good reason why I should not just install Gutsy (which does not seem to exhibit this and other problems) instead of Hardy ?

Thanks.

---

### Post by knight0450 on 2008-10-10
> **Nikitas350 said:**
> Open the terminal (Apllication-->accesories--->terminal) and type "gksudo gedit /etc/dbus-1/system.d/NetworkManager.conf". Then you replace the 
<allow send_interface="org.freedesktop.NetworkManager"/> with <deny send_interface="org.freedesktop.NetworkManager"/> (there are three it the text). Then save the changes and reboot. This will not permit firefox (or pidgin) to communicate with network manager and the state will be always online in firefox...

It happened when I upgraded to 8.10.
And thanks for help.

---

### Post by elj4176 on 2008-10-11
same here. the problem is back in 8.10.
pidgin does the same thing

---

### Post by new fish on 2008-10-23
thank you nikitas350. I'm new to Linux and your suggestion really works well
great post man!

---

### Post by RLuck on 2008-10-26
> **Nikitas350 said:**
> Open the terminal (Apllication-->accesories--->terminal) and type "gksudo gedit /etc/dbus-1/system.d/NetworkManager.conf". Then you replace the 
<allow send_interface="org.freedesktop.NetworkManager"/> with <deny send_interface="org.freedesktop.NetworkManager"/> (there are three it the text). Then save the changes and reboot. This will not permit firefox (or pidgin) to communicate with network manager and the state will be always online in firefox...

SO Many Thanks for this post  
I thought I would go nutz - thinking there must be some way in the preferences of Firefox.  

Bob

---

### Post by IggoOnTour on 2008-10-28
i just registered to thank you! A LOT!

---

### Post by asbesto on 2008-10-30
> **rmrfstar said:**
> To follow up (although no one will likely read this), I believe the correct way to disable offline mode in Firefox is:

1) Start Firefox
2) In the address bar, type about:config
3) Search for "offline"
4) Toggle (double-click) browser.cache.offline.enable to "false"


Yes, THIS is the correct mode! The other one imploded my network manager and I was not able to connect to any network anymore! :(

THANK YOU!
:popcorn:

---

### Post by Hobgoblin on 2008-11-08
> **Nikitas350 said:**
> Open the terminal (Apllication-->accesories--->terminal) and type "gksudo gedit /etc/dbus-1/system.d/NetworkManager.conf". Then you replace the 
<allow send_interface="org.freedesktop.NetworkManager"/> with <deny send_interface="org.freedesktop.NetworkManager"/> (there are three it the text). Then save the changes and reboot. This will not permit firefox (or pidgin) to communicate with network manager and the state will be always online in firefox...

This hosed the rest of my network connections, when I'm home I want to be able to use my wireless connection.

Changed toolkit.networkmanager.disable in Firefox to true and all is well.

---

### Post by svc985 on 2008-12-08
> **Nikitas350 said:**
> Open the terminal (Apllication-->accesories--->terminal) and type "gksudo gedit /etc/dbus-1/system.d/NetworkManager.conf". Then you replace the 
<allow send_interface="org.freedesktop.NetworkManager"/> with <deny send_interface="org.freedesktop.NetworkManager"/> (there are three it the text). Then save the changes and reboot. This will not permit firefox (or pidgin) to communicate with network manager and the state will be always online in firefox...



Thanks a lot Nikitas350 for the advice.:guitar:

---

### Post by SwordGreen on 2008-12-24
Yeah, it works, Thank you very much.

---

### Post by pistacoppu on 2009-02-03
> **igray78756 said:**
> If you like how NetworkManager works, but you simply want to be able to use FireFox while not connected to a network (i.e. for web development, etc.), you can edit the following special configuration in FireFox (use about:config-- click on link for more info):

[toolkit.networkmanager.disable]("http://kb.mozillazine.org/Toolkit.networkmanager.disable")

This will leave NetworkManager alone and let it do it's thing, but FireFox will still function in offline mode.

thank igray
that worked for me, i set the value to true, and firefox is no more offline by default, i have firefox 3.0.5 and ubu 8.10 .
That doesn't not interfere with network manager so your wifi will keep working well.
i use emesene that works anyway, so pidgin may still have problems

---

### Post by SergeiFranco on 2009-02-25
I use kubuntu and this behaviour is bloody stupid.
I don't understand the point of this, as clearly I don't want for browser to decide if I am connected or not.
Every time I reboot, I "loose" connection.
Is there a proper way to disable this stupidity in GTK apps, without affecting network manager operation?

---

### Post by pratiks19 on 2009-05-17
open Firefox and type 'about:config' in the address bar, accept the promise, then find and set ....

```
toolkit.networkmanager.disable = true
```

it worked for me.

---

### Post by lnx on 2009-06-01
> **Nikitas350 said:**
> Open the terminal (Apllication-->accesories--->terminal) and type "gksudo gedit /etc/dbus-1/system.d/NetworkManager.conf". Then you replace the 
<allow send_interface="org.freedesktop.NetworkManager"/> with <deny send_interface="org.freedesktop.NetworkManager"/> (there are three it the text). Then save the changes and reboot. This will not permit firefox (or pidgin) to communicate with network manager and the state will be always online in firefox...

I have four "allow send_interface=" in the sections:
<policy user="root">,
<policy user="haldaemon">,
<policy at_console="true">,
<policy context="default">

Shall I change all four instances?

---

### Post by ejlal on 2009-07-11
> **pratiks19 said:**
> open Firefox and type 'about:config' in the address bar, accept the promise, then find and set ....

```
toolkit.networkmanager.disable = true
```
thanks, this solved it  for me.

---

### Post by mikeymouse on 2009-07-15
Nikitas350:
  Thankyou the offline bit in firefox was driving me old:
 mikeymouse ):P

---

### Post by gosho on 2010-08-04
> **igray78756 said:**
> If you like how NetworkManager works, but you simply want to be able to use FireFox while not connected to a network (i.e. for web development, etc.), you can edit the following special configuration in FireFox (use about:config-- click on link for more info):

[toolkit.networkmanager.disable]("http://kb.mozillazine.org/Toolkit.networkmanager.disable")

This will leave NetworkManager alone and let it do it's thing, but FireFox will still function in offline mode.
Only this resolve my problem. The others methods does not helped me.

---

### Post by aliirani on 2010-09-19
> **lnx said:**
> I have four "allow send_interface=" in the sections:
<policy user="root">,
<policy user="haldaemon">,
<policy at_console="true">,
<policy context="default">

Shall I change all four instances?

I think this is <policy user="haldaemon">
But this way dont solved my problem!

my probelem soved with [B]igray78756's solution
But my pidgin still this problem!!:(:(:(
I use ubuntu 10.04!
[/B]

---

### Post by daqron on 2010-12-17
> **igray78756 said:**
> [toolkit.networkmanager.disable]("http://kb.mozillazine.org/Toolkit.networkmanager.disable")

This will leave NetworkManager alone and let it do it's thing, but FireFox will still function in offline mode.

Perfect. Thank you!

---

### Post by garethdails on 2012-05-04
hello there  tony  here is there  contact info , they have a wealth of knowledge , tell them  garth  recommened you

---

