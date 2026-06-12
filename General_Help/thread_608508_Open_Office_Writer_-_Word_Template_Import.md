---
title: "Open Office Writer - Word Template Import"
date: 2007-11-10
forum: General Help
---

### Post by Jose Catre-Vandis on 2007-11-10
We are just in the process of re-branding at work, and are creating a set of word templates for use by everyone. I am the Linux user amongst loads of windows users. Our word templates use images in the background.

On opening or importing word templates into Open Office Writer I see no images in the background. It doesn't seem to matter whether the images are in the header on in the background or watermark. The same happens with a plain word document.

Is it possible to configure OOw to import these templates correctly, or is this a bridge too far?

Yes, I can create templates with images in OOw format, but this makes it more difficult for me to build and work on the setups with my other users? I need to work with the word templates.

---

### Post by Jose Catre-Vandis on 2007-11-11
bump?

---

### Post by Zill on 2007-11-11
I have no idea how to do this.  However, I have found the [OOo Forums]("http://www.oooforum.org/") very helpful and it may be worth posting your query there.

---

### Post by Jose Catre-Vandis on 2007-11-12
Think I have the answer here:

[http://openoffice.blogs.com/openoffice/2007/08/taking-your-mic.html](http://openoffice.blogs.com/openoffice/2007/08/taking-your-mic.html)

but when I run the document converter wizard in Gutsy I get a non resizable dialog that is not big enough to allow me to use it!:evil:

---

### Post by Zill on 2007-11-12
Sorry Jose but the link does not seem to work - it just goes to the OOo Search page :-(
What is the **name** of the thread?

---

### Post by Zill on 2007-11-12
Jose:  The OOo Document Converter Wizard opens fine on my Dapper PC.  I don't have any files to convert so didn't actually run the wizard but the dialog box seems to be normal size and quite usable.

Have you had problems with other OOo dialog boxes?

A related thread [http://ubuntuforums.org/archive/index.php/t-450304.html]("http://ubuntuforums.org/archive/index.php/t-450304.html")   suggests removing the folder ~/.openoffice.org2 to restore OOo window sizes to default so this might be worth a try - you would lose your settings though :-(
It might be worth renaming the folder temporarily and then trying to run the Document Converter Wizard to get your templates sorted out.

---

### Post by Jose Catre-Vandis on 2007-11-12
Link updated - sorry about that
[http://openoffice.blogs.com/openoffice/2007/08/taking-your-mic.html](http://openoffice.blogs.com/openoffice/2007/08/taking-your-mic.html)

---

### Post by Jose Catre-Vandis on 2007-11-12
> **Zill said:**
> Jose:  The OOo Document Converter Wizard opens fine on my Dapper PC.  I don't have any files to convert so didn't actually run the wizard but the dialog box seems to be normal size and quite usable.

Have you had problems with other OOo dialog boxes?

A related thread [http://ubuntuforums.org/archive/index.php/t-450304.html]("http://ubuntuforums.org/archive/index.php/t-450304.html")   suggests removing the folder ~/.openoffice.org2 to restore OOo window sizes to default so this might be worth a try - you would lose your settings though :-(
It might be worth renaming the folder temporarily and then trying to run the Document Converter Wizard to get your templates sorted out.

All the other wizard dialogs open correctly, this one is only @ 3x3cm square

[ATTACH]50018[/ATTACH]

and i tried renaming and creating new .officeorg2 folder but same problem. 

This is with OOo 2.3

Thanks for you help with this one :)

---

### Post by Jose Catre-Vandis on 2007-11-13
Now on my PC at work which uses OOo 2.2

Starting document converter wizard here finds an error in the macro:twisted:

```
Inadmissible value or data type
Index out of defined range
```

Looks like I am destined not to achieve in this effort!

---

### Post by Zill on 2007-11-13
Seems like Gutsy and OOo 2.3 do not play well together :-(

The original problem seems to be down to the VBA macros in the template(s), rather than the watermark etc.  Although OOo has its own BASIC, I haven't heard of any method of correctly importing MS VBA macros.  Maybe someone else can help with this...

Good luck :|

---

### Post by Jose Catre-Vandis on 2007-11-13
There are no macros in my template

---

### Post by Zill on 2007-11-13
Sorry Jose - I misunderstood.  Your reference to "error in the macro" refers to the OOo Document Converter code then?

I suggest you raise a bug report with OOo on this.

---

