---
title: "page numbers and index in open office writer?"
date: 2007-09-05
forum: General Help
---

### Post by larsdk on 2007-09-05
Hi there,

I quite often need to build a new document, which follows this scheme:

page 1: title, no page number
page 2: Table of contents, no page number
page 3: The first actual page, so therefore this should be "page 1" when inserting pagenumbers. 

In word I would do it using sections, but I just can't get it working right in OO writer.

Thanks in advance.
Lars

---

### Post by tszanon on 2007-09-05
> **larsdk said:**
> Hi there,

I quite often need to build a new document, which follows this scheme:

page 1: title, no page number
page 2: Table of contents, no page number
page 3: The first actual page, so therefore this should be "page 1" when inserting pagenumbers. 

In word I would do it using sections, but I just can't get it working right in OO writer.

Thanks in advance.
Lars

I don't remember exactly, but it has to do with page styles. One thing I learned from using Open Office is that everything should be done with styles, and the exceptions done manually. People usually don't bother using styles, but they're helpful.

So, it would be the case of creating a page style that has page numbers. After the index, insert a page break and inform in the dialog box that the new page style will be the one you created and inform also the new page number (1).

Using styles, creating the index will be very very easy. But right now I don't remember how to do it, I'm not at home.

---

### Post by larsdk on 2007-09-08
i have been trying to, but I can't really get it to work... Suggestions anyone?

---

### Post by tszanon on 2007-09-08
> **larsdk said:**
> i have been trying to, but I can't really get it to work... Suggestions anyone?
I'm giving the instructions based on a new document. If you have already written something, then you'll have to adapt them, but I don't think it would be hard.
1. Create the title page, as usual (attached image #1).
2. Leave a blank page for the index. It will be created later.
3. Create a new Page Style. Go to Format > Styles and Formatting. A dialog box will appear. Select the Page styles, like shown in the attached image #2. Right click the dialog box, click New.
4. Another dialog box will appear. Rename it as you wish, change whatever you need, and save it.
5. Place the cursor in the end of the index page (Ctrl + End). Insert a manual page break: Insert > Manual break..., then select Page break, select the new style, and the page number of the new page. See attached image #3. Click OK.
6. In the new page, insert Header (or Footer). Click Insert > Header > <new page style>.
7. Inside Header/Footer, insert page number. Click Insert > Fields > Page Number.

I guess that's what you want regarding page numbers.

**About the index**
When typing the headings, always use the styles Heading 1, Heading 2, and so on.
1. ABC (style heading 1)
1.1 jdjdjd (style heading 2)
1.2 khkhkh (style heading 2)
2. fkhoytott (heading 1)
2.1. iuiuiuiuiui (heading 2)
3. gkgkgk (heading 1)
....

Then, go back to that blank index page and click Insert > Indexes and Tables > Indexes and Tables...
In the dialog box, type the desired title, make sure the type is Table of Contents and click OK. You can make a lot of changes there, but I haven't done it in a long time, so I don't remember what could be done.

Hope it all works as expected! :)

---

### Post by eggdeng on 2007-09-08
For what you need to do, there is a simpler way. Go directly to the page where you want the numbering to start and choose Insert field -> Page number. Now situate the cursor in the field, right-click and choose fields from the pop-up menu. In the Offset box at the bottom, introduce a negative number. For example, if you are on the fourth page and you want the page number to read 1, put -3. You will find the numbering adjusts accordingly. 
I hope this is not hijacking the thread but does anyone know how to make footers appear on some pages and not on others?

---

### Post by tszanon on 2007-09-08
> **eggdeng said:**
> For what you need to do, there is a simpler way. Go directly to the page where you want the numbering to start and choose Insert field -> Page number. Now situate the cursor in the field, right-click and choose fields from the pop-up menu. In the Offset box at the bottom, introduce a negative number. For example, if you are on the fourth page and you want the page number to read 1, put -3. You will find the numbering adjusts accordingly.
Hey, that's much easier. Thanks!

> **eggdeng said:**
> I hope this is not hijacking the thread but does anyone know how to make footers appear on some pages and not on others?
When the document has multiple page styles, you can do that. You'll see that when inserting the header/footer, you must choose a page style, like in my example above. The pages formatted with the selected page style will have a footer, and the other will remain untouched.

---

### Post by eggdeng on 2007-09-09
I was hoping to avoid Page Styles but it does seem to be the only way. Thanks.

---

### Post by tszanon on 2007-09-09
> **eggdeng said:**
> I was hoping to avoid Page Styles but it does seem to be the only way. Thanks.
Maybe someone else has a better way of doing this, like you did before. But that's the only way I know of doing it. :)

---

### Post by vanadium on 2007-09-09
Do not avoid styles. Instead seek to use them. It are styles that allow you to automate the word processing. Page styles indeed are the tool to use here. In my opinion, this is one point where Ooo is much better than the awkward Word sections.

You know about the Openoffice.org user forum? [www.oooforum.org](www.oooforum.org) is an excellent place to discuss issues on using Open Office.

---

### Post by tszanon on 2007-09-09
> **vanadium said:**
> You know about the Openoffice.org user forum? [www.oooforum.org](www.oooforum.org) is an excellent place to discuss issues on using Open Office.
Thanks! I thought there would be an OOo forum, but never searched for it.

---

