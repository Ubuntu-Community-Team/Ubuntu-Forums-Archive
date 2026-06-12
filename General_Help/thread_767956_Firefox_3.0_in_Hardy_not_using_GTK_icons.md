---
title: "Firefox 3.0 in Hardy not using GTK icons"
date: 2008-04-26
forum: General Help
---

### Post by Zeedok on 2008-04-26
I upgraded to Hardy yesterday and am ironing out a few minor wrinkles.  Now that I am using Firefox 3 (which seems faster :)) the theme I was using is not available.  There don't seem to be many themes available for 3.0 as yet.  I don't use anything fancy, but the icons do not match the rest of my system.

After some reading I am left with the impression that Firefox should be using the system icon set - but in my case it clearly isn't (eg I am using nuove XT for my other icons, but my firefox 'folder' icons are blue, in Nuove they are yellow).  I am using compiz (advanced features enabled) and emerald for my window decorations (in case that is relevant).

How can I get firefox to use my system icons?  Or failing that, does anyone know of a collection of 3.0 themes that I could check out?

---

### Post by sdennie on 2008-04-26
You could try going to Tools->Add-ons->Themes and make sure you are using the default firefox theme.  That appears to make it use the system theme.

---

### Post by Zeedok on 2008-04-26
Already checked that, I'm afraid. Changing the colour does make it's way into Firefox, but the icons do not.

Any other suggestions?

---

### Post by sdennie on 2008-04-26
Another thing you could try would be to start firefox from a terminal and with the -P option.  That will allow you to setup a "clean" profile and see if Firefox still shows the same behavior.  It's not a fix necessarily but, it might help in finding the cause of the issue.

---

### Post by FredB on 2008-04-26
I think you will have to install ubufox package in order to get a better display.

---

### Post by Zeedok on 2008-04-26
So starting from the command line wuth the -p option (and creating a new profile) made no difference.  If by ubufox, you mean the Ubuntu firefox extension, it is already installed (by default isn't it?).  Enabling and disabling it makes no difference.  As I said before, some of the theme changes (like colour) do seem to make it into Firefox, but the icons do not change, regardless of the icon set I choose.

---

### Post by RawMustard on 2008-04-26
Because your chosen icon theme doesn't contain the correct .png folder icons in status/gtk-directory.png. Firefox will not see svg files and it doesn't for some reason honour the index.theme fallback options.  You'll need to create these folders and add the icons yourself until someone fixes Firefox properly.

Anyway, that's what I've noticed running Firefox-3.0.b5 here on my feisty64 install.

---

### Post by Zeedok on 2008-04-26
I think you've got it right.  I can change the icons successfully, though only if I choose an icon theme with svg icons.

I have to say that this irritates me a little.  My favourite icon set (NuoveXT) only comes in png format.  The developer does have a firefox theme, though guess what - only compatible with Firefox 2.  I've been through the firefox addons pages and there are <10 themes that are compatible with 3.0 (and none of them match my system icon theme).  The majority of icon sets in Gnome-Look are in png format too.  OS integration is all well and good, but . . .

---

### Post by Zeedok on 2008-04-26
Sorry, I misread your post:

> Firefox will not see svg files and it doesn't for some reason honour the index.theme fallback options. You'll need to create these folders and add the icons yourself until someone fixes Firefox properly.

By this I am guessing firefox needs a gtk-directory.png file to use for the bookmarks on the toolbar, which it usually looks for in the status folder within .icons, correct?

I tried renaming the icon image I liked 'gtk-directory' in all the status folders (ie 16x16, 72x72 etc) but nothing happened.  Have I missed a step?

---

