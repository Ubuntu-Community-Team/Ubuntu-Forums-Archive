---
title: "how to change ~/.config/dconf/user"
date: 2022-08-06
forum: General Help
---

### Post by Skaperen on 2022-08-06
one of the userids i use keeps notifying me (each time i login) that the "Download" directory is missing even though it is there.  then i notice it has the wrong path for the home directory part.  searching around, only file "~/.config/dconf/user" has that wrong path.  i want to change it to the correct path, but the paths are different length and the file is in some binary format.  does anyone know how to get to these settings or which app to run to edit these settings.

it would be nice if there is a app that can recurse through every GUI menu and search for requested keywords and strings.

---

### Post by arraybolt3 on 2022-08-06
That's the DConf database. You'll probably want to find the key that's been messed up using one of the search techniques listed here: [https://askubuntu.com/questions/169704/how-to-search-dconf-for-keys-or-values](https://askubuntu.com/questions/169704/how-to-search-dconf-for-keys-or-values) (For in the event that link stops working, the command to use is [FONT=var(--ff-mono)][FONT=courier new]dconf dump / | grep SEARCH-TERM[FONT=arial], replace [FONT=courier new]SEARCH-TERM[/FONT] as appropriate, this will search keys and values.[/FONT][/FONT]) [/FONT]Once you've figured out which key is wonky, you should be able to use gsettings (CLI) or dconf-editor (GUI) to fix it.

---

### Post by Skaperen on 2022-08-06
ok.  but i still want to find where it gets set.  but you'll need to know which key with this being one big DB for dconf.  so here is a dump of the file using a dump program i created:
```

000000000  47566172 69616e74 00000000 00000000  18000000 e0010000 00000028 10000000 |GVariant...................(....|
000000020  00000000 00000000 01000000 03000000  05000000 08000000 09000000 09000000 |................................|
000000040  0a000000 0a000000 0b000000 0b000000  0e000000 0e000000 0f000000 10000000 |................................|
000000060  21d1c1a0 0d000000 e0010000 16007600  f8010000 fe010000 72d1713b 0f000000 |!.............v.........r.q;....|
000000080  fe010000 09004c00 08020000 0c020000  c2af890b 07000000 0c020000 04004c00 |......L.......................L.|
0000000a0  10020000 14020000 53c406db 05000000  14020000 10004c00 24020000 28020000 |........S.............L.$...(...|
0000000c0  8301403f 01000000 28020000 0b007600  38020000 54020000 b4f44cbd 02000000 |..@?....(.....v.8...T.....L.....|
0000000e0  54020000 07004c00 5c020000 60020000  440dce24 0d000000 60020000 0b007600 |T.....L.\...`...D..$....`.....v.|
000000100  70020000 73020000 d4b50200 ffffffff  73020000 01004c00 74020000 80020000 |p...s...........s.....L.t.......|
000000120  45dc7d1c 0d000000 80020000 0c007600  90020000 93020000 17199c7c 07000000 |E.}...........v............|....|
000000140  93020000 05004c00 98020000 9c020000  691048b4 0d000000 9c020000 09007600 |......L.........i.H...........v.|
000000160  a8020000 ab020000 4b50900b 07000000  ab020000 04004c00 b0020000 b4020000 |........KP............L.........|
000000180  7b95cbcb 03000000 b4020000 12007600  c8020000 ce020000 6bdab262 09000000 |{.............v.........k..b....|
0000001a0  ce020000 0d004c00 dc020000 f0020000  4d36ff03 0d000000 f0020000 0f007600 |......L.........M6............v.|
0000001c0  00030000 03030000 9e3767a2 0b000000  03030000 08004c00 0c030000 10030000 |.........7g...........L.........|
0000001e0  6c6f636b 2d616674 65722d73 63726565  6e736176 65720000 00000000 00757472 |lock-after-screensaver.......utr|
000000200  616e7366 65722f00 04000000 636f6d2f  05000000 75706461 74652d6e 6f746966 |ansfer/.....com/....update-notif|
000000220  6965722f 0c000000 73686172 65642d70  61746800 00000000 2f686f6d 65322f6c |ier/....shared-path...../home2/l|
000000240  696e6b65 64696e2f 446f776e 6c6f6164  73000073 7562756e 74752f00 03000000 |inkedin/Downloads..subuntu/.....|
000000260  6c6f636b 2d6f6e2d 6c696400 00000000  0000622f 09000000 02000000 0b000000 |lock-on-lid.......b/............|
000000280  6c617465 2d6c6f63 6b696e67 00000000  00006261 7070732f 0d000000 69646c65 |late-locking......bapps/....idle|
0000002a0  2d68696e 74000000 0000626f 72672f00  0f000000 72656c65 6173652d 63686563 |-hint.....borg/.....release-chec|
0000002c0  6b2d7469 6d650000 7698ec62 00756c69  6768742d 6c6f636b 65722f00 0a000000 |k-time..v..b.ulight-locker/.....|
0000002e0  08000000 00000000 06000000 0e000000  6c6f636b 2d6f6e2d 73757370 656e6400 |................lock-on-suspend.|
000000300  01006262 6c75656d 616e2f00 01000000                                      |..bblueman/.....|

```
the bad path starts at 0x0238.  it was the path that user ("linked" it gets isolated into its own userid because of how much they try to spy).  the "/home2" needs to be "/home".

