---
title: "Missing jsmath fonts - please help!"
date: 2008-01-29
forum: General Help
---

### Post by JohnPhys on 2008-01-29
I'm going insane trying to figure this out, I would greatly appreciate any help.

I'm trying to get the jsmath fonts to appear in firefox, though I always get the red "missing jsmath fonts" box (such as when using the sage mathematics software, from here 

[https://www.sagenb.org/](https://www.sagenb.org/)  )

Just browse some of the notebooks.  I don't see any nice fonts, they're all unicode.  Does anyone else ahve this problem?

I've installed jsmath and jsmath-fonts, restarted firefox, run fc-cache......I'm going insane, please help!

--John

---

### Post by teich on 2008-02-15
It's a bit late I'm sure but I just stumbled across the solution:

[http://www.math.union.edu/~dpvc/jsMath/download/jsMath-fonts.html](http://www.math.union.edu/~dpvc/jsMath/download/jsMath-fonts.html)
I downloaded  TeX-fonts-10.zip.  Ignore what they are saying on that page, Ubuntu can of course handle the TTF fonts.  Put the .ttf files in ~/.fonts/ and do sudo fc-cache -fv.  You should be good to go.

I tried sudo apt-get install jsmath-fonts(...etc) and had no luck.  Maybe these are only for server-side things that use jsmath?  I noticed that apt-get lists apache as recommended when installing.

Anyway, hope this helps you or others.
teich

---

### Post by JohnPhys on 2008-02-28
That seems to have worked, thanks!

---

### Post by niteshifter on 2008-04-20
Hi,

JohnPhys wasn't the only one going 'round the bend, I was also. Thank you teich! Would've clicked the Thanks icon - but it's a no show.

The procedure is a bit different for Gutsy (7.10) - there is no ~/.fonts folder.

Goto the webpage in teich's post, select the .zip file you want. Unpack the zip file, open the folder created.

1. Click on the desktop.
2. Press Ctrl+L (brings up the Open Location dialog)
3. Type fonts:/// 
4. Click the Open button

Select all the downloaded fonts and drag them to the Fonts folder. **They will not appear in the fonts folder nor will applications have access to them until you log out of GNOME (Ctrl+Alt+Backspace) and log back in.** (Known bug in GNOME)

Voila! Sage notebook no longer moans about missing jsMath fonts.


Alternate way to get to the fonts folder:

1. Click System, then Appearance.
2. Click the Fonts tab.
3. Click the Details button.
4. Click the Go to Fonts Folder

---

