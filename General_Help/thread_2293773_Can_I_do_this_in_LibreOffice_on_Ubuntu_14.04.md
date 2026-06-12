---
title: "Can I do this in LibreOffice on Ubuntu 14.04?"
date: 2015-09-07
forum: General Help
---

### Post by dave194 on 2015-09-07
Using OpenOffice in Ubuntu 10.10 I could open a text file as "WesternEurope Windows 1252 WinLatin" character set, edit it, and save in the same format.  But now that I'm on Ubuntu 14.04 I have only LibreOffice and would like to do the same, but can't see how to do it -- if possible.

Actually, SAVING the file in "WesternEurope Windows 1252 WinLatin" is not the problem -- I just save as "Text Encoded," check off the Edit Filter Settings box, and select the last option a the bottom:  "WesternEurope Windows 1252 WinLatin" -- but the problem is OPENING such files in the first place.   I have thousands of such files that were created on Windows, and when they open in Libre Office, the curly quotes and certain other characters display as "?" in a box.

Then when I successfully save as "WesternEurope Windows 1252 WinLatin" in LibreOffice, the "?" remains instead of the original curly quotes, etc.

Please advise?

Thanks,
Dave

---

### Post by SeijiSensei on 2015-09-08
Do a Google search for "libre office character encoding" and you'll see some answers.

Is there a reason you need to keep Win-1252 as the character set?  Have you tried saving in UTF-8 ( "Unicode") and seeing if that works for you and anyone you need to share documents with?  Most all modern computers now support UTF-8.  It's the standard in Ubuntu and other Linux distributions, and Windows supports it as well, though it might not be the default. 

You can change the character encoding of any file with the handy **iconv** command-line utility.  For instance,
```
iconv -f WINDOWS-1252 -t UTF-8 -o newfile.docx oldfile.docx
```
to translate from Win-1252 to UTF-8.  For a complete list of supported character sets, run the command "iconv -l".

---

### Post by dave194 on 2015-09-08
Thank you, [**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195").  That is very helpful information.  

I do not need to keep Win-1252 as the character set.  But I do need to preserve the curly quotes, hyphens, and so on.  I'm editing a couple hundred HTML files on a website with around a thousand pages, and they should look consistent when I'm done.

(I change the file extension from .htm to .txt before opening them, since LibreOffice automatically makes a lot of changes to HTML files, adding and re-arranging items under <head></head> and adding spacing, etc.  My editing involves changing only a handful of words in each file, and I don't want anything else to change.)

I don't have my Ubuntu laptop with me at the moment, but I will try what you suggest when I arrive home.

Thanks, very much!

---

### Post by SeijiSensei on 2015-09-08
If you really want platform-independent pages you should use [HTML entities]("http://dev.w3.org/html5/html-author/charref") like "&quot;", "&hyphen;" and the like.  The browser will translate the entities to their best representations given the available language and character set.

Some like &middot; and &mdash; are quite useful.  The curly quotes are &ldquo; and &rdquo;.

---

### Post by dave194 on 2015-09-08
Absolutely!  I agree.  And that is how I do it when I code pages myself.  Unfortunately these 1000+ pages I need to make minor edits to were created by a Microsoft Word process in Windows that saved a Word document as HTML, and the Microsoft process used the Win-1252 characters in the resulting HTML documents.  So, I'm stuck with them on this project.

---

### Post by SeijiSensei on 2015-09-08
Maybe a simple script can help?
```

#!/bin/sh
FILES=/path/to/the/files
NEW=/path/to/the/processed/files

cd $FILES
for f in *.htm
do
     iconv -f WINDOWS-1252 -t UTF-8 -o /tmp/$f $f
     sed 's/"/&quot;/g' < /tmp/$f > $NEW/$f
     rm -f /tmp/$f
done
exit 0

```
That's a quick-and-dirty method of converting all .htm files in the FILES directory to UTF-8 and replacing the double quote with its entity.  It will create corresponding files in the NEW directory.

---

### Post by dave194 on 2015-09-09
> **SeijiSensei said:**
> Do a Google search for "libre office character encoding" and you'll see some answers.

Is there a reason you need to keep Win-1252 as the character set?  Have you tried saving in UTF-8 ( "Unicode") and seeing if that works for you and anyone you need to share documents with?  Most all modern computers now support UTF-8.  It's the standard in Ubuntu and other Linux distributions, and Windows supports it as well, though it might not be the default. 

You can change the character encoding of any file with the handy **iconv** command-line utility.  For instance,
```
iconv -f WINDOWS-1252 -t UTF-8 -o newfile.docx oldfile.docx
```
to translate from Win-1252 to UTF-8.  For a complete list of supported character sets, run the command "iconv -l".
Thank you, very much!  That works perfectly.

Now I can do the editing in gedit -- which was my preference originally.  After running iconv, I just change the charset line at the beginning of the HTML file from iso-8859-1 to UTF-8.

Now the curly quotes, hyphens, etc., appear in gedit and in web browsers after saving.

Thanks very much!  You saved my day!

---

### Post by dave194 on 2015-09-09
> **SeijiSensei said:**
> Maybe a simple script can help?
```

#!/bin/sh
FILES=/path/to/the/files
NEW=/path/to/the/processed/files

cd $FILES
for f in *.htm
do
     iconv -f WINDOWS-1252 -t UTF-8 -o /tmp/$f $f
     sed 's/"/&quot;/g' < /tmp/$f > $NEW/$f
     rm -f /tmp/$f
done
exit 0

```
That's a quick-and-dirty method of converting all .htm files in the FILES directory to UTF-8 and replacing the double quote with its entity.  It will create corresponding files in the NEW directory.

Thank you, again, for this additional code.  It makes it much easier to work with multiple files.

Your help is greatly appreciated!!!

---