they should have implemented paths in the database as relative to the discovered actual home direct or if led by a "/" then absolute and prefer relative unless the path is being explicitly set absolute, such as a path nowhere in the home directory.  then this could start with ".config/".

---

### Post by Skaperen on 2022-08-06
previous post won't let me edit it to fix the code containment.  *i can edit this post, so there must be a size limit for editing.*

---

### Post by deadflowr on 2022-08-07
> **Skaperen said:**
> previous post won't let me edit it to fix the code containment.  *i can edit this post, so there must be a size limit for editing.*

No, your code brackets were wrong.
code should be in [noparse]```
 stuff 
```[/noparse]
but you post [noparse][code] stuff [/output][/noparse]
(Capitalization does not matter, fwiw)
I fixed the broken code tags, if it's not parsing it correctly it's outside what code tags can do.

---

### Post by ActionParsnip on 2022-08-07
Does the user own it's Downloads folder? Also check case. Linux is very case sensitive

---

### Post by &amp;KyT$0P# on 2022-08-07
> **Skaperen said:**
> does anyone know how to get to these settings or which app to run to edit these settings.

[FONT=Courier New]dconf-editor[/FONT] if you want a GUI, or [FONT=Courier New]dconf[/FONT] (package [FONT=Courier New]dconf-cli[/FONT]) if you want a Terminal/command-line program.

---

