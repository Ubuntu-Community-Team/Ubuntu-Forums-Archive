---
title: "Creating an ISO"
date: 2008-05-17
forum: General Help
---

### Post by dlbrando on 2008-05-17
Does anybody have a link to a good howto for creating an image cd out of a set of files.  I Downloaded rosetta stone but need to make iso cd's out of the individual languages.

---

### Post by Monicker on 2008-05-17
You should be able to do it with genisoimage:

genisoimage -o foo.iso /some/dir

---

### Post by ibuclaw on 2008-05-17
You can make one with Brasero.
When you click burn, switch the "Select Drive" tab from "RW Drive" to "File Image".

Else, you could always use "**mkisofs**" in the terminal.

```
mkisofs file1 file2 folder1 folder2 etc > output.iso
```
But that only makes a bog standard iso file (some characters are replaced or left out in the file-naming conventions).

For more infomation on mkisofs.
```
man genisoimage
```

Regards
Iain

---

### Post by HalPomeranz on 2008-05-17
For simple data CDs that can be shared between Linux/Unix/Windows/MacOS systems, mkisofs is extremely straightforward to use from the command-line:

mkisofs -J -r -o <ISOfilename> <list of files/dirs to include in image>

So, as an example:

mkisofs -J -r -o test.iso file1 file2 file3

If you want to create a CD with a complicated directory structure on it, your best bet is to build the directory setup on your local hard drive along with all the files you want to include in their proper places, and then just run mkisofs on the top-level directory (this is what I normally do).

Remember that you can check how your ISO turned out by mounting it locally:

sudo mount -o loop,ro <ISOfilename> /media/iso

You should then be able to browse the /media/iso directory and check that things ended up the way you expected.

---

### Post by ibuclaw on 2008-05-17
> **HalPomeranz said:**
> 
Remember that you can check how your ISO turned out by mounting it locally:

sudo mount -o loop,ro <ISOfilename> /media/iso

You should then be able to browse the /media/iso directory and check that things ended up the way you expected.

"ro" is not needed in the list of options, as ISO images are generally Read-Only by default.

```
sudo mount -o loop <ISOfilename> /media/iso
```
:lolflag:I've saved you the effect of three characters!!

Regards
Iain

---

### Post by ramjet_1953 on 2008-05-18
If you would rather use a GUI, instead of the command line, [COLOR="Blue"]ISO Master[/COLOR] will do it for you very nicely.

You can install it from the [COLOR="Blue"]Accessories[/COLOR] sub-menu in [COLOR="Blue"]Applications>Add/Remove[/COLOR], or by typing [COLOR="Red"]sudo apt-get install isomaster[/COLOR] in a terminal.

Regards,
Roger :cool:

---

