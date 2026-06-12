---
title: "can't use network manager"
date: 2007-01-16
forum: General Help
---

### Post by m.musashi on 2007-01-16
I have network manager (nm applet) installed on my laptop but I can't use it to connect to my network. It loads and is on the top panel. I am currently using the default network tool and it works fine. However, I understand that network manager will allow me to use WPA so I'd like to get it to work. Right now it only tells me there are no wired connections (actually the only option is wired network and it's grayed out). After searching the forum I found several references to selecting add new network but no option like that exists. It is enabled but doesn't do anything. I made some suggested changes to  /etc/network/interfaces and commented out everything except lo but that didn't help either. I'm thinking I need to somehow get the default app to stop controlling networking but I don't know how to do that or if that is really what I need to do.

Any help would be appreciated.

---

### Post by discord on 2007-01-16
I had to get and compile a version myself. the ubuntu packaged one did not work for me... do a google search....

---

### Post by m.musashi on 2007-01-17
Yeah, that's an option but I'd rather try and figure out if there is a way to disable the default network tool and force nm-applet to manage netowrking instead - if that is in fact a cause of the problem. I scanned through a lot of threads though and didn't see any good solutions or similar problems.

I thought maybe nm-applet couldn't handle a hidden ssid (even though it is supposed to) so I unhid mine but it didn't help - nm-applet still didn't see the available wireless network or allow me to create any manual connections.

---

### Post by featherking on 2007-01-17
The easiest way to get it to start controlling your network interfaces (plural because it will also control your wired connection) is to open up (in gnome, not sure on kde) System > Admin > Networking (the default networking tool) open the properties for all the devices there, whether wired or wireless and in the properties dialog box clear the box that says 'enable this connection' this should change the output of your /etc/network/interfaces file to read:
```

auto lo
iface lo inet loopback
```

You may need to exit NetworkManager and restart your networking for these changes to take effect by running

```
sudo killall NetworkManager
```

then
```

sudo /etc/init.d/networking restart
```

To bring Network manger back type
```

sudo NetworkManager
```

Now make sure (by right clicking the NM icon) that wireless is enabled, if so, simply left-click the icon to select a nearby network or specify by selecting 'connect to other wireless network' and fill out the information required (encryption type, SSID, TKIP key, etc)

Everything should work now.. however as a side note! Networkmanager cannot (currently) use static ip addresses, this was a problem of mine a few times. Having said that once you get it going it is pretty reliable, at least for me. Good luck!

---

### Post by m.musashi on 2007-01-17
Thank you! That worked. It seems a bit slow to connect - a minute or so - but it is working. I'll see what happens after a restart. It looks like I can also set up WPA so that is my next task.

Thanks again for the excellent tutorial. You should write this up. I spent a couple hours searching the forum for this with no luck. I can't imagine I'm the only one with this problem. After all, this is a new edgy install.

---

### Post by featherking on 2007-01-18
Not sure why it is slow to connect, generally right after i login i get a message that ive connected before i can even see the icons on my desktop.

Glad that you got it going, as for the tutorial i had never considered it..

---

### Post by m.musashi on 2007-01-18
It seems slow on just the one laptop. On my wife's it seems much faster. Maybe there is something I can clean up or maybe it just needs a reboot.

Follow up question: NM asks to store the password in the keyring something and asks me to set a password for that. When I log out and in it asks for the keyring password before connecting. Can I disable or automate that? I suppose it's a security measure but unless the laptop is stolen I don't see the benefit and if it's stolen then I have more problems than my wireless network.

EDIT: In trying to solve this I managed to delete the NM icon from the panel. I don't suppose you would know how to add it back? It's not add to panel and un-installing and reinstalling didn't help either. I also tried a custom app launcher but that didn't help either.

---

### Post by featherking on 2007-01-18
The keyring stores passwords for a lot of different things, and it is protected by a password itself. I did manage to find a way to have it not prompt me anymore but it was a long time ago, i will keep checking for you.

As for the deleted icon, the only place i can think of to check would be in System > Preferences > Sessions. Under 'Startup Programs' make sure it says somewhere:

```
nm-applet --sm-disable
```

This should run the icon at startup. Again, the keyring thing was something like the PAM keyring or something, i will post if i find the answer...

---

### Post by featherking on 2007-01-19
Here is a How To someone has written, i dont know if it was the same one i followed but its the same basic idea, that pam_keyring package is the one that uses your login and the keyring password too, here is the [[COLOR="Red"]link[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=192281&highlight=pam+keyring")

---

