---
title: "How do you rename a Bluetooth device?"
date: 2015-11-19
forum: General Help
---

### Post by Jake_Lester on 2015-11-19
I hope I'm just being an idiot, because this seems like it should be a simple thing to do. How do you rename a Bluetooth device, such as a wireless mouse? All the instructions on the first few pages of searching only refer to the local Bluetooth adapter, not the device. I haven't been able to find a way to adapt those instruction over to the device. Can anyone fill me in on how to accomplish this?

Thank you!!


edit: I'm running Trusty 14.04

---

### Post by Vladlenin5000 on 2015-11-19
I'm pretty sure you can't but let's wait for the input of a real expert ;-), shall we?

---

### Post by QDR06VV9 on 2015-11-19
Well I am no expert here by any means but this worked on Trusty(14.04)
You can't change bluetooth device name from control panel in ubuntu yet. Here is the [bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/837196"), which provides this workaround:


If you want to change the bluetooth device name permanently, you have to create a file called /etc/machine-info which should have the following content:

```
PRETTY_HOSTNAME=device-name
```
After this, restart the Bluetooth service:

```
sudo service bluetooth restart
```
I am not really sure sudo is needed to restart buletooth but that was recomended to me.
Or reboot. 
Good Luck

---

### Post by Jake_Lester on 2015-11-19
Thanks for the replies folks! 

Vlad, that's a bummer! It's fairly trivial to do in other OSes, I'd hope Ubuntu could do this pretty easily :/ I'll wait to see...

Runrickus, thanks for the guide! I've actually tried this out already. This seems to change the name for the host device (my computer's Bluetooth adapter). I'm looking for a way to change the external device's name. That is, I want to rename my Bluetooth mouse or headset.

---

### Post by Vladlenin5000 on 2015-11-19
TBH, I never gave it a second thought until now, thanks to your thread :p
I wouldn't mind renaming my "Q7" as "headphones". But it's no like we need to know the device's name after pairing so I keep it as is.

---

### Post by Jake_Lester on 2015-11-19
Yea, I never cared until I got in a dozen Apple Bluetooth mice that are all named "Joe Blow's Mouse" or whatever. OSX must rename all the Apple mice to whatever the user's name is. Some cryptic device name is fine, but I don't want to resell these mice that have actual people's names that pop up when you try to pair. And I'm in a Linux shop, so I can't easily hook them up to an OSX machine to rename them. I blame Apple.

---

