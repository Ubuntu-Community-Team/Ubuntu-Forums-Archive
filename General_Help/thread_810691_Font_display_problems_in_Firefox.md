---
title: "Font display problems in Firefox"
date: 2008-05-28
forum: General Help
---

### Post by Lime84 on 2008-05-28
I've noticed that some website fonts seem to be displayed incorrectly in Linux- they seem to be slightly larger than in Windows, which in many cases causes the website layout to get messed-up. The problem is particularly visible in case of small frames with text inside, parts of the text are either cut off or are sticking outside the frame.

Here's a small example, a fragment of the front page of Onet.pl- a large polish news portal. Notice how one of the lines doesn't fit entirely in the frame. 

[[IMG]http://img517.imageshack.us/img517/619/onetzb9.th.png[/IMG]](http://img517.imageshack.us/my.php?image=onetzb9.png)

This is just an example that was easiest to find, I get it all over the web, English sites included. So far, I've pinpointed Tahoma and Verdana to be causing the problem- removing them fixes the size issue. This is hardly a fix though, as these fonts are a must when browsing the web and disabling them makes many websites incredibly ugly or causes page layout issues of it's own.

---

### Post by Kinnza on 2008-05-28
yeah im having the same problem
i found that in edit-preferances-content
you can choose the font, and next to it there is an- advanced where you can choose differant fonts and sizes

problem is i couldnt find the right font that will look "normal"

---

### Post by Lime84 on 2008-05-28
Many websites override Firefox font settings, so they have no effect on them. Sure, you can untick the "allow pages to choose their own fonts" option, but this causes even bigger display problems.

---

### Post by Lime84 on 2008-05-30
Bump

---

### Post by kerry_s on 2008-05-30
sudo dpkg-reconfigure fontconfig-config

say no to bitmap, reboot

---

### Post by Lime84 on 2008-05-30
I've set it to Native>Automatic>No. Still nothing ](*,)

I know I can't make my web fonts look as good as on Windows, due to some patent or other, but I wish they'd at least be the same size.

---

### Post by kerry_s on 2008-05-30
you rebooted?

give me a screen shoot of your font settings in firefox.

like this

---

### Post by Lime84 on 2008-05-30
Yup, I rebooted. I've got windows settings on my Firefox, they don't matter though because websites where the problem is visible override them.

As I have mentioned before, only Verdana and Tahoma (most popular web fonts) seem to be the problem. If I uncheck the "allow the websites to choose their own fonts" option, the problem dissapears because the fonts get replaced with something else. Unfortunately, the "something else" is usually very bad looking and/or causes some other layout problem. Maybe this could get fixed if Verdana and Tahoma had replacements which are using the exact same measures, but I know of no such fonts.

---

### Post by Bakon Jarser on 2008-05-30
Maybe installing msttcorefonts will help.  I see Verdana is included.

sudo apt-get install msttcorefonts

---

### Post by Lime84 on 2008-05-30
I've got mstcorefonts, they are the cause of the problem, not the solution. Having them is still better than losing my eyesight to the Ubuntu defaults.

---

### Post by kerry_s on 2008-05-30
> **Lime84 said:**
> Yup, I rebooted. I've got windows settings on my Firefox, they don't matter though because websites where the problem is visible override them.

As I have mentioned before, only Verdana and Tahoma (most popular web fonts) seem to be the problem. If I uncheck the "allow the websites to choose their own fonts" option, the problem dissapears because the fonts get replaced with something else. Unfortunately, the "something else" is usually very bad looking and/or causes some other layout problem. Maybe this could get fixed if Verdana and Tahoma had replacements which are using the exact same measures, but I know of no such fonts.

you can use a ~/.fonts.conf to redirect the fonts to the fonts you want. you have to make it if you don't have 1 already.

here's what mine looks like:

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Helvetica</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Sans</string>
 </edit>
</match>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Verdana</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Sans</string>
 </edit>
</match>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Arial</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Sans</string>
 </edit>
</match>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Lucida</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Sans</string>
 </edit>
</match>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Times</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Roman</string>
 </edit>
</match>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Courier</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Mono</string>
 </edit>
</match>

</fontconfig>


```

---

### Post by snerd on 2009-05-30
I just use the View-Zoom-Zoom In-Zoom Out to get close to how I like it. Most webpage fonts are too small, and Zooming it once makes it better. Make sure the "Zoom Text Only" box is ticked first.

---

