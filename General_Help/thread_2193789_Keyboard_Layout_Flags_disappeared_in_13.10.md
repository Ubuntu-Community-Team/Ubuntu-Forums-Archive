---
title: "Keyboard Layout Flags disappeared in 13.10"
date: 2013-12-14
forum: General Help
---

### Post by r_avital on 2013-12-14
Running 13.10 Unity.  I have 4 keyboard layouts (the maximum allowed).

In 13.04, the flags were displaying correctly on the panel.  I had the proper settings in dconf/gconf whatever that was.  I had the flags in the correct /home/myhome/.icons/flags.  They're still there.  At this point, after the upgrade to 13.10 the panel displays an icon with a two-letter code for the language (En, Fr, Es, etc.) with no flags

It seems the app or applet that shows the keyboard indicator/options has changed, because the buttons/menus on the new one (from 13.10) is different.  Does it even take account of the flags setting?  Is it possible at all to display flags in the Unity panel for the currently selected keyboard layout?  And if so, how?

Again, the only change to the system was the upgrade from 13.04 to 13.10.

---

### Post by r_avital on 2013-12-22
bump

---

### Post by r_avital on 2014-01-10
Bump, plus I found out additional info on this askubuntu page: [http://askubuntu.com/questions/10223/display-current-layout-language-code-country-flag-in-keyboard-indicator](http://askubuntu.com/questions/10223/display-current-layout-language-code-country-flag-in-keyboard-indicator)

Installed gxneur.
Ran it.  No application window opened.  This is supposed to be a GTK2.0 front-end to xneur, but for whatever reason it doesn't display.  And I do have a GTK-2 theme active, so I presume I do have a GTK 2.0 rendering engine running, correct?

I also read on the same page that the ability to display flags had been removed (although much earlier than Saucy) because "someone" felt that displaying flags was "inappropriate" -- who the *%&%^#$ does anyone think they are to dictate what's appropriate on your desktop or mine???  If this was true for a previous ubuntu release and is now showing up as a regression, this is truly frustrating.

Why is it, that with every "upgrade" and every new release, simple things like this become so much more difficult?  If at least I could count on LTS releases to be stable, that would be fine, but we've all seen the train-wreck that 12.04 was.

At any rate, does ANYONE have flags showing up in the keyboard indicator, or ANY keyboard indicator, in Saucy 64Bit in a Unity session?

Thanks in advance.

---

### Post by r_avital on 2014-01-20
bump

---

### Post by r_avital on 2014-04-06
bump.
folks, I'm only asking for a clear yes/no.  If this has been diabled for some reason in Saucy-64Bit, then someone please confirm.

It would be nice to know if was just an oversight and it's going to be re-enabled in 14.04.  It would even be nicer if someone knew of some other way, like a utility or something to re-enable it in saucy.

And yes, I did set the showflags to "yes" in the configuration editor.

Thanks

---

### Post by r_avital on 2014-04-09
This is how I solved the problem -- minor and insignificant as it is, there is nothing more frustrating than a feature that used to work perfectly and has been impacted and made useless or absent, by an "upgrade."

Since the legitimate and sensible procedures to display the country flags for the respective keyboard layouts was failing, I thought of manipulating the images that *are* displaying.  After some hunting around I found them in:

 /usr/share/icons/ubuntu-mono-dark/status/22 
and
/usr/share/icons/ubuntu-mono-light/status/22

In those directories, the image files are named:

 indicator-keyboard-En.svg for English 
indicator-keyboard-Fr.svg for French
indicator-keyboard-Es.svg for Spanish ... you get the idea.  There is one of each in both the "light" and "dark" directories named above.  Some of them, like English, will also have the "....En-1.svg" "....En-2.svg" .... "....En-32.svg" -- and ditto for French and Spanish, and most others.

... and yes, Saucy, in its windows-like consistency, sometimes displays the light version, sometimes the dark version, no rhyme or reason to it.  So rather than spend an eternity trying to figure it out, since I don't give a flyin'... The matter is of no consequence to me, I edited both versions in both the "light" and "dark" directories.

The editing:  An svg image is nothing more than an .xml file, and can be edited with a text editor.  That does not mean you can get the flags into it that way.

Example:  To display a boring "En" on a boring grey background, Ubuntu uses this xml file: indicator-keyboard-En.svg

Here are the contents of the original file:
```
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<svg width="22" xmlns="http://www.w3.org/2000/svg" version="1.1" height="22">
 <defs>
  <mask id="m">
   <rect y="0" x="0" style="fill:#fff" height="22" width="22"/>
   <text y="15.5" x="1.5" style="font-size:12;font-family:Ubuntu;font-weight:500;fill:black">En</text>
  </mask>
 </defs>
 <rect style="fill:#3c3c3c" mask="url(#m)" rx="2" height="20" width="20" y="1" x="1"/>
</svg>
```
As you can tell, there's hardly any graphics elements here, but this is used to draw a couple of letters on a grey background.

To get your own flag image(s) into an SVG file, you'll need to install Inkscape.

If you use the fancy new "Ubuntu Software Center," Don't.  It's not your friend.  Use it to install "Synaptic" and use Synaptic, a real package management system, to install and manage packages on your machine, but searching for "Inkscape" iin the software center should find you the package and all releted dependencies.

Once you've installed it, you can open your flag image in it, and simply save it AS an SVG file.  This will produce an xml file with all the necessary trimmings meeting all the necessary requirements, but most significantly, a long alphanumeric string (inside a properly formatted xml tag), that represents your image.

Make sure your flags are not too large, byte-wise.

Now, for example, if you were trying to make one for the French flag, once you've produced the svg version of your flag, open that file in your favorite editor, along with: /usr/share/icons/ubuntu-mono-light/status/22/indicator-keyboard-Fr.svg.  Again, I did it twice, once just like this, and once again for the same file in the "light" directory.  *Make sure you're opening it as root*, because you're going to edit that file (use "gksudo gedit" in the beloved HUD).

Also, [COLOR=#ff0000]**make sure you back up the original**[/COLOR] indicator-keyboard-Fr.svg.  [COLOR=#ff0000]_***If you brick your computer, don't come to me.***_[/COLOR]

What you want to do next, is merge the "image" tag from your flag-svg file with the indicator-keyboard-Fr.svg file, as below:
```
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<svg width="30" xmlns="http://www.w3.org/2000/svg" version="1.1" height="18">
<image
     width="30"
     height="18"
     xlink:href="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEAAAAArCAYAAADIWo5HAAAABHNCSVQICAgIfAhkiAAAAKdJREFU
aIHt0LEJwmAYBuHvD1joEhYZxDqdC7iA+ziDG2SBFBkoYGGKuMQPD8J7AxzHtRpfR/Xks9f8vtd0
u3bVfpe1tsez2uXc1Tt0tf0hGaADNBmgAzQZoAM0GaADNBmgAzQZoAM0GaADNBmgAzQZoAM0GaAD
NBmgAzQZoAM0GaADNBmgAzQZoAM0GaADNBmgAzQZoAM0GaADNBlQR9MNlKHqpBsoPwoXC6lf4Ybf
AAAAAElFTkSuQmCC
"
     id="image3028"
     x="0"
     y="0" />
</svg>
```

Everything between "<image" and "/>" came from the french flag svg file produced by Inkscape.  Everything above and below came from the original indicator-keyboard-Fr.svg file.

Note, that the final "</svg>" properly terminates the "<svg" tag started on line 2. This displays correctly on my panel as the French flag.  That long alphanumeric string that begins right after "base64," is the actual "meat" of the image, and this one is the shortest of all the flags (4) I've edited.

I've picked a size of 30 pixels wide by 18 pixels tall for all my flags, they make a pleasing effect and seem to match perfectly the height of other indicator icons on the panel.

As always, your mileage may vary.

I want to offer my sincere thanks to all who offered guidance in this echo-chamber of a thread.  And to Canonical, Kudos!  Healthcare.gov is finally working!  You done good!

---

### Post by Claus7 on 2014-08-31
Hello,

thank you very much for your post! It was really helpful in order to do exactly the same thing to 14.04.
I just want to add some minor information while I followed your procedure:

I wanted to use [these]("http://www.iconarchive.com/category/culture/no-patriot-icons-by-mayosoft.html") icons which are png files and have a size of 128x128.
As the OP said, someone might have to change the size in order for the icons to show up/show-up-correctly.
Here I would like to add that the resize procedure does not work when the file is in svg format. So, you download the files (flags) you like and then you type the command:
```
convert -size 22x22 USA-icon.png -resize 22x22 USA-icon_22x22.png
```
for the english language. 
What this command is doing see [here]("http://linux.about.com/od/commands/l/blcmdl1_convert.htm").
I would avoid using the resize option from nautilus, since the background of the flag icon was turning to black.
Now, open inkscape and just save the file to svg. Just to add that while opening the file leave the option embed as it is. 
The rest you will have to do are exactly as the OP described (concerning the parts that they have to be merged).

The language files I had to change for my case were:
indicator-keyboard-En.svg for the english language and
indicator-keyboard-Gr.svg for the hellenic language.
I did not change anything about files that they had numbering (e.g. indicator-keyboard-Gr-5.svg).

Log out and back in and you will see the results!

The process that is described [here]("http://askubuntu.com/questions/10223/display-current-layout-language-code-country-flag-in-keyboard-indicator") did not work for me (the .icons and similar process).

EDIT: The humanities themes do not have such icons (indicator-keyboard-XX.svg) under /usr/share/icons/Humanities/status/22/  If you want an icon of your preference to appear in those themes, just copy paste the icon in that folder, even if previously did not exist.

Regards!

---

