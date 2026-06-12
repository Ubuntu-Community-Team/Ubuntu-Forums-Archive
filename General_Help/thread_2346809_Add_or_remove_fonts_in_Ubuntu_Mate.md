---
title: "Add or remove fonts in Ubuntu Mate"
date: 2016-12-19
forum: General Help
---

### Post by heroquestelf on 2016-12-19
First off, I'm running Ubuntu Mate 16.04.1 LTS on a Toshiba Satellite with a 2x Intel Core2 Duo CPU (T550 @ 1.83GHz) with 3071MB of memory.

I have a couple of questions. First off, I'm a bit of a font junkie and a font snob, so that's where this is coming from.

**First question: *(font snob)*** is it possible to remove system fonts in Ubuntu Mate. Specifically, I'd like to remove the fonts that are in languages which I do not know, for example, Japanese. I don't know Japanese. I have no interest in learning Japanese. These fonts are a waste of space. Is there any way I can remove them?

**Second question: *(font junkie)*** In my younger days I collected fonts and would load my machine down with them. Eventually I ran into someone who told me that I was bogging myself down because Windows is not equipped to handle a huge amount of fonts, and installing all of those fonts into my system was actually making it boot up slower because Windows has to read and validate the entire C:/Windows/fonts file directory at boot. So my question to all of you terribly handsome people is this: if I decided to get crazy and dump all 1032 font files that I have into my ~/.fonts file, what would my machine do?

---

### Post by howefield on 2016-12-19
> **heroquestelf said:**
> **First question: *(font snob)*** is it possible to remove system fonts in Ubuntu Mate. Specifically, I'd like to remove the fonts that are in languages which I do not know, for example, Japanese. I don't know Japanese. I have no interest in learning Japanese. These fonts are a waste of space. Is there any way I can remove them?

Well yes, you can remove any package from your system using the terminal and apt remove/purge including the fonts packages.

There is a GUI application called font-manager which I haven't used so can't vouch for it...

```
Description-en_GB: font management application for the GNOME desktop
 Font Manager currently allows the user to:
  - Preview installed fonts
  - Compare installed fonts
  - Easily install or remove fonts
  - Easily activate and de-activate installed fonts
  - Specify different directories to search for fonts
  - Group fonts into "Collections", and easily activate or
    de-activate groups of fonts
  - Export "Collections" to an archive for easy backup, sharing, etc.
  - Provides quick access to all GNOME font utilities.
```

You can count the fonts installed on your system with...

```
fc-list | wc -l
```

> **Second question: *(font junkie)*** In my younger days I collected fonts and would load my machine down with them. Eventually I ran into someone who told me that I was bogging myself down because Windows is not equipped to handle a huge amount of fonts, and installing all of those fonts into my system was actually making it boot up slower because Windows has to read and validate the entire C:/Windows/fonts file directory at boot. So my question to all of you terribly handsome people is this: if I decided to get crazy and dump all 1032 font files that I have into my ~/.fonts file, what would my machine do?

I do not believe that you will see a system performance degradation at boot as you describe above (or at the least, not noticeably so) but certain applications which let you choose a particular font might take longer to boot as it scans the fonts folder, eg gimp, libreoffice, ect.

---

