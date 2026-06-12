---
title: "KDE wrecked my Ubuntu"
date: 2008-02-26
forum: General Help
---

### Post by Randybob on 2008-02-26
I'm rather new to Ubuntu. I've had Gutsy installed for several weeks now, and I thought I'd try KDE alongside GNOME. So I followed the instructions [here]("http://www.psychocats.net/ubuntu/kde") to do that. I wanted to switch back to GNOME, and noticed it was having problems installing more themes - when I clicked the Install button under Appearance, the dialog box was empty. So I used the command at the bottom of the guide I linked to in order to get rid of KDE. It didn't seem to completely remove it, so I used the command at the bottom [here]("http://www.psychocats.net/ubuntu/puregnome") (the really long one) to REALLY remove it. The desktop went away when I told it I really did want to remove the KDE daemon, and it gave me the command line. There was no prompt, only the cursor (under some processes, that had been finished). I assumed it was finished doing what it was doing, so hit Ctrl-Alt-Del, and when Ubunut started up, it was with the Kubuntu splash screen again. Worse, Ubuntu now thinks my screen res is 2048x1600, and I can't change it. I can't get into Synaptic to reload the NVIDIA drivers either. 

I just want to get Ubuntu back in good working order again. I'm not opposed to trying KDE alongside GNOME again, I just want to do it right so both desktop environments work the way they are supposed to. How do I fix this mess?

---

### Post by SOULRiDER on 2008-02-26
try doing
```
sudo aptitue remove kubuntu-desktop
```
just in case and then reinstalling ubuntu-desktop wouldnt hurt so you can just do
```
sudo aptitude install ubuntu-desktop
```

See if that helps a bit.

---

