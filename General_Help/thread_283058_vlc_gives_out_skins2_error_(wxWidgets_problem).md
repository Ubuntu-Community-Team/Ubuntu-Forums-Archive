---
title: "vlc gives out skins2 error (wxWidgets problem?)"
date: 2006-10-23
forum: General Help
---

### Post by prattler on 2006-10-23
Hello,

firstly, I have searched the VLC forum and found [some threads]("http://forum.videolan.org/viewtopic.php?t=14733"), but none of them guided me to an answer :(

I have installed vlc via aptitude and it is giving out this error when launched from terminal:
[00000272] skins2 interface error: no suitable dialogs provider found (hint: compile the wxWidgets plugin, and make sure it is loaded properly)

It starts, but nothing seems to be working.

Before this I have compiled aMule from source using [this guide]("http://www.amule.org/wiki/index.php/Compilation_Installation"). It involved compiling and installing wxGTK, which, I think, might be source of my problems.. Trying [to remove]("http://www.amule.org/wiki/index.php/How_to_uninstall_wxWidgets") this aMule's wxGTK didn't help either.

Could someone please give me some details about this wxWidgets/wxWindows thing and why isn't VLC using it's wxvlc library?

---

