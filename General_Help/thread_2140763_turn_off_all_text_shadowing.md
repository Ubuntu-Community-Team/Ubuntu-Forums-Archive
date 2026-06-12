---
title: "turn off all text shadowing"
date: 2013-04-30
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2013-04-30
Anyone know a way to turn off all text shadowing? If not in one place, piecemeal would do. 

Shadowing often plays heck with readibility and I'm not aware of real evidence it EVER enhances it. It is probably worse for those of us who change colors and zoom to enhance readibility but the attached is a particularly egregious example of what shadowing can to to readibility with colors unmodified and in which zooming in our out does NOT make it better. This particular example is a pdf (pretty darned fscked format) opened in Firefox but the problem is not linited to this application or file type. I'm finding it a big problem in epubs read with fbreader, for example.

Thanks for reading and double thanks if you have suggestions.

---

### Post by vasa1 on 2013-04-30
> **Dreamer Fithp Apprentice said:**
> Anyone know a way to turn off all text shadowing? If not in one place, piecemeal would do. 

Shadowing often plays heck with readibility and I'm not aware of real evidence it EVER enhances it. ....

AFAIK, it isn't possible to turn off **all** text shadowing in one place if by **all** you mean **globally**. 

Also, I wouldn't know about pdf files and ereaders..

But I have turned off text shadows in regular web pages by including
```
* { text-shadow: none !important; }
``` in the CSS sheet for browsers.

I've done something similar in gtk themes but that's a little by trial and error. I search for "shade" or "shadow" in the relevant theme files and if I feel a line should be changed on commented out, I do so. 

Could you please provide a generally accessible link for me to download a small pdf file showing the shadow effect?

Edit: it looks like you're already in "high contrast" mode. So, the gtk/kde themes shouldn't be relevant for you.

---

### Post by Dreamer Fithp Apprentice on 2013-05-01
Thanks, Vasa1.> **vasa1 said:**
>  . . . I have turned off text shadows in regular web pages by including
```
* { text-shadow: none !important; }
``` in the CSS sheet for browsers.Strangely, I can't copy and paste that. I can't highlight it. Highlight and copy are working fine in other tabs. Shutting down Firefox and reopening it didn't change this. Oh, well, that's another subject.  Do you mean userContent.css or userChrome.css? Anyway I typed it in by hand to both, after some mysterious stuff in userChrome.css I must have pasted in there before (darn, I must remember to comment EVERYTHING immediately); and in the case of  userContent.css, it was empty, now it has that line, assuming I didn't make a typo. It hasn't have any effect on that pdf. I'll have to exeriment a bit with copies of the 2 files and restarting Firefox on some appropriate test page to evaluate it's effect on regualr html pages.


> **vasa1 said:**
> I've done something similar in gtk themes but that's a little by trial and error. I search for "shade" or "shadow" in the relevant theme files and if I feel a line should be changed on commented out, I do so. Thanks, I'll try that.

