---
title: "root-tail error in fluxbox"
date: 2007-02-19
forum: General Help
---

### Post by r0ck80y on 2007-02-19
Hi,

I am running dapper 6.06 on fluxbox and i just installed root-tail. Upon giving the following command as a normal user:
```

$ root-tail -g 600x650+1+1 -fn fixed /path/to/log/file,yellow &
```

the error is: "unable to create fontset for font 'fixed', exiting"

If i give this same command as root, the error is :
```
 Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
Cant open display (null)

```

Any idea,  whats wrong? 
P.S. This same command works in mandriva 2007 :D

---

### Post by r0ck80y on 2007-02-19
Anyone???

---

### Post by yabbadabbadont on 2007-02-21
It worked for me.  Perhaps you are missing some font package?  I pretty much installed every one of the fonts listed as a dependency of ubuntu-desktop.  (plus some others ;))  I don't actually have ubuntu-desktop installed, just the fonts it lists.  I did an expert server install with the alternate cd and have just added Xorg, Fluxbox, and a few other things that I use.

Here are the fonts I have installed:
```

i   gsfonts                         - Fonts for the Ghostscript interpreter(s)  
i   gsfonts-other                   - Additional fonts for the ghostscript inter
i   gsfonts-x11                     - Make Ghostscript fonts available to X11   
i   msttcorefonts                   - Installer for Microsoft TrueType core font
i   ttf-bengali-fonts               - Free TrueType fonts for the Bengali langua
i   ttf-devanagari-fonts            - Free TrueType fonts for languages using th
i   ttf-freefont                    - Freefont Serif, Sans and Mono Truetype fon
i   ttf-gujarati-fonts              - Free TrueType fonts for the Gujarati langu
i   ttf-indic-fonts                 - Metapackage for free Indian language fonts
i   ttf-kannada-fonts               - Free TrueType fonts for the Kannada langua
i   ttf-malayalam-fonts             - Free TrueType fonts for the Malayalam lang
i   ttf-oriya-fonts                 - Free TrueType fonts for the Oriya language
i   ttf-punjabi-fonts               - Free TrueType fonts for the Punjabi langua
i   ttf-tamil-fonts                 - Free TrueType fonts for the Tamil language
i   ttf-telugu-fonts                - Free TrueType fonts for the Telugu languag
i   xfonts-100dpi                   - 100 dpi fonts for X                       
i   xfonts-75dpi                    - 75 dpi fonts for X                        
i   xfonts-artwiz                   - x11 fonts created by Artwiz, TigerT, and D
i   xfonts-base                     - standard fonts for X                      
i   xfonts-scalable                 - scalable fonts for X                      
i   xfonts-terminus                 - Fixed-width fonts for fast reading        

```
I hope that helps.

---

