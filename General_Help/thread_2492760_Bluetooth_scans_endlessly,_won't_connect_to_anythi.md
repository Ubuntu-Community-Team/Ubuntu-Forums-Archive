---
title: "Bluetooth scans endlessly, won't connect to anything, 22.04"
date: 2023-11-22
forum: General Help
---

### Post by jdkcarlson on 2023-11-22
Please let me know if there is a better subforum for this.

I am running Ubuntu 22.04 on a 2022 Thinkpad. Unlike with previous versions, Bluetooth worked immediately for me. It continued to until about a month ago. There was no obvious event marking the transition, as far as I can recall.

It would only connect to a single known pair of headphones immediately after startup, and then after a restart or two, it never reconnected at all. 

In Settings, Bluetooth seems to scan endlessly without finding anything. Doing  "scan on" and "devices" in bluetoothctl is more successful, temporarily.

```
[bluetooth]# devices
Device 20:00:00:00:29:B5 RZE-BT700E
[NEW] Device 6B:12:45:AF:EE:2B LE-Obsidian
[DEL] Device 6B:12:45:AF:EE:2B LE-Obsidian
[NEW] Device 6B:12:45:AF:EE:2B LE-Obsidian
[bluetooth]# pair 6B:12:45:AF:EE:2B
Attempting to pair with 6B:12:45:AF:EE:2B
Failed to pair: org.bluez.Error.ConnectionAttemptFailed
[DEL] Device 6B:12:45:AF:EE:2B LE-Obsidian
[bluetooth]# devices
Device 20:00:00:00:29:B5 RZE-BT700E
[bluetooth]# scan on
Failed to start discovery: org.bluez.Error.InProgress
[bluetooth]# connect 20:00:00:00:29:B5
Attempting to connect to 20:00:00:00:29:B5
Failed to connect: org.bluez.Error.Failed br-connection-page-timeout

```

The same devices do connect fine to my phone. I have tried uninstalling and reinstalling bluez* and some other things on StackExchange forums, and it's not impossible I've made things worse, but the behavior is not markedly differnt than before.

Please help me diagnose and fix this.

---

### Post by dragonfly41 on 2023-11-22
I use Bluetooth Manager GUI to inspect devices. Install and try that.
Also in Synaptic Manager search "bluetooth" to see what is installed.

---

### Post by jdkcarlson on 2023-11-22
Is that blueman-manager?

That shows the RZE-BT700E but doing "search" doesn't show up my other headphones LE-Obsidian even when I set them to pair. Trying to connect to RZE-BT700E gives br-connection-page-timeout.

Searching "bluetooth" in synaptic shows the following as installed (typed by hand from reading the GUI, so I hope I transcribed successfully):

```
blueman
bluez
bluez-alsa-utils
bluez-btsco
bluez-cups
bluez-firmware
bluez-hcidump
bluez-meshd
bluez-obexd
bluez-tests
bluez-tools
gir1.2-gnomebluetooth- 42.0-5
gnome-bluetooth-3-common 42.0-5
gnome-bluetooth-common 3.34.5-8
libasound2-plugin-bluez
libbluetooth3
libgnome-bluetooth-3.0-13
libgnome-bluetooth13
libkf5bluezqt-data
libkf5bluezqt6
libldacbt-abr2
libldacbt-enc2
libmm-glib0
modemmanager
pulseaudio-module-bluetooth
qml-module-org-kde-bluezqt
rfkill
tlp
tlp-rdw
totem-plugins
```

---

### Post by dragonfly41 on 2023-11-22
Blueman .. yes.

I don't see one list with your items but when I do individual searches such as blueman, bluetooth bluez I see the packages installed.

But what I do is .. bottom docky panel 3x3 button > Activities> search Blue.. and tick on Bluetooth Manager to launch.

Or click on topbar Aplications > System Tools > Bluetooth Manager

Further tips here on using bluetoothctl