> **vasa1 said:**
> Could you please provide a generally accessible link for me to download a small pdf file showing the shadow effect?Here's the link I made the screenshot from:
[http://sphinxsai.com/CTVOL4/ct_pdf_vol_4/CT=38%20%281032-1035%29.pdf](http://sphinxsai.com/CTVOL4/ct_pdf_vol_4/CT=38%20%281032-1035%29.pdf)
And if I thought that part in the screenshot looked bad, it's because I hadn't look further down the page at the smaller type where the effect is much worse. Zooming in and out doesn't seem to effect it. I use the color toggle extension that checks and unchecks "let pages override my color choices" with choices set to foreground,white/background,black. The screenshot is with Color toggle in the "off" mode so to speak, i.e., with the "allow" box checked. When I toggle to unchecked the problem changes in character, with a lot more white, and on the whole, gets worse. I have to run now, but it occurs to me I should try it with allow checked and the prefs returned to default. The color toggle extension is touted as allowing you to switch between default and a custom color profile but if you look closely at what it does, that isn't quite true.

> **vasa1 said:**
> Edit: it looks like you're already in "high contrast" mode. So, the gtk/kde themes shouldn't be relevant for you.I don't follow you there, unless you're saying that the theme isn't gtk.  The basic point is look in the theme for statements about shadow that I could try modifying, right? Seems like it is worth a try in any kind of theme. Of course, that perception may be becaue I don't really know what I'm doing. I just tinker until I break it. :)

Thanks. Like whatshisname, I shall return.

---

### Post by vasa1 on 2013-05-02
Your thread is a real puzzle.
What are your computer specs (including the screen)?
What exactly is your operating system and which version is it? If it is indeed Lubuntu, what exactly do you choose at log in time?
What version of Firefox are you using?
What operating system theme are you using if it is not high contrast?
What theme are you using for Firefox?
What extensions have you installed in Firefox? Looks like you at least have Stylish installed.
Do you have Evince (aka Document Viewer) installed? If so, how does the same pdf file appear in that?

I viewed the pdf file you provided in Firefox's built-in pdf viewer. I didn't see any problems anywhere on the page right up to 287%.
I saved the pdf file to disk and then viewed it in Evince (aka Document Viewer). I didn't see any problems anywhere on the page right up to 400%.

---

### Post by Dreamer Fithp Apprentice on 2013-05-02
> **vasa1 said:**
> Your thread is a real puzzle.
What are your computer specs (including the screen)?Processor        : 2x Intel(R) Pentium(R) D CPU 3.40GHz
Memory        : 4047MB (803MB used)
-Display-
Resolution        : 1920x1080 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation

> **vasa1 said:**
> What exactly is your operating system and which version is it?Lubuntu Precise 64 bit installed from the regular CD; Mate DE added.
Kernel        : Linux 3.2.0-40-generic (x86_64)
Compiled        : #64-Ubuntu SMP Mon Mar 25 21:22:10 UTC 2013
C Library        : Unknown
Default C Compiler        : GNU C Compiler version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) 
Distribution        : Ubuntu 12.04.2 LTS
Desktop Environment        : Mate (Window Manager: Marco)


> **vasa1 said:**
> If it is indeed Lubuntu, what exactly do you choose at log in time?My regular user name.

> **vasa1 said:**
> What version of Firefox are you using?20.0

> **vasa1 said:**
> What operating system theme are you using if it is not high contrast?High Contrast Inverse

> **vasa1 said:**
> What theme are you using for Firefox?LCARStrek 2.17

> **vasa1 said:**
> What extensions have you installed in Firefox? Looks like you at least have Stylish installed.- Color toggle 0.15
- ColorfulTabs 18.5
- Config Descriptions 1.0
- Custom Buttons 0.0.5.5
- DownloadHelper 4.9.14
- DownThemAll! 2.0.16
- DownThemAll! AntiContainer 1.2.3
- Extension List Dumper 1.15.2
- Flashblock 1.5.17
- Prefsearch 0.2
- RightToClick 2.9.4
- Stylish 1.3.1
- Tab Kit - Tab Highlighter 0.1.0
- Theme Font & Size Changer 7.0
- Toolbar Buttons 1.0
- Ubuntu Firefox Modifications 2.6

> **vasa1 said:**
> Do you have Evince (aka Document Viewer) installed?Yes. And it is the default for pdfs.

> **vasa1 said:**
> If so, how does the same pdf file appear in that?The shadowing is dramatically less, almost invisible. Hmmm . . . Now I'm beginning to think this is a different phenomenon, perhaps not  shadowing at all in the sense of something done by software but some sort of artifact of the monitor. The "shadow" is offset directly to the right by about twice the width of the line in a character whereas I believe intentional text shadowing is, by convention, offset to the right AND DOWN. Perhaps specular reflection off some internal layer or double refraction through the topmost clear layer.  The appearance does not vary much with viewing angle though. I think this is the same thing I am annoyed by in epubs read in fbreader but it is much worse in the epubs. That might be attributable to color choices because I have fbreader set to red on black. Now that I'm attuned to thinking of it as possibly a separate phenomenon altogether, I'm peering closely at my Pluma (text editor, fork of Gedit) and I see, quite faintly, the same thing there. Possibly it is the faintest of the 3 because I have it set to "Cobalt" white on dark blue. Ahh, it's on lxtrminal, set to white on black, too. So faint I'd never have noticed it without looking hard for it. I think that proves it's not the same issue. Whatever the issue is in fbreader (and detectably, just barely, but not noticeably, present in Pluma and Lxtermial, now that I look hard for it) must be entirely different from the one with this pdf read in Firefox. So now, in light of that, I must reconsider, as to how many of the times I've been annoyed by "text shadowing" it was really some situation like the red on black fbreader that caused a problem always present, but normally too faint to be noticed, to be more extreme than it is in most circumstances. So now that I realize there ARE 2 different things going on I'll try to keep track of what does what under what circumstances. It could be that cases where the problem actually IS shadowing, like, presumably, this example of reading a black on white pdf in firefox are a minority too small to be concerned about. So, until I have accumulated some more data, evaluated in light of this this 2-separate-causes hypothesis, I wouldn't want you shouldn't spend too much effort figuring out what your Socratic questions have made me realize may be a rare glitch rather than a regular annoyance.

