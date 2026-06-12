---
title: "Please help me about installing libmp3lame for kdenlive"
date: 2014-12-15
forum: General Help
---

### Post by josh-photography on 2014-12-15
Hey guys, when I try to render my file to Mp4, it doesnt work because it says: Audio codec not supported: libmp3lame?
I don't know where to download this and I don't even know what codec is for. Where can I get an update for kdenlive to get missing codecs? They also said I should have FFMPEG installed but I have it already thanks!

---

### Post by oldos2er on 2014-12-15
Open a terminal (Ctrl-Alt-t) and copy/paste the following command into it: ```
sudo apt-get update && sudo apt-get install libmp3lame0
``` You'll be asked to enter your password, nothing will be echoed to the screen when you enter it, just FYI.

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by mc4man on 2014-12-15
The odds are it's already installed,** if so** then maybe try moving ~/.kde/share/config/kdenliverc to a backup (kdenliverc.bak)  & see if that helps

---

