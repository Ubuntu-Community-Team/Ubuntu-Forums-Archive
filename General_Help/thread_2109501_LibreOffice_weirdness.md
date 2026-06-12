---
title: "LibreOffice weirdness"
date: 2013-01-27
forum: General Help
---

### Post by Buntu Bunny on 2013-01-27
I'm working on a writing project, text is justified and first line indented. On some of the paragraphs, the first line of text appears aligned left, not justified. The settings are for the entire paragraph to be justified, and I cannot find anything amiss. What's weird, is that if I try to correct that first line myself, letters added or deleted are in different words, *not* where the cursor is. Insert function is off. This is not happening in all paragraphs, only some. Any ideas what's going on and how to correct it?

---

### Post by tgalati4 on 2013-01-27
Are you sure it's not a graphics problem?  Can you print to PDF then print out on paper and look at the alignment.  Compare the PDF on the screen with the printed output and note any differences.  Are you using a strange or custom font?

If you can, attach one page of the document with the defects to this thread and I will test with libreoffice that comes with 12.10.  It may be a bug that has been fixed in a newer version.  Only testing will tell.

---

### Post by Buntu Bunny on 2013-01-27
Tgalati4, I appreciate your response. Wouldn't you know it but I had trouble repeating the problem to comply with your request. My workaround for the problem paragraphs has been to cut and paste them to a simple text editor, and then back to LibreOffice. 

I tried to upload the page as a pdf, but it exceeds the forum's KB limit.  I'm just using Times New Roman, Arial for chapter titles, nothing fancy. Page size is 6 by 9 inches. How would I tell if it's a graphics problem?

Original text was in block paragraphs. The problem seems to occur if I format the paragraph first (justify the text), and then backspace it up to meet the preceding paragraph. When I hit the tab key, the first line remains left aligned. I'm not sure if that makes much sense, but it's never happened before. If I join the two paragraphs first and then hit tab for the indent, no problem.

I might should mention that I'm using Xfce, if that makes a difference.

---

### Post by Buntu Bunny on 2013-01-27
OK. I've got the one paragraph on one page. That should give you something to experiment with, and hopefully see what's going on.

---

### Post by Adam_GUI on 2013-01-27
I've tried opening your document.

Xubuntu 12.04.
XFCE 4.10
LibreOffice Version 3.6.4.3 (Build ID: 2ef5aff)

The page is 6x9, Times New Roman, 12PT font with half-inch margins all the way around.

Nothing looks wrong that I can see.  The entire page is set to be Justified.
I kept typing within the document and nothing acts out-of-place.

I started each new paragraph with a Tab indent and typed two additional blocks.

If the cursor is acting up as far as placement and typing, then I'm curious about your video card and if you've set anything odd as far as compiz settings.  I know that the issue could be a fluke or a version mis-match.  But, everything set up within the document as far as general formatting looks golden.

---

### Post by Buntu Bunny on 2013-01-28
> **Adam_GUI said:**
> I've tried opening your document....
If the cursor is acting up as far as placement and typing, then I'm curious about your video card and if you've set anything odd as far as compiz settings.  I know that the issue could be a fluke or a version mis-match.  But, everything set up within the document as far as general formatting looks golden.

Adam_GUI, thank you for taking the time to take a look. Your results do indeed make it sound like something with my system.

My video card is listed as  Advanced Micro Devices [AMD] nee ATI Device 9642. I've done nothing with the Compiz settings knowingly, I'm just a plain vanilla user!

The problem is only in the first line of some paragraphs; the ones I use backspace to remove blank lines between paragraphs. Actually, as soon as I backspace, the text returns to a left alignment, even if I've already formatted it justified. Also, so far, it has only occurred in this particular document. 

I think I'll try another chapter as a new document and see what happens.

---

### Post by HermanAB on 2013-01-28
I have seen this kind of nonsense.  My solution is to do a round trip conversion: Export the file to say MS .doc, then restart LO and import the doc file and save as ODF, then restart again and open the ODF.

