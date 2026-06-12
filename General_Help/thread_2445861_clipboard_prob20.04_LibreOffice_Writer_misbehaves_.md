---
title: "clipboard prob:::20.04 LibreOffice Writer misbehaves on right mouse click/copy or cut"
date: 2020-06-21
forum: General Help
---

### Post by Kris_M on 2020-06-21
see post 4 and ff


20.04 LibreOffice Writer sometimes misbehaves on right mouse click/copy or cut / paste.

That is, after highlighting a section, many times when I do it I either get the previous thing copied or nothing.

Highlight, then Ctl c and Ctl v work correctly.

Anyone else notice this?

---

### Post by ajgreeny on 2020-06-21
Not seen it but it sounds more like a mouse hardware problem than anything to do with LO.

Do you have another  mouse  you can try?

---

### Post by Kris_M on 2020-06-21
> **ajgreeny said:**
> Not seen it but it sounds more like a mouse hardware problem than anything to do with LO.

Do you have another  mouse  you can try?
Thanks.

I tried a wired mouse and it did the same thing. I played with it a bit and most times if I right click, copy, right click, copy, then paste it works, but sometimes it takes 3 times. (for this test I was copying from LibreOffice to text editor though discovered the problem just moving stuff around in L O W.) Only on LibreOffice Writer. Not on other things with listed text - can copy past first time, never skips. Tried different font but no difference. Weird. this is my 3rd 20.04 build. Same on all 3. weird. I even tried clicking a few times to make sure window is active but no diference - sometimes it just doesn't see what I'm doing. even though it offers me "copy" etc.

---

### Post by Kris_M on 2020-06-21
I installed Apache OO on POL and it does the same but I saw something... so back here to Libra:

On Libre:
If I click on a few characters in the text and highlight it, the little "Paste" icon in the top bars lights up. When I right click and choose copy, it shuts off. THUS it is saying there is nothing to paste and indeed when I try to paste it (here or elsewhere, there is nothing.

Why is it doing that?
If I repeat, then it lights up and there is indeed something to paste.

and sometimes when I start LibreO W up there is already something in clipboard.

-->This is a prob of clipboard not being set/reset correctly...


The first right-click copy loads clipboard
paste does not empty it
it takes TWO right-click copies to replace clipboard's contents.
It NEVER empties.

I can clear it with xsel -bc but the first time I use it the problem starts up again.

I install parcellite, reboot, run it, contents or prior boot are still in clipboard.[URL="https://wiki.ubuntu.com/ClipboardPersistence"]
[/URL]

---

### Post by habana on 2020-06-21
This is a bug - it is really annoying. See [https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1879968](https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1879968)

Please add your name to he list of those affected.

---

### Post by Kris_M on 2020-06-21
> **habana said:**
> This is a bug - it is really annoying. See [https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1879968](https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1879968)

Please add your name to he list of those affected.

No. This was reported back in 2010 a bunch of times. If Canonical has no interest in it other than to suggest we use the DOS 3.11 method of Ctl+c or x or v, I shan't push them. I seem to try Ubuntu about every year.....  Maybe it'll get fixed in 30.04 LTS

---

### Post by Kris_M on 2020-06-21
Someone on askubuntu said that Ubuntu Wayland desktop didn't have that problem and indeed it doesn't. However you have to Mickey Mouse for a minute with apps tray and Activities (clicking them furiously) to get it to show the apps tray and the apps in the side bar. Not particularly well executed.

---

### Post by ajgreeny on 2020-06-22
Do you use some clipboard manager package that may be affecting the copy/paste actions of your system?

---

