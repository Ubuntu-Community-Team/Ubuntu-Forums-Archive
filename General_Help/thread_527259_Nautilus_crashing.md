---
title: "Nautilus crashing"
date: 2007-08-16
forum: General Help
---

### Post by michaelzap on 2007-08-16
As of this morning, Nautilus has become very unstable. It's crashing on me when opening new windows, navigating in the tree, or inserting a USB disk. I haven't been able to get it to come back to life after it crashes without restarting, which is a major pain in the patoot.

Although perhaps it's not really Nautilus after all but rather something more elemental... When Nautilus stops responding I find that I also cannot save open documents from SMB shares or open files from anywhere from inside a program (for example, Bluefish). The file open navigator shows no files and also stops responding.

I don't see any CPU spikes or anything else going on in the System Monitor when this happens.

I'm running 32-bit Feisty with all updates on an Intel Core 2 Duo. I also have Google Desktop and Trevino's Compiz Fusion and Emerald running, although I'm trying it without those last two now to see if that helps. I believe the only updates this morning were for Amarok and the Vorbis libraries, so I don't know what's going on...

Anyone experiencing the same issue or have any ideas?

---

### Post by Chaotic Thought on 2007-08-16
I haven't had this specific problem, but in the past when I've had problems, temporarily disabling the desktop icons sometimes helps. To do this, go to a command line and type **gconftool** and you will get the gnome configuration editor. I can't remember the specific key to edit, but check under "apps" and "nautilus" and one of the settings is "enable desktop" or something similar. After you turn it off, you'll have to relogin to your session.

---

### Post by Aesir09 on 2007-08-16
i dont know much about Linux yet, but somehting i just thought of is maybe in safe mode or somehting install beryl and 

**make sure you have your 3d drivers enabled!** and right click on the beryl icon on your panel and select Beryl as your window manager instead of GTK?

---

### Post by michaelzap on 2007-08-16
So far it hasn't crashed using Metacity instead of Compiz Fusion and Emerald, so that may turn out to be the culprit. If it is, I can live without those until the issue is resolved in a later update. I have too much work to get done to be worrying about effects right now...

But what's odd about that (if that is what caused the problem; I'm still not certain) is that I don't think my Compiz setup has changed at all since yesterday when everything was working fine.

@Chaotic Thought: When I launch gconf-editor and look at the desktop icon settings in there they all have values of <schema> that can't be edited, so I'm not sure how to change that.

---

### Post by Chaotic Thought on 2007-08-16
Sorry, I told you the wrong key: it is in "desktop" instead of apps. The "desktop" key is in the top level, and under it is "nautilus" and one of those settings controls drawing the icons.

Sorry I can't be more specific I'm at work right now and can't verify. Hope it helps

---

### Post by michaelzap on 2007-08-16
OK I've been using my PC all day with no problems since I turned off Compiz Fusion and Emerald. So that does seem to be causing the problem with Nautilus (or volume management in general). Anyone else experience this?

---

