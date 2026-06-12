---
title: "Where is the folder for installed fonts"
date: 2022-12-26
forum: General Help
---

### Post by satimis on 2022-12-26
Hi all,

Ubuntu 22.04 desktop

Please advise where can I find the folder/directory for installed fonts.

Thanks in advance

Regards

---

### Post by Dennis N on 2022-12-26
> **satimis said:**
> Please advise where can I find the folder/directory for installed fonts.
Linux has standard locations for installed things, like applications, themes, icons, fonts. 

When installed by the OS installer, or from a repository with admin privileges (sudo), they are under /user/share/fonts/<type-of-font>/<name-of-font>, 
or /user/share/fonts/<name-of-font>

Look there and you will find them.

You can optionally download a font file and put it in /usr/share/fonts, or ~/.local/share/fonts. or ~/.fonts. The last is, I think, depricated.

---

### Post by satimis on 2022-12-26
> **Dennis N said:**
> Linux has standard locations for installed things, like applications, themes, icons, fonts. 

When installed by the OS installer, or from a repository with admin privileges (sudo), they are under /user/share/fonts/<type-of-font>/<name-of-font>, 
or /user/share/fonts/<name-of-font>

Look there and you will find them.

You can optionally download a font file and put it in /usr/share/fonts, or ~/.local/share/fonts. or ~/.fonts. The last is, I think, depricated.
Hi,

Thanks for your advice.

I have been searching the full path of font folders/directories.

On Libre Office Writer
I found;
Arial Black
Comic Sans MS
C059
etc.
Where are their folders, including their full path ?

Also on Activities -> Fonts
I found;
Arial Bold
Century Schoolbook L, Bold
Courier 10 Pitch, Bold
etc.
Where are their folders, including their full path ?

Font Manager can't help me out.

I need their full path to run ImageMagick

Regards

---

### Post by grahammechanical on 2022-12-26
On both 22.04 and 20.04 if I open the Fonts utility and select a font I see an "Info" button. I click on that button and am given a location of the selected font. For example, Arial is located at /usr/share/fonts/truetype/msttcorefonts/Arial.ttf

Regards

---

### Post by satimis on 2022-12-26
> **grahammechanical said:**
> On both 22.04 and 20.04 if I open the Fonts utility and select a font I see an "Info" button. I click on that button and am given a location of the selected font. For example, Arial is located at /usr/share/fonts/truetype/msttcorefonts/Arial.ttf

Regards
Thanks for your advice.

Activities -> fonts
I couldn't find "Fonts utility" there and I couldn't select any font there.

Pls refer to attached screenshot

Regards

---

### Post by Holger_Gehrke on 2022-12-27
That probably is the font utility grahhammechanical was talking about. Its actual name is 'gnome-font-viewer'. On my system it tends to hang and not react to any mouse clicks for several minutes until it becomes responsive (it's probably busy loading all the fonts and caching them and doing whatever else it needs to do ...). When it finally starts working, clicking on a font produces an overview with samples at different sizes and a button labeled info in the title bar.

Holger

---

### Post by satimis on 2022-12-27
> **Holger_Gehrke said:**
> That probably is the font utility grahhammechanical was talking about. Its actual name is 'gnome-font-viewer'. On my system it tends to hang and not react to any mouse clicks for several minutes until it becomes responsive (it's probably busy loading all the fonts and caching them and doing whatever else it needs to do ...). When it finally starts working, clicking on a font produces an overview with samples at different sizes and a button labeled info in the title bar.

Holger
Hi Holger,

Thanks for your reply.  I also found those fonts on your screenshot.

What I expect to find is the font folder and its full path.  I need it for operating ImageMagick.  I don't expect it is so difficult to find on Ubuntu 22.04

Regards

---

### Post by Holger_Gehrke on 2022-12-27
> **satimis said:**
> I need it for operating ImageMagick.

The output of 'convert -list font' or 'identify -list font' might be helpful in this case ...

Holger

---

### Post by satimis on 2022-12-28
> **Holger_Gehrke said:**
> The output of 'convert -list font' or 'identify -list font' might be helpful in this case ...

Holger
Hi,

Thanks

Regards

---

