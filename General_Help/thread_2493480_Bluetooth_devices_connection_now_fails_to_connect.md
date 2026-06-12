---
title: "Bluetooth devices connection now fails to connect"
date: 2023-12-16
forum: General Help
---

### Post by dragonfly41 on 2023-12-16
Bluetooth was working fine yesterday with multiple devices seen in Bluetooth Manager.
But today failure to connect.

I am using wired devices as backup.


I can use Blueman GUI or CLI bluetoothctl in Ubuntu.
But .. Failed to connect: org.bluez.Error.Failed

On all devices.
Devices work without problems on Windows 10.

Could this be a recent kernel update? Seems to be 20.04 related from what I have read.
How to troubleshoot? Perhaps time to upgrade to 22.04?
All devices are paired and trusted, but cannot connect whether through Bluetooth Manager or bluetoothctl.

P.S. I am listening to this using Bluetooth Bose headphone.

[https://www.youtube.com/watch?v=1I1vxu5qIUM&ab_channel=BranchEducation](https://www.youtube.com/watch?v=1I1vxu5qIUM&ab_channel=BranchEducation)

---

### Post by #&amp;thj^% on 2023-12-16
Have you looked at:
```
systemctl status bluetooth.service
```
Sometimes it reveals something.
ie:
```
systemctl status bluetooth.service |grep -e "src/profile.c:record_cb() "
Dec 16 13:30:46 me-Legion-5-zfs bluetoothd[1717]: src/profile.c:record_cb() Unable to get Hands-Free Voice gateway SDP record: Host is down

```

---

### Post by dragonfly41 on 2023-12-17
I have launched into earlier Ubuntu installation just to answer. 
Quick reply. Tried that tip, nothing untoward seen. But OS now has a mind of is own.  Even old hard wired mouse device is intermittent on clicking but works in this older OS.
Looked at Settings > Bluetooth > devices are not connected.
I will be incommunicado for a while until I can sort this out. Might install a fresh Ubuntu 22.04.
Thanks for idea.

---

### Post by dragonfly41 on 2023-12-17
Thanks for idea. Status "running". No errors reported.
Blueman refuses to connect Logitech keyboard + Logitech mouse but oddly connects Bose headphones and a mobile phone. So it is Logitech vendor choosy which narrows it down.
The odd point is that this occured in last two days so I was wondering if a kernel upgrade might be the cause. I explored ways of finding the last date of kernel upgrade which I think was Dec 15 .

---

### Post by dragonfly41 on 2023-12-18
For the benefit of others with Bluetooth + Ubuntu 20.04 + Logitech ..

I tried an old wired mouse and keyboard (Dell) for a while but the mouse at intermittent times failed to click. I found a site that suggested Ctrl+Alt+F3 then immediately Ctrl+Alt+F1 to get out of the mouse locking .. but it came back and I was about to try installing fresh Ubuntu.

Then I tried again to fix mouse and keyboard by going to top bar Settings > Bluetooth and removing mouse and keyboard to reinstall.

Then I found ...

[https://askubuntu.com/questions/1270419/20-04-logitech-mx-keys-wont-pair-with-bluetooth](https://askubuntu.com/questions/1270419/20-04-logitech-mx-keys-wont-pair-with-bluetooth)


bluetoothctl
power off
power on
agent KeyboardOnly
default-agent
pairable on
scan on
pair <mac address>
## the passkey will be printed, enter it on your keyboard ##
trust <mac address>
connect <mac address>
quit

That tip got the Bluetooth mouse working again so I can ditch the wired mouse.

I will now turn to the keyboard following same bluetoothctl routine but this gets me out of a hole.

Remember this seems to be a Ubuntu 20.04 + Logitech issue.

If keyboard is restored I will mark this as solved.

---

### Post by dragonfly41 on 2023-12-19
Solved.

I am back to previous working state with Bluetooth (Blueman) and Logitech MX Keys (keyboard)  and Logitech MX Master 3S (mouse).
I opened Blueman (Bluetooth) GUI to grab MAC addresses of each device.
Then I applied the bluetoothctl sequence of commands as found in earlier post.


bluetoothctl
power off
power on
agent KeyboardOnly
default-agent
pairable on
scan on
pair <mac address>
## the passkey will be printed, enter it on your keyboard ##
trust <mac address>
connect <mac address>
quit



At the point of pairing the passkey is shown in terminal and this is typed into keyboard.
Complete with the trust and connect commands but these can be seen on Blueman.
It seems that the pairing is the important step, typing in passkey to complete pairing.
When using only Blueman GUI I have seen passkeys popup on screen so there are two ways of pairing.


I don't know why the pairing was lost when it had previously been working.


What I have found is that this issue is mainly with 20.04 and Logitech.  Other devices such as Bose are working without glitch.  Hopefully this glitch will disappear when upgrading to 22.04.

---

