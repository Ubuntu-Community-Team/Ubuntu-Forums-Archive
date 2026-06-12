---
title: "Korean layout appears to not have hangul characters"
date: 2022-02-19
forum: General Help
---

### Post by bluemajician on 2022-02-19
I'm currently struggling to get Korean input working. Here's what I've tried thus far:

 - I've added both "Korean" and "Korean 101/104 key compatible" layouts under Settings > Region and Layout > Input Sources. Other than the actual input not changing, cycling between inputs appears to work with the default Super+Space keys. I also went from there to Manage Installed Languages and installed needed packages according to the GUI prompts.
 - I have also installed gnome-tweaks and gone to Tweaks > Keyboard and Mouse > Additional Layout Options > Korean Hangul/Hanja keys and added both right control and right alt as Hangul keys.
 - I uncommented the ko_KR locales in locale.gen and ran `sudo locale-gen`.
 - When my testing didn't seem successful, I rebooted the system and tried the inputs again without change. I've been testing in Firefox, LibreOffice Writer, and Gnome Shell.

After those configuration steps, I've tried several methods of typing Hangul in either Korean layout that I've found on the internet or guessed.
 - I've tried both holding the right Ctrl or Alt keys and just pushing them to toggle the input change, with no effect.
 - I've used  Ctrl+Space with both left and right Ctrl keys. I've done the same with Alt.
 - I've tried left and right Alt+Shift to toggle.

I have not managed to input any Hangul characters thus far.

I noticed that the keyboard representation I see when I click on the "eye" icons under Settings > Region & Language for each language does not have any Hangul characters, even when I press the designated right Alt and Ctrl keys, and I wondered if this might be an indicator of the problem.

Does anyone have further advice on typing Korean Hangul characters on Ubuntu?

EDIT: I have also installed IBus-Hangul, rebooted, and tried a few more key combinations while in the Korean modes to try to get Hangul input with no change (I mixed the Esc and CapLock key with Ctrl and Alt various ways, as well as Shitf+Space). I found what seemed like a [good tutorial,]("https://davejansen.com/enable-korean-input-on-ubuntu-19-10/") but some of the steps at the end aren't current; there is no settings cog next to either Korean input source in the settings menu, for example. Is there a way I might still get to that IBusHangul setup menu in that tutorial?

**EDIT2: Silly me, there's a separate "Korean (Hangul)" layout. It works now. Marking as solved.**

For anyone else who gets confused and needs the correct steps: Install ibus-hangul, uncomment ko_KR.UTF-8 from the /etc/locale.gen file and run sudo locale-gen. Add Korean (Hangul) under Settings > Region & Language > Input Sources. Then open Manage Installed Languages and when prompted, let the system install additional packages.

The default Shift+Space method can easily switch your input between English/Latin and Hangul and I've stumbled with that already. You can disable this by working in the IBusHangul setup menu by clicking on the cog next to Korean (Hangul) in Settings > Region & Language. You can set the Hangul key in the Gnome Tweaks menu as described above.

---

