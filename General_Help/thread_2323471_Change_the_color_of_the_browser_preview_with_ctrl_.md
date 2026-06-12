---
title: "Change the color of the browser preview with ctrl + tab in Firefox"
date: 2016-05-05
forum: General Help
---

### Post by Salil_Surendran on 2016-05-05
Hello,
When I do Ctrl+tab in Firefox the browser preview window does come up but the selected tab is not highlighted such that it be clearly visible and is very difficult to spot. I am using Ubuntu 16. All the images in /usr/share/unity/icons are svg files. Which one of the files should I change to get the ctrl+tab highlight changed in firefox?

---

### Post by Frogs Hair on 2016-05-05
Please use default font.

---

### Post by Salil_Surendran on 2016-05-06
Any help here? Which icon in [COLOR=#000000]/usr/share/unity/icons controls this?[/COLOR]

---

### Post by vasa1 on 2016-05-06
I'm not sure it's an issue related to */usr/share/unity/icons*. Have you tried changing your gtk3 theme? It's probably got to do with the css used by the current theme. 

I use the Greybird theme which is part of the *shimmer-themes* package in the Software Center (Just run *sudo apt-get install shimmer-themes* or *sudo apt install shimmer-themes* (if you don't want the .deb to be stored in */var/cache/apt/archives*)). It seems to be able to handle a lot of gtk3 aspects some other themes, including the default Ambiance/Radiance duo, stumble over.

You could also try Adwaita which is baked into gtk 3.18 and which supposedly should be perfect since it's made by the GNOME's themselves.

---

### Post by Salil_Surendran on 2016-06-08
> **vasa1 said:**
> I'm not sure it's an issue related to */usr/share/unity/icons*. Have you tried changing your gtk3 theme? It's probably got to do with the css used by the current theme. 

I use the Greybird theme which is part of the *shimmer-themes* package in the Software Center (Just run *sudo apt-get install shimmer-themes* or *sudo apt install shimmer-themes* (if you don't want the .deb to be stored in */var/cache/apt/archives*)). It seems to be able to handle a lot of gtk3 aspects some other themes, including the default Ambiance/Radiance duo, stumble over.

You could also try Adwaita which is baked into gtk 3.18 and which supposedly should be perfect since it's made by the GNOME's themselves.

This didn't fix the problem. Anything else that I can try?

---

### Post by Salil_Surendran on 2016-06-16
Bump

---

### Post by leunam12 on 2016-06-16
Ctrl+Tab in Firefox goes to the next tab in my computers. What is the browser preview window?

---

### Post by Habitual on 2016-06-17
The firefox *version*?

---

### Post by vasa1 on 2016-06-17
> **leunam12 said:**
> Ctrl+Tab in Firefox goes to the next tab in my computers. What is the browser preview window?
Maybe you have this in about:config
```
browser.ctrlTab.previews;false
```

I made a new profile and the setting was as above. I flipped it to "true" and then used Ctrl+Tab. This opened the New Tab page (which I normally don't bother with).

The first image shows nothing selected and the second is with my mouse pointer hovering over one "tile" if that's what they're calling it.

---

### Post by leunam12 on 2016-06-18
> **vasa1 said:**
> Maybe you have this in about:config

Ok, I can see it now, but the hilighting is very subtle; the hilighted tab doesn't have a drop shadow, that's it, not really evident, you have to look really hard.

Thanks, I didn't know this feature.

---

### Post by vasa1 on 2016-06-18
> **leunam12 said:**
> Ok, I can see it now, but the hilighting is very subtle; the hilighted tab doesn't have a drop shadow, that's it, not really evident, you have to look really hard.

Thanks, I didn't know this feature.

I'm guessing that there's no highlighted tab, per se, unless you hover your mouse pointer over a tile. Then, the change in appearance is very clear.

---

