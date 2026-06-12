---
title: "Document has XFA forms, currently unsupported."
date: 2015-10-27
forum: General Help
---

### Post by 2CV67 on 2015-10-27
I know this problem has been addressed several times previously, but I am asking again because some previous solutions seem to no longer work & I hope there may be some new solutions...

A lot of government agencies (French in my case) are pushing on-line methods (good!) & providing downloadable forms (good!) but which seem to require use of Adobe Acrobat Reader (less good!).

My latest example this week is this form for declaring sale of a vehicle:
[https://www.service-public.fr/particuliers/vosdroits/R20300](https://www.service-public.fr/particuliers/vosdroits/R20300)

When you try to download this form, you are warned it requires "Adobe Reader version 8.0 or +".

When you try to open it with Document Reader or Chromium or whatever, you get:
> To view the full contents of this document, you need a later version of the PDF viewer. You can upgrade to the latest version of Adobe Reader from [www.adobe.com/products/acrobat/readstep2.html](www.adobe.com/products/acrobat/readstep2.html)
For further support, go to [www.adobe.com/support/products/acrreader.html](www.adobe.com/support/products/acrreader.html)

I tried Okura, which gave me:
> Document has XFA forms, currently unsupported.

Is there ANY way, today, of reading, filling & saving these forms in Ubuntu?

The only option I have so far is using Windows...
I thought those days were over!

---

### Post by col48 on 2015-10-27
I'm not sure that clicking on the link invokes an attempt to download;  it looks to me as though it is trying to open the document.  If you were able to truly download it - that is to acquire a local copy on your computer, you could try a few other possibilities - for instance LibreOffice which has a PDF component.

The [English] Wikipedia entry for Acrobat...
[https://en.wikipedia.org/wiki/Adobe_Acrobat](https://en.wikipedia.org/wiki/Adobe_Acrobat)

... says the latest Linux version (as of 2013) is 9.5.5, so maybe it is possible to update?

---

### Post by HermanAB on 2015-10-27
Google for 'Master PDF Editor for Linux'.  

It is free for personal use and supports XFA forms.  

However, I have not used it, so while I found it for you, I cannot vouch for it.

---

### Post by QDR06VV9 on 2015-10-27
> **2CV67 said:**
> I know this problem has been addressed several times previously, but I am asking again because some previous solutions seem to no longer work & I hope there may be some new solutions...

A lot of government agencies (French in my case) are pushing on-line methods (good!) & providing downloadable forms (good!) but which seem to require use of Adobe Acrobat Reader (less good!).

My latest example this week is this form for declaring sale of a vehicle:
[https://www.service-public.fr/particuliers/vosdroits/R20300](https://www.service-public.fr/particuliers/vosdroits/R20300)

When you try to download this form, you are warned it requires "Adobe Reader version 8.0 or +".

When you try to open it with Document Reader or Chromium or whatever, you get:


I tried Okura, which gave me:


Is there ANY way, today, of reading, filling & saving these forms in Ubuntu?

The only option I have so far is using Windows...
I thought those days were over!
See HermanAB's post.

> **HermanAB said:**
> Google for 'Master PDF Editor for Linux'.  

It is free for personal use and supports XFA forms.  

However, I have not used it, so while I found it for you, I cannot vouch for it.
+1 I can verify [Master PDF]("https://code-industry.net/free-pdf-editor/") works, Downloaded and open with Master PDF. 
Use it quite often.
Kind Regards

---

### Post by 2CV67 on 2015-10-27
Thanks everybody for your suggestions!

col48: I did download it OK but couldn't open it.

HermanAB & runrickus: YES - Master PDF Editor works, thank you!

Not 100% yet, but close...

... some parts of the form are shown with Greek symbols instead of the normal French alphabet!

runrickus' screenshot shows even weirder symbols in places.
Opened with Acrobat, all the symbols are normal French (like English except accents).

I didn't search yet for any clues on that one.

---

### Post by 2CV67 on 2015-10-28
This is what the form should look like (Acrobat in W8.1)

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/acro_zpsyibszzub.jpg[/IMG]


And this is what you see with Master PDF Editor in Ubuntu

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/mpe_zpsq85kdrbk.jpg[/IMG]

Clearly unusable at the moment.

I will continue to dig...

---

### Post by col48 on 2015-10-29
Even in the French text, the fonts are not quite the same, and different fonts are used in different places in the form.  Could it be that Master PDF Editor could not find all the fonts it needs in the Ubuntu side? I understand that sometimes fonts may be embedded in the document and sometimes not - in the latter case there could be a difference between the Windows and the Ubuntu installations.

Please keep digging - the solution will be informative.

Bonne chance, mon ami.

---

### Post by 2CV67 on 2015-10-29
I contacted Code Industry Limited (supplier of MPE) & they quickly replied, asking for a copy of the form to investigate.

I will update this thread when/if there is anything new.

---

### Post by QDR06VV9 on 2015-10-29
I am not sure if you are opposed to using Adobe Acro Reader?
And am using Arch today but works well enough.
To install: It used to be in the Canonical Partners repository, But I never use it, But check there first.
If not see this for Trusty.
[http://ubuntuhandbook.org/index.php/2014/04/install-adobe-reader-ubuntu-1404/](http://ubuntuhandbook.org/index.php/2014/04/install-adobe-reader-ubuntu-1404/)
Hope this works for you! I also attached a Screen to show!
Kind Regards

---

### Post by 2CV67 on 2015-10-31
Runrickus - I will cover Adobe Reader in a separate post.

I got a very rapid reply from Code Industry Ltd (Thanks!) which I include here:

> This happens because you don't have required fonts installed in your system.
...
Master PDF Editor doesn't install additional fonts into system like Adobe does.
In Master PDF Editor press Ctrl + D and go to Fonts tab to see what fonts are used in the file and install them in your system.

If it's possible, please, post this solution on the forum, so this may help somebody else.
Anyways, we'll put our efforts to avoid these issues in next versions.

Nice approach!

Ctrl+D gives me:

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/fonts_zpsvirmluzx.jpg[/IMG]

I looked all through SynApt "font" without finding those fonts.
So now my problem is how to find & install them...

---

### Post by 2CV67 on 2015-10-31
Adobe Reader in Ubuntu?

If Adobe Reader had still been available via the repositories, I would have installed it, in spite of some Linuxian scruples, because it does actually work.
But it is no longer available "officially".
As a rule, I only install things I can get GUI through SynApt.

Adobe/Linux seems to be a cul-de-sac now, so even if I could install it today, I would expect to need an alternative soon, wouldn't I?

I found this article for 14.04 (but 15.04 etc??):
[http://ubuntuhandbook.org/index.php/2014/04/install-adobe-reader-ubuntu-1404/](http://ubuntuhandbook.org/index.php/2014/04/install-adobe-reader-ubuntu-1404/)

That lead me to this one for 14.10:
[http://ubuntuhandbook.org/index.php/2014/10/install-adobe-reader-ubuntu-14-10/](http://ubuntuhandbook.org/index.php/2014/10/install-adobe-reader-ubuntu-14-10/)
The comments of dissatisfied "customers" is not encouraging!

I have a "spare" 14.04LTS so I tried the above 14.04 article procedure there:
- Downloaded Adobe Reader 9.5.5 enu (concerned it was i386 vs my 64-bit system...)
- Installed Gdebi
- Install Reader with Gdebi (which pulled in 61 dependencies & froze after installation & couldn't be closed, even with Alt+F4)
Reader showed OK in the Dash but didn't open at all.
No reaction when trying to open the .pdf file with Reader.

I then installed the libraries mentioned in point #4 of the article & everything works OK, but I don't know why.
I really don't enjoy blindly following instructions to fiddle with my system!

Anyway, I then returned to 15.04 & again followed the instructions from the 14.04 article:
- Install Reader with Gdebi (which only pulled in 17 dependencies, but still froze afterwards).
Reader showed immediately in the Dash & opened OK.
Reader was not available as an option when right-clicking on the .pdf file to "Open with...".
After a reboot, Reader was available to "Open with" & worked OK.
No problem with fonts, filling, etc.

I wondered if the right fonts were now available for Master PDF Editor, but no - it still shows greek symbols.

So now I have Adobe Reader & it works perfectly.
But do I need something else in reserve for the future (when forms will require Adobe Reader 10 or +)?

---

### Post by QDR06VV9 on 2015-10-31
I had already checked the fonts that were in the Downloaded  PDF, and downloaded and installed them but it made no difference.

][IMG]http://i.imgur.com/NEraW3Y.png[/IMG]

The only good result was the Adobe Reader.
I would have never blindly recommended a link for a how to with out doing it myself first.
And for Newer Adobe versions we can only hope some one keeps it current.
Kind Regards

---

### Post by Ralph L on 2015-10-31
I too am struggling with XFA pdf forms.  I downloaded the free linux version and, while it opened the form, most of the menu and toolbar items were grayed out and didn't work.  I couldn't even copy text from the form.  Are you using the "paid for" version or the free version??  If you are using the free version, is it necessary to "unlock" or "enable" the form in some way so that the menu and toolbar items work???

---

### Post by QDR06VV9 on 2015-10-31
> **Ralph L said:**
> I too am struggling with XFA pdf forms.  I downloaded the free linux version and, while it opened the form, most of the menu and toolbar items were grayed out and didn't work.  I couldn't even copy text from the form.  Are you using the "paid for" version or the free version??  If you are using the free version, is it necessary to "unlock" or "enable" the form in some way so that the menu and toolbar items work???
Did you follow this?
[http://ubuntuhandbook.org/index.php/2014/04/install-adobe-reader-ubuntu-1404/](http://ubuntuhandbook.org/index.php/2014/04/install-adobe-reader-ubuntu-1404/)

[COLOR=#000000]After a reboot, Reader was available to "Open with"[/COLOR]

---

### Post by col48 on 2015-10-31
If a particular (non-embedded) font is unavailable, is there a way to nominate a substitute font to whatever code is interpreting the PDF?  Maybe, at worst, a universal default?

I suspect not, but I think it is a question worth asking!

---

### Post by QDR06VV9 on 2015-10-31
Fonts in PDF files.
[http://www.prepressure.com/pdf/basics/fonts](http://www.prepressure.com/pdf/basics/fonts)

---

