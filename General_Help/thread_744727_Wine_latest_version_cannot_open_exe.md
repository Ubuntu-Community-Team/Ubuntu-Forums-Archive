---
title: "Wine latest version cannot open exe"
date: 2008-04-03
forum: General Help
---

### Post by Dabblo on 2008-04-03
Hi folks, I have freshly installed Ubuntu 7.10, however I have installed the latest wine through terminal it didn't install. Then I noticed it synaptic package manager so I decided to finish installing it that way. I have no right click option to open the .exe direct over the icon. Also wine doesn't appear in the open with other applications list. Wine is in the applications menu at the top and I can browse that way. I figure I have done something wrong and would appreciate some help please.

Regards Dai

---

### Post by mc4man on 2008-04-03
> I have no right click option to open the .exe direct over the icon
you won't get that till you actually run an .exe with wine. You could use terminal wine <path to exe> or below
> Also wine doesn't appear in the open with other applications list
choose use custom command and either browse to wine or use '/usr/bin/wine'


edit; it's usually good to run apps from terminal at least once to ck. if errors exist - 2 ex.
wine /home/doug/.wine/drive_c/dvdsoft/DGIndex.exe
wine '/home/doug/.wine/drive_c/Program Files/DVD-RB PRO/Rebuilder.exe'
notice '.....' for space (program files) in path

---

