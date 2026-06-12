---
title: "OO.o modifies what I type in a cell"
date: 2008-06-02
forum: General Help
---

### Post by commodore on 2008-06-02
I enter a date in my own formating to OO.o calc and OO.o just turns it into it's own format I don't like. I can't find anything in the options.

---

### Post by noynac on 2008-06-02
> **commodore said:**
> I enter a date in my own formating to OO.o calc and OO.o just turns it into it's own format I don't like. I can't find anything in the options.
Click on *Format > Cells > Numbers* and select the date format you prefer. You can also construct your own date format.

---

### Post by CameO73 on 2008-06-02
Select the cells you want formatted as your date. Then right-click and select Format Cells... (or use the Format -> Cells... menu)

In the Numbers tab (first one) select Category Date and your preferred Format. If the preset formats are not what you wanted, you could enter your own. Click on the Help button in the Format Cells dialog and click on the Number Format topic (at the bottom). There you'll find a list of psosible format codes.

---

### Post by commodore on 2008-06-02
Thanks for your help. Your solution works. I think it's really hard to find your way in OO.o and Office. I prefer programs which don't do everything for me.

---

### Post by commodore on 2008-06-10
Is there any way to make it default? Currently I have to format cells for each document.

---

### Post by niteshifter on 2008-06-10
Hi,

> Is there any way to make it default? Currently I have to format cells for each document.

Yes. In a fresh OOo Calc (not an existing document) press F11 (or click Format in the menu, then click Styles and Formatting). In the dialog that pops up are listed the various styles for  cells or page.

At the top of that dialog, left side are the selectors for cell and page styles. You want cell styles - it's the left one, but hover your cursor over it to be sure, then click it.

From there you can either make a completely new style or edit the Default by right clicking on Default, then click Edit. As to which to do, read the rest, paying attention to items 1 and 2, below.

Styles in OOo are normally tied to each *_document_*, not to the application (Calc or Writer), but each application can have a default template. So, here you have two options:

1. If you wish to leave OOo's default behavior alone, then make a new style. Simply save this blank sheet (as a template) and use it as a template for new sheets. If this is acceptable to you, stop here.

2. If you wish this new style to be used for every invocation of Calc from now on, you need to change the default template and edit the Default style. Instructions for changing the default template are in OOo's help - search for this phrase "Change default template" (sans quotes), it should take you right to the procedure to do this. It's a bit lengthy, but not complicated. It also describes how to reset the default template.

---

