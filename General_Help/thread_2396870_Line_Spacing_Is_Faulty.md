---
title: "Line Spacing Is Faulty"
date: 2018-07-22
forum: General Help
---

### Post by skyesharica on 2018-07-22
Hi Friends.  I've just done a clean install of Ubuntu 18.04 LTS.  I am writing a book.  I'm having difficulty with line spacing.  Nothing seems to fix it.  The settings don't work.  Occasionally I am 1.5 line spacing instead of single line spacing.

---

### Post by HermanAB on 2018-07-22
Well, which editor are you using???

---

### Post by skyesharica on 2018-07-22
> **HermanAB said:**
> Well, which editor are you using???

Thanks Herman.  I'm not sure what you mean by editor - LibreOffice Writer is what I'm using?

---

### Post by The Cog on 2018-07-22
I know of two ways to edit the line spacing. 

Firstly, you can edit the paragraph's style by clicking the paragraph and choosing the menu pull-down Styles -> Edit Style, or by right-clicking a paragraph and in the menu select Styles -> Edit Style... This allows you to change the base style the paragraph uses, and this change will propogate to all paragraphs in the document that use that style. This is the way I recommend styling your document. Re-styling the entire book is then really quick and easy.

Secondly, you can directly change the format of a paragraph by placing the cursor somewhere in the paragraph (or highlighting several paragraphs) then right-click and choose Paragraph from the menu. This setting applies only to the selected paragraphs and overrides the properties configured in the paragraph style. 

My guess is that you have a mixture of the two in your document, and I think it's probably best to find the paragraphs that have overridden the chosen style and choose Styles->Clear Direct Formatting (Ctrl-M shortcut).

You can create new styles easily and you probably only want a handful of styles throughout your book. Only use direct formatting when you want a small and unusual change from the normal syles. It took me a whle to realise when I started to use LibreOffice that the styles you see text drawn in are a combination of the chosen style in the toolbar but possibly overriden by local direct formatting changes. Once I got the hang of it I think it's great. But you have to realise that changing a paragraph style in the toolbar might not change what you see because direct format has already overridden the styles value.

---

### Post by Holger_Gehrke on 2018-07-22
Time for an excerpt from the "Word Processing 101" lecture ...

Do not touch the "Enter"-key ! It does not do what you think it does. Enter produces an end-of-paragraph not an end-of-line. When writing normally, just go on typing when reaching the right margin, the program will break lines on its own without you doing anything. You only hit enter when you want to end a paragraph. The program will insert a bit of horizontal space to mark the end of one paragraph and the beginning of the next. If you actually need to end a line but not the paragraph (for example when writing an address or verses ...) use shift-enter which inserts a line-break. You can use ctrl-F10 or View->Formatting Marks in the menu or the Button in the tool bar marked with what look like a horizontally mirrored capital "P" with a double vertical stroke to see various special marks in the text (spaces, tabulators, paragraph breaks, line breaks, page breaks ...).

Holger

---

### Post by skyesharica on 2018-07-23
> **The Cog said:**
> I know of two ways to edit the line spacing. 

Firstly, you can edit the paragraph's style by clicking the paragraph and choosing the menu pull-down Styles -> Edit Style, or by right-clicking a paragraph and in the menu select Styles -> Edit Style... This allows you to change the base style the paragraph uses, and this change will propogate to all paragraphs in the document that use that style. This is the way I recommend styling your document. Re-styling the entire book is then really quick and easy.

Secondly, you can directly change the format of a paragraph by placing the cursor somewhere in the paragraph (or highlighting several paragraphs) then right-click and choose Paragraph from the menu. This setting applies only to the selected paragraphs and overrides the properties configured in the paragraph style. 

My guess is that you have a mixture of the two in your document, and I think it's probably best to find the paragraphs that have overridden the chosen style and choose Styles->Clear Direct Formatting (Ctrl-M shortcut).

You can create new styles easily and you probably only want a handful of styles throughout your book. Only use direct formatting when you want a small and unusual change from the normal syles. It took me a whle to realise when I started to use LibreOffice that the styles you see text drawn in are a combination of the chosen style in the toolbar but possibly overriden by local direct formatting changes. Once I got the hang of it I think it's great. But you have to realise that changing a paragraph style in the toolbar might not change what you see because direct format has already overridden the styles value.


Thanks but no matter what I do I get a different result every time I try.  The program is clearly very faulty.  If I fiddle around with 'Clear Direct Formatting' I finally get a result, but it takes a lot of trying and re-trying.

> **Holger_Gehrke said:**
> Time for an excerpt from the "Word Processing 101" lecture ...

Do not touch the "Enter"-key ! It does not do what you think it does. Enter produces an end-of-paragraph not an end-of-line. When writing normally, just go on typing when reaching the right margin, the program will break lines on its own without you doing anything. You only hit enter when you want to end a paragraph. The program will insert a bit of horizontal space to mark the end of one paragraph and the beginning of the next. If you actually need to end a line but not the paragraph (for example when writing an address or verses ...) use shift-enter which inserts a line-break. You can use ctrl-F10 or View->Formatting Marks in the menu or the Button in the tool bar marked with what look like a horizontally mirrored capital "P" with a double vertical stroke to see various special marks in the text (spaces, tabulators, paragraph breaks, line breaks, page breaks ...).

Holger

