---
title: "Performance seems way worse than it should be when involving the GPU"
date: 2016-04-03
forum: General Help
---

### Post by Hungry Man on 2016-04-03
I have a Lenovo T540P with an nvidia graphics card - the 730m. On Windows, gaming is smooth, most GPU-related things are. However, on Ubuntu, I've noticed really terrible performance in two areas:

1) HD videos in VLC, using the nvidia drivers
2) Wine gaming. I've been playing Path of Exile, which I've run on much weaker systems at much higher resolution. On WINE, I'm running it using only 720p and all of the graphics options down low. Still I run into huge lag issues when there are a lot of GPU heavy actions going on.

I realize the 730m is not exactly the most powerful card, but, as I said, I've had a weaker GPU before and had better performance.

So, basically, I'm looking to improve GPU performance specifically.

---

### Post by X-RED_Tech on 2016-04-03
The obvious question is which nvidia drivers version? Nvidia recommends 361.42, by the way.

---

### Post by Hungry Man on 2016-04-03
> **X-RED_Tech said:**
> The obvious question is which nvidia drivers version? Nvidia recommends 361.42, by the way.
In the 'Additional Drivers' interface I have 352.63 selected, and that's the newest version I see there.

---

### Post by X-RED_Tech on 2016-04-03
Add the 'official' PPA:
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
```

Then you'll have more options in Additional Drivers. Apply the 361 and reboot. Test.

---

### Post by Hungry Man on 2016-04-03
Hm. Got this error when adding the ppa:

PermissionError: [Errno 13] Permission denied: '/etc/apt/sources.list.d/google-chrome.list'

So once I figure that out I'll continue.

edit: OK, installing and then I'll reboot.

---

### Post by X-RED_Tech on 2016-04-03
Keep us posted...
That error is totally unrelated but suggests other problems in that system.

---

### Post by SeijiSensei on 2016-04-03
I suggest using SMPlayer and choosing the VDPAU video driver.  I recommend the version from Doug McMahon's repository for 14.04 with mpv as the player engine.  
```

sudo add-apt-repository ppa:mc3man/trusty-media
sudo add-apt-repository ppa:mc3man/mpv-tests
sudo apt-get update
sudo apt-get install smplayer mpv

```
In SMPlayer, choose Options > General, then type "/usr/bin/mpv" in the executable box.  Finally, click on the Video tab and choose "vdpau" from the list.

The "trusty-media" repository is designed to work with 14.04, the current version of Ubuntu with long-term support.

---

### Post by Hungry Man on 2016-04-04
Yeah the error was unrelated, I had modified that file to and inadvertently broken some other things.

Performance still seems quite week - I'm thinking it may be due to my wine configuration for this? I'm also unable to run the application above 720p without it crashing with "invalid parameters received" any time I up the resolution.

As for using a different player, I could, but my guess is that I'd run into the same performance problems because it's not really specific to VLC but seemingly to my GPU.

---

### Post by Hungry Man on 2016-04-04
Yeah the error was unrelated, I had modified that file to and inadvertently broken some other things.

Performance still seems quite weak - I'm thinking it may be due to my wine configuration for this? I'm also unable to run the application above 720p without it crashing with "invalid parameters received" any time I up the resolution.

As for using a different player, I could, but my guess is that I'd run into the same performance problems because it's not really specific to VLC but seemingly to my GPU.

---

