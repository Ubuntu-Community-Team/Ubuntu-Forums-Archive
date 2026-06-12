---
title: "Shift + Numeric Shortcuts Not Working"
date: 2013-06-24
forum: General Help
---

### Post by JoshuaMiller0 on 2013-06-24
Hey. I have been using Xubuntu 12.04 since the day it was released now and I have noticed one massively annoying bug or error when it comes to using some "shortcuts". I am struggling to explain this because they aren't really shortcuts and I didn't want to be too specific. 

Basically what I found was that every time I use the shift key + one of either numeric 2 or numeric 6 it will not work. When I am typing I can type them fine (Shift + 2 = @, Shift + 6 = ^), but if they are shortcuts or buttons within a program to do anything that is not typing, they will simply not work and do nothing.

**This could be an error with Java (6 and 7) or ****LWJGL**** or ****Minecraft**. When I play Minecraft I find that when I am holding the shift key, I cannot hotkey using Shift + 2 or Shift + 6. It simply does not work. 

Things I have tried:
[LIST]
[*]If I change the Minecraft controls to use another button instead of shift, it works fine, so it is probably not Minecraft.
[*]If I load the game with Java 6 instead of 7 it still does not work, so it is probably not Java.
[*]It does not work with the most recent version of LWJGL (development build), the most recent stable build or the ancient version that Minecraft uses by default. So it is probably not LWJGL.
[*]The problem does not occur on my Ubuntu 12.04 setup, my Windows 7 setup and my Windows Vista setup even though they are _the exact same setup_ (I literally copied all the files over). I have no reports of anyone else having the problem, but on google I have found other Xubuntu users with the issue.
[/LIST]

After this I am pretty sure it is Xubuntu. Please help me, I have been putting up with it for over a year now (it may have been on Xubuntu 11.04) and I really want to be able to hotkey and not to die and get banned from my server :P.

---

### Post by JoshuaMiller0 on 2013-06-26
Bump

---

### Post by JoshuaMiller0 on 2013-06-27
Bump

---

### Post by JoshuaMiller0 on 2013-06-29
Bump

---

### Post by JoshuaMiller0 on 2013-06-30
Bump

---

### Post by Buntu Bunny on 2013-06-30
Joshua, I'm sorry you aren't getting any help. I use Xubuntu 12.04 too and never knew about the shift plus numeric keys. Anyway, I tried it in both LibreOffice Writer and Leafpad, but shift plus 2 or 6 did nothing. I don't play Minecraft.

---

### Post by JKyleOKC on 2013-06-30
I've been using Xubuntu since 7.04, now on 12.04, and never found any shift+numeric shortcut keys. My keyboard settings show only a few shortcut combinations, none of which involve the shift key. What applications are involved for you?

---

### Post by JoshuaMiller0 on 2013-07-01
> **Buntu Bunny said:**
> Joshua, I'm sorry you aren't getting any  help. I use Xubuntu 12.04 too and never knew about the shift plus  numeric keys. Anyway, I tried it in both LibreOffice Writer and Leafpad,  but shift plus 2 or 6 did nothing. I don't play Minecraft.
> **JKyleOKC said:**
> I've been using Xubuntu since 7.04, now on 12.04, and never found any shift+numeric shortcut keys. My keyboard settings show only a few shortcut combinations, none of which involve the shift key. What applications are involved for you?

Like I said, it is hard to explain, because it isn't really a shortcut key, but excluding typing, shift + 2 and shift + 6 does not work. Happened on two installs of Xubuntu on two different PCs.

It would be nice to find another program that needs such a hotkey and test it.

---

### Post by JKyleOKC on 2013-07-01
> **JoshuaMiller0 said:**
>  excluding typing, shift + 2 and shift + 6 does not work.Unfortunately "does not work" doesn't give us enough information to be able to help at all! If you can tell us what you expect "shift + 2" to do, and similarly for "shift + 6" result, together with what actually happens, then we may be able to at least let you know what is (or is not) going on.

I'm also a bit confused by "excluding typing" because typing is almost the only purpose of most keys on the keyboard. However many programs do use hotkey-like combinations to provide commands to them, such as control+c to interrupt a running program, or in some editors to copy selected text to the clipboard. Few, though, use the shift key to provide such a switch in meaning; most use control, alt, or both.

The way in which your finger's pressure on a key gets translated into data for a program is quite complicated behind the scenes. Basically, each key is a separate switch, and when the switch is closed by pressing on the key, it generates a numeric "key code" that has no necessary relation to the key's label or intended meaning. That key code goes to the computer, where a driver program translates the key code into either a data character or a command action. Most drivers, so far as I know, recognize only a few command actions and translate all other key codes into data. However the shift, control, and alt keys get special treatment; they are not themselves translated, but instead provide modifiers that can (but do not have to) change the translation of other keys.

The command actions specified for the driver to recognize are, in Xubuntu, listed in the Settings Manager's "keyboard" section. All other combinations have to be recognized by the individual programs that respond to them. Thus telling us what program is involved, and what you expect to happen, is essential before we can offer much in the way of help.

