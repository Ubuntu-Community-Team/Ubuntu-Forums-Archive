---
title: "How can I edit PDF text?"
date: 2022-11-17
forum: General Help
---

### Post by Paddy Landau on 2022-11-17
I have a PDF, where one charity's name is misspelled, just once. Two letters were swapped: "Trussel" was spelled "Trussle".

I literally need to swap those two letters, and do nothing else to the PDF. I don't have access to the source document.

I've tried LibreOffice Draw, which unfortunately loses images.

I tried Master PDF Editor (available on Flatpak), and as far as I can tell, it doesn't have the functionality to edit text (if it does, please explain where I can find it!).

I loaded the PDF into Bless (a text and hex editor), but the text appears to have been encoded (probably compressed).

I've tried several other utilities, including online, and I haven't managed to find something that will let me do this one simple thing!

How can I do this, please? I use Ubuntu 22.04, but I'm happy to use Windows if necessary.

(If there isn't an answer, I know how to add an overlay text. I'm trying to avoid doing that, because it looks like hack; it needs to align perfectly, and of course I need to get the correct font, font size, font weight, and font style.)

Thank you

---

### Post by TheFu on 2022-11-17
PDF is meant to be a write-only file format.  That's part of the design.  Depending on how the document was created the text might be inside it as text or it might be an image.  ASCII-85 is the normal encoding, probably ZIP compressed, but I don't know.

Maybe try printing to a postscript file, find the text inside it, then re-convert that postscript back into PDF.  I've never done this, but it might work.

Besides that, you'll need to use an annotation, which is just a layer over the existing read-only document.  Annotations are displayed after a page is displayed, so there may be a perceptible delay.  When printing with annotations, the layers can be merged, but they will still be separate layers, but the display of the base document + swapped 2 characters likely won't be noticed, assuming you get the correct font and alignment into the new PDF.  'Xournal' is the tool I've used for stuff like this. Just be certain to "export" the new PDF.

Can you not just contact the person who created the document and get them to swap those characters?

---

### Post by Paddy Landau on 2022-11-17
> **TheFu said:**
> PDF is meant to be a write-only file format.
Interestingly, I have just discovered [Sejda]("https://www.sejda.com/"). It did exactly what I wanted&#8230;

But&#8230;

It moved the text to a different location! I am still trying to figure it out.
> **TheFu said:**
> Besides that, you'll need to use an annotation &#8230; 'Xournal' is the tool I've used for stuff like this.
I tried doing this with Xournal++ (the updated version of Xournal), and unfortunately it lost many of the images.
> **TheFu said:**
> Can you not just contact the person who created the document and get them to swap those characters?
No. He is in on holiday without his laptop, and I'm helping someone working under a tight deadline!

---

### Post by TheFu on 2022-11-17
Did you try the postscript method?

---

### Post by HermanAB on 2022-11-17
If all else fails, you can use Gimp photo editor.

---

### Post by Paddy Landau on 2022-11-17
Thanks, everyone. I found that I could get Xournal++ work in the end. I'm using that instead, even though it's not ideal.

GIMP isn't a good option, because it converts everything to images, so the text becomes non-searchable.

I started with Postscript, but then I realised that I have no clue how to edit a Postscript file!

---

### Post by TheFu on 2022-11-17
> **Paddy Landau said:**
> I started with Postscript, but then I realised that I have no clue how to edit a Postscript file!

I'd think that any text editor should work.

Postscript is a full language with page layout and fonts specified for ASCII text and images.  In theory, the same text, unencoded from PDF, would be inside the postscript file.  I haven't kept up with postscript.  PDF has been constantly changing to add more anti-security features since the mid-1990s when it was first introduced.  In fact, the original way to create PDF files was to print them using a postscript virtual printer printing and Acrobat Distiller accepted the .ps files as input to create PDF files.

---

### Post by Paddy Landau on 2022-11-17
> **TheFu said:**
> I'd think that any text editor should work.
...
Postscript is a full language with page layout and fonts specified for ASCII text and images...
That's interesting! I learn something every day. I'll try tomorrow when I'm back on my computer.

---

### Post by HermanAB on 2022-11-17
Since you only want to move a single character, you could try editing the file with hexedit.

---

### Post by Paddy Landau on 2022-11-18
> **HermanAB said:**
> Since you only want to move a single character, you could try editing the file with hexedit.
As mentioned in the OP, I already tried a hex editor, but the characters are encoded (probably compressed).
> **wjdanilich said:**
> Postscript is concise and expressive! Take some time to learn postscript and its unique syntax and semantics. I've used it for printing holiday envelops, merging addresses, automatically sizing the margin, dividing the print area into sub-regions, etc. Easy to maintain.
Thanks. I don't know that I have time to learn Postscript! But I'll keep it in mind.

---

