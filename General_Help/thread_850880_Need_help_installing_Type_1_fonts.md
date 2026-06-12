---
title: "Need help installing Type 1 fonts"
date: 2008-07-06
forum: General Help
---

### Post by kahlil88 on 2008-07-06
I have some Adobe Type 1 fonts that won't install (Garamond specifically). I tried placing them in the ~/.fonts directory and refreshing the font cache, but that didn't work. I tried restarting and I still can't use them.

---

### Post by Elfy on 2008-07-06
Found this - it might help - make sure to read both posts, worked on feisty apparently.

[http://ubuntuforums.org/showthread.php?t=452955](http://ubuntuforums.org/showthread.php?t=452955)

---

### Post by kahlil88 on 2008-07-06
Doesn't seem to work...just got a bunch of errors. Can I convert them to TrueType fonts, or is there perhaps a free alternative designed to be compatible with Adobe Garamond?

---

### Post by kerry_s on 2008-07-06
for the adobe fonts you need the gs to Xll font program, i forget what it's called.
open synaptic and click on the right side to high light a line so it will search as you type, type gs
look for the 1 that says it provides type 1 to x11.

sorry, i'm not on linux right now.

okay, it's called gsfonts-x11, so:
**sudo apt-get install gsfonts-x11**

---

### Post by Elfy on 2008-07-06
> gsfonts-x11Didn't know you could do that in synaptic, useful :)

---

### Post by kahlil88 on 2008-07-06
Alrighty, I installed it. What next?

---

### Post by kerry_s on 2008-07-06
> **kahlil88 said:**
> Alrighty, I installed it. What next?

restart X, logout and press ctrl+alt+backspace

---

### Post by kahlil88 on 2008-07-06
So what's this gsfonts-x11 thing supposed to do exactly?

---

### Post by kerry_s on 2008-07-06
> **kahlil88 said:**
> So what's this gsfonts-x11 thing supposed to do exactly?

make type 1 available to X, aka: so it shows up in the font selection menu so you can select and use.

---

### Post by kahlil88 on 2008-07-06
Still doesn't seem to be working...I don't really care so much about *using* the Adobe Garamond fonts. I just have some PDFs that look really terrible because the fonts aren't installed.

---

### Post by kerry_s on 2008-07-06
try this>
open a terminal to your ~/.fonts folder where you have the font:

cd ~/.fonts
mkfontdir
mkfontscale

---

### Post by kahlil88 on 2008-07-06
> **kerry_s said:**
> open a terminal to your ~/.fonts folder where you have the font:

cd ~/.fonts
mkfontdir
mkfontscale

I've done that a few times, but no luck so far.

---

### Post by kerry_s on 2008-07-06
okay, i assuming your checking the pdf since thats where you want to use the font.

try checking if the font is in the font selection list of other programs, that will tell us if the font is detected and usable.

if it is usable in other programs, then we need to look at the pdf viewer.
i need to know which pdf viewer your using.
not sure where to go from there. :confused:

---

### Post by kahlil88 on 2008-07-06
I'm using [Evince]("http://www.gnome.org/projects/evince") 2.22.2, and it looks like OpenOffice finds the font. I noticed that the PDF refers to it as **AGaramond** rather than **Adobe Garamond**. Is there a way to alias the font?

---

### Post by kerry_s on 2008-07-06
of course there is, it's linux. :)

you need to create a .fonts.conf file if you don't have 1 already:

**editor ~/.fonts.conf**
put

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

<match target="pattern" name="family">
		<test name="family" qual="any"><string>AGaramond </string></test>
		<edit name="family" mode="assign">
			<string>Adobe Garamond</string>
		</edit>
	</match>

</fontconfig>

---

### Post by kahlil88 on 2008-07-06
Awesome, it worked like a charm! There are a few fonts in the PDF that are still showing up weird, but I'm pretty sure it's because they're Semibold, as **mkfontscale** returned errors with the semibold fonts:
```
Unknown Type 1 weight "Semibold"
Couldn't determine weight for gdsbi___.pfb
Unknown Type 1 weight "Semibold"
Couldn't determine weight for gdsb____.pfb
```

---

### Post by kerry_s on 2008-07-06
hmmm, not sure what to do about that.
let me look it up and get back to you.

i got and idea, of how to fix it by adding more alias's, but i can't remember the exact wording. what you want to do is give a weight to those fonts(gdsbi,gdsb).

---

### Post by kerry_s on 2008-07-06
okay, i got a headache. :( i'm going to lay down, if you want to try to get this on your own, here is the manual:
[http://fontconfig.org/fontconfig-user.html](http://fontconfig.org/fontconfig-user.html)

---

### Post by kerry_s on 2008-07-06
sorry, to much reading is killing me. :)

back to your problem, try this:

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

<match target="pattern" name="family">
<test name="family" qual="any"><string>AGaramond</string></test>
<edit name="family" mode="assign">
<string>Adobe Garamond</string>
</edit>
</match>

<match target="font">
<test name="family" qual="any">
<string>gdsb</string>
</test>
<test compare="more_eq" name="weight"><int>140</int></test>
<edit mode="assign" name="embolden"><bool>true</bool></edit>
</match>
<match target="font">
<test name="family" qual="any">
<string>gdsbi</string>
</test>
<test compare="more_eq" name="slant"><int>80</int></test>
<edit mode="assign" name="matrix">
<times>
<name>matrix</name>
<matrix>
<double>1</double><double>0.2</double>
<double>0</double><double>1</double>
</matrix>
</times>
</edit>
</match>


</fontconfig> 


i'm just going off what you put, but i think you might have to change "gdsb,gdsbi" to the actual font name "Adobe Garamond" or "AGaramond" not sure what will work, your going to have to play with it. good luck

---

### Post by gerrit on 2008-07-11
Hi,

I'm trying to install Agaramond too, and found every one speaking about the directory **~/.fonts**  . My problem is that I cannot find that dir! (using Ubuntu 8.04 & openoffice 2.4) Where is this dir?


I can find a dir with type1 fonts all right ( /usr/share/fonts/type1/gsfonts ) and I tried to put the font in there, but it did not work, even when restarting the whole system.

regards, Gerrit

---

### Post by Elfy on 2008-07-11
That's a hidden folder in home - got your home in nautilus - do Ctrl+H - can you see it now if not make it - it must have the . at front of the name.

---

### Post by kerry_s on 2008-07-11
> **forestpixie said:**
> That's a hidden folder in home - got your home in nautilus - do Ctrl+H - can you see it now if not make it - it must have the . at front of the name.

if you don't have 1 already you need to make it.

---

### Post by Elfy on 2008-07-11
That's what I said ;)

> can you see it now if not make it 

---

### Post by kerry_s on 2008-07-11
> **forestpixie said:**
> That's what I said ;)

i was still waking up, didn't have coffee yet. :lolflag:
sorry!

---

### Post by gerrit on 2008-07-12
Hi,
I created ~/.fonts and put the font-files in there, then ran the two commands you specified in post #11 (mkfontdir and mkfontscale) but even then I cannot find Agaramond in OpenOffice. Any idea what to do next?

Another question: I see a lot of fonts in openOffice, also some true types I installed from the repository, so one way or an other it looks like this ~/.fonts dir is not crucial for using "external fonts", or am I wrong?

Further, installing them in the users home dir would not make those fonts unavailable when logging in as a different user?

regards, Gerrit

---

### Post by gerrit on 2008-07-13
Strange, *Agaramond* now appears in Gimp and Inkscape, but **not** in OpenOffice; even after restarting Gnome. Did not check that before, since I'm using OOo most of the time.(Before I installed TTF fonts from the repository and they *do* appear in OpenOffice all right.)

So the problem here seems to be with OOo in stead off with "fonts in general".


Any ideas, please?

---

