---
title: "MS Bluetooth Keyboard and Mouse"
date: 2007-02-23
forum: General Help
---

### Post by PiZZLE on 2007-02-23
ok when i was running Dapper i had my microsoft bluetooth mouse and keyboard running perfectly, waking up from sleep and on booting up. ive searching high and low, i think ive tried editing EVERY bt file on the filesystem and NOTHING. i can get it to work if i do a "sudo hidd --search" but once the KB and mouse go to sleep they wont wake up and i have to pair again. ive tried setting legacy keyboard in my bios also, when i do that my BT keyboard works in grub but when i get to the ubuntu login screen, neither my BT keyboard works or my wired keyboard. if i can get all this to work ill be a happy camper, can someone throw some suggestions my way? thanks

---

### Post by dakota34 on 2007-02-23
This steps outlined in this link were what finally did the trick for me, using Microsoft bluetooth keyboard & mouse:  [https://help.ubuntu.com/community/BluetoothSetup?highlight=(bluetooth](https://help.ubuntu.com/community/BluetoothSetup?highlight=(bluetooth))

Try the procedure outlined in the "Connect Devices at Startup" section about two-thirds of the way down the page.

---

### Post by PiZZLE on 2007-02-23
> **dakota34 said:**
> This steps outlined in this link were what finally did the trick for me, using Microsoft bluetooth keyboard & mouse:  [https://help.ubuntu.com/community/BluetoothSetup?highlight=(bluetooth](https://help.ubuntu.com/community/BluetoothSetup?highlight=(bluetooth))

Try the procedure outlined in the "Connect Devices at Startup" section about two-thirds of the way down the page.

i tried that. another thing is i cant access /etc/init.d/bluez-util i even tried installing the packages and still nothing.

---

### Post by dakota34 on 2007-02-24
Here's a different, briefer set of instructions specific to Edgy that I had bookmarked, don't know if you've tried this already, but it might be worth trying:

[https://help.ubuntu.com/community/BluetoothMouse](https://help.ubuntu.com/community/BluetoothMouse)

---