### Post by Impavidus on 2022-11-18
Indeed in PostScript (on which PDF is based) this should be pretty easy, as PS is usually (but not always) uncompressed. Open the PS file in a text editor and look for the string, then swap the letters and save it. Strings in PS are in parentheses, so look for something like (Trussle). It may be in the file in a slightly different form, for example like (T) -2 s (russle), where the -2 s encodes some negative [kerning]("https://en.wikipedia.org/wiki/Kerning") between the T and the r. There may be multiple words and spaces in the string, but not if the text uses variable-width spaces. If there is kerning between or directly before the characters you want to swap, that may give a somewhat ugly result. Alignment of the rest of the document won't change.

I love playing with handcrafted PostScript. Machine-generated PostScript is usually not so readable.

(I wanted to post this last night, but then the site went down.)

---

### Post by Paddy Landau on 2022-11-18
> **Impavidus said:**
> … a slightly different form, for example like (T) -2 s (russle), where the -2 s encodes some negative [kerning]("https://en.wikipedia.org/wiki/Kerning") between the T and the r.
This is what helped me, thank you. It was separated into multiple segments as follows:
6(T)31(russ)3(l)3(e )

I used the Postscript method (a bit too late as the deadline was yesterday), and it worked like a charm. I've put this into my notes for future reference.

---

### Post by mIk3_08 on 2022-11-18
> **Paddy Landau said:**
> I have a PDF, where one charity's name is misspelled, just once. Two letters were swapped: "Trussel" was spelled "Trussle".

I literally need to swap those two letters, and do nothing else to the PDF. I don't have access to the source document.

I've tried LibreOffice Draw, which unfortunately loses images.

I tried Master PDF Editor (available on Flatpak), and as far as I can tell, it doesn't have the functionality to edit text (if it does, please explain where I can find it!).

I loaded the PDF into Bless (a text and hex editor), but the text appears to have been encoded (probably compressed).

I've tried several other utilities, including online, and I haven't managed to find something that will let me do this one simple thing!

How can I do this, please? I use Ubuntu 22.04, but I'm happy to use Windows if necessary.

(If there isn't an answer, I know how to add an overlay text. I'm trying to avoid doing that, because it looks like hack; it needs to align perfectly, and of course I need to get the correct font, font size, font weight, and font style.)

Thank you
Have you tried LibreOffice writer? I have tried my pdf file format to be open using LibreOffice writer and I successfully opened it and I am also amaze when I can also edit the file using LibreOffice writer on Linux Ubuntu 22.04 LTS. Regards and cheers.

---

### Post by Paddy Landau on 2022-11-18
> **mIk3_08 said:**
> Have you tried LibreOffice writer?
If I try to open with LO Writer, it automatically changes to LO Draw.

I don't know what's going on. With the PDF that I needed to change, LO Draw loses some of the images. But, with another very similar PDF, LO Draw works perfectly! I don't understand why.

---

### Post by mIk3_08 on 2022-11-19
> **Paddy Landau said:**
> If I try to open with LO Writer, it automatically changes to LO Draw.
 Even if you open first the LO Writer application then later open the pdf file using the LO Writer under the open menu file options of the LO writer, It still automatically changes the LO Writer to LO Draw? Regards and cheers

---

### Post by Paddy Landau on 2022-11-19
> **mIk3_08 said:**
> Even if you open first the LO Writer application then later open the pdf file using the LO Writer under the open menu file options of the LO writer, It still automatically changes the LO Writer to LO Draw? Regards and cheers
Yes, that is correct. When I do that, LO has the open window with an empty Writer document, and another window with the PDF opened in Draw.

If yours behaves differently, I would find that unusual. Try it again to see what happens. The screenshot shows the top of my window indicating which part of LO is open.

---

### Post by mIk3_08 on 2022-11-19
Try to delete libre office folder located at home/username/.config/ Let see what will happen. I think it will generate back when once you open the libreoffice writer again. Regards and cheers.
home/username/.config/libreoffice

---

### Post by Impavidus on 2022-11-19
Converting a pdf file into an editable libreoffice writer document isn't trivial. Maybe libreoffice writer sometimes succeeds and opens the file, and sometimes (on more complex pdfs) it fails and calls libreoffice draw to open the file.

---

### Post by Paddy Landau on 2022-11-19
> **mIk3_08 said:**
> Try to delete libre office folder…
No, I'm not going to do that. I'm perfectly happy with LO opening it in Draw, as that's what it's supposed to do.

---

### Post by maglin2 on 2022-11-19
I've tried about a dozen and not yet found a pdf I could open with LO Writer - LO Draw always opens instead. Pity though.

---

### Post by Paddy Landau on 2022-11-19
> **maglin2 said:**
> I've tried about a dozen and not yet found a pdf I could open with LO Writer - LO Draw always opens instead. Pity though.
Is it a pity, though? Draw has been programmed to deal with PDFs, and it wouldn't make sense to open it in Writer, which uses an entirely different internal structure. A PDF is much more like Draw than Writer, because it makes extensive use of blocks, unlike Writer.

