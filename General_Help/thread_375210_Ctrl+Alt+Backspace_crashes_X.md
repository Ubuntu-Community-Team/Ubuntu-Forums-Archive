---
title: "Ctrl+Alt+Backspace crashes X"
date: 2007-03-03
forum: General Help
---

### Post by gejr on 2007-03-03
Well..not only Ctrl+Alt+Backspace. Also manually logging out seems to crash X. I've never had trouble with this in the past. When I hit ctrl+alt+backspace programs close down and i get back to the login screen. After I enter my username and password it seems to freeze. I've gone to tty1 and run a "killall gdm" -> "gdm restart", but it doesnt help. The splash screen never shows up. Only the mouse is visible on a black background. After a while a white square gets drawn in the upper left corner and from there nothing. Only thing I can do is restart the computer. That gets everything back to normal.

Are there any logs or anything I could look at/post here to help me understand what's causing the problem?

thanks!

---

### Post by teaker1s on 2007-03-03
okay well two suggestions
1) ```
sudo dpkg-reconfigure xserver-xorg
```
try any or all these at boot by editing grub
```
NOAPIC NOAPCI NOSMP
```

---

### Post by TheCelloFellow on 2007-03-03
Well, on my box (xubuntu not gnome ubuntu) ctrl+alt+backspace is the built in keystroke to kill X. (And GDM restarts it). Also, the best way to restart GDM is `sudo /etc/init.d/gdm restart`, which uses init to do a proper restart. (Hint: That works on other daemons like apache and all sorts of other things too.)

Reconfiguring X sounds like a good idea.

---

### Post by gejr on 2007-03-03
I tried reconfiguring the xserver-xorg..no success. Neither was restarting gdm the sudo /etc/init.d/gdm restart -way.

What can I do? Do I really have to opt for that menu.lst-thingy? Ive never had this problem before :S

---

### Post by teaker1s on 2007-03-03
grub isn't scarey, as all changes are temp until we make them permanant.

at boot if you don't see grub hit esc
then pick latest kernel and hit "e"
you will now see comands and a long one.
 example between 
root=dev/hda1  ro splash
edit so
root=dev/hda1 [COLOR="Red"]NOAPIC [/COLOR] ro splash
hit return and boot
 it if works and you are happy boot with selected command(s) then login, open terminal
```
sudo update-grub
```

---

### Post by gejr on 2007-03-03
ok..I've added APCI APIC ASMP to grub and whoa..it works. What on earth did that do?:D 

Thanks a lot!

---

### Post by teaker1s on 2007-03-03
keep an eye on cooling fans-should be fine,but mainly it's how software can interact with hardware see below. only disable feature(s) that cause you an issue


[acpi]("http://www.google.co.uk/search?hl=en&defl=en&q=define:ACPI&sa=X&oi=glossary_definition&ct=title")
[apic]("http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller")
[smp is duel core support]("http://en.wikipedia.org/wiki/Symmetric_multiprocessing")

---

### Post by gejr on 2007-03-03
I may have been a little too quick about this. The problem reappeared after I reconfigured the x server again. The scrolling on websites was jumpy, so I figured it had something to do with my x config. Now I've fixed this problem, but the ctrl+alt+backspace problem is back. After waiting a long time for something to show up after I did the ctrl+alt+backspace I got this:

**Link to image:**
[http://geo.norvegium.no/Screenshot-1.png]("http://geo.norvegium.no/Screenshot-1.png")

---

### Post by teaker1s on 2007-03-03
I don't honestly know your exact issue, you can try one or more combinations in grub, they affect system by disabling features that kernel accesses.
```
NOAPIC NOAPCI NOSMP
```

maybe this isn't a total solution but it's worth trying a combo of them

---

### Post by gejr on 2007-03-03
Seems it's a problem with network-manager. I uninstalled network-manager and went back to WEP+Network-admin. Hopefully Feisty will have integrated WPA-support. I never seem to understand how to setup wpa_supplicant :)

Thanks for your help mr.teaker!

---

### Post by gejr on 2007-03-04
Well..couldn't quite settle with that. I've realized that running:
"sudo /etc/init.d/dbus restart" before I restart gdm makes it work. What can be the reason this works so beautifully? Is networkmanager really this evil?

---

