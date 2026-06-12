---
title: "lenova G700 boot to usb flash drive and uefi device tutorial may work on others too"
date: 2014-03-02
forum: General Help
---

### Post by AgentZ86 on 2014-03-02
Hi all just wanted to give a quick how to on this

OK you get blank screen on your lenova G700 for Ubuntu 13.10 flash drive

Assuming you created your USB bootable flash drive properly and it's ready to boot up your G700

[LIST]
[*]Press the nova key which brings up your boot menu
[*]Select bios, then boot option and change the boot option from uefi to legacy
[*]Then save and exit
[/LIST]

It will restart but you really don't want that you want boot menu again
[LIST]
[*]So turn off and power back up with the nova key again to get the boot menu
[*]This time select boot menu
[*]Then when you see the list of boot devices you want the one that show your flash drive (but there may be 2 of them) One will suggest that it's a USB HD this is the one you want and NOT the UEFI device
[/LIST]

Ok, now that it's booting you should get the pre-slplash Ubuntu screen and it (might start to boot) but really we want to boot to (nomodeset) option which might be too late now. However you want to see if it will boot without that first so let it try to boot.
If you get a blank screen again (you may even hear the ubuntu drum roll indicating it's loaded but you still have blank screen)
Thats ok we will reboot to usb hd again

However, this time when you see the ubuntu splash screen you will hit (F6) and may see option to select your language thats ok. Select it, then hit (F6) again for the option screen
***NOTE on lenova the F6 = Fn+F6 you will see this indicated in orange on your keyboard (Fn means function key which has to be pressed to make the F6 key function as an actual F6 key otherwise the key will do something else) Just FYI on that.

Anyhow, once you get past the language selection and are into the options screen you will select (nomodeset) from the selection and there will be an X next to your selection to show that you have selected it
Press esc to exit that menu

And then (try ubuntu without installing) if thats what you want or install it if that is what you want

Anyhow hope this helps and may help with others who have uefi device on their partiction or some other security crap on the hard drive preventing it from booting to usb stick

**The short version:**
nova button power on to change bios to boot with legacy device instead of uefi
nova button to select boot menu to boot from usb hd aka legacy device (not uefi memory)
ubuntu splash screen comes up hit F6 to get into options mode and select (nomodset)
try ubuntu without installing or install as you desire

Hope this helps

---