We'd like to know what is going wrong, but you have to let us know a lot more details to make that possible!

---

### Post by JoshuaMiller0 on 2013-07-01
> **JKyleOKC said:**
> Unfortunately "does not work" doesn't give us enough information to be able to help at all! If you can tell us what you expect "shift + 2" to do, and similarly for "shift + 6" result, together with what actually happens, then we may be able to at least let you know what is (or is not) going on.

I'm also a bit confused by "excluding typing" because typing is almost the only purpose of most keys on the keyboard. However many programs do use hotkey-like combinations to provide commands to them, such as control+c to interrupt a running program, or in some editors to copy selected text to the clipboard. Few, though, use the shift key to provide such a switch in meaning; most use control, alt, or both.

The way in which your finger's pressure on a key gets translated into data for a program is quite complicated behind the scenes. Basically, each key is a separate switch, and when the switch is closed by pressing on the key, it generates a numeric "key code" that has no necessary relation to the key's label or intended meaning. That key code goes to the computer, where a driver program translates the key code into either a data character or a command action. Most drivers, so far as I know, recognize only a few command actions and translate all other key codes into data. However the shift, control, and alt keys get special treatment; they are not themselves translated, but instead provide modifiers that can (but do not have to) change the translation of other keys.

The command actions specified for the driver to recognize are, in Xubuntu, listed in the Settings Manager's "keyboard" section. All other combinations have to be recognized by the individual programs that respond to them. Thus telling us what program is involved, and what you expect to happen, is essential before we can offer much in the way of help.

We'd like to know what is going wrong, but you have to let us know a lot more details to make that possible!

That all makes sense and I am sorry. I do not know the correct terminology because it works fine when trying to input an at symbol (@) or a(n) ^ [index symbol?] in the in-game chat and in any other chat feature. The problem I have only found with Minecraft and I am not sure what to test it with to prove it is not Minecraft/ Java.

I am currently uploading a video running Minecraft to show you what I cannot do. I cannot see this being of much help, but it is probably the best way I can explain the problem. It would help a lot if I was told some things I could try to test if the problem is Minecraft/Java and not Xubuntu.

Upload complete. Video can be viewed [here]("http://youtu.be/Y73hr70HVtU").

---

### Post by JKyleOKC on 2013-07-01
>  It would help a lot if I was told some things I could try to test if the problem is Minecraft/Java and not Xubuntu.Sorry; I'm not a gamer so can't be much help I'm afraid. My best guess at this point would be that it's either Java or Minecraft, and based on the way other programs handle such stuff I'd be inclined to think it's Minecraft itself...

With the upload link you've given, perhaps someone else who does play Minecraft will be able to help a bit more.

---

### Post by JoshuaMiller0 on 2013-07-01
> **JKyleOKC said:**
> Sorry; I'm not a gamer so can't be much help I'm afraid. My best guess at this point would be that it's either Java or Minecraft, and based on the way other programs handle such stuff I'd be inclined to think it's Minecraft itself...

With the upload link you've given, perhaps someone else who does play Minecraft will be able to help a bit more.


I agree it could be Java and more likely Minecraft, but I do not get the issue on Ubuntu 12.04, Windows 7 or Windows Vista. It is not gaming related, it is software related. I agree it sounds like it is Minecraft, however why does it only happen on Xubuntu? Do you know of any Java programs where I could test the shift + numeric commands?

---

### Post by JKyleOKC on 2013-07-01
> why does it only happen on Xubuntu? Do you know of any Java programs where I could test the shift + numeric commands? Well, that certainly does indicate that the driver in Xubuntu is doing something differently from the others. I did a bit of delving into the Applications -> Settings menu and found something called "Keyboard Input Methods" that just might be what is causing your problem. I've not gone into it any deeper than just opening it up to see what's there, but it does seem to have various special modifier settings. You might search for more detail about it...

As for Java programs to test, sorry I don't know of any. Hopefully this new lead may shed some light, though.

---

### Post by JoshuaMiller0 on 2013-07-01
> **JKyleOKC said:**
> Well, that certainly does indicate that the driver in Xubuntu is doing something differently from the others. I did a bit of delving into the Applications -> Settings menu and found something called "Keyboard Input Methods" that just might be what is causing your problem. I've not gone into it any deeper than just opening it up to see what's there, but it does seem to have various special modifier settings. You might search for more detail about it...


Well thanks... But I am not very good with (X)Ubuntu and I still have no idea what I am doing.. Or searching...

I have already spent numerous hours searching for a fix to this problem to no avail, until I decided to post a thread and bump it every 24 hours. Any help on what to search would be grately appreciated :P. I am glad we may be finally getting somewhere.

---

### Post by JoshuaMiller0 on 2013-07-02
Well... we are back to this again.

 Bump.

---

### Post by JoshuaMiller0 on 2013-07-03
Bump.

---

### Post by JoshuaMiller0 on 2013-07-04
Bump

---

### Post by JoshuaMiller0 on 2013-07-06
Bump.

---

