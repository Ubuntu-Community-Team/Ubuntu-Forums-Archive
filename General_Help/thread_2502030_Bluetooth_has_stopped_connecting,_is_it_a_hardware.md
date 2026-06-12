---
title: "Bluetooth has stopped connecting, is it a hardware issue?"
date: 2024-10-30
forum: General Help
---

### Post by goemonburo on 2024-10-30
Up until yesterday Bluetooth was working reliably on my Lubuntu 22.04LTS system.  I remember having to fiddle with bluetoothctl initially to get it to pair with my wireless earbuds but afterwards, for months if not years, I've just taken them out of the case and a few moments later they'd pair.  

As of yesterday, however, there's a "beep" from the earbuds instead of the "Connected," confirmation and "bluetoothctl show" simply hangs...trying to scan hangs, either from the cli or from the "Add Bluetooth Device" window.

I've verified that the earbuds pair fine to Bluetooth on my phone...so I don't think it's a hardware issue with the earbuds or that they're not charged or something dumb like that.  None of my other bluetooth devices are pairing anymore with the computer either (over ear headphones, bluetooth speaker).

I've also found that commands such as "bluetoothctl devices" also come up with absolutely no response (tried both that and "sudo bluetoothctl devices"), when I'd expect at least to see a few listings of the known devices after a second or two.  I've tried several variations of restarting it, such as "sudo service bluetooth restart" and "sudo systemctl restart bluetooth."  Again...nothing.  No error message, no information, just the cursor hangs until I hit Cntl-C.

I feel like maybe a recent update messed up the Bluetooth driver module or maybe my bluetooth controller has failed (?!), but have zero way to sleuth that.  Could anyone out there walk me through a few steps to diagnose this?

---

### Post by dragonfly41 on 2024-10-30
Recently I had to fiddle around with Bluetooth connection to devices and I found that by installing a new desktop session Plasma (X11) - to switch at login time - allowed more insights into Bluetooth. After I boot up at the point where login password is inserted there is a button bottom right of screen where (after various experiments) I can switch between:

awesome
LXGt Desktop
Plasma (X11)
ubuntu
Xfce Session

Now as I write in Plasma (X11) I can see Bluetooth in bottom bar and I have two devices connected.

So all I can suggest is try a different desktop session. But remember that Plasma introduces quite a payload.

Other than that (which is a big step)  I suggest booting up LiveUSB "Try Ubuntu" to see if you can connect to devices.

[Later note] I searched command history .. history | grep plasma

and found this command I used earlier to install Plasma (X11) desktop session

sudo apt install plasma-workspace-wayland

---

### Post by goemonburo on 2024-10-30
Thanks, @Dragonfly41, I appreciate the suggestion, but I'm not looking to migrate to another desktop.  I suspect that there's a way to list the bluetooth device, see what module it's running, and maybe walk back to an earlier module or something.

Fingers crossed someone out there knows how to do that.

---

### Post by dragonfly41 on 2024-10-30
My approach is to try in different environments.

I'm back in ubuntu session.
I opened command terminal and to remind me of commands history when I last played with Bluetooth I have run 


~$ history | grep bluetooth
  253  bluetoothctl
  312  bluetoothctl
  629  bluetoothman
  718  sudo rm -r /var/lib/bluetooth/
  719  sudo apt reinstall --purge bluez gnome-bluetooth
  722  bluetoothctl
  723  sudo apt reinstall --purge bluez gnome-bluetooth
  724  lsmod | grep bluetooth
  725  sudo systemctl status bluetooth
  727  bluetoothctl
  818  bluetoothctl
 1200  history | grep bluetooth

---

