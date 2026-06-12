---
title: "Amarok permission problems..."
date: 2007-12-30
forum: General Help
---

### Post by Moonfrost on 2007-12-30
Ok, I installed Ubuntu Ultimate Edition 1.6 for the second time...I used Amarok a lot before going to OpenSUSE 10.3 (amazing distro...but I missed having everything just "working" out of the box), when I had it before it worked perfectly under normal user...now that I re-installed UUE 1.6 Amarok won't start because of connection problems or something like that...I didn't copy the errors because I kinda figured out what was happening, I went and opened a terminal and typed "amarok" and of course all files that were trying to execute said "permission denied" next to them, so it was just like I thought. I tried sudo amarok and it worked perfectly. The problem I'm having though it that I don't know where Amarok is installed by default (searched everywhere but couldn't find it) so I need anyone here that knows to tell me where it could be installed by default...because I'm pretty sure of I find the executable that I just right-click it, go to properties and set permissions right? probably will have to be root for that though...if I'm wrong, would anybody be kind enough to correct me and guide me how to make Amarok be usable under my normal user account? thanks a lot in advance...

Anybody? please! I use Amarok a lot and don't want to have to open a terminal every time I want to use it!

---

### Post by snacker on 2008-01-01
Have you tried the "locate amarok" or "which amarok" commands?

---

### Post by Moonfrost on 2008-01-01
> **snacker said:**
> Have you tried the "locate amarok" or "which amarok" commands?

No, I just logged in as root, went to the hidden .kde, right clicked on it and went to properties, permissions and set the owner to my username and also set the permissions to read and write. Also, there was an options with a checkmark (which wasn't marked) that said to also set those permissions to the enclosed files/folders...after that, Amarok worked perfectly under my normal user account...

---