---

### Post by Buntu Bunny on 2013-01-28
> **HermanAB said:**
> I have seen this kind of nonsense.  My solution is to do a round trip conversion: Export the file to say MS .doc, then restart LO and import the doc file and save as ODF, then restart again and open the ODF.

HermanAB, that's similar to what I've ended up doing, except I simply copy and paste the problem paragraph to a simple text editor, either Gedit or Mousepad. I find they remove all invisible code and formatting when going from one word processor to another. I'm glad to know though, that I'm not the only one who has experienced this problem!

---

### Post by Buntu Bunny on 2013-01-28
> **Adam_GUI said:**
> 
Xubuntu 12.04.
XFCE 4.10
LibreOffice Version 3.6.4.3 (Build ID: 2ef5aff)


Or, maybe it's the version of LibreOffice itself. I'm using

Xubuntu 12.04.
XFCE 4.10
LibreOffice Version 3.5.4.2 
Build ID: 350m1(Build:2)

---

### Post by Buntu Bunny on 2013-01-28
OK. So I tried to reproduce the problem in a fresh document. I copied and pasted from an .odt file to Leafpad, then to the a new .odt document. No problem with the first line in any of the paragraphs, but there is an added space at the end of some lines in some paragraphs. Screenshot attached.

Thanks to Adam_GUI's help, I don't think the problem is reproducible elsewhere, unless someone can try with the same LibreOffice version I'm using:  LibreOffice Version 3.5.4.2, Build ID: 350m1(Build:2) 

The workaround is to copy the problem paragraph to the text editor, and then copy and paste it back into the LibreOffice document. That seems to work, but is an annoying additional step. Not sure why it hasn't been happening before, but it's an odd problem now.

---

### Post by Impavidus on 2013-01-28
The offending line in the screenshot is justified, not left aligned, but has a trailing space. You can see that because the standard with of a space in this screenshot is about 4--5 pixels (visible in the last line of the paragraph), but spaces in the offending line have been widened to about 8--9 pixels. The trailing space is about 5 pixels in size, the space before the last word of that line (require) is also about 5 pixels. It seems that either the word "require" has been shifted to the left by about 5 pixels or the spaces before and after have been replaced by fixed width spaces, without preventing a line break after the fixed width space. Or some tab characters and strangly placed tab stops are mixing things up.

That's my analysis of the problem. I don't have a solution though.

---

### Post by Buntu Bunny on 2013-01-28
> **Impavidus said:**
> 
That's my analysis of the problem. I don't have a solution though.

It's appreciated nonetheless. The original problem can be seen in the attachment to comment #4. It's as though there is an indent on the right side as well as the left.

When I copied the paragraph in the screenshot to Leafpad, I could see where there was obviously some spacing issues, as though I'd hit the enter key in the middle of every other sentence (which I had not. I only hit enter for a new paragraph). When I corrected those, I could copy and paste the offending paragraph back into LibreOffice with no further problems; the text was perfectly justified on both sides, no spaces. At least I have a workaround. :)

---

### Post by tgalati4 on 2013-01-28
I opened the sample and I didn't see any problem.  I'm running 12.10 with libreoffice:

3.6.2.2.  It's obviously a problem with space and block justification handling.  It may be a bug that is fixed in the newer version.  Like most things, you have to justify the pain of using Windows versus the weird stuff in libre/open office.

I prefer simple, left justification, so that the "kerning" of the words does not change.  With block justification, some lines get stretched out and look strange.  This slows down reading and causes a distraction.

---

### Post by Buntu Bunny on 2013-01-28
Tgalati4, thanks for checking it out. It is a pain, but at least there's a workaround and even that is better than Windows. :)

---

### Post by Buntu Bunny on 2013-02-14
> **Impavidus said:**
> The offending line in the screenshot is justified, not left aligned, but has a trailing space....

Update. Simple fix, go to end of line and hit backspace. Tah-dah!

I may be slow to figure things out, but I usually do eventually. :)

---

