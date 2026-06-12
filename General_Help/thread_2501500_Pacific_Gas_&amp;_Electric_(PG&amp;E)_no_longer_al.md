---
title: "Pacific Gas &amp; Electric (PG&amp;E) no longer allows Firefox"
date: 2024-10-10
forum: General Help
---

### Post by Ralph L on 2024-10-10
I run Xubuntu 22.04 and Firefox. I just went to the Pacific Gas & Electric (PG&E) (California) website to pay my bill. Got a message that they no longer allow Firefox to access their website. Somehow I got to Mozilla about the problem and they said they were aware of this. Also told me to add an extension to Firefox called Chrome Mask. Its supposed make Firefox look like Chrome. It didn't work.

I have tried to keep Microsoft and Google software off my Xubuntu laptop, because of their proclivity to take information that they apparently distribute to others. Also, I don't like monopolies. I think its really bad, when a public utility like PG&E supports only monopolies like Microsoft and Google. I called PG&E and they said to get used to it. I contacted the CA PUC and they said they couldn't care less. I called my Congressman, Vince Fong, and got the brushoff. Makes me mad!!

Anyway, has anybody got a solution to allow Firefox access to PG&E??? Anybody tried to use Chrome Mask. Maybe I don't know how to  use it. Anybody know of any other Firefox extension that might work??

Any help is appreciated.................

---

### Post by dragonfly41 on 2024-10-10
Have you considered Brave browser? More secure.

---

### Post by 1fallen on 2024-10-10
+1 for Brave, if it works and I can't see why it wouldn't.

---

### Post by dragonfly41 on 2024-10-10
Well being a curious soul I tried accessing this through Brave.

[https://m.pge.com/#login](https://m.pge.com/#login)

No issues.

Oops, sorry.  [COLOR=#333333][FONT=DIN-Regular]The Firefox and Brave browsers are not supported.[/FONT][/COLOR]

---

### Post by 1fallen on 2024-10-10
@Ralph L there is MS Edge in Flatpak which worked nicely.

```
[FONT=monospace][COLOR=#000000]flatpak install com.microsoft.Edge [/COLOR]
[/FONT]
```
Permissions:
```
[FONT=monospace][COLOR=#000000]**com.microsoft.Edge**[/COLOR][COLOR=#000000] permissions: [/COLOR]
    ipc            network                cups                   pcsc                     pulseaudio                    wayland         x11 
    devices        file access [1]        dbus access [2]        bus ownership [3]        system dbus access [4]        tags [5]



```
[/FONT]

---

### Post by dragonfly41 on 2024-10-10
Another thought. For isolation perhaps run a VM in Ubuntu? then you can install a "supported browser". A few days ago I embarked on an experiment emulating Android Studio in Ubuntu (Plasma KDE session needed however) so you might try a Samsung browser inside Android Studio. That should fool them.

---

### Post by donald187 on 2024-10-10
Chromium worked (on Debian).

---

### Post by bobunderwood99 on 2024-10-10
I am a PG&E customer who pays my bill with Firefox.

 Been getting the "unsupported browser" messages for months - just go on through. Don't know what will happen when they implement their "new account". I'd try Chromium.

PG&E = monopolistic behavior; CPUC: corrupt and useless.

---

