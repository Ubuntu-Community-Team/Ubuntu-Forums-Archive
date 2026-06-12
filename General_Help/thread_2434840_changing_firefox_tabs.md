---
title: "changing firefox tabs"
date: 2020-01-11
forum: General Help
---

### Post by Skaperen on 2020-01-11
i would like to change the color of which tab is the currently viewed tab in firefox because when i have a lot of small tabs which is often the case for me i find it hard to see which tab i am currently at.  if an extension exists to do this, i'd like one that can give another color to the previously viewed tab so i can go back quickly.  even better would be a (fading) rainbow of colors for a few previous tabs, like red, orange, yellow, green, blue, violet.  how can i do something like this?  the current method is just too hard for my age old eyes to see very well.

---

### Post by crip720 on 2020-01-11
I have not used them myself, but do remember reading about a few extensions for tab management.  A google search for 'firefox tab management' should point you in the right direction.

---

### Post by Holger_Gehrke on 2020-01-12
Or you could set up a userChrome.css file.

```

@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");

/* red background on the active tab */
tab.tabbrowser-tab hbox.tab-content[selected=true] {
  background-color:red !important;
}

```

Copy and paste this into an editor and save as userChrome.css in ~/.mozilla/firefox/[COLOR=#ff0000]your_profile_directory_here[/COLOR]/chrome/ (replace the red part).
The browser reads userChrome.css when it starts, so a restart of the browser should be necessary. To find the right selector to change other parts of the browser use the Browser-Tools from Extras->Web-Developer.

Holger

---

### Post by Skaperen on 2020-01-12
i added the file and restarted Firefox.  there is no change.  all the tabs are still the same one shade of gray.

---

### Post by Holger_Gehrke on 2020-01-13
That's strange. With these settings in ~/.mozilla/firefox/39z18i5t.default/chrome/userChrome.css I get what you can see in the attached image.

Holger

[ATTACH=CONFIG]284797[/ATTACH]

---

### Post by Dennis N on 2020-01-13
Just changing the Firefox theme might help. Many show a difference in the active tab that makes it easy to pick out. See attached screenshot of Adwaita Arc Firefox theme.

---

### Post by Skaperen on 2020-01-13
> **Dennis N said:**
> Just changing the Firefox theme might help. Many show a difference in the active tab that makes it easy to pick out. See attached screenshot of Adwaita Arc Firefox theme.

how do i change theme?  i see nothing for this in preferences.  is Adwaita Arc included?

---

### Post by Dennis N on 2020-01-13
> **Skaperen said:**
> how do i change theme?  i see nothing for this in preferences.  is Adwaita Arc included?

Open the Firefox Menu (at far right of address bar), then
**Customize > Themes > Get More Themes**.
On next screen, there is a search box at the top if you know the name (or part of it), or you can browse the categories.

I think you need to briefly install a theme to see what it really looks like. If you don't like it, click Remove and try another. You can switch between installed themes from the Add-ons Manager:
Tools > Add-Ons

---

### Post by bernard010 on 2020-01-13
I like your idea of changing tab colors. Let me know if you find one. 
I tried all of the other Themes did not care for any of them. Firefox even has Stylish - custom themes. It is a Firefox Extension with over 1000 themes. That is all I could find.
[https://addons.mozilla.org/firefox/addon/stylish/ ]("https://addons.mozilla.org/firefox/addon/stylish/")

Go to ad-on's or ctl+shift+A

---

### Post by Skaperen on 2020-01-14
> **Dennis N said:**
> Open the Firefox Menu (at far right of address bar), then
**Customize > Themes > Get More Themes**.
On next screen, there is a search box at the top if you know the name (or part of it), or you can browse the categories.


i go to **Customize** but there is no **Themes** there.

---

### Post by Holger_Gehrke on 2020-01-14
There's a button at the bottom of the screen labelled 'Themes' which gives you a pop-up menu with 'Get More Themes' as one of the options. This is simply a link to [https://addons.mozilla.org/de/firefox/themes/](https://addons.mozilla.org/de/firefox/themes/)

Holger

---

### Post by Skaperen on 2020-01-14
found it at the bottom.  Adwaita Arc makes all the tabs black except the active one is gray.

---

### Post by Skaperen on 2020-01-14
now i wonder if these themes could change the yellow and orange colors i get from ubuntuforums.org.  i'm ready for a color change.

---

### Post by Skaperen on 2020-01-26
are there any other themes that color the active tab different?  or do need to try lots of them to see?

---