I'll experiment with colors some, and perhaps try different graphics card drivers until I have a clearer idea of what is going on. Thank you very much for your help.

---

### Post by vasa1 on 2013-05-02
> **Dreamer Fithp Apprentice said:**
> ...
My regular user name.
....
Couple of points ... Since you're using Lubuntu, I'd think that MATE is redundant. Doesn't Lubuntu give you that GNOME 2 look after all?

And when I asked about the choice at log-in, I was referring to the options one gets. IIRC, there's regular Lubuntu and Lubuntu for notebooks (or some such thing) and Openbox.

I also forgot to ask about whether you've installed the Microsoft fonts (ttf-mscorefonts-installer) via lubuntu-restricted-extras or done anything unusual font-wise.

Anyway, all the best in trouble-shooting :)

---

### Post by Dreamer Fithp Apprentice on 2013-05-02
> **vasa1 said:**
> Couple of points ... Since you're using Lubuntu, I'd think that MATE is redundant. Doesn't Lubuntu give you that GNOME 2 look after all?Not just a matter of casual appearance. Mate is far and away more functional for me than the DE that comes with Lubuntu or any of the officially approved DEs. This is a touchy issue in this forum. Praising Mate or dissing Gnome 3 will get you in almost as much hot water as telling people to enable the root account.  I sometimes wonder how much of this is  "fan boy syndrome" and how much is due to actual Canonical or Gnome developers here incognito with wounded pride. Mate is great. The panels are superior to the lxde panel and the Gnome 3 classic panel. Pcmanfm just plain sucks as a file manager. It crashes constantly on double clicking directories and is missing half the functionality of Nautilus or Caja. Leafpad is more like MS Notepad than Gedit, i.e., not as useful for writing scripts, and it isn't easily tweakable to readable color schemes. The menus aren't nearly as easy to edit in lxde, although it can be done. Mate is great. Honestly, I may switch to Debian Mint, just because that community isn't afflicted with such irrational hostility to Mate, even to the point of occasional lying. I'm not accusing you of any of this you understand, but if you peruse some old threads it's not hard to find what I'm talking about.

> **vasa1 said:**
> And when I asked about the choice at log-in, I was referring to the options one gets.Mate. The log in screen has such tiny fonts and low contrast colors that I don't normally actually read it. I just type my password in blind. So I forgot about there being a DE choice.

> **vasa1 said:**
> I also forgot to ask about whether you've installed the Microsoft fonts (ttf-mscorefonts-installer) via Lubuntu-restricted-extras or done anything unusual font-wise.Mscorefonts is not installed. I don't recall installing any fonts.

Thanks.

---

### Post by Dreamer Fithp Apprentice on 2013-06-18
For anyone experiencing similar problems, I'll update this. It is totally clear to me now that there ARE 2 seperate issues. The significant one seems to only occur with pdfs. The other issue is pretty minor and seems to  be derived from the physical characteristics of the monitor. With the pdfs I can run zoom in and out a bit and usually find some setting where the effect is minimal in any one part of the document. But the setting that minimizes the effect will be different in different in parts of the document with different fonts. So to read the darn thing I have to ride the zoom, repeatedly adjusting it. Pdfs suck anyway. From now on if I really need to read more than a few lines of a pdf I'll download and convert it.

---

