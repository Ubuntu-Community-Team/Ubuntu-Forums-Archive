---
title: "Hindi language display problems"
date: 2014-07-11
forum: General Help
---

### Post by nashtrik on 2014-07-11
Running Trusty, installed Hindi language pack but upon opening some website with hindi text the ,display doesn't show hindi letters properly. Any help shall be highly appreciated. Screenshot of a website with hindi text and the actual diplay is being attached. Thanks[ATTACH=CONFIG]254643[/ATTACH][ATTACH=CONFIG]254643[/ATTACH]

---

### Post by oldos2er on 2014-07-11
Moved to General Help.

---

### Post by nashtrik on 2014-07-11
whatever you conveyed or intended to convey just went above my head....Please elaborate

---

### Post by oldos2er on 2014-07-11
I moved your thread from Installation and Upgrades to General Help, since your question doesn't concern installing and/or upgrading Ubuntu.

---

### Post by varunendra on 2014-07-13
Hello nashtrik,

The problem you are having is a problem of how pdf's are handled by the browser plugins and is common for Linux and Windows. At least that's what I have seen so far.

Try downloading the file instead of directly opening it within the browser, and then open it using system application dedicated to reading PDF files. If the font used within the PDF is embedded in it, or if it is installed in your system, it should appear correctly then.

If still not displayed correctly, check the fonts that are used and whether they are embedded : "File > Properties > Font tab" in the default PDF viewer (evince) in Ubuntu.

By the way, as you can see in my profile details, I am an Indian and have first hand experience with Hindi fonts in PDF files in both Ubuntu and Windows.

**PS:**
Both screenshots you attached are same.

---

### Post by nashtrik on 2014-07-15
Thanks a lot for your reply varun...the document contains non-embeddable fonts which are substituted by the fontconfig and the display is incorrect. I have screenshots of all the fonts that are not the part of standard pdf format, kindly guide how to install these fonts. Thanks.[ATTACH=CONFIG]254734[/ATTACH][ATTACH=CONFIG]254735[/ATTACH][ATTACH=CONFIG]254736[/ATTACH][ATTACH=CONFIG]254737[/ATTACH][ATTACH=CONFIG]254738[/ATTACH]

---

### Post by varunendra on 2014-07-15
Just double-click the desired font to open it in Font-Viewer >> click on "Install" button.

To install multiple fonts at once, crate a directory in /usr/share/fonts/[COLOR="#0000CD"]<font type>[/COLOR]/ directory  >> copy the fonts into this directory >> run "**fc-cache -f -v**" command to update font cache. Some applications like libre-office may require you to log out >> re-login to recognize the new fonts.

For example, to copy a group of some true-type fonts, something like the following can be done (assuming your fonts are in a directory called "MyFonts" in your Home) -
```
cd MyFonts
sudo mkdir /usr/share/fonts/truetype/**[COLOR="#0000CD"]myfonts[/COLOR]**
sudo cp *.TTF /usr/share/fonts/truetype/myfonts
sudo fc-cache -f -v
```
Then log-off > re-login.

This will install all the fonts in your MyFonts directory into a newly created directory "myfonts" in /usr/share/fonts/truetype directory. Creating a new directory in the /usr/share... directory is not necessary, you could copy them right in the /usr/share/fonts/truetype directory, but it's just a good practice to keep your custom fonts in custom directories.

A detailed guide on this (I hope you won't need that after reading above) : [http://www.wikihow.com/Install-TrueType-Fonts-on-Ubuntu](http://www.wikihow.com/Install-TrueType-Fonts-on-Ubuntu)

---

### Post by nashtrik on 2014-07-20
Thanks Varun..now the display is perfect.

---

