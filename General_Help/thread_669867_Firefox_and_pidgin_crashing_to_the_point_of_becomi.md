---
title: "Firefox and pidgin crashing to the point of becoming useless.."
date: 2008-01-16
forum: General Help
---

### Post by jesushero on 2008-01-16
I am using Ubuntu Studio 7.10 Gutsy on an Intel P4 2.6 GHz with an asus mboard, nvidia nv34 FX5200 and 512mb ram. Ethernet connection, desktop not laptop.

Since the first few updates and after installing flash and java runtime environment firefox started crashing every now and then. Now, a few weeks later, it crashes all of the time. I'm typing fast now!! I usually can't get anything done!!!! Pidgin crashes as well, for no apparent reason. No related log entries. No specific pattern of use of either firefox or pidgin!!!


HEEEEEEEELP!!!! I can't stand it anymore!!!! Any ideas???????

---

### Post by Schnooze on 2008-01-16
I think there is a current bug with flash right now but wait for another reply

---

### Post by gunbladeiv on 2008-01-16
for firefox maybe your flash plugin has some bug which is everyone already know.
to fix this, you need to remove your flash by add/remove program or using synaptic package.
Then download flash source from flash website.
extract the source file.
type in terminal:
[LIST]
[*]mkdir ~/.mozilla/plugins
[*]cp install_flash_player_9_linux/libflashplayer.so ~/.mozilla/firefox/plugins
[*]sudo aptitude install nspluginwrapper
[*]nspluginwrapper -i ~/.mozilla/plugins/libflashplayer.so
[/LIST]

For pidgin crash, i dont know the problem, cause mine never crash unless i do sumthing stupid.

---

### Post by jesushero on 2008-01-17
Hello, thanks for replying.

I've got the flash source, and an installer with it. I had used the installer to install it at first, not nspluginwrapper. 

I tried to uninstall it to do the nspluginwrapper procedure but I can't seem to find it on Add/Remove or Package Manager!!! How should I uninstall it?? 

Does nspluginnwrapper create a file with the same name? If so, running it as root should replace the existing files without any need for uninstall. Or not?? 

Any suggestions would be welcome! Thanks again!

---

### Post by madflyguy on 2008-01-17
Are you using KDE or gnome for your gui? I've tried KDE and firefox was all but useless. However I am having trouble with pidgin crashing. I'm running 7.10 with gnome, and have "advanced desktop effects" installed and working. Pidgin will crash intermittently, I can't pin it down to any one thing I'm doing just yet. I also have some additional (asian) languages installed but do not use SCIM when pidgin is up and running.  Anyone read anything about this? :(


EDIT: Pidgin has crashed 3 times now when i've entered some text into an IM window and sent it, my name shows up and the text starts to show up and then pidgin crashes. Maybe when the chat log goes from no scroll to scrolled?

---

### Post by jesushero on 2008-01-17
I'm using gnome. I've never tried kde, but for some reason ubuntu studio comes with some kde-related libraries and stuff like that (I discovered this recently when a kde-related library update came up at update-manager). I searched a bit and found I have 10-15 kde-related files on my system. 

Would the gnome stuff I'm using be compatible with kde (Ardour GTK, Pure Data, Jack Control, Gimp, Cinelerra, etc)?

Firefox seems to be getting worse every day.. Pidgin crashes once a day approximately...

So would kde solve the firefox problem, considering I'd still be using flash and java as I have to deal with java applets for some projects I am working on? Any ideas or relevant experience from others???

Thanks everyone for replying up to now! Hope I get this solved!!!

---

