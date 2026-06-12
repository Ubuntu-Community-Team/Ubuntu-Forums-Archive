---
title: "Unable to search unencrypted pdf file"
date: 2008-02-01
forum: General Help
---

### Post by kung fu buntu on 2008-02-01
I'm unable to search [this]("http://www.csse.uwa.edu.au/~angie/thesis.pdf") pdf file. It has happened with other files before but I ignored the issue at the time.

What does this file has different? How can I search it?

I'm using kpdf.

Thank you.

---

### Post by dcstar on 2008-02-02
> **kung fu buntu said:**
> I'm unable to search [this]("http://www.csse.uwa.edu.au/~angie/thesis.pdf") pdf file. It has happened with other files before but I ignored the issue at the time.

What does this file has different? How can I search it?

I'm using kpdf.

Thank you.

That is because it looks like this PDF only contains converted images, not any actual text.

I'd say it has been done to make it harder to steal the content.

---

### Post by kung fu buntu on 2008-02-02
I don't think its that.

In kdpf when you select a region it shows either "copy text" or "copy image". And with this pdf file it says "copy text".

If it were to protect content it would be encrypted. IMO this is some other weird problem... maybe due to fonts used or software versions.

---

### Post by kung fu buntu on 2008-02-05
For future reference:
[http://bugs.kde.org/show_bug.cgi?id=157236](http://bugs.kde.org/show_bug.cgi?id=157236)

I'm still to figure out how to fix this problem...

---

### Post by seventhc on 2008-02-05
I just opened this file with evince, and I could not highlight in the same way I can with other pdf files. This is what got when I copied. I was only trying to copy a few words but obviously got more since I had no real control as in normal pdf files.
```
                                                   &#338;&#8249; &#8240; &#8222;&#8225; &#8222;&#402;
                                                   kk&#8249;0&#352;d 0&#710;&#8224;&#8230;pmj &#8218;
                                  &#8364;iku ~}|(z{&#8482;yww$&#8482; k`U&#402;rp&#8217;gonmki&#8225;f
                                    g               x vu ts q j ljhg
                                                         d e&#8482;
                       &#8220;uG&#8218;h u X &#732;I t ©Y X SVU&#8211;i¢&#8221;&#8220;QVI X g&#8217;&#8216;HHFD
                                 Q &#8212; TQIT &#8226; p b &#710; G T G Y &#8240; T E
                                                           p gb
                                       &#710; bI b E &#8224; p b
                                        SE W 4g&#8218;PhG &#8225;&#8222;gb X `Q e b &#8230;
                                           pb T &#8364;Ta E b
                                           i&#8222;UT X Ug&#402;T SQ X &#8218;p
              T Y
      &#8364;HYPG X UTHPYG&#8364;H5yT X urxfwpib d HgvT e UPTG fd X `Q UW ir7g§igHE fd
                                         Q aYu Y e T t sbq pb hbb e
                                            T EScS2U``U4UT UW
                                                  Q bQ aTQYTI X
                                                PIRPIVUT SRPIHFD
                                                   G GI EQ G E
                                   # ) ¥ £     6 £ ¥ %   @ £
                                    ¤¤C©§5B ¤¤¢¢A¢ 
8 6 % #' 1 )' # £ ¥ %   ¦ % ¥   !   ¥ £   &#776; ¦ £ £ ¡
 97543 20(¤% ¤¤¢&¤&¢$# "   &#776; ©§¤¥ ¤¢ 

```So I would think that it is this file being protected in some way.
edit: Just read the bug report so forget what I said. ;)

---

### Post by wanchai on 2008-03-19
This is apparently a problem with GhostScript and fonts, see here:
[http://www.oooforum.org/forum/viewtopic.phtml?t=15299&highlight=]("http://www.oooforum.org/forum/viewtopic.phtml?t=15299&highlight=")

In OpenOffice.org you will get searchable PDF, no matter what type of font you use, if you convert to PDF. But when you print, either via CUPS or using extendedPDF, you'll get this gibberish as posted above unless you use PostScript fonts.

---

### Post by wanchai on 2008-03-20
Here are some examples: One PDF was printed from OOo (searching does not work), the other one was generated directly from OOo (searching works). The difference seems to be in the encoding of the fonts. Adobe Reader 8 shows the encoding as "built-in" for the file written by OOo, whereas in the Ghostscript output it is "Ansi" for the Type 1 (PostScript) and "Custom" for the TrueType font.

Why print? Because I need to control which headings get transformed into bookmarks. The OOo plugin *extendedPDF* does a good job on that, but it generates PDF via printing to PS and running ghostscript.

---

### Post by ryanhaigh on 2008-03-20
I know it isn't what your looking for but you may want to look at an optical character recognition program if you are having to deal with these issues on a regular basis. It certainly isn't perfect but may be useful.

---

