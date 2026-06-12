---
title: "What are the generic fonts in Ubuntu?"
date: 2015-01-18
forum: General Help
---

### Post by TriforceOfKirby on 2015-01-18
So in applications, there are fonts named: "Sans", "Serif", "Monospace", etc. What fonts are these actually? Are these the system default fonts? Can they be changed? For example, could "Sans" be made to use Arial?

---

### Post by kerry_s on 2015-01-19
of course the can, you just need to create a ~/.fonts.conf file with your settings. log out & back in, be good to go.
if i remember right i think those point to the dejavu fonts.

just google for a how to on the config file.

---

### Post by Impavidus on 2015-01-19
Arial is not installed by default, because it's a Microsoft font with a license incompatible to Ubuntu's licence. You can install Arial by installing the package **ttf-mscorefonts-installer** and accepting the licence. There are several packages pulling in this one as a dependency, so you may already have it.

---

### Post by buzzingrobot on 2015-01-19
"fc-match sans", "fc-match serif", etc. in a terminal will display the specific fonts mapped to those generics.  E.g., deja vu sans is mapped to sans.

Note that fonts used in web pages are determined by a page's CSS. Firefox allows that to be overridden, but the results may break a page's design and structure.

---

### Post by TriforceOfKirby on 2015-01-19
Ok so what if I wanted to change the system-wide config and not just the user config? Specifically I would like to use the Source Pro family made by Adobe; Source Sans Pro, Source Serif Pro, and Source Code Pro.

---

### Post by buzzingrobot on 2015-01-19
Fontconfig manages font mapping. System settings are in /etc/fonts.  A ~/.fonts.conf overrides what's set there for that user. 

A system of linked files is used to enable/disable particular mappings.  You should research fontconfig in some depth before trying to manipulate entries in /etc/font. I'm not aware of a GUI tool.

(I believe copying a working ~/.fonts.conf to /etc/fonts as 'local.conf' has the same impact system-wide. Try that first.)

---

### Post by TriforceOfKirby on 2015-01-20
So is this correct for the font config format?
```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
    <alias>
        <family>serif</family>
        <prefer>
            <family>Source Serif Pro</family>
        </prefer>
    </alias>
    <alias>
        <family>sans-serif</family>
        <prefer>
            <family>Source Sans Pro</family>
        </prefer>
    </alias>
    <alias>
        <family>monospace</family>
        <prefer>
            <family>Source Code Pro</family>
        </prefer>
    </alias>
</fontconfig>

```
And this is saved as local.conf in /etc/fonts correct?

---

