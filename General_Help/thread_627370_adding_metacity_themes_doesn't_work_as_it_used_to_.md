---
title: "adding metacity themes doesn't work as it used to - what am I doing wrong?"
date: 2007-11-30
forum: General Help
---

### Post by dwasifar on 2007-11-30
In earlier versions, when we had the Theme manager as a separate menu entry, installing a metacity theme added that theme to the list of available themes, and you could then select it.

But in Gutsy, in the Appearance manager, if I add a metacity theme, the only way I can get it to appear in the list is to click the Apply button as soon as it is installed.  Then it comes up as "Custom" and I have to manually name it.  If I don't Apply it as soon as it is installed, the theme files are copied to ~/.themes, but the theme itself never shows up in the themes window of the Appearance manager.  This is true whether I add the theme by drag and drop, or by clicking the Install button.

Am I making some DUH mistake here?

---

### Post by dwasifar on 2007-11-30
bump bump bumpity bump bump

---

### Post by dwasifar on 2007-11-30
Well, I figured it out, sort of, and fixed it, sort of.

Apparently any theme you add in Appearance>Themes needs an index.theme file in its directory.  If that's not there, the theme components are available in the Customize tab, but the theme itself is not a choice in the Themes tab.  The index.theme files are strange beasts; I haven't quite figured out how it is that Nautilus displays them as having the theme's filename when an ls in terminal shows them as index.theme.  But no matter.

To save myself a bit of work when installing themes, I cooked up a little script file to create index.theme files for any installed themes that are missing them.  Download it here: [http://www.dwasifar.com/fixthemes.tar.gz]("http://www.dwasifar.com/fixthemes.tar.gz")

Extract it into your home directory (along with the index.theme file included, which is a template).  When you run it, it will look in all the subdirectories of your .themes folder and create an appropriate index.theme in any one that doesn't already have one.  Then next time you look at Appearance>Themes, they'll all be there.

---

