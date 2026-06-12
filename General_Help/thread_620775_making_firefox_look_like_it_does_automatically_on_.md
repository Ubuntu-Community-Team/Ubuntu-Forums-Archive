---
title: "making firefox look like it does automatically on windows"
date: 2007-11-23
forum: General Help
---

### Post by melasaurus on 2007-11-23
OK. i've looked & looked up for threads on this topic.. & i can't find jack squat.  i don't want to "mess with" all of the visual settings (fonts & colors in edit>preferences) to make ff look how it did automatically on windows xp and such.  i want to just be given pre-set/written settings..  or something to download. haha :) thanks

---

### Post by dpar on 2007-11-23
I wouldn't know how it is supposed to look on Windows, but I would imagine it would use different fonts and such, so.......

If you don't want to mess with the fonts,etc., then I would guess that your sol.

---

### Post by sstusick on 2007-11-23
Firefox looks just like it does on Windows, on Ubuntu. Though, the theme you choose for GTK does effect how Firefox looks...you CAN download a different Firefox theme...and it will look that way regardless of what GTK theme you choose.

---

### Post by melasaurus on 2007-11-23
ahh! so gtk theme.. is that my computers theme? haha

---

### Post by melasaurus on 2007-11-23
bump bumpppppppp - why would gtk theme effect it?

---

### Post by sstusick on 2007-11-23
Yes, GTK theme is your GNOME Desktop's theme.

---

### Post by rune0077 on 2007-11-23
The default Firefox theme is the same, no matter if you run it on Windows or Linux or Mac (well, the icons are the same, the fonts might not be). If you set both your windows and linux theme to "Default Firefox" they really ought to look the same, I think.

---

### Post by Sukarn on 2007-11-24
> **rune0077 said:**
> The default Firefox theme is the same, no matter if you run it on Windows or Linux or Mac (well, the icons are the same, the fonts might not be). If you set both your windows and linux theme to "Default Firefox" they really ought to look the same, I think.

Except a few things I've noticed to be different -
[LIST=1]
[*]Default font is different (I think that on windows FF uses M$ fonts)
[*]Preferences button is under Edit in Linux and under Tools in Windows
[*]Autoscroll is enabled by default in windows, and disabled in Linux
[/LIST]

That's all I can think of from the top of my head at the moment.

Pardon my grammar.

---

### Post by sstusick on 2007-11-24
If you want the same fonts in Firefox/Linux, as in Firefox/Windows, then install the Windows fonts in Linux.

I believe there is a thread around here somewhere that explains how to do this process.

---

### Post by rune0077 on 2007-11-24
> **sstusick said:**
> If you want the same fonts in Firefox/Linux, as in Firefox/Windows, then install the Windows fonts in Linux.

I believe there is a thread around here somewhere that explains how to do this process.

You can do it from Synaptic. Just search "msttcorefont", then download them.

---

### Post by melasaurus on 2007-12-03
well thank you. i realized that by changing themes you can even change the way firefox's fonts and other things appear.

---

### Post by sstusick on 2007-12-06
> **rune0077 said:**
> You can do it from Synaptic. Just search "msttcorefont", then download them.
I just took my fonts from Windows and copied them over to Ubuntu :)

---

### Post by sstusick on 2007-12-06
> **melasaurus said:**
> well thank you. i realized that by changing themes you can even change the way firefox's fonts and other things appear.
Yep. 

It's all part of getting everyone to blend in ;)

---

### Post by pedro_cesar on 2007-12-10
I find that the firefox looks smoother and the fonts and -radio- buttons look better in Windows. Here are some steps you can follow to make your Ubuntu's firefox look smoother, to me; it looks even better than the window's after this is done.
> 
Open Firefox and go to Edit->Preferences->Content->Fonts & Colors->Advanced
where it says, serif, select 'Bitstream Vera Serif'
where it says, Sans-serif, select 'Bitsteam Vera Sans
where it says, Monospace, select 'Bitsteam Vers Sans Mono'

To improve Firefox, some people recommend installing the package mscorettfonts. However, this package makes extensive changes to your system. It puts Microsoft fonts everywhere (not just in Firefox). The Bitstream are as good or better and don't mess with your system. You can always reverse the changes if you don't like what you see.

--------------
I found this guide was posted originally [here]("http://ubuntuforums.org/showthread.php?t=91280")


Close Firefox

Now open a terminal and follow these steps:
-wget [http://grupenet.com/wp-content/uploads/2007/06/firefox-widgets.tar.gz](http://grupenet.com/wp-content/uploads/2007/06/firefox-widgets.tar.gz)
-go to your home folder and decompress the file: firefox-widgets.tar.gz
-sudo cp /usr/share/firefox/res/forms.css /usr/share/firefox/res/forms.css.backup
-cat firefox-form-widgets/res/forms-extra.css | sudo tee &#8211;append /usr/share/firefox/res/forms.css > /dev/null
-sudo cp -r firefox-form-widgets/res/form-widgets /usr/share/firefox/res/
-rm -rf firefox-form-widgets

--------------
I have been told that doesn't always works allright, I don't know why. So here I have another guide that should always work. It did for me.
**Note: **If you followed the previous steps, and they didn't work, uninstall theme before continuing
**How: **type "sudo cp /usr/share/firefox/res/forms.css.backup /usr/share/firefox/res/forms.css" in a terminal (without the quotes).

Now you're good to go...
-Download [this]("http://ubuntudaily.com/wp-content/uploads/firefox-widgets-10.tar.bz2") file and extract it
-In the terminal go to the extracted folder
-type ./install
-Choose option 1 to install (Note there are more options, you might want to see what they do in case you need them sometime)
-If asked, enter your password
-Restart Firefox

---

