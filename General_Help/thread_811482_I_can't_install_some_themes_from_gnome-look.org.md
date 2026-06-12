---
title: "I can't install some themes from gnome-look.org"
date: 2008-05-29
forum: General Help
---

### Post by quinnten83 on 2008-05-29
Hi, 
I am having some problems installing some themes like vitality black.At first I tried installing through Appearance option, but I can't find the theme in the theme selection screen, even though i get the message that the theme was correctly installed
Also installed by untarring to the .themes folder and the theme folder is present, but I still can't select it.

I opened the theme folder and compared it to another theme and I saw the Index file looks different for both themes (see attached picture).

 I can open both in gedit, and they have similar content. When I check the properties for both themes (by right clicking) they have similar properties. 

I'm kinda stumped, does anybody know why these themes won't install normaly and how I can make them install?

---

### Post by rune0077 on 2008-05-29
> **quinnten83 said:**
> Hi, 
I am having some problems installing some themes like vitality black.At first I tried installing through Appearance option, but I can't find the theme in the theme selection screen, even though i get the message that the theme was correctly installed
Also installed by untarring to the .themes folder and the theme folder is present, but I still can't select it.

I opened the theme folder and compared it to another theme and I saw the Index file looks different for both themes (see attached picture).

 I can open both in gedit, and they have similar content. When I check the properties for both themes (by right clicking) they have similar properties. 

I'm kinda stumped, does anybody know why these themes won't install normaly and how I can make them install?

The theme you''ve installed is probably not a complete theme, and hence won't show up under themes. Themes can also be:

Icons: new icons
Controls: the gtk layout
Window borders: metacity theme
Pointer: mouse cursors

You can change all these in Apperances by hitting the "Customize" button. So figure out which of these your installed theme is, click "Customize", go to the appropriate tab and your installed theme should be listed there.

---

### Post by quinnten83 on 2008-05-30
yeah, that is the thing.
A colleague was runnnig Ubuntu on the live cd and he had the transparacies and colors and everything setup the moment he installed. Me, I couldn't even find it in the theme selection windows.
But i will check it out, I probably overlooked something or misunderstood the concept.

---

### Post by rune0077 on 2008-05-30
Maybe you misunderstood me (or maybe I misunderstood you). I just tried to install the vitality-black theme, and it works on my end, like this:

Download it to a folder.

Open System > Preferencens > Appearances

Click "Install" and select the downloadable theme. (it should now be in the .themes directory)

Still in System > Preferences > Appereances, click "Customize", and then the tab called "Controls" (it's the first one, so need to click it).

Vitality-black is there, on the list, so I just select it.

If that doesn't work, I'm not sure what is wrong.

---