Thanks for that tip.  Yes, View->Formatting Marks does work.  It might help.  Thanks.

---

### Post by HermanAB on 2018-07-23
In general, first write the document, then format it.

If the document has to go to a printer, then they would want it with as little formatting as possible, since whatever formatting you do will cause problems for them.

If the document has to become an electronic book, then you probably would want to use a different program to format it.

---

### Post by The Cog on 2018-07-23
The program is not faulty, but it can take a little getting used to.  I guess your struggling with it has left a misxure of direct formatting and maybe a mixture of styles, and maybe a paragraph breaks where you don't expect them. It may be worth pressing Ctrl-A to select the entire document, then menu Clear Direct Formatting, then select one style (maybe Text Body) to ensure that the entire document is on just one known style. Then you can hunt for unwanted paragraph or missing breaks more easily. Then change the style of the titles and other bits that shouldn't be Text Body (but by clicking the paragraph and choosing a style from the list, not using direct formatting). That should get the document in a good position for editing and prettying up the individual styles. For anything you are going to use more than a couple of times, create a new style. Finally, use direct formatting on the few little bits that need to be different.

---

### Post by skyesharica on 2018-07-23
> **HermanAB said:**
> In general, first write the document, then format it.

If the document has to go to a printer, then they would want it with as little formatting as possible, since whatever formatting you do will cause problems for them.

If the document has to become an electronic book, then you probably would want to use a different program to format it.

Oh thanks for that.  Oh no - I've used a great deal of italics, bold, and underlining.  It's really essential for the book.  So is that the case with all publishers?  Can't they include your formatting, if it's important?  Publishing must be very advanced these days, with computers now.  Or is it a printing press problem?

---

### Post by HermanAB on 2018-07-23
"Can't they include your formatting, if it's important?"
Find a publisher and read their guidelines - BEFORE you start.

---

### Post by skyesharica on 2018-07-23
> **HermanAB said:**
> In general, first write the document, then format it.

If the document has to go to a printer, then they would want it with as little formatting as possible, since whatever formatting you do will cause problems for them.

If the document has to become an electronic book, then you probably would want to use a different program to format it.

Thankyou so much for the tip.  I've just researched publishing formatting and you're absolutely right.  It's best I know now.  It's a lot of change but I'm so appreciative of the warning.  Thanks again Herman.  :popcorn:

> **HermanAB said:**
> "Can't they include your formatting, if it's important?"
Find a publisher and read their guidelines - BEFORE you start.

Thanks Herman.  They seem to be pretty tough about it.  Only a very small amount of books are accepted - they are looking for quick ways to toss away submissions.  Thanks again for the so important tip.  I do tend to format all the time.  I've been criticized here for it.  I've learned not to do it in forums either.  I use to think I was cheering people up with lovely colours and fonts.  Oh well, you live and learn.  :D

> **The Cog said:**
> I know of two ways to edit the line spacing. 

Firstly, you can edit the paragraph's style by clicking the paragraph and choosing the menu pull-down Styles -> Edit Style, or by right-clicking a paragraph and in the menu select Styles -> Edit Style... This allows you to change the base style the paragraph uses, and this change will propogate to all paragraphs in the document that use that style. This is the way I recommend styling your document. Re-styling the entire book is then really quick and easy.

Secondly, you can directly change the format of a paragraph by placing the cursor somewhere in the paragraph (or highlighting several paragraphs) then right-click and choose Paragraph from the menu. This setting applies only to the selected paragraphs and overrides the properties configured in the paragraph style. 

My guess is that you have a mixture of the two in your document, and I think it's probably best to find the paragraphs that have overridden the chosen style and choose Styles->Clear Direct Formatting (Ctrl-M shortcut).

You can create new styles easily and you probably only want a handful of styles throughout your book. Only use direct formatting when you want a small and unusual change from the normal syles. It took me a whle to realise when I started to use LibreOffice that the styles you see text drawn in are a combination of the chosen style in the toolbar but possibly overriden by local direct formatting changes. Once I got the hang of it I think it's great. But you have to realise that changing a paragraph style in the toolbar might not change what you see because direct format has already overridden the styles value.

Thanks again for all of this.  As it turns out I have to use double line spacing for the whole book - for publishers.  To be honest I found your post a bit hard to understand.  It's here now.  So I can return to it and really study it.  It might make or break my document.  As the spacings and all sorts of things are pre-requisites for publishers.  Thanks again for your lengthy trouble.  :D

> **Holger_Gehrke said:**
> Time for an excerpt from the "Word Processing 101" lecture ...

Do not touch the "Enter"-key ! It does not do what you think it does. Enter produces an end-of-paragraph not an end-of-line. When writing normally, just go on typing when reaching the right margin, the program will break lines on its own without you doing anything. You only hit enter when you want to end a paragraph. The program will insert a bit of horizontal space to mark the end of one paragraph and the beginning of the next. If you actually need to end a line but not the paragraph (for example when writing an address or verses ...) use shift-enter which inserts a line-break. You can use ctrl-F10 or View->Formatting Marks in the menu or the Button in the tool bar marked with what look like a horizontally mirrored capital "P" with a double vertical stroke to see various special marks in the text (spaces, tabulators, paragraph breaks, line breaks, page breaks ...).

Holger

Thanks again Holger.  I'll study this more closely.  I have just found out that formatting is extremely important, or your book could be very very easily tossed by publishers.  :D

---

