---
title: "Trying to understand how F-Spot works"
date: 2007-11-10
forum: General Help
---

### Post by kag on 2007-11-10
Since Picasa is too laggy on my computer, I figured why not switch to F-Spot. I understand F-Spot works with a SQLite DB which is stored somewhere in the home folder. What is in that DB?

1 When you import pictures, what exactly does the "Copy files to the Photos folder" checkbox do? If you leave it unchecked, the pictures are going to be added to the catalogue from where they are? And if you check it, they are going to be copied to the Photos folder and added to the catalogue from the new location (so this way there's not going to be any reference to the original files)?

2. When you take a picture and, for example, you crop it and ajust the colors. I understand it's not going to alter the original files because you can always make new "version"s of it. But is the modified copy stored somewhere (where?) ? Or are the modifications being applied on-the-fly like some Picasa ajustements?

I just want to be sure about what's going to keep my original files intact, and what's going to modify them (either the picture data or the EXIF metadata).

Thanks!!!

---

### Post by kag on 2008-02-29
Bump!

---

### Post by badmedic on 2008-02-29
Hi Kag,

You appear to be correct on 1. - Here is a quote from the F-Spot site:
> 
Import

You can import photos from your hard drive or your camera. When you import your photos into F-Spot from your camera, it will always make a copy of them, leaving you free to clear your camera's memory. By default, F-Spot will make a copy of photos imported from your hard drive. **Uncheck the "Copy" option on the import dialog or hold "Shift" when dragging photos into F-Spot if you do not wish to copy them from your hard drive.**

By default, F-Spot copies your photos to the ~/Photos folder. You can change the folder F-Spot uses in Preferences dialog (Edit » Preferences). 

For your second question I am not sure... you could always import a couple test images and edit one... If I had to guess the edited versions are probably going to show up in the same directory or a hidden subdirectory.

You can probably get a better answer from the creators - [http://f-spot.org/](http://f-spot.org/)

---

