---
title: "sesson goes idle with ATI XGL"
date: 2007-05-13
forum: General Help
---

### Post by awatts on 2007-05-13
For some reason after I install XGL and Beryl in Feisty (although I have had this issue since dapper), the screen goes black, as if a screen saver was on.  It is only really an issue if I am watching a movie because I have to keep getting up and moving the mouse.  I have a 2gh AMD Turion Compaq Presario v2000 with an ATI Radeon Xpress 200m  video card.  I wonder if I am still the only one who is experiencing this (since i've inquired about this with previous releases).  Any of your thoughts on a solution would be appreciated.

---

### Post by ollielowe on 2007-05-25
yeah,

i'm getting the same sorta problems with xgl or whatever
can't logout, suspend, hibernate, only can shutdown
which is a problem when i'm on my laptop.

---

### Post by mcduck on 2007-05-25
That's a common issue with XGL. The solution is to add following section into your xorg.conf:

```
Section "ServerFlags"
   Option "BlankTime" "0"
   Option "StandbyTime" "0"
   Option "SuspendTime" "0"
   Option "OffTime" "0"
EndSection
```

---

### Post by ollielowe on 2007-05-26
hmm...
still not working :-(
and by the way i have the same laptop as you awatt, so getting all the same problems...
i got that code in, now it works for only my gnome sessions:), not with xgl. However, I did get xgl to suspend, logout etc. I changed my

Section "Extensions"
	Option		"Composite"	"False"
EndSection

----------------------------------- to..

Section "Extensions"
	Option		"Composite"	"True"
EndSection

But this made my xgl session go all fuzzy, everything was unreadable so I 'felt' my way to logout and changed my compisite to false again.

sigh...

---

