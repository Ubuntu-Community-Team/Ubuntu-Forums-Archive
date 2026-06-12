---
title: "Small Accessibility Problem: Is there a way to give my mouse cursor a custom color?"
date: 2021-08-04
forum: General Help
---

### Post by themrshadyslim on 2021-08-04
Hi,

So I am currently running Ubuntu 21.04 using GNOME.

So in the settings the only customization I was able to do was change the my mouse size, which does help, but I want to be able to change the color as well

Looking online with a search engine, all of the results just talk about changing the size despite explicitly asking about changing the color.

Some results mentioned using GNOME-tweaks to further customize mouse settings, but there is nothing there about changing the color of the mouse. At most I see options to change to different mouse icons. There was no way to add new icons via the tweaks gui, and I have no knowledge on where that would be located via CLI

Any help on this matter would be appreciated

---

### Post by scorp123 on 2021-08-04
You could try a different mouse cursor theme, e.g. one that is more colorful?

[https://www.gnome-look.org/browse?cat=107]("https://www.gnome-look.org/browse?cat=107")

---

### Post by scorp123 on 2021-08-04
If you prefer getting one from the official repositories, then this one might be for you:

```

sudo apt install oxygen-cursor-theme-extra

```

The "oxygen-cursor-theme-extra" package contains many colorful variations of the "Oxygen" cursor theme as the name suggests. Once this package is installed you should be able to select a suitable one from e.g. Gnome Tweaks.

---

### Post by Dennis N on 2021-08-04
To change just the color, you use Gimp.
Open the cursor file for the cursor to be recolored from the cursor folder inside the cursor's theme foder, for example left_ptr.
Recolor. You can use fill tool, and then some pixel level touch-up.
Export as "X11 mouse cursor" (.xcm file). 
Rename the .xcm file the same as the original file.
Replace the original file.

Before starting, I suggest you save the originals in case you want to restore them.

---

### Post by themrshadyslim on 2021-08-04
> **scorp123 said:**
> You could try a different mouse cursor theme, e.g. one that is more colorful?

[https://www.gnome-look.org/browse?cat=107](https://www.gnome-look.org/browse?cat=107)

I may look into to this, and see if any one pops out to me. I will also download that package and see what they offer

I might go with the other's poster more manual solution since I do like the default mouse style. I just want it a different color.

Though changing the color should be a pretty simple process for DE. I am still a novice when it comes to programming and more focused on full stack web dev, but maybe I can try to work on a solution my self. Whose repository would I have to raise an issue on the github? My initial thought is GNOME since I think this with the DE settings.

---

### Post by themrshadyslim on 2021-08-04
> **Dennis N said:**
> To change just the color, you use Gimp.
Open the cursor file for the cursor to be recolored from the cursor folder inside the cursor's theme foder, for example left_ptr.
Recolor. You can use fill tool, and then some pixel level touch-up.
Export as "X11 mouse cursor" (.xcm file). 
Rename the .xcm file the same as the original file.
Replace the original file.

Before starting, I suggest you save the originals in case you want to restore them.

Thanks for the detailed guide!! Though I feel like there should be some programmatic way of doing this. How monumental of a task would be to go into GNOME's code? This should just be a setting in the GUI

---

### Post by Dennis N on 2021-08-04
> **themrshadyslim said:**
> Thanks for the detailed guide!! Though I feel like there should be some programmatic way of doing this. How monumental of a task would be to go into GNOME's code? This should just be a setting in the GUI
Well, it doesn't take long to change just the major cursors: left pointer, hand (over links), grab. These 3 are all I did. Also, I've only done this with non-resizable cursors (one size only). 

You can also make animated cursors with a utility called xcursorgen. For example, you can make a blinking cursor (2 switching colors) that's easily located on the screen. This thread deals with this in part:

[https://ubuntuforums.org/showthread.php?t=2384798](https://ubuntuforums.org/showthread.php?t=2384798)

The image attached to post #8 shows two images used that alternate to create the illusion of blinking.

---

