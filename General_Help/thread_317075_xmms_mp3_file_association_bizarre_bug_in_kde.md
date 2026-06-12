---
title: "xmms mp3 file association bizarre bug in kde"
date: 2006-12-11
forum: General Help
---

### Post by vigleik on 2006-12-11
I have a strange problem with file associations on edgy eft using kde. I'm trying to associate mp3 files to xmms, but no matter what I do xmms stays at the bottom of the list of programs associated to mp3-files. I've tried setting the file associations in the control center, or using the konqueror settings, or right-clicking on an mp3-file and choosing properties.

I just installed edgy eft (6.10), or rather I installed 6.06 and upgraded and installed kde since 6.10 liked my monitor even less than 6.06. This is not a huge problem as I can always choose "open with" and then xmms, but it's just so mysterious.

I had no trouble making xmms the default program for ogg, flac, and other formats. I also managed to set xmms as the default player in nautilus, but I don't want to be forced to use that. Has anyone else seen anything like this?

Vigleik

---

### Post by x64Jimbo on 2006-12-11
What program is opening as default? Can you go into ITS preferences and un-check the mp3 checkbox for supported filetypes?

---

### Post by vigleik on 2006-12-11
> **x64Jimbo said:**
> What program is opening as default? Can you go into ITS preferences and un-check the mp3 checkbox for supported filetypes?

Noatun was the default program, but "movie player" and "rhythmbox music player" are also on the list of programs that support mp3 and I can choose either of those as the default without any problem.

When I try to uncheck mp3 as supported filetype for any of these, I get the following message:
*Could not save properties. You do not have sufficient access to write to /usr/share/applications/totem.desktop.*

I can change the default player any way I want as root. So I guess I could mock around with write permissions for these files, though I'm a little bit scared of messing up my system.

---

### Post by x64Jimbo on 2006-12-11
That is really bizarre. All your prefs should be stored in your home directory and under your control - root access should not be required for any personal preference change. Tread lightly.

---

