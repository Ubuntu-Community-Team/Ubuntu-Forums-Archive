---
title: "Table of contents won't show chapter numbers"
date: 2016-10-13
forum: General Help
---

### Post by Bucky Ball on 2016-10-13
Hi all,

Managed to get my head around [this problem]("https://ubuntuforums.org/showthread.php?t=2339597&p=13555800&viewfull=1#post13555800"), now on to the next. Before or after I fixed the previous problem I haven't been able to get this to work.

Create a table of contents no problems, get the chapter names in there no problem, but for the life of me can't get them to show numbers and tab stops. For instance, if I have the chapter headings '1. Built Environment', '1.1 Coffee Shops', '2. Muggings' in the text, it won't be reflected in the table of contents, I'm only getting:

> Built Environment
Coffee Shops
Muggings

... instead of:

> 1. Built Environment
[INDENT]1.1 Coffee Shops[/INDENT]
2. Muggings

Xubuntu 16.04, Libreoffice Writer 5.1.4.2 (see link at beginning of post for how I'm creating the chapter numbers in the body of the text).

---

### Post by dragonfly41 on 2016-10-14
Since you have no replies I'll throw in an idea.

Instead of considering the table of contents TOC usage inside LibreOffice Writer I suggest that pandoc.org might be useful in managing your 115 page document.

Is the original content written in markdown?   I recommend the Atom editor with Markdown Preview Plus plugin installed.

e.g. using pandoc command line
you might convert your odt document back to markdown (as the baseline)
then edit your markdown source adding TOC
and finally convert markdown to odt (including table of contents).

[http://pandoc.org/MANUAL.html](http://pandoc.org/MANUAL.html)

[http://pandoc.org/getting-started.html#step-7-command-line-options](http://pandoc.org/getting-started.html#step-7-command-line-options)

```

--toc, --table-of-contents
Include an automatically generated table of contents (or, in the case of latex, context, docx, andrst, an instruction to create one) in the output document. This option has no effect on man,docbook, docbook5, slidy, slideous, s5, or odt output.

--toc-depth=NUMBER
Specify the number of section levels to include in the table of contents. The default is 3 (which means that level 1, 2, and 3 headers will be listed in the contents).

```

One advantage of using pandoc is that you can convert your document into many different targets including slide presentations.

---

### Post by Bucky Ball on 2016-10-15
So this is how you do it. 
____

[LIST]
[*]The trick is Tools> Outline Numbering. Set that up, level 1, 2, 3, however many and how you want.
[*]
[*]Open Styles and Formatting (F11) and go to Paragraph Styles. Right click and 'modify' Heading 1. Go to 'Outline and Numbering' tab and you will notice it is greyed out but with the settings 'Level 1' and 'Outline Numbering'. (If you go to 'Outline and numbering' at 'Heading 2' it is set to 'Level 2: Outline Numbering'.) In other words, it corresponds to however you've set up Tools> Outline Numbering> Level 1, 2, 3 etc. 
[*]
[*]Type some text, put the cursor at the beginning, double click 'Heading 1' or select it from the paragraph style drop-down top left toolbar and you should get a heading number (chapter number) and the text should change to however you have formatting 'Heading 1' with 'Modify'.
[*]
[*]Now, Insert> Table of Contents and you should get a table of of contents with your text in it and with the correct number.
[/LIST]
My result is something like the first pic attached, exactly what I was after. :) 

The numbered headings in the text are formatted as 'Heading 1' and 'Heading 2' where appropriate and the TOC is *automatically* 'Contents 1' 'Contents 2' etc. You don't need to set that.

* Note: Any headings you don't want numbered, either in the text or TOC, format as 'Heading' or simply add to TOC as you would normally via Insert> Table of Contents and Index> Index entry. 

* It should also be noted that when creating a numbered heading, if you right click it and go 'down one level' numbering works as it should *if* you have set up Outline Numbering for level 2 *and* modified Heading 2 as the 'down one level' number will be 'heading 2' *not* 1. Confusing to start but getting simpler. 
____

It is a bit of a web. Heading 1 seems to be linked with Content 1 in the Table of Contents and both are linked to Outline Numbering *by default*. (This is why I was having trouble using 'Header' and not 'Heading 1'.) This took me forever to work out as I could not find this information clearly stated anywhere. Got there in the end.
____ 

So, to the current oddity. I saved the first file containing the first picture attached below as a template because I knew it was working and set up perfectly for what I wanted to do. Open that template and paste my 110 page dissertation in there, go through the whole thing changing what I had as 'Headers' and 'Contents 1' and all sorts in an attempt to get this to work to 'Heading 1'. At the end of all that, right click my TOC and 'Update' and ... it worked!!! To a point. 

Now I have spent three hours comparing the template with the new version of the dissertation made from the template as Level 2 numbering is appearing twice in the TOC. For instance.

3.1 3.1 Hats

... instead of 

3.1 Hats

See second pic attached below. No doubt it is something simple, obvious and right at the end of my nose. Think I'll post another thread  about that (once I've pulled remaining hair out) as my original issue here is solved and as per my last thread re. Libreoffice linked in my first post here: hope this saves a future traveller some time cos took me ages! ;)
____

* Update: Fixed oddity in second screenshot now. Right click TOC> Entries and make level 2 look like the third pic below. All levels should look like that for this layout. 

Problem was I'd chucked a bunch of hyperlinks and other things in there trying to fix it and couldn't work out how to remove them. You click the errant block and hit delete. Doh! :|

---

