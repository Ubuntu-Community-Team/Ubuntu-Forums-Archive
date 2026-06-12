---
title: "Cannot Connect To WPA Personal Wireless Network.."
date: 2008-05-24
forum: General Help
---

### Post by GCoffee on 2008-05-24
Hello All, 

Today I wake up to find the most annoying problem of all-time, My wireless has stopped working, what makes it worse still, is that it is working in windows.. It was working perfectly yesterday!

Its A Netgear DG834G Router and my pc is attached to the WG111v2 adapter that came with the router.. It is a wpa personal network and is fairly old.

Please Help Me, this is infuriating and really annoying!

Your sincerely,
GCoffee.

---

### Post by shifty_powers on 2008-05-24
what actually happens when you try to connect?

---

### Post by ibuclaw on 2008-05-24
Have you tried reseting the WPA password keyring?

Press "**ALT+F2**"
Type into the textbox:
```
nautilus ~/.gnome2/keyrings
```
Then hit "Enter" to run the command.

In the new nautilus window, rename "**login.keyring**" to "**login.keyring.bak**"

Right-Click your Nm-Applet and deselect "**Enable Wireless**"
Repeat that again to re-enable wireless.

Left-Click on your Nm-Applet and select your Wireless Router.
Enter in your WPA Password, and click "OK".

A new keyring will be made if you have successfully logged in.

[EDIT]
If you PC isn't picking up your wireless dongle, open up a terminal and type in:
```
sudo modprobe ndiswrapper
```

[EDIT2]
Also, what repositories are you tied to?
I had a problem the other week when I added "hardy-proposed" into my sources file and upgraded everything.

One problem it caused was that nm-applet wouldn't load till about 3-5 mins after my first session started.

Regards
Iain

---

### Post by nealesiebert on 2008-05-30
> **GCoffee said:**
> Hello All, 

Today I wake up to find the most annoying problem of all-time, My wireless has stopped working, what makes it worse still, is that it is working in windows.. It was working perfectly yesterday!

Its A Netgear DG834G Router and my pc is attached to the WG111v2 adapter that came with the router.. It is a wpa personal network and is fairly old.

Please Help Me, this is infuriating and really annoying!

Your sincerely,
GCoffee.

_________________________________________________________________________

Hi this has been happening to me too

I haven't used the key thingy suggested above but I just found the following thread on the forum...

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)
HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc. 

Post #1 has a whole lot of stuff about configuring WPA etc, but if that is already working have a look at post #2

I followed the steps, and now my wireless network works when I boot without having to go into the network settings and retype my passphrase! What a relief

Just so you know what to look for here it is ............



Some users reported (including myself) that the network has to be restarted every time after startup... Apparently this is a bug.

Here is a workaround that helps restart the network during boot so that one does not have to do it manually after logging on to the system.

Create startup script:
Quote:
sudo gedit /etc/init.d/wireless-network.sh
Add this line & save file:
Quote:
/etc/init.d/networking restart
Change permission (executable):
Quote:
sudo chmod +x /etc/init.d/wireless-network.sh
Create symbolic link:
Quote:
sudo ln -s /etc/init.d/wireless-network.sh /etc/rcS.d/S40wireless-network
[Note: You may have to choose a boot sequence other than S40.]

Restart...

---

### Post by brunolalb on 2008-06-11
> **tinivole said:**
> Have you tried reseting the WPA password keyring?

Press "**ALT+F2**"
Type into the textbox:
```
nautilus ~/.gnome2/keyrings
```
Then hit "Enter" to run the command.

In the new nautilus window, rename "**login.keyring**" to "**login.keyring.bak**"

Right-Click your Nm-Applet and deselect "**Enable Wireless**"
Repeat that again to re-enable wireless.

Left-Click on your Nm-Applet and select your Wireless Router.
Enter in your WPA Password, and click "OK".

A new keyring will be made if you have successfully logged in.

[EDIT]
If you PC isn't picking up your wireless dongle, open up a terminal and type in:
```
sudo modprobe ndiswrapper
```

[EDIT2]
Also, what repositories are you tied to?
I had a problem the other week when I added "hardy-proposed" into my sources file and upgraded everything.

One problem it caused was that nm-applet wouldn't load till about 3-5 mins after my first session started.

Regards
Iain

Thanks Iain!
that renaming idea worked just fine with me!
now I can surf in the internet without a wire attached!

thanks a lot!!:)

---

