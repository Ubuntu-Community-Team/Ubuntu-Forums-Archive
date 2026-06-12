---
title: "Strange Thunar notification on clicking unmount?"
date: 2014-04-01
forum: General Help
---

### Post by vasa1 on 2014-04-01
**Background:** I have Thunar 1.6.3 but my system is a bit mixed up ... Openbox session running on parts of Lubuntu and Xubuntu. I'm mentioning this because it's possible that what I'm seeing is an artifact of my system and not the "norm".

I have a 500GB USB mounted.
When I right-click on the device in Thunar's side-panel and choose Unmount, I see a very, very brief flash of what appears to be notification pop-up.
To catch it, I mounted the device again and followed the procedure described here: [http://askubuntu.com/a/352200](http://askubuntu.com/a/352200) . So I opened a terminal window and pasted the following code:
```
dbus-monitor "interface='org.freedesktop.Notifications'"    |     \
grep --line-buffered  "member=Notify\|string"
```

Then, on unmounting, the screen showed this:

```
[04:14 PM] ~ $ dbus-monitor "interface='org.freedesktop.Notifications'"    |     \
> grep --line-buffered  "member=Notify\|string"
   string ":1.37"
method call sender=:1.26 -> dest=:1.35 serial=67 path=/org/freedesktop/Notifications; interface=org.freedesktop.Notifications; member=Notify
   string "Thunar"
   string "drive-harddisk-usb"
   string "Writing data to device"
   string "There is data that needs to be written to the device "TOSHIBA EXT" before it can be removed. Please do not remove the media or disconnect the drive"
         string "urgency"
^C
[04:43 PM] ~ $ 

```

Can a Thunar user please comment?

---

### Post by slickymaster on 2014-04-01
It could be related to having a open directory on the media. _fuser_ or _lsof_ should tell you which process has a file open on the media

You could try to umount from a terminal to check if it is a GUI related issue.

---

### Post by vasa1 on 2014-04-01
> **slickymaster said:**
> It could be related to having a open directory on the media. _fuser_ or _lsof_ should tell you which process has a file open on the media

You could try to umount from a terminal to check if it is a GUI related issue.
I was pretty sure I closed everything related to the media. Anyway, I checked with *lsof | grep TOSHIBA* to confirm and then did the unmount.

I can unmount from the terminal but my questions are specific to unmounting via Thunar:
[LIST]
[*]I've never seen notification bubbles disappear so quickly. What makes that particular notification disappear so fast? 
[*]What do the contents mean?
[/LIST]

---

### Post by slickymaster on 2014-04-01
I'm wondering if that pop-up notification isn't the thunar dialog notification informing you that it is safe to remove the media or disconnect the drive from the computer.
However this notification will only be displayed if support for _libnotify_ is enabled, and you have installed a notification daemon. A notification daemon for Xfce is available from the Xfce Goodies Project.

---

### Post by vasa1 on 2014-04-01
> **slickymaster said:**
> I'm wondering if that pop-up notification isn't the thunar dialog notification informing you that it is safe to remove the media or disconnect the drive from the computer.Well, the text doesn't seem to convey that impression.
> **slickymaster said:**
> However this notification will only be displayed if support for _libnotify_ is enabled, and you have installed a notification daemon. A notification daemon for Xfce is available from the Xfce Goodies Project.Lubuntu uses xfce's notification system and I get other notifications as usual. So that doesn't explain why this particular notification disappears so fast that it's not readable. It goes off really quickly.

---

### Post by Dennis N on 2014-04-01
> Can a Thunar user please comment? 

I see this very brief notification every time I remove a usb flash drive in Xubuntu 12.04. It was previously mentioned in this thread:

[http://ubuntuforums.org/showthread.php?t=2146111](http://ubuntuforums.org/showthread.php?t=2146111)

See My post #4 in that thread.

It would be good if the developers adjusted the display time. It does not obey the "Disappear after" time set for notifications.

---

### Post by vasa1 on 2014-04-01
> **Dennis N said:**
> I see this very brief notification every time I remove a usb flash drive in Xubuntu 12.04. It was previously mentioned in this thread:

[http://ubuntuforums.org/showthread.php?t=2146111](http://ubuntuforums.org/showthread.php?t=2146111)

See My post #4 in that thread.

It would be good if the developers adjusted the display time. It does not obey the "Disappear after" time set for notifications.

The content of the notification could be improved as well:

---

### Post by slickymaster on 2014-04-01
You could probably ping Nick Schermer (nick@xfce.org or at #xfce-dev channel) on that, since is the upstream maintainer.

---

### Post by vasa1 on 2014-04-01
> **slickymaster said:**
> You could probably ping Nick Schermer (nick@xfce.org or at #xfce-dev channel) on that, since is the upstream maintainer.
I thought I'd post about this at the Xfce forums but I can't find a "start a new thread" button there! My login and password are fine though. Anyway, I guess all this is a bit late for 14.04.

---

### Post by slickymaster on 2014-04-02
> **vasa1 said:**
> I thought I'd post about this at the Xfce forums but I can't find a "start a new thread" button there! My login and password are fine though. Anyway, I guess all this is a bit late for 14.04.

Yeah, you're right about being late for 14.04, but in six months from now we'll be welcoming a new release.

The "start a new thread" button in the Xfce forums is called 'Post new topic', and it's located in the bottom right of the window, just scroll all the way down. I'm attaching a screenshot of it.
[ATTACH=CONFIG]251651[/ATTACH]

---

### Post by vasa1 on 2014-04-02
> **slickymaster said:**
> ...
The "start a new thread" button in the Xfce forums is called 'Post new topic', and it's located in the bottom right of the window, just scroll all the way down. I'm attaching a screenshot of it.
...
Thanks! [http://forum.xfce.org/viewtopic.php?pid=32549#p32549](http://forum.xfce.org/viewtopic.php?pid=32549#p32549)

---

### Post by slickymaster on 2014-04-02
You're very welcome vasa1, and thanks for opening that thread at the Xfce forums.

---

