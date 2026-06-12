---
title: "Remove duplicate lines from a very large file"
date: 2018-10-13
forum: General Help
---

### Post by wildmanne39 on 2018-10-13
Hello, I have a large libreoffice file that I want to remove duplicate lines from, I am using this command:
```
awk '!x[$0]++' infile.odt > outfile.odt
```
it runs and completes but when I try to open the new file it is corrupted, any suggestions for a better way to do this, libreoffice can not repair the new file created.

Thanks

---

### Post by sudodus on 2018-10-13
Is there a lot of special formatting (by LibreOffice), or would it be an option to create a plain text file (ASCII file) and use **sort | uniq** or something else if you can't sort it without destroying it and after put it into LibreOffice again?

---

### Post by The Cog on 2018-10-13
Don't forget that .odt files are compressed archives with multiple files inside them. I would think the first thing to do is to extract the contents of the odt file and look to see which of the contents files contains the text that needs editing. After editing, you might be able to re-archive the file.

It might be easier to copy-paste the text into a text editor, do the work with the text file, and then re-import into a new odt document. This would of course lose all text properties like font, indentation etc. This is basically what sudodus describes.

---

### Post by wildmanne39 on 2018-10-13
I did not know that odt files are compressed, now it makes more sense. I tried before posting to do it wit awl in txt format and it outputted a couple of characters that was it, now I know why. No formatting is not a big issue. I will try when I get what is suggested when I get home I am on my cell at the moment.

---

### Post by The Cog on 2018-10-13
Sorry I can't remember the archive type, but I think it's something well known like zip or tar.gzip.

---

### Post by Holger_Gehrke on 2018-10-13
It's zip. The file with the actual content is 'content.xml'. Since there are no line endings in that file, you need to do some basic xml-parsing to do anything useful with it.

Holger

---

### Post by wildmanne39 on 2018-10-13
Thanks everyone! copying the file into my text editor then saving it and running the awk command I posted worked.

---

### Post by sudodus on 2018-10-13
Congratulations :KS

Edit:

And *thanks for the method with awk to remove duplicate lines* without sorting the lines. (I tested and it works for me too) :-)

---

### Post by wildmanne39 on 2018-10-13
Thank you sudodus!

---

