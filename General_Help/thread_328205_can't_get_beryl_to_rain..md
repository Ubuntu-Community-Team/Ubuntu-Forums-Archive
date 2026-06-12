---
title: "can't get beryl to rain."
date: 2006-12-30
forum: General Help
---

### Post by TheRingmaster on 2006-12-30
I can't get the rain plugin to work on my beryl/built-in aiglx/nvidia quadro2 MXR/EX/GO

I press shift-f9 nothing or any other key combination that controls water effects.

---

### Post by _simon_ on 2006-12-30
Is it actually enabled?

You might be better posting on the Beryl forum: [http://forum.beryl-project.org/](http://forum.beryl-project.org/)

---

### Post by kesman on 2006-12-30
Isn't the rain-command assigned the super+f9 combination by default? Super key is usually the windows-key on your keyboard, but there's been problems with it. You should check gnome's keyboard settings or change the one beryl uses to start the rain plugin.

---

### Post by strabes on 2006-12-30
Shift + F9 is the default command. Make sure the rain plugin is actually enabled. Also, reset all the rain settings to default with the buttons that look like brushes.

---

### Post by TheRingmaster on 2006-12-30
> **strabes said:**
> Shift + F9 is the default command. Make sure the rain plugin is actually enabled. Also, reset all the rain settings to default with the buttons that look like brushes.

yes it is actually enabled. Shift-F9 does not work though.

---

### Post by hikaricore on 2006-12-30
Ok what you need to do is disable beryl for a sec, close beryl-manager and open a terminal.

From this terminal run:

```
beryl-manager
```

Then enable beryl (keeping the terminal open) and try the key commands for the water effects.  Watch the terminal for error messages.  If you see something almost exactly like this:

**beryl: water: GL_ARB_fragment_program is missing**

Chances are, your video card or drivers do not support the rendering of the water effects, or something is not configured right.

I had this issue with my integrated intel chipset and have heard of some people having the problem on certain video cards.  If you don't get an error message about anything, check to see again if it's enabled and if the shortcut keys are enabled.  Keep checking for error messages and if you find one, you may want to ask around the beryl forums to see if anyone else has had this issue and if there is a possible solution to it.

Good luck,

--Aaron

---

### Post by TheRingmaster on 2006-12-30
> **hikaricore said:**
> Ok what you need to do is disable beryl for a sec, close beryl-manager and open a terminal.

From this terminal run:

```
beryl-manager
```Then enable beryl (keeping the terminal open) and try the key commands for the water effects.  Watch the terminal for error messages.  If you see something almost exactly like this:

**beryl: water: GL_ARB_fragment_program is missing**

Chances are, your video card or drivers do not support the rendering of the water effects, or something is not configured right.

I had this issue with my integrated intel chipset and have heard of some people having the problem on certain video cards.  If you don't get an error message about anything, check to see again if it's enabled and if the shortcut keys are enabled.  Keep checking for error messages and if you find one, you may want to ask around the beryl forums to see if anyone else has had this issue and if there is a possible solution to it.

Good luck,

--Aaron
> petey@petey-desktop:~$ beryl-manager
petey@petey-desktop:~$ XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: No GLXFBConfig for default depth, falling back on visinfo.

** (process:4974): WARNING **: get_setting_is_integrated not found in backend ini

** (process:4974): WARNING **: get_setting_is_read_only not found in backend ini

** (process:4974): WARNING **: get_setting_is_integrated not found in backend ini

** (process:4974): WARNING **: get_setting_is_read_only not found in backend ini
Initiating splash
[Snow]: Loaded Texture /usr/share/beryl/snowflake2.png
beryl: water: GL_ARB_fragment_program is missing
No framebuffer_object support! (only simple blur aviable)
No fragment_program support! (only simple blur aviable)
Reloading all options.
[Snow]: Loaded Texture /usr/share/beryl/snowflake2.png
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing




Yes I do have some errors

---

