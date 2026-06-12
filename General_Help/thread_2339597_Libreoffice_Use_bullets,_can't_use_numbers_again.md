---
title: "Libreoffice: Use bullets, can't use numbers again"
date: 2016-10-10
forum: General Help
---

### Post by Bucky Ball on 2016-10-10
Hi all,

Odd problem in Libreoffice 5.1.4.2 on Xubuntu-core 16.04 which I'm currently digging about trying to solve.

Have a large document with numbered chapters. For example '1. Built Environment'. Problem is, if that chapter has a bulleted list in it, next time I try to number a chapter heading it gives me a bullet! Infuriating and really need to get around this somehow as working on a 100 page dissertation for my masters. 

I tried this as suggested on another thread: 'Tools> Autocorrect> Autocorrect Options> Options' and switched off the bullet and numbering options in there to no avail. Still the same and that's as far as I've got. Here's an example. I try to do this:

1 Hats
[LIST]
[*]Trilby
[*]Sombrero
[/LIST]
2 Coats

... then '2 Coats' will wind up as bulleted, not numbered. I've tried to trick it in numerous ways to no avail. I moved the numbering 'Down one level' (down one more and up and ...) but that didn't work either. Not to do with the spacing but something more obscure me thinks ...

Anyone familiar with this issue and any suggestions?

* Hmm. Just found this

> When in Writer: If you press the Enter key in an empty numbered paragraph, the numbering stops.

[From here]("https://help.libreoffice.org/5.0/Common/Turning_off_Bullets_and_Numbering_for_Individual_Paragraphs"). Wonder if that's got anything to do with it as the heading is numbered then there's a space under that before the text, which would create an emply paragraph switching numbering off. I'm guessing the same doesn't apply to bulleted lists as it's not happening for them. They won't go away!

---

### Post by Bucky Ball on 2016-10-11
Bump. Not getting anywhere with this and starting to wonder what the heck I should do. This is a 117 page document with a heap of chapter numbers I'm going to need to rethink if I can't get this working as it should ...

There have been other problems with numbering but this is the most significant and game-changing.

---

### Post by howefield on 2016-10-11
Are you formatting an already typed document or creating it now ?

I'm probably misunderstanding the issue but for me, a double press of the return key after bulleting the list switches off the bullets. It is a slightly newer LibreOffice but I doubt that has any bearing on it.

---

### Post by Bucky Ball on 2016-10-11
Creating the document. 40,000 word dissertation (currently being hacked back from 52,000!). 

Yes. Enter key three times, actually. Once to go to the next line after the last bullet point, once to get rid of the bullet that creates, once to create a space below the bulleted list to start a new line of text. When that chapter end, create next chapter title, add the chapter number by hitting the numbered list icon, right click and 'Continue previous numbering', the number turns into a bullet instead of the next chapter number. 

As I was researching it I started to think that maybe there was another way of doing this when I started reading about [Outline Numbering]("https://help.libreoffice.org/Writer/Outline_Numbering"). Have been playing around with it but can't work it out ... yet ... but I may also be barking up the wrong tree.

---

### Post by howefield on 2016-10-11
> **Bucky Ball said:**
> Yes. Enter key three times, actually. Once to go to the next line after the last bullet point, once to get rid of the bullet that creates, once to create a space below the bulleted list to start a new line of text.

Still 2 presses for me to reproduce what you have in the OP.

Anyway, good luck with your work.

---

### Post by Bucky Ball on 2016-10-11
Cheers, howefield, and thanks for trying. I see a chink of light and the project is actually, finally coming together. Two years later ... :)

PS: Yea, good example. At the end of 'sombrero' I hit enter and it give me the next bullet point ready to go. Hit enter again and it removes the bullet point and the tab stop and leaves me on the same line. Enter again and gives me a space and ready to start on the text again ('Coats', but when I number coats, gives me number 1, right click and 'continue previous numbering', gives me a bullet ... infuriatin'). ;)

---

### Post by Bucky Ball on 2016-10-12
We have bingo! Fixed, seems rock solid and I figured out something else on the way. How to get level numbering happening consistently and accurately (see my pic attachment down below).
____

So, in Libreoffice:

[LIST=1]
[*]View> Styles and Formatting> List styles> Numbering 1> right click and 'modify'. Format the numbering how you like it. Then ...
[*]
[*]Paragraph Style> Header> right click and 'modify'. Format as you like, but the important part is in the 'Outline and Numbering' tab, in the drop-down 'Numbering Style' list *choose 'Numbering 1'*, the numbering style you edited.
[*]
[*]So far so good. Now, put the cursor in front of the text you want numbered, go to the 'Paragraph Style' selection drop-box at the top-left in the toolbar and select 'Header'. You should get your header format with your numbering format. Apparently, this is what's called linking a list style with a paragraph style.
[/LIST]
When you hit return after it will put you on a numbered line. Hit return again, paragraph style, and numbering, off. Sweet! Create a bulleted list, stop bulleting, choose 'Header' in the paragraph style drop-down again, you'll get the correct number in the sequence. 

The numbering works exactly the same way as if you were using the regular numbered list function. Right click on it and you can move it up or down a level, restart numbering and the number will change accordingly. 

Note: I used 'Headers' and 'Numbering 1'. Guess there are all kinds of possibilities with further experimentation, e.g. changing 'Headers' and 'Numbers' to, say, 'Contents 1' and 'Lists 1'. Guess choosing the paragraph style 'Contents 1' would create a list from the selected text.
_____ 

Just finished going through 115 pages and all my headings are now numbered, present and correct at the right levels. Happy man. :)

This method is literally 'bullet proof'. You can put a bulleted list, and possibly a numbered list using the regular method, between the headings and it doesn't seem to bother things. Took me hours to work out so hope this helps someone along the trail.

*PS: To get chapter numbers to appear in your table of contents you need to do things slightly differently (using 'Heading 1', 'Heading 2', etc. instead of 'Header'), [so see my other thread here for how]("https://ubuntuforums.org/showthread.php?t=2339851&p=13556960&viewfull=1#post13556960").

---

