---
title: "Setup 640x480 30Hz Output on DVI-I"
date: 2013-04-10
forum: General Help
---

### Post by airsoftsoldrecn9 on 2013-04-10
I have an NVIDIA GF210 Card with an available DVI-I that I am converting to component cable to my old CRT television (yes I know)

I know the television has a display capability of NTSC 480i but NVIDIA Server X does not allow me to select anything other than 60Hz output (which I guess is progressive).

Can I modify the xorg.conf in a way to force interlacing on a screen or is the hardware not allowing interlaced output?

I have tried adding a flag for interlacing.

[COLOR=#000000][FONT=Times New Roman]The config file may have multiple [/FONT][/COLOR]Monitor sections. There should normally be at least one, for the monitor being used, but a default configuration will be created when one isn't specified.**Monitor** sections have the following format:
[INDENT]

**Section "Monitor"****    Identifier "***name***"***    entries**    ...***EndSection**[/INDENT]The only mandatory entry in a **Monitor** section is the **Identifier** entry.
The **Identifier** entry specifies the unique name for this monitor. The **Monitor** section provides information about the specifications of the monitor, monitor-specific **Options**, and information about the video modes to use with the monitor. Specifying video modes is optional because the server now has a built-in list of VESA standard modes. When modes are specified explicitly in the **Monitor** section (with the **Modes**, **ModeLine**, or **UseModes** keywords), built-in modes with the same names are not included. Built-in modes with different names are, however, still implicitly included.
The entries that may be used in **Monitor** sections are described below.
......**Flags "***flag***"*** ...*specifies an optional set of mode flags, each of which is a separate string in double quotes. **"Interlace"** indicates that the mode is interlaced. **"DoubleScan"** indicates a mode where each scanline is doubled. **"+HSync"** and **"-HSync"** can be used to select the polarity of the HSync signal. **"+VSync"** and **"-VSync"** can be used to select the polarity of the VSync signal. **"Composite"** can be used to specify composite sync on hardware where this is supported. Additionally, on some hardware, **"+CSync"**and **"-CSync"** may be used to select the composite sync polarity........

---

