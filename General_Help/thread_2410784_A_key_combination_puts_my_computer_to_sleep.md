---
title: "A key combination puts my computer to sleep"
date: 2019-01-20
forum: General Help
---

### Post by Jason_Hunter on 2019-01-20
I've just gotten a new keyboard and some kind of key combination puts the computer to sleep; not sure which combination. 

Is there some way to disable completely sleep/hibernation from keyboard? I never want it to sleep; this is a stationary computer and is always on.

---

### Post by Jason_Hunter on 2019-01-22
Nobody got any clue?

---

### Post by Frogs Hair on 2019-01-22
The Ubuntu version would be helpful to know because the power settings are found in different places depending on DE. On 18.04 with the default desktop automatic suspend can be disabled from settings power. I don't know the key binding for sleep because it's not listed in settings-devices-keyboard unless I missed it. Lock screen is listed though.

---

### Post by Jason_Hunter on 2019-01-26
Thank you 

I'm using 18.04 and I find no relevant settings in Settings->Power

---

### Post by Jason_Hunter on 2019-01-26
The key combination that puts the computer to sleep is Fn+l

So, if I press and hold the function key and hit the letter "l"

---

### Post by dmnur on 2019-01-27
Unfortunately GNOME no longer provides a way to configure the suspend key behavior. But you can configure **systemd-logind** directly.

To do this, edit **/etc/systemd/logind.conf**. You'll find there this line:
```
#HandleSuspendKey=suspend
```
Change it to this:
```
HandleSuspendKey=ignore
```
Save the file and reboot; if you don't want to reboot now, you can *inhibit* suspend key handling with this command:
```
nohup systemd-inhibit --what=handle-suspend-key sleep 30d &>/dev/null &
```

---

### Post by Jason_Hunter on 2019-01-27
That's just excellent;) thanks

---

