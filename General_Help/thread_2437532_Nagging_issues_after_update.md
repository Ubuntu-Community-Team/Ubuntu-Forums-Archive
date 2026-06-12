---
title: "Nagging issues after update"
date: 2020-02-25
forum: General Help
---

### Post by Drowz0r on 2020-02-25
Hello all

Recently moved to the new Ubuntu and I have three really annoying issues:

1) Screenshots no longer work. In my browser etc I've got a plugin which allows some work arounds but naturally this stops me screenshotting the desktop. The screenshot sound and animation fires, but I don't get a prompt to save the image and I cannot just paste into something like kolour paint either. Quite a show stopper for some of my work.

2) Thunderbird's body headers are compact and I cannot find any Godly way to get back to full headers.

3) Ubuntu got really really really confused with my 3 monitor set up. "monitor 1" was actually definied with all the spec of monitor 2, despite being in the monitor 1 port, and if I turned off monitor 1, monitor 2 would in fact turn off. I eventually rectified this but monitor 3 just will not display anything at all. The hardware itself is all fine and tested - works with other machines and so on. Cables checked etc...

---

### Post by Holger_Gehrke on 2020-02-25
Regarding the screenshot issue here's a quote from the [manual]("https://help.ubuntu.com/stable/ubuntu-help/screen-shot-record.html.en#screenshot"):
"When you use a keyboard shortcut, the image is automatically saved in     your Pictures folder in your home folder with a file name that     begins with Screenshot and includes the date and time it was     taken."

Can't help you with the other two since I don't use Thunderbird and only have two displays (which work the way I want ...)

Holger

---

### Post by Drowz0r on 2020-03-08
> **Holger_Gehrke said:**
> Regarding the screenshot issue here's a quote from the [manual]("https://help.ubuntu.com/stable/ubuntu-help/screen-shot-record.html.en#screenshot"):
"the image is automatically saved in     your Pictures folder in your home folder with a file name that     begins with Screenshot and includes the date and time it was     taken."


Thanks. I looked there but it's empty. :/

---

### Post by him610 on 2020-03-08
It also says this, > If you do not have a Pictures folder, the images will be saved in your home folder instead.

---

### Post by GhX6GZMB on 2020-03-08
"[COLOR=#000000]Recently moved to the new Ubuntu"

Erm... 16.04 is "new Ubuntu"?


[/COLOR]

---

### Post by CelticWarrior on 2020-03-08
> **ml9104 said:**
> "[COLOR=#000000]Recently moved to the new Ubuntu"

Erm... 16.04 is "new Ubuntu"?


[/COLOR]

New for the OP, perhaps. But already old according to the usual standards. That said, and considering only the hardware described in the post, 16.04 should be fine. The problem is it has an year left of support. I wouldn't consider that release right now unless I had a very compelling reason like some piece of software that hasn't been updated to work with new kernels or something like that.

---

### Post by GhX6GZMB on 2020-03-08
> **Drowz0r said:**
> Hello all
1) Screenshots no longer work. In my browser etc I've got a plugin which allows some work arounds but naturally this stops me screenshotting the desktop. The screenshot sound and animation fires, but I don't get a prompt to save the image and I cannot just paste into something like kolour paint either. Quite a show stopper for some of my work.


My screenshots work by using the PrtScr or Alt-PrtScr key. The shots are placed on the Clipboard (using transient storage in /tmp) and can be inserted into any program using the "Paste" command. No reason to save them somewhere else first. 
'scrot' and 'xclip' are your friends.

[https://ubuntuforums.org/showthread.php?t=2433158](https://ubuntuforums.org/showthread.php?t=2433158)

---

### Post by Drowz0r on 2020-05-22
> **ml9104 said:**
> "[COLOR=#000000]Recently moved to the new Ubuntu"

Erm... 16.04 is "new Ubuntu"?


[/COLOR]

Hadn't updated my signature, with everything else that needed fixing.

---

### Post by Drowz0r on 2020-05-22
> **him610 said:**
> It also says this,

Sorry, I should have been clearer, it wasn't in either locations.

---

### Post by Drowz0r on 2020-05-22
I did another format, the monitor situation is marginally better, but it still labels my monitors incorrectly.

I've also noticed I cannot remove the lockscreen and each time I turn my PC on it requires a password to login, despite having both lockscreen and password stuff all switched to "off". Annoyingly, due to it thinking my TV is my primary monitor (despite telling it otherwise) it means my login stuff is on a TV on the other end of the room.

---

### Post by TheFu on 2020-05-22
Best to ask 1 question per thread and provide sufficient background on the OS.
Release, DE at a minimum.

We still don't know what release is being run, but Wayland had issues with screen shots, so if Wayland is being used, change to X11/Xorg before login using the "gear" settings.

Thunderbird can show full headers. It is under the "View" menu --> Headers --> All.  God or Dog have nothing to do with this.  You can also use the *View Message Source* option. Where that is probably depends on the mode you use for viewing messages.  Thunderbird issues really should be addresses to the Mozilla forums. I know it is a hassle to use and yet another account to have and the answers are often "don't do that."  Since I run an email server for a few clients behind a VPN, I often run into certificate issues with Thunderbird since they've decided to make some changes that cannot be over-ruled so our certs work.  It is like they don't understand the idea of an email gateway providing the real security so the monster end-user email server doesn't need to be nearly as secure.

---

