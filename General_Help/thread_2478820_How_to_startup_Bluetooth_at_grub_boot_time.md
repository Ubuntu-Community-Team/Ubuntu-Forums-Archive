---
title: "How to startup Bluetooth at grub boot time?"
date: 2022-09-06
forum: General Help
---

### Post by dragonfly41 on 2022-09-06
[https://www.logitech.com/en-gb/products/keyboards/mx-keys-wireless-keyboard.html](https://www.logitech.com/en-gb/products/keyboards/mx-keys-wireless-keyboard.html)

I checked if this subject has been raised in forum but found no hits.


I purchased a Logitech MX Keys keyboard which operates quietly, keys back illuminated.  For the time being, my old Dell clackety clack mechanical keyboard must remain connected in parallel by USB port. Two connected keyboards: wired and wireless.


The Logitech MX Keys is useful when trying to type silently and not disturb others nearby.
However my quandary is that there is a dead zone on booting up. The Logitech (which previously has been paired with Ubuntu and works fine) cannot of course operate until bluetooth is in play - even at grub time.

I use rEFInd GUI and this is the first layer to navigate, but at that point there is no bluetooth.

I must keep the old USB connected keyboard to get me through (a)the [rEFInd]("https://ubuntuforums.org/ROOT--rEFInd_313.html") login UI theb (b) to desktop process and then (c) I must apply command
 

```
sudo service bluetooth start

```

before Logitech wireless keyboard kicks in.


How do I eliminate this dead zone so that Bluetooth is in play *before* I start using login UI such as [rEFInd]("https://ubuntuforums.org/ROOT--rEFInd_313.html") which has buttons to select.? My old keyboard can then be disconnected.


An example of [rEFInd]("https://ubuntuforums.org/ROOT--rEFInd_313.html") UI is here.
[https://github.com/bobafetthotmail/refind-theme-regular](https://github.com/bobafetthotmail/refind-theme-regular)


A brief search found this ...
[https://askubuntu.com/questions/17504/how-can-i-have-a-bluetooth-keyboard-auto-connect-at-startup](https://askubuntu.com/questions/17504/how-can-i-have-a-bluetooth-keyboard-auto-connect-at-startup)


And also another user with same quandary.
[https://superuser.com/questions/1734897/logitech-mx-keys-wireless-keyboard-not-working-on-usb-in-bios-and-bootloader](https://superuser.com/questions/1734897/logitech-mx-keys-wireless-keyboard-not-working-on-usb-in-bios-and-bootloader)


But my purchase of Logitech MX did not supply a dongle.  It successfully connects only after boot process (which requires old keyboard for a period).


There are a few quirks in Logitech MX Keys which need to be learned by the new user. For example you need to use fn key (3rd button to the right of space key) to enable F1 to F12 buttons.  But otherwise it is useful to bring peace in a shared room if you are clacking away typing on an old mechanical keyboard.

---

### Post by ActionParsnip on 2022-09-06
Run:
```

sudo systemctl [FONT=inherit]enable[/FONT] bluetooth

```

---

### Post by dragonfly41 on 2022-09-06
I confess I'm surprised that this works. I applied the command, shut down, rebooted - but the rEFInd GUI buttons can still not be clicked on.  I did get through to desktop because the rEFInd GUI auto clicks on *default *selected button after a delay, but if I have other buttons to click on such as Windows button in GUI this does not work for me.

I assumed that Bluetooth was already enabled.

I was about to try @reboot as discussed here.

[https://askubuntu.com/questions/814/how-to-run-scripts-on-start-up](https://askubuntu.com/questions/814/how-to-run-scripts-on-start-up)

So, partly answered. Thanks.

---