---

### Post by #&amp;thj^% on 2022-11-19
> **Paddy Landau said:**
> I have a PDF, where one charity's name is misspelled, just once. Two letters were swapped: "Trussel" was spelled "Trussle".


I tried Master PDF Editor (available on Flatpak), and as far as I can tell, it doesn't have the functionality to edit text (if it does, please explain where I can find it!).



Paddy I was able to change/modify all text in any PDF i had availble.
With flatpak master pdf editor. Please see screenshot
```
flatpak list
Name           Application ID                  Version Branch     Installation
Master PDF Ed… …t.codeindustry.MasterPDFEditor 5.9.06  stable     system
Freedesktop P… org.freedesktop.Platform        22.08.3 22.08      system
Mesa           …reedesktop.Platform.GL.default 22.1.7  22.08      system
nvidia-470-14… ….Platform.GL.nvidia-470-141-03         1.4        system
Intel          …eedesktop.Platform.VAAPI.Intel         22.08      system
openh264       ….freedesktop.Platform.openh264 2.1.0   2.2.0      system
Arc-Dark Gtk … org.gtk.Gtk3theme.Arc-Dark              3.22       system
KDE Applicati… org.kde.Platform                        5.15-22.08 system
Firefox        org.mozilla.firefox             107.0   stable     system

```
I installed mine like, and this is  just if your method was different.
```
flatpak install flathub net.codeindustry.MasterPDFEditor
Looking for matches…
Required runtime for net.codeindustry.MasterPDFEditor/x86_64/stable (runtime/org.kde.Platform/x86_64/5.15-22.08) found in remote flathub
Do you want to install it? [Y/n]: 

net.codeindustry.MasterPDFEditor permissions:
    ipc       network              wayland              x11
    dri       file access [1]      dbus access [2]

    [1] xdg-config/kdeglobals:ro
    [2] com.canonical.AppMenu.Registrar, org.kde.KGlobalSettings,
        org.kde.kconfig.notify

```
The word I changed was Deep into DOOp
Was the PDF in question locked?

---

### Post by maglin2 on 2022-11-19
> **Paddy Landau said:**
> Is it a pity, though? 

Only from a purely personal standpoint - I am fairly familiar with use of LO Writer, but not at all familiar with LO Draw. 

This thread has been very helpful. I too had a pdf which required one word (part of an email address) changing. I have now done that in LO Draw, (again, too late, but something I was unaware I could easily do until I read this thread).

---

### Post by mIk3_08 on 2022-11-19
> **1fallen said:**
> MasterPDFEditor 
Thanks for sharing 1fallen. I think this is cool. I maybe install this later. Regards and cheers.

---

### Post by Paddy Landau on 2022-11-20
> **1fallen said:**
> Paddy I was able to change/modify all text in any PDF i had availble. With flatpak master pdf editor.
Unfortunately, I can't do this! I also installed the Flatpak version. But, when I try to save my changes, first it says that the free version will insert a watermark, which I accept; and then, when I save, it responds, "You are not allowed to use this function in the free version. The unregistered version will install a watermark."

Nothing is saved.

So, it doesn't work for me.
> **maglin2 said:**
> This thread has been very helpful.
Agreed!

---

### Post by #&amp;thj^% on 2022-11-20
> **Paddy Landau said:**
> Unfortunately, I can't do this! I also installed the Flatpak version. But, when I try to save my changes, first it says that the free version will insert a watermark, which I accept; and then, when I save, it responds, "You are not allowed to use this function in the free version. The unregistered 

Paddy it seems by no fault of mine, I sort of mislead you, My darling wife paid for the registration with out telling me, after I asked what she paid, well lets just say she is not sleeping in the big bed for a spell. Good Grief that's quite a price tag for something I'll only use on a few occasions.
I'm glad your good sport about this.

---

### Post by Paddy Landau on 2022-11-20
> **1fallen said:**
> Good Grief that's quite a price tag for something I'll only use on a few occasions.
I just had a look at the price. Ouch!

Please check that you don't have automatic renewal set on your card, because it's an annual fee, not a one-off.

The combination of Xournal++, free online resources, and LibreOffice Draw should satisfy most people's needs.

---

### Post by #&amp;thj^% on 2022-11-20
> **Paddy Landau said:**
> I just had a look at the price. Ouch!

Please check that you don't have automatic renewal set on your card, because it's an annual fee, not a one-off.

The combination of Xournal++, free online resources, and LibreOffice Draw should satisfy most people's needs.

Yes that is good info, I did set it to not renew, and it seems i missed the 30 day refund policy.
I'm going to get some Good back rubs for a while, as pay back...:lolflag:

---

