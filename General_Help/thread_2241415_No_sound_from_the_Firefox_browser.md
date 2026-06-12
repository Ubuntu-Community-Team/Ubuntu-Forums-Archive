---
title: "No sound from the Firefox browser"
date: 2014-08-26
forum: General Help
---

### Post by cjsmall on 2014-08-26
I have a new bare metal installation of xubuntu 14.04.1 on a Xeon system.  I am getting no sound out of the Firefox 31 browser when, for example, I play a youtube video or preview a song at a music site.  The audio on this system is working properly.  All music and video players work, the sound system passes all hardware tests, and these same sites produce sound from the Chrone and Opera browsers.  I have reloaded the firefox package with no improvement.  I can't think of an option setting in Firefox that would control the sound output.  Is anyone else seeing this behavior and can you suggest something that might fix the situation?  Thnaks.

---

### Post by vasa1 on 2014-08-26
> **cjsmall said:**
> ... I can't think of an option setting in Firefox that would control the sound output.  Is anyone else seeing this behavior and can you suggest something that might fix the situation?  ...
Sound works for me. Is it possible some extension is interfering? 

Could you try with all extensions disabled?

Also, could you go into **Help, Troubleshooting Information** and paste the bits relating to plug-ins within ```
 tags? For example, this is what I see:
[CODE]plugin.disable_full_page_plugin_for_types	application/pdf
plugin.importedState	true
plugin.sessionPermissionNow.intervalInMinutes	0
plugin.state.flash	1
plugin.state.gecko-mediaplayer	1
plugin.state.gecko-mediaplayer-dvx	1
plugin.state.gecko-mediaplayer-qt	1
plugin.state.gecko-mediaplayer-rm	1
plugin.state.gecko-mediaplayer-wmp	1
```

A somewhat drastic approach is to "reset" Firefox. That option should appear near the top right of the Troubleshooting Information page. If you haven't invested too much into customizing Firefox, it shouldn't be a problem.

---

### Post by cjsmall on 2014-08-26
I created a new profile with no extensions at all and the sound problem exists.  Under this profile, the only plugin line on the troubleshooting page is:

     plugin.disable_full_page_plugin_for_types   application/pdf

However, I think I may have a clue as to what might be wrong.  On that page it shows the following under the Graphics section:

Adapter Description NVIDIA Corporation -- Quadro K4000/PCIe/SSE2
Device ID   Quadro K4000/PCIe/SSE2
Driver Version  4.4.0 NVIDIA 331.38
GPU Accelerated Windows 0/1 Basic
Vendor ID   NVIDIA Corporation
WebGL Renderer  NVIDIA Corporation -- Quadro K4000/PCIe/SSE2
windowLayerManagerRemote    false
AzureCanvasBackend  cairo
AzureContentBackend cairo
AzureFallbackCanvasBackend  none
AzureSkiaAccelerated    0

There is a K4000 graphics card in this system and it has an on-board audio subsystem which I assume would drive speakers in an attached display through a DisplayPort connection.  (I'm not there yet in my setup configuration!)  The audio GUI shows two output devices:

    * HDA NVidia
    * Built-in Audio

The motherboard built-in audio is the active audio system which everything is using.  I'm beginning to think that Firefox may be trying to use the currently disabled an unattached Nvidia audio system along with the graphic.  about:config offers no additional clues when I search on "audio". 

How can I test this for certain, and what can I do to force Firefox (and potentially other applications) to use the built-in audio subsystem?  Of course, the problem may still be something else.

Thanks for the feedback.  You've already showed me something new about this release of Firefox!

---

### Post by vasa1 on 2014-08-26
> **cjsmall said:**
> I created a new profile with no extensions at all and the sound problem exists.  Under this profile, the only plugin line on the troubleshooting page is:

     plugin.disable_full_page_plugin_for_types   application/pdf

However, I think I may have a clue as to what might be wrong.  ...
... How can I test this for certain, and what can I do to force Firefox (and potentially other applications) to use the built-in audio subsystem?  Of course, the problem may still be something else.
...
I don't know anything about hardware but it's curious that you have only one plugin line. While having or not having the Shockwave Flash plugin would be understandable, it's odd that the gecko-mediaplayer is missing.

Does anyone else *not* have the gecko-mediaplayer listed in **about:addons**?

When I run **apt-cache show gecko-mediaplayer**, there's this line at the end:```
Task: lubuntu-desktop
``` So I'm guessing it's possible that Xubuntu users may not see this plugin.

---

### Post by vasa1 on 2014-08-26
> **cjsmall said:**
>  ... and these same sites produce sound from the Chrone and Opera browsers. ...
If you have a recent version of Opera, that's very similar to Chrome and maybe Opera has adopted Chrome's plugins as well.

Could you try installing gecko-mediaplayer to see if that will get you sound in Firefox?
You can see what will be installed by running ```
sudo apt-get install --simulate gecko-mediaplayer
```Then, if you're willing to go ahead, just drop the **--simulate**.

---

### Post by cjsmall on 2014-08-26
The **gecko-mediaplayer** package was not installed.  Iinstalled it and rebooted.  Now it does show up as four separate plugins as seen in the attached image:

[IMG]http://smallthoughts.com/photos/misc/gecko_plugin.png[/IMG]

**apt-cache show gecko-mediaplayer** does now show **Task: lubuntu-desktop**.  However, the troubleshooter page still only lists the following plugin entries:

plugin.disable_full_page_plugin_for_types       application/pdf
plugin.expose_full_path true
plugin.importedState    true

Firefox still will not produce any sound, even if I set the plugin to **Always Activate**.

So this doesn't seem to address the problem.

> Could you try installing gecko-mediaplayer to see if that will get you sound in Firefox?

I assume you mean the **gnome-mplayer** which was automatically installed by the gecko package.  Yes, this works fine, like all of the other media players.

I'm open to more ideas!  :-)

---