[https://devicetests.com/fixing-bluetooth-headphone-connection-issue](https://devicetests.com/fixing-bluetooth-headphone-connection-issue)

---

### Post by jdkcarlson on 2023-11-22
Hi, this list is what I get in the Synaptics manager when I search Bluetooth. 

I have Bluetooth Manager via the 3x3 panel and search, and it turns out that's the same application called from the command line by blueman-manager. With it, I'm able to do this, from my last message:

[INDENT][It] shows the RZE-BT700E but doing "search" doesn't show up my other headphones LE-Obsidian even when I set them to pair. Trying to connect to RZE-BT700E gives [the error] "br-connection-page-timeout".[/INDENT]

---

### Post by dragonfly41 on 2023-11-23
Have you followed the tips in the link above .. re: bluetoothctl in terminal.

Is Obsidian seen using devices command?

Have you tried all suggested tips?  

Reinstall pulseaudio-module-bluetooth
Change Visibility Settings in Blueman Bluetooth Manager

---

### Post by jdkcarlson on 2023-11-26
Hi, no, I missed the link. I'll check that out after this message.

As to the other things, I just did sudo apt remove pulseaudio-module-bluetooth, then sudo apt install pulseaudio-module-bluetooth.

I've just now set visibility in Blueman preferences to "permanently visible." A search in Blueman now shows up Obsidian.

I trusted it, and asked it to pair. It said it was paired, then said pairing had failed, then said it had disconnected.

---

### Post by dragonfly41 on 2023-11-27
> [COLOR=#000000]A search in Blueman now shows up Obsidian.[/COLOR][COLOR=#000000]
[/COLOR]Well at least it is seen by Blueman.  In searching around I recollect reading that Obsidian (I have only experience with BOSE) is a bit choosy about version of host Bluetooth. I would explore that theory to rule out that possibility of mismatch. I see that Obsidian refers to 5.3. But it is just one thought to eliminate. Best checked in Obsidian forum.

I posted a link to Obsidian but as I guessed "Obsidian" is used by different vendors. So I leave you to track down the correct forum.

[Postscript]

Further links in researching Bluetooth version / compatibility.

[https://techreviewadvisor.com/bluetooth-5-3-vs-5-2/](https://techreviewadvisor.com/bluetooth-5-3-vs-5-2/)

and


[https://askubuntu.com/questions/591803/how-to-check-bluetooth-version-on-my-laptop](https://askubuntu.com/questions/591803/how-to-check-bluetooth-version-on-my-laptop)
[h=3]"While not part of the original question, someone reading this may also wonder how to get the bluetooth version of a bluetooth peripheral (I know I did):"[/h]

---

### Post by jdkcarlson on 2023-11-28
"LE-Obsidian" is indeed a pair of Bose bluetooth headphones.

Would host bluetooth have changed with some update? These headphones and this computer worked fine together for about eighteen months before this incompatibility happened.

Where is the link to Obsidian you said you posted? And do you mean on Ubuntu Forums, or elsewhere?

I will follow the other links now.

[UPDATE:]

I've read the link comparing Bluetooth versions 5.2 and 5.3, and the StackExchange post on versions. hciconfig -a returns HCI and LMP versions 5.2 (0xb). hcitool info on my headphones returns "Operation not permitted." sudo !! gives "Input/output error". My assumption is that this is because my headphones can't connect anyway(?)

---

### Post by dragonfly41 on 2023-11-28
I have various BOSE devices working but yours (which I do not have) seem to be problematic.  

Perhaps post a question in a dedicated discussion such are here. And of course BOSE.

[https://www.headphonesty.com/2021/09/bose-bluetooth-headset-pairing-problems/](https://www.headphonesty.com/2021/09/bose-bluetooth-headset-pairing-problems/)

[https://www.zdnet.com/article/how-to-pair-bose-bluetooth-headphones-to-any-device/](https://www.zdnet.com/article/how-to-pair-bose-bluetooth-headphones-to-any-device/)


If you had a Windows dual boot or Android or VM you could try installing BOSE Connect App. I don't think it runs on Ubuntu. My last (corrected: Logitech not BOSE) purchase was a webcam .. but it only works on Windows.

In the link above there is some discussion about forgeries not connecting. I hope that doesn't apply to yours. First time I learned about that.

[P.S.] And here is a variant of the theme.

[https://askubuntu.com/questions/1292166/how-to-connect-my-bose-headphones-to-ubuntu-through-bluetooth](https://askubuntu.com/questions/1292166/how-to-connect-my-bose-headphones-to-ubuntu-through-bluetooth)

And since BOSE is kernel dependent this might account for this ..

> [COLOR=#000000] There was no obvious event marking the transition, as far as I can recall.[/COLOR][COLOR=#000000].

Can you revert to older kernel perhaps to experiment if there is a kernel dependency. But simplest approach is to run Connect App on Windows to test.[/COLOR]

---

### Post by jdkcarlson on 2023-11-29
My greatest fear is that it could be not my device, but some physical damage to the computer. My device was a gift that came in very official-looking packaging with documentation, registraton options, etc., so I assume it is authentic.

I will attempt the other fora. 

I do not have a Windows dual boot option, though I have Wine. That might be enough, although when I search for the Bose Connect app, I find <https://www.bose.com/apps/bose-connect>, which runs on phones and tablets, and so on, not laptops, and my device (QuietComfort 700) is not listed among the devices it helps with.

On my next reboot, I will attempt to use an older kernel, and report back.

---

### Post by dragonfly41 on 2023-11-29
If you have an earlier liveUSB lying around (with older kernel) you could try that in "Try Ubuntu" session (not reinstalling Ubuntu). But of course you will need to install blueman etc. into LiveUSB as in earlier discussions.  And also it will not be persistent so it is one time test. This might give you some clue separate from normal desktop.

---

### Post by jdkcarlson on 2023-11-29
To troubleshoot, I've in the past held down a button at startup and been given a list of kernels of various vintages to boot with, so I'd hoped I could do this here as well; is that not what you meant, or adequate for the purposes of testing Bluetooth connectivity?

---

### Post by dragonfly41 on 2023-11-29
Yes. Either way just to answer your question .. what has changed since they last worked?
The only thought of change might be an updated kernel since they last worked. So yes. Try a vintage around the date they last worked was the general idea. That would be better than LiveUSB since you can choose at boot.

---

### Post by dragonfly41 on 2023-11-29
This seems relevant.

[https://www.bose.co.uk/en_gb/support/articles/HC2782/productCodes/qc_earbuds_ii/article.html](https://www.bose.co.uk/en_gb/support/articles/HC2782/productCodes/qc_earbuds_ii/article.html)

Are you sure the phones are fully charged? Perhaps they are not retaining charge? Tips in above link.

---

### Post by gregory7 on 2024-04-27
[https://knowledgebase.frame.work/ubuntu-bluetooth-S1PGxfho](https://knowledgebase.frame.work/ubuntu-bluetooth-S1PGxfho)
I couldn't connect my headphones but then followed this algorithm successfully

---

### Post by dragonfly41 on 2024-04-28
My Logitech keyboard and mouse are very tetchy.
They have previously worked but not today so I use wired keyboard/mouse until I can fathom what is wrong. My MX keyboard keeps flashing on device [1] and I don't know how to reset the darned thing to steady state.  It is seen in Bluetooth Manager. I will try the suggested workflow but how do I restore the flashing keyboard light to steady before starting? Switching keyboard on/off has no impact. Keyboard usage is a mystery.

---

