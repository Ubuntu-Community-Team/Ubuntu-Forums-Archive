---
title: "possible to right click &quot;create new LibreOffice document&quot; in Xubuntu?"
date: 2014-08-23
forum: General Help
---

### Post by 777funk on 2014-08-23
I miss this feature in Windows (MS word) and regular Ubuntu. Is there a way to do this in Xubuntu?

---

### Post by Dennis N on 2014-08-23
You can set up a page with your preferred settings and save it in the Templates folder. Then, right-click on empty area in file manager window, and select "create document" and your LibreOffice template page will be one option for the new document.

---

### Post by 777funk on 2014-08-23
Thanks,
I'm not sure what the first part entails. What does set up a page with prefered settings mean? I assume in Open Office? 

I don't see create document as an option in the file manager (in Xubuntu). It was an option in Ubuntu though. In Xubuntu, I can only create a blank text editor document upon right clicking.

---

### Post by Elfy on 2014-08-23
Open writer - save that in Templates as writer.

Will appear in the right click menu as writer and give you option for a name when you open it.

---

### Post by JKyleOKC on 2014-08-23
> **777funk said:**
> I don't see create document as an option in the file manager (in Xubuntu). It was an option in Ubuntu though. In Xubuntu, I can only create a blank text editor document upon right clicking.Once you have added your own template to the $HOME/Templates directory, you'll get the list box when you select "Create document..." from Thunar's right-click menu. I have four such templates set up here. The list box will contain the names of every file in your Templates directory, with "New Empty File" (the blank text document you mention) listed at the bottom.

---

### Post by 777funk on 2014-08-26
I get the idea now. Thanks! I'm not sure however how to create the  Template in the $HOME/Templates directory. I see in LibreOffice Writer  that I can save as template. Does this save in the directory you speak  of or do I need to do something special? I tried creating a template in  Writer's default directory and it didn't seem to work for Thunar's right  click menu.

---

### Post by JKyleOKC on 2014-08-26
I don't use libreoffice myself; abiword does all that I need here. However the general rule for creating templates for Thunar is to use "Save as..." from the file menu of whatever program is involved, and be sure to navigate to the $HOME/Templates directory/folder. The actual file can be empty, in most cases, although if you have a preference for paragraph styles and so on you can configure them into the file before saving it -- and some programs don't let you save an empty file so you may need to put a word or two into it to get it saved. Once it's saved, though, you should be able to open it, delete those, and save it back under the same name.

I try to give the saved template a name that will identify the program I want to launch. For example, my template for Abiword is named "AbiWord.doc" and was saved in what abiword calls "Microsoft Word" format but is actually RTF. Any file created using this template will have the same configuration; the name-change dialog that pops up just before the file is created highlights "AbiWord" but not ".doc" so that I can give the new file a new name without affecting the final four characters -- unlike Windows, which highlights the entire name when renaming.

Remember, this usage of templates is implemented in Thunar itself and has nothing at all to do with LibreOffice itself, or what LibreOffice calls by the same name! It's an unfortunate bit of confusion, I fear.

---

### Post by 777funk on 2014-09-05
> **JKyleOKC said:**
> I don't use libreoffice myself; abiword does all that I need here. However the general rule for creating templates for Thunar is to use "Save as..." from the file menu of whatever program is involved, and be sure to navigate to the $HOME/Templates directory/folder. The actual file can be empty, in most cases, although if you have a preference for paragraph styles and so on you can configure them into the file before saving it -- and some programs don't let you save an empty file so you may need to put a word or two into it to get it saved. Once it's saved, though, you should be able to open it, delete those, and save it back under the same name.

I try to give the saved template a name that will identify the program I want to launch. For example, my template for Abiword is named "AbiWord.doc" and was saved in what abiword calls "Microsoft Word" format but is actually RTF. Any file created using this template will have the same configuration; the name-change dialog that pops up just before the file is created highlights "AbiWord" but not ".doc" so that I can give the new file a new name without affecting the final four characters -- unlike Windows, which highlights the entire name when renaming.

Remember, this usage of templates is implemented in Thunar itself and has nothing at all to do with LibreOffice itself, or what LibreOffice calls by the same name! It's an unfortunate bit of confusion, I fear.

Thanks for the detailed steps and clarification. It works!

---

### Post by JKyleOKC on 2014-09-05
Glad to hear it! Since my reply, I've installed LibreOffice and like it much more than AbiWord...

---

