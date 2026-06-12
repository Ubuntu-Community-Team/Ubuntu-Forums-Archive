---
title: "use an input file to define types of files to find"
date: 2013-02-24
forum: General Help
---

### Post by twinturbotom on 2013-02-24
So I'm looking for all file types of pdf, doc, docx, ppt, pptx.  May even want to look for strings in the file name.    I think it would be most flexible to create an input file defining what I'm looking for.  Without the input file I'm  doing this ugly 1 liner:

```
 find -iname "*.pdf" -o -iname "*.docx" -o -iname "*.doc".....etc.
```I hate repeating myself, -iname .... -o... unacceptable!  There has to be a better way!  What is it?

My first thought is to create an input file that lists the types I want to keep:
```
*.pdf
*.doc
*.docx
*a_string*
```and load that into find; however I can't seem to get it right.  My redirecting IO, piping, and chaining skills are a work in progress!

Second thought is to do a better job of composing an expression:
*[pdf doc docx] 

but I'm doing something wrong with that too!

Any direction would be greatly appreciated.

In the end I'm deleted around 500GB of data that is NOT of the file types I'm finding here.  Thinking once I can find the stuff I need I should be able to pipe or invert the selected and pass it to a recursive rm.

THANKS!

---

