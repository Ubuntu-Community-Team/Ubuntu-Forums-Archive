---
title: "where are the additional fonts?"
date: 2016-11-07
forum: General Help
---

### Post by Richard-S on 2016-11-07
Here is a post from Ask Ubuntu:

[I]Also, there are lots of fonts available as software packages. Font  packages are named in the form ttf-* or otf-*. It is better to install  fonts as packages instead of manually if possible. You can use tools  such as Synaptic, apt-get or the Ubuntu Software Centre. The Software  Centre has a dedicated fonts section.
[/I]
When I go to the software center and type in search for "fonts" I get "No application found." How do I get to the dedicated fonts section?

Richard

---

### Post by 1clue on 2016-11-07
Yesterday I had badness after what started as a simple upgrade. Shortly after it supposedly finished, the system rebooted itself without asking, and then I couldn't login to the gui.

I wound up logging in via ssh from another box, installed xubuntu-desktop and logged in using that.

One of the messages I found involved Microsoft fonts, and some .exe files that couldn't be written to some directory or other.

I had other things on my mind which were more pressing (like being able to do my work) so I sort of skimmed over it.

This may be pertinent.

---

### Post by SeijiSensei on 2016-11-07
To get the Microsoft TrueType fonts, you need to install the **ttf-mscorefonts-installer** package.  When the screen appears asking you to accept the Terms, tab to the <OK> field and hit enter.

As for other font packages, I have no idea where they are kept.  I have an archive of fonts from other sources including Microsoft that I load routinely on new machines.  The only .deb package I've installed is the corefonts one.

---

### Post by CantankRus on 2016-11-07
Synaptic has a fonts section though I've never installed from here and appear to be mostly language fonts.
What sort of font are you looking for?

---

### Post by Richard-S on 2016-11-08
I have used Baskerville and Times New Roman for many years. I can certainly change if those are not readily available.

Another, and more important, question is: How do I enter characters such as a dash using the keyboard code. The code for a long dash is:  U+2015.  I read in the help to hold down Ctrl and Shift and press u and the four digit number and then Enter. All I get when I do this is an underlined u.

In Windows I pressed Alt and the four digit code, but that does not work here.

(I run Ubuntu 16.04. The forum won't allow me to change my old profile until I have ten posts.)

Richard

---

### Post by vasa1 on 2016-11-08
> **Richard-S said:**
> ...
When I go to the software center and type in search for "fonts" I get "No application found." How do I get to the dedicated fonts section?
...
Do you have Synaptic Package Manager installed? 
As the image shows, clicking on "Sections" (where the red mouse pointer is) generates the list in the panel above where I've boxed three font-related entries.

Alternatively, if you open your terminal and run *apt search fonts | less*, you'll get a very long list of fonts. Since you want MS fonts, your best bet is to go the ttf-mscorefonts route as suggested by SeijiSensei.

---

### Post by CantankRus on 2016-11-08
The package SeijiSensei referred to, **ttf-mscorefonts-installer**, installs these fonts....
  [LIST]
[*]Andale Mono
[*]  Arial Black
[*]  Arial (Bold, Italic, Bold Italic)
[*]  Comic Sans MS (Bold)
[*]  Courier New (Bold, Italic, Bold Italic)
[*]  Georgia (Bold, Italic, Bold Italic)
[*]  Impact
[*]  Times New Roman (Bold, Italic, Bold Italic)
[*]  Trebuchet (Bold, Italic, Bold Italic)
[*]  Verdana (Bold, Italic, Bold Italic)
[*]  Webdings
[/LIST]

For entering Unicode charcaters, after pressing ctrl+shift+u release all keys, type in the hex code then press enter.
The guides I see say to hold down ctrl+shift while typing hex codes as well. Doesn't work here.

---

### Post by Impavidus on 2016-11-08
Hold ctrl+shift, type u followed by the hexadecimal code, then release ctrl+shift. Or hit ctrl+shift+u, type the hexadecimal code and hit enter or space. The first doesn't always work. While I hold left ctrl and left shift, or right ctrl and right shift, the 2 and 8 on my numeric keypad don't work. Left ctrl+right shift or right ctrl+left shift works, but is not convenient. Numeric row always works. So it may depend on your keyboard.

Also consider using the compose key. Compose key sequences are easier to memorise than hexadecimal codes. I don't think there's an easy code for the horizontal bar (U+2015), but there is for the em-dash (U+2014: <compose> - - -).

---

### Post by Richard-S on 2016-11-08
I tried left Ctrl  + left Shift + u, then released them and typed 2015 and hit Enter. I got a dash.

Richard

---

