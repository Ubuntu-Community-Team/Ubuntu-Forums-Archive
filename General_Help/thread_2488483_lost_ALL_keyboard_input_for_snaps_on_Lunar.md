---
title: "lost ALL keyboard input for snaps on Lunar"
date: 2023-07-05
forum: General Help
---

### Post by bob15 on 2023-07-05
Hi-

Recently I had to remove my ~/.cache directory due to a HOMEDIR change (I mention it since I believe it may be relevant).

Sometime after that, I have lost keyboard input to ALL snaps. Using firefox as an example, I can not type in the URL address bar, or in web forms, etc. Other snaps are the same, no keyboard but all seem to be X clients (I do not use wayland).

If I stop IBUS, I can type in Firefox, but I can not type in a terminal or other non-snap applications. (I have no idea why IBUS ever was running since I only use US English).

How can I fix keyboard input for snaps?

I've googled this and there appear to be instances going all the way back to 2020 (and some before) with no clear solution.
I do see some posts related to sockets in .cache (which is why I mentioned what I did above).

Where do I even begin to troubleshoot???

Removing and re-installing does not help.

I don't see anything out of the ordinary when I issue:
snap connections firefox 

When I run firefox from the command line I do see the following at the end of startup:
(firefox:50812): IBUS-WARNING **: 22:36:44.423: Unable to connect to ibus: Could not connect: Permission denied

So am thinking it's IBUS related....

Any help or pointers would be greatly appreciated.
Bob

---

### Post by bob15 on 2023-07-05
Sorry to follow-up my own post but I just found this:
[https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/2008279](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/2008279)

I am running Kubuntu Lunar.....

