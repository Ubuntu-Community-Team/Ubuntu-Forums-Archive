---
title: "How to have Bluetooth radio off at startup?"
date: 2017-03-28
forum: General Help
---

### Post by F3BQ3DP on 2017-03-28
I'm a new and fully-updated Xubuntu 16.10 user. Ideally, I'd like Xubuntu to remember my Bluetooth radio status across reboots as I've set it in the Bluetooth taskbar applet -- on or off. Failing that, I'd like it to start with the radio off. As it stands, it always starts with the radio on.

I found a fix that entails adding an *rfkill* command to **rc.local**. It seems to work for many users, but not for me. I suspect it is because my system is under *systemd*. It any case, it did not work for me after a reboot, even though I do have *rfkill* installed.

Then there is another fix which has you stop and disable **bluetooth.service** with *systemctl*. This does seem to work to disable the Bluetooth service, but that is not what I want. The problem is that it makes the Bluetooth applet disappear, and I would have to go through the same manual CLI process to reenable the service if I want to use it again. I just want the radio off; the service should stay, so I can enable and disable the radio quickly from the taskbar.

Is there any way to get the behavior I want?

---

### Post by Bucky Ball on 2017-03-29
You shouldn't need to go to those lengths. Open 'Sessions and startup> Applications autostart tab' and you should see something there related to bluetooth. You may even have Bluez or something starting at boot. Untick all bluetooth related autostart apps and restart. 

Good luck. ;)

PS: Welcome to the mix and Xubuntu rocks. Be aware that 16.10 is an interim release with nine months support, meaning you will need to upgrade to 17.04 mid-year. If you're not far down the track, may have been better to start there or with 16.04 LTS, a very stable and long-term support release which is supported until 2019. Either way, enjoy the learning curve and the OS. ;)

---

### Post by F3BQ3DP on 2017-03-29
Thank you for the friendly reply. However, what's offered under Application Autostart is a checkbox for the Blueman Applet. As I said, I do want this applet to autostart. I just want it to start with my Bluetooth radio off -- or for my Bluetooth radio state to be remembered across reboots. The latter behavior is possible and default with WiFi (if my radio was off when I shut down, it's off when I start up) and sound (stays muted across reboots). But it's not apparent whether it's possible for Bluetooth.

---

### Post by #&amp;thj^% on 2017-03-29
> **F3BQ3DP said:**
> Thank you for the friendly reply. However, what's offered under Application Autostart is a checkbox for the Blueman Applet. As I said, I do want this applet to autostart. I just want it to start with my Bluetooth radio off -- or for my Bluetooth radio state to be remembered across reboots. The latter behavior is possible and default with WiFi (if my radio was off when I shut down, it's off when I start up) and sound (stays muted across reboots). But it's not apparent whether it's possible for Bluetooth.
If I follow you or understand correctly...You will need to edit this:
```
sudo -H gedit /etc/rc.local 
```
and add this before the line with exit 0:
```
rfkill block bluetooth
```

You should still be able to enable Bluetooth through the top bar applet.

This should work for most systems but it looks like there are a few bugs lurking in the kernel's ACPI for Thinkpads. [B]If you're on a Thinkpad, add the following to /etc/rc.local:
[/B]
```
echo disable > /proc/acpi/ibm/bluetooth
```

---

### Post by #&amp;thj^% on 2017-03-30
I guess none of that worked for you so I will add to this.
Actually changing /etc/bluetooth/main.conf was enough for me.

Search for the line at the bottom:

```
InitiallyPowered = true
```

and change the value to: (As Root)

```
InitiallyPowered = false
```
Save and close.

Hope this one works for you.

---

### Post by F3BQ3DP on 2017-03-30
Thanks very much for following up. You're right, I had tried the *rfkill *solution, but I had not used the */proc* line as well. I had high hopes for that addition, because I do have a Thinkpad. Unfortunately, after my last reboot, Bluetooth was still on.

I will try the [COLOR=#000000]*/etc/bluetooth/main.conf* method. I am a little skeptical, because the term [/COLOR]*[COLOR=#000000][FONT=&amp]InitiallyPowered [/FONT][/COLOR]*[COLOR=#000000]does not appear among the many commented-out defaults in this file, nor anywhere else. But I will try adding the line and will report back.[/COLOR]

---

### Post by #&amp;thj^% on 2017-03-30
Wow really, it dose not show it?:confused:
Can we see it here: "/etc/bluetooth/main.conf"
I have the Lenovo T430 and all is good...But with Ubuntu Mate && Unity as De's

---

### Post by F3BQ3DP on 2017-03-30
I rebooted with that *main.conf* line added. No improvement.

The opportunity to reboot was afforded by a sudden hard freeze. In addition to this, my WiFi keeps hanging, and I'm having to manually reconnect every so often. My mouse left button gets stuck to "depressed" in software all the time, and I don't know why. It's death by a thousand papercuts.

With all gratitude for your help, I think I'm done with this OS. Maybe I will move to the LTS version, to another distro, or back to Windows.

---

### Post by #&amp;thj^% on 2017-03-30
> **F3BQ3DP said:**
> I rebooted with that *main.conf* line added. No improvement.

The opportunity to reboot was afforded by a sudden hard freeze. In addition to this, my WiFi keeps hanging, and I'm having to manually reconnect every so often. My mouse left button gets stuck to "depressed" in software all the time, and I don't know why. It's death by a thousand papercuts.

With all gratitude for your help, I think I'm done with this OS. Maybe I will move to the LTS version, to another distro, or back to Windows.
I Also had problems with WiFi droping in 16.10: but no such problems with LTS 16.04.
If you do decide to stay and give that a try (16.04 LTS), I think you will be happier with your experience.
None the less sorry to hear about your problems with 16.10.
Best of Luck and Kind Regards

---

### Post by Bucky Ball on 2017-03-30
> **1fallen said:**
> If you do decide to stay and give that a try (16.04 LTS), I think you will be happier with your experience.

Give Xubuntu 16.04 LTS a try. :)

I don't know if you downloaded the ISO from the Xubuntu official site or checked the ISO after the download, but [download from here]("http://xubuntu.org/getxubuntu/") and good luck.

---

