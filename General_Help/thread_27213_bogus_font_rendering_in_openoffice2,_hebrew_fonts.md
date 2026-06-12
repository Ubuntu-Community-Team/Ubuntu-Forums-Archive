---
title: "bogus font rendering in openoffice2, hebrew fonts"
date: 2005-04-15
forum: General Help
---

### Post by mangar on 2005-04-15
when trying to write some stuff in hebrew, the fonts where non-antialiased, 
and got some strange artifacts.

culmus fonts, msstcorefonts are installed.
openoffice.org2 1.9.79.2 (the latest in hoary repo's)
nachlieli fonts, also happens when using miriam fonts.
i've also tried using the following command (after searching the forums):

fc-cache -v

the fonts are still bad.

attached:
the offending odt file (compresse with tgz) doc's are uploadable, but
not odt files?
a screenshot.

note:
  after minimizing and maximazing the writer window, the visual artifacts seen
  in the screenshot where removed, and the text where neglible again
  (although the content of the text is total nonsense)
  the fonts are still non-antialiased, so my guess is that it's a rendering error.

note2:
i've got the following error when trying to upload the files:
----------------------8<----------------------------------------------------
Server Error
The following error occurred:

[code=SERVER_RESPONSE_CLOSE] The server closed the connection while reading the response. Contact your system administrator. 
-----------------------8<-----------------------------------------------------
therefore, i'll use verbal explanation:
the fonts appear garbled: letters apear on top of each other, some parts of
the letters are missing, and the whole hebrew text is rendered unreadable.
also there's no antialiasing.
when the window is minimaized and maximaized, the artifacts disappear, and the
text is readable again.

the text i wrote in hebrew:
&#1489;&#1504;&#1504;&#1492; &#1489;&#1504;&#1504;&#1492; &#1489;&#1504;&#1504;&#1504;&#1504;&#1504;&#1492;!! &#1505;&#1490;&#1503; &#1512;&#1488;&#1513; &#1506;&#1497;&#1512;&#1497;&#1497;&#1514; &#1512;&#1506;&#1504;&#1504;&#1504;&#1504;&#1492;!!!

(there's and error with weakly idented letters with openoffice, like exlamation marks
"!" and the closure (?) marks: "(" ")", when using mixed rtl, ltr text (i.e. hebrew and emglish in the same sentence, like writing  " f() " -  the result will be " ()f ")

the meaning of the sentence :
 banana banana banananana!! the subordinate mayor of ra'a'nananana!!!!

which actually means nothing (it's from a tv show).


mangar

---