Further up my manual start of firefox it did state:
[FONT=monospace][COLOR=#000000][Parent 50812, Main Thread] WARNING: Unable to connect to ibus: Could not connect: Permission denied: 'glib warning', file /build/firefox/parts/firefox/build/toolkit/xre/nsSigHandlers.cpp:167[/COLOR]

So it appears similar (the same?)...

But according to that bug, the dev [/FONT]edited /var/lib/snapd/apparmor/profiles/snap.firefox.firefox and added the following rule:

    @{HOME}/.cache/ibus/dbus-* rw,

But I already have this in my snap.firefox.firefox file on line 1850...

But I still get the "Could not connect: Permission denied"

?????


[FONT=monospace]

[/FONT]

---

### Post by bob15 on 2023-07-05
Said fixed in snapd [COLOR=#000000][FONT=&quot]2.58.3+23.04ubuntu1

[/FONT][/COLOR]Mine is:

$ dpkg -l snapdDesired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version               Architecture Description
+++-==============-=====================-============-============================================
ii  snapd          2.59.1+23.04ubuntu1.1 amd64        Daemon and tooling that enable snap packages

---

### Post by #&amp;thj^% on 2023-07-06
> **bob15 said:**
> 
So am thinking it's IBUS related....

Any help or pointers would be greatly appreciated.
Bob

Sounds reasonable, see if this has permissions to your keyboard with firefox only:
```
env IBUS_USE_PORTAL=1 firefox
```
Just a heads up this might be a complete mess to fix, if the above command now works with your keyboard.

---

### Post by bob15 on 2023-07-07
Hi @1fallen... thanks for the response... yes I tried:

[COLOR=#000000]env IBUS_USE_PORTAL=1 firefox

[/COLOR]
[COLOR=#000000][/COLOR]And unfortunately it still did not work... and after a couple of key presses, the Konsole gets flooded with these:

(firefox:80175): IBUS-WARNING **: 14:40:28.405: Events queue growing too big, will start to drop.
[Parent 80175, Main Thread] WARNING: Events queue growing too big, will start to drop.: 'glib warning', file /build/firefox/parts/firefox/build/toolkit/xre/nsSigHandlers.cpp:167



So I guess the question now is: how can I recreate the missing socket(?) files in my ~/.cache dir?

Is there some kind of utiltiy to address this? If not, any ideas or pointers would be greatly appreciated.

Thx.

---

### Post by #&amp;thj^% on 2023-07-07
bob15 I'm a snap free type of guy, so i might not be of any help to you on this one.
```
dpkg -l snapd
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  snapd          <none>       <none>       (no description available)

```
As a final suggestion, I would try to re-install snapd:
```
sudo apt install --reinstall snapd
```
Log out and back in, any difference?
Or paste back any errors shown.

---

### Post by MAFoElffen on 2023-07-08
Okay... So you deleted a ~/.cache directory... When you delete ~/.cache or ~/.config, usually an application recreates it when the application starts again. This is true, except for Snaps.

For Snaps-- Firefox, if in the address dialog, you anter about:cachge, the bottom setting is where it is located. For mine, it's at: "/home/mafoelffen/snap/firefox/common/.cache/mozilla/firefox/yy3x8gtk.default/cache2"

 Also, if you use the browser to navigate to "about : profiles" (without those added spaces) it will tell you where the profiles are located... So Snaps locations for those "are" different now.

---

### Post by bob15 on 2023-07-08
Thanks again 1fallen... unfortunately a reinstall w/logout and login did not work.

MAFoElffen - I checked about:cache and mine is (for firefox):
/home/rcc/snap/firefox/common/.cache/mozilla/firefox/ct9rg6k6.default-release-1677595353959/cache2

Even though I have no keyboard input for any x based snap.....

If I move any of those dirs to new names to have them recreated (as suggested), they are recreated, but the keyboard still does not work... on ANY x based snap.

Looking at the bug report above, it appears a file based socket is used as either the basis for a "snap connection" or is a part of the one.

If I cd ../.. and then look for all file based sockets in that cache dir with:
$ find . -type s

I get no results.

I'm back to thinking either I'm missing a socket in my "new" .cache or a new one needs to be created.

If these sockets are involved in snap connections, I would hope someone would think to have some kind of utility to recreate them if they are not there ... at some point, either at start or at run-time.

Not sure where to go from here...

---

### Post by #&amp;thj^% on 2023-07-08
> **bob15 said:**
> 

Not sure where to go from here...

Wish I had better news, have a look here: [https://forum.snapcraft.io/t/no-snap-applications-respond-to-keyboard-input-on-clean-install-of-xubuntu-22-04-lts/32422](https://forum.snapcraft.io/t/no-snap-applications-respond-to-keyboard-input-on-clean-install-of-xubuntu-22-04-lts/32422)
Maybe start here:
> jamesh
Nov '22

@jason0x21: to help debug what&#8217;s going on on your system, it&#8217;d be helpful to see how the ibus bus is configured on your system. There should be a text file in ~/.config/ibus/bus/ that is used to find where the socket is located. It should start with a comment like &#8220;This file is created by ibus-daemon&#8221;.

Could you provide the contents of this file in a reply here? The file doesn&#8217;t contain any sensitive information.

---

### Post by bob15 on 2023-07-09
Yes! 1fallen... I just found that too... headed there next.

Thank you (and MAFoElffen) for the input you have provided. It has helped.

Headed over to that forum to see what the snap gurus have to say.

Bob

---

### Post by bob15 on 2023-07-10
Solved!

Net net... the local ~/.cache dir can NOT be linked to any other location. It has to be a directory and a directory specifically in that location (with the current version of snapd).

[https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/2026758](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/2026758)

---

### Post by #&amp;thj^% on 2023-07-10
Nice Good work and thanks for adding your solution, very helpful.

---

### Post by mcassaniti on 2024-06-26
My issue is almost the same as the original poster. I wasn't sure if I should create a new post or not. I'm running glib2.80 on Ubuntu 24.04 with KDE. For some reason the AppArmor profile is blocking access to IBUS and I don't know why. Please note that I started firefox using a snap as the same user running everything else on my desktop.

Relevant AppArmor profile details:
```

# Path: /var/lib/snapd/apparmor/profiles/snap.firefox.firefox

profile "snap.firefox.firefox" flags=(...) {
   ... SNIP ...
   # This allows the right access __if the process owner matches the file owner__
   owner @{HOME}/.cache/ibus/dbus-* rw,

   # This allows the right access for me but shouldn't be necessary
   @{HOME}/.cache/ibus/dbus-* rw,

   ... SNIP ...
}

# Relevant kernel output
AVC apparmor="DENIED" operation="connect" class="file"  profile="snap.firefox.firefox"  name="/home/mcassaniti/.cache/ibus/dbus-Xfrnxka9" pid=5148  comm="pool-firefox" requested_mask="wr" denied_mask="wr" fsuid=60102  ouid=65534

```

My UID is 60102. What I find unusual is the **ouid=65534** piece. Can someone help me with this cause I think this is the crux of the issue and I have no reasonable explanation for it. I've checked that the appropriate DBUS files are owned by me.

---

### Post by wildmanne39 on 2024-06-27
Yes please start you own thread this one is almost a year old and is very close to automatically closing and since its marked solved you will be more likely to get help in your own thread in the appropriate sub-form and an descriptive title.

Welcome to the forum and thank you.

I am closing this thread.

---