### Post by arraybolt3 on 2022-08-07
[QUOTE="Skaperen"] [COLOR=#000000]ok. but i still want to find where it gets set. but you'll need to know which key with this being one big DB for dconf. [/COLOR][/QUOTE]
For searching the database:

[FONT=arial]```
 dconf dump / | grep SEARCH-TERM 
```

I would replace SEARCH-TERM with "/home2/linkedin/Downloads" and see if that tells you which key is bad. Then you can edit it with gsettings or dconf-editor.
[/FONT]

---

### Post by Skaperen on 2022-08-07
> **deadflowr said:**
> No, your code brackets were wrong.
code should be in [noparse]```
 stuff 
```[/noparse]
but you post [noparse][code] stuff [/output][/noparse]
(Capitalization does not matter, fwiw)
I fixed the broken code tags, if it's not parsing it correctly it's outside what code tags can do.

right.  i had a brain glitch because i had just used an "output" containment on the Python forum and didn't notice my error until i posted it.  then when i tried to edit it, it gave me an empty editing buffer.

i generally type in lower case, even the first letter of a sentence.  "code" or "Code" or "cOdE" is all the same in brackets, yeah i know.  thanks for fixing the tag so i don't need to re-post it.

---

### Post by Skaperen on 2022-08-07
> **ActionParsnip said:**
> Does the user own it's Downloads folder? Also check case. Linux is very case sensitive

yes, the file is correctly owned.  it was a mismatch of actual and expected paths.  the file was at "/home/..." but some code was trying to stat "/home2/..." which used to exist but not on the new laptop (all users are now in /home/ ... i just need to fix these lingering bad references).  it's not as simple as doing "s@/home2/@/home/@" on binary files since that would cause a 1 byte shift and put values in unexpected positions (even though an x86 can load them if it knew of the offset shift).

---

### Post by Skaperen on 2022-08-07
> **halogen2 said:**
> [FONT=Courier New]dconf-editor[/FONT] if you want a GUI, or [FONT=Courier New]dconf[/FONT] (package [FONT=Courier New]dconf-cli[/FONT]) if you want a Terminal/command-line program.

right.

but i'm curious where this would be originally set.  there are lots of GUI ways to set things, supposedly to make it easier for GUI-oriented people who seem to just "know" how to descend to exactly the right menu or applet that sets what they want.  i've set many things with such applets, especially in Xfce, but later need to change things, but can't find it (the first time i had no idea where i was).

---

### Post by Skaperen on 2022-08-07
i wonder if the 2 ways that **halogen2** described are the only ways for this setting.  lots of things can be found by "GUI browsing" (just going up and down the menus and finding a setting you want to be different using some fancy mechanism designed for it.  many things are described by the menu descent steps or tabs to click on to get there.

---

### Post by &amp;KyT$0P# on 2022-08-07
What is the full dconf path of this setting's key?

---

### Post by Skaperen on 2022-08-09
**@halogen2** i don't know what the key is.  the posted hex dump is the whole file so everything to know about it is there. user "linkedin" used to be at "/home2/linkedin" but is now at "/home/linkedin" (all home directories are there except for system stuff).  this db did not get update.  but my curiosity was piqued by this ... i want to know were the typical graphical user interface user is expected to find it for that particular setting as opposed where set any dconf stuff.

i started this thread not as finding a way to change it (i haven't done a *duckduckgo* search for it, yet) but as understanding how GUI users are expected to understand the whole menu layout.  so i'm still wanting to know where it is in the menu layout. i.e. the "first > second > third > fourth" kind of path typically described for GUI use (no terminal commands).

---

### Post by Skaperen on 2022-08-09
yes, i'm a big time terminal/cli user from the text console days, and on Unix, the tty serial port days.  i remember what 110 baud teleprinting was like.  but i am wanting to learn the GUI way of things.  how would a graphics-only user find this?

---

### Post by &amp;KyT$0P# on 2022-08-09
> **Skaperen said:**
> **@halogen2** i don't know what the key is.  the posted hex dump is the whole file so everything to know about it is there. 

Sorry, I don't know how to read the full key path from the hex dump and it's not possible to answer your question without knowing the full key path.

You should be able to determine the full key path from reading the full output of [FONT=Courier New]dconf dump /[/FONT] as arraybolt3 suggested earlier: most of the path will be a header enclosed in [ ] and the last path component will be before the =

---

### Post by Skaperen on 2022-08-09
i don't think i need to know the key.  i just want (out of curiosity) to know how to get to the app(let) for this, if there is one.  this is a user i rarely use, so i could just *rm* the database and let it think i'm just start the user and it can fill all this in.  i think it did it that way, before.  i'll just *mv* the file to keep it in case i want to put it back.

---

### Post by &amp;KyT$0P# on 2022-08-10
> **Skaperen said:**
> i just want (out of curiosity) to know how to get to the app(let) for this, if there is one.

Understood, but dconf is widely used by many different applications and desktop environment components, so trying to answer your question without knowing the full dconf key path is about as impossible as trying to shoot a mosquito with a nerf arrow at night while blindfolded.

---

### Post by Skaperen on 2022-08-10
based on the nature of the setting, as opposed to a specific dconf DB key, is how the typical GUI user (who would not be a user at all if CLI was the only way of things) would find where to go in the menu to find how to change whatever they want to change.  may this specific setting has no menu applet to make a change and using *dconf* in CLI is all there is.  or maybe there is one that is improperly placed.  if so, its developer probably does not realize that no one else knows about it.

what if the *dconf* CLI command did not exist and all DB stored settings were made via library calls or messages to a DB daemon?

---

