---
title: "Really strange behavior while booting"
date: 2013-12-13
forum: General Help
---

### Post by ceciliasp on 2013-12-13
[COLOR=#333333][FONT=UbuntuRegular]My computer have dual boot, Windows 8 (pre-installed) and Ubuntu 12.04[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]On a random basis, I can't boot to Ubuntu. I get to see the GRUB screen with all the booting options but sometimes, after the countdown (or after pressing enter when the countdown does not appear) the screen stays dark and nothing happens. After rebooting or running the live usb and rebooting again I can boot into Ubuntu. I don't know if the following has anything to do with this but a few days ago I configured the hybrid suspend option to be able to hibernate. The script shows like this:[/FONT][/COLOR]
# Always use suspend_hybrid instead of suspend
if [ "$METHOD" = "suspend_hybrid" ]; then
METHOD=suspend
fi
PM_HIBERNATE_DELAY=300  # time in seconds until hibernate (suspend to disk) occurs; 900 means 15 minutes"
[COLOR=#333333][FONT=UbuntuRegular]I really can't tell if both things are related or not, but I think that this configuration might have caused some damage to my booting system. Can anybody point me in what direction I should start looking for a solution?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Thanks Cecilia[/FONT][/COLOR]

---

### Post by Iowan on 2013-12-13
Duplicate thread:
[http://ubuntuforums.org/showthread.php?t=2193640](http://ubuntuforums.org/showthread.php?t=2193640)

Please check the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):
> Use color and font properties for highlighting portions of your text, and not for all of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post. ALL CAPS is interpreted as screaming. Funky non-uniform font size/color is difficult for those who are visually impaired. If you are having problems with reading the font, please adjust your browser.
Do not cross post, or post the same thing in multiple locations.

---

