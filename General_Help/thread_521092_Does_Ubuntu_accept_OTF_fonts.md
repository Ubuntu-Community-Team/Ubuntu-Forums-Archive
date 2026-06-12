---
title: "Does Ubuntu accept OTF fonts?"
date: 2007-08-09
forum: General Help
---

### Post by mjpatey on 2007-08-09
I've tried copying OTF fonts into a subdirectory of /var/lib/defoma/fontconfig.d/ (as root, of course)... and they go there, but do not show up as fonts in "System-->Preferences-->Fonts" or in any apps which use fonts.

I've also tried pasting them into my ~/.fonts directory, and though they copy there, still nothing happens.

Finally, I've also tried putting them in the fonts:/// directory (a.k.a. the "Font Folder"), but Ubuntu won't let me even copy them there (all the fonts in the folder have padlock icons on them, maybe meaning the contents of the folder can't be altered?)

So... am I to take this to mean that Ubuntu won't let me use OTF fonts, or am I just not putting them in the right place?

Thanks,

-Mark

---

### Post by linuxwizard on 2007-08-09
[https://help.ubuntu.com/community/FontInstallHowto](https://help.ubuntu.com/community/FontInstallHowto)

---

### Post by mjpatey on 2007-08-09
Thanks, that was a good tutorial for installing TTF fonts.  Any idea about OTF fonts?

I did just find this quick tutorial:

[http://www.stuermer.ch/blog/convert-otf-to-ttf-font-on-ubuntu.html](http://www.stuermer.ch/blog/convert-otf-to-ttf-font-on-ubuntu.html)

And it's actually solved my problem, albeit in a clunky, workaround-ish sort of way.  The script it tells you how to create will actually convert an OTF font to TTF format in FontForge, and it worked perfectly for me!

A note: as a commenter pointed out, the script as presented in the article contains those pretty "smart quotes" which need to be replaced manually in the .sh file with standard quotes, or the script will return an error.

Assuming at this point that Ubuntu doesn't deal directly with OTF fonts, this seems like a pretty good workaround.  Hope this helps someone else, too!

-Mark

---

### Post by kostkon on 2007-08-09
> **mjpatey said:**
> I've tried copying OTF fonts into a subdirectory of /var/lib/defoma/fontconfig.d/ (as root, of course)... and they go there, but do not show up as fonts in "System-->Preferences-->Fonts" or in any apps which use fonts.

I've also tried pasting them into my ~/.fonts directory, and though they copy there, still nothing happens.

Finally, I've also tried putting them in the fonts:/// directory (a.k.a. the "Font Folder"), but Ubuntu won't let me even copy them there (all the fonts in the folder have padlock icons on them, maybe meaning the contents of the folder can't be altered?)

So... am I to take this to mean that Ubuntu won't let me use OTF fonts, or am I just not putting them in the right place?

Thanks,

-Mark

Ubuntu can recognise and use OTF fonts just fine. I have many OTF fonts inside the *.fonts* folder and they work just fine.

But some applications like *OpenOffice* (I know, this is not good) and *Firefox* do not support such type of fonts thus they will not show up in these programs. On the contrary, you can use OTF fonts in *Gimp*, for example.

Now about the padlocks; some system-wide fonts belong to the *root* user and that's why they show up with padlocks on them, this is normal, don't worry.

You should be able to copy and paste them to your *.fonts* directory and as you said you are able to do it. Now, to solve the problem that they do not show up in applications that support OTF fonts, then there is a simple solution.

When you put some fonts into your fonts folder, the system automatically rebuilds the system *font cache*. For various reasons this sometimes does not happen so you have to do it manually. Thus, after you put some fonts into your *.fonts* folder, manually rebuild the *font cache* like this in a terminal:

```
sudo fc-cache -f -v
```

Then check if the fonts appear in a application that supports OTF fonts, like in *Gimp* or any other application you want to use and you believe it can work with them.

Thus, if you want to use them in an application that will support them, then you can keep them as OTF, and with a *font cache* rebuild I believe you will be OK. If you want to use them in a program that does not support them, then you should convert them to TTF.

---

### Post by mjpatey on 2007-08-09
You know, that's just about the most complete and helpful answer I've ever seen to any question on any forum anywhere.  Thank you!!!

After some more playing around last night, I did discover just what you said, that Gimp is fine with .OTF.  So I copied all the fonts into the alphabetical folders in /var/lib/defoma/fontconfig.d/ (since that was where I'd put the first one which worked), and voila!  I have working OTF fonts, at least in Gimp.  That's mostly where I wanted to be able to access them.

I did notice that the rest of the files in these directories are simply links to the font files, but putting actual OTF files in the same directory worked just fine regardless.

So pasting to the ~/.fonts directory should do it too... I'll give that a shot.

Thanks again for your help!!!

-Mark

---

### Post by Beyo on 2008-03-11
Unfortunately Open Office cannot handle some OTF fonts like Diavlo ( it is free font available from Exlibris foundry ). Hovewer Open Office under Windows recognizes this font perfectly...so , where is the trick in Ubuntu? is openoffice ubuntu version little broken?

---

