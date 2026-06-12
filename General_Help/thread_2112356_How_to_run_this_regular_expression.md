---
title: "How to run this regular expression?"
date: 2013-02-04
forum: General Help
---

### Post by YourSurrogateGod on 2013-02-04
I have the following documentation at my job:
> Use Excel for Windows to export all sheets of the spreadsheet as HTML. Open each file in the saved *_files folder with a text editor. Use a Grep replace operation, replace
```
 <tr[^<]*<td[^>]*>\s*(.*?\r*.*?)(<span\s*style="mso-spacerun:\s*yes">\s*</span>)?\s*</td>\s*<td.*?td>\s*<td[^>]*>\s*(.*?\r*.*?)(<span\s+style="mso-spacerun:\s*yes">\s*</span>\s*)?</td>\s*(<td.*?</td>\s*)*?</tr>\s*
```

 with 
```
\1\t\3\n
```

 (Replace \r with \n if the above pattern doesn't match.) 

How would I run that regular expression?  What command could I use?

---

### Post by Impavidus on 2013-02-04
Use sed. Documentation can be found here: [http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

It should be something like```
sed -e 's/expression/replacement/' file >output
```I haven't completely checked the expression, but it seems you want to replace lines of an html table with lines of a tab separated table. What puzzles me is the presence of \1 and \3 in the replacement and the absence of \( and \) in the pattern.

---

### Post by steeldriver on 2013-02-04
> **Impavidus said:**
> What puzzles me is the presence of \1 and \3 in the replacement and the absence of \( and \) in the pattern.

I guess that would imply the expression assumes the use of gnu extended regex i.e. sed **-r** ?

---

### Post by Impavidus on 2013-02-04
Could be. I'm not that good at regular expressions.

---

### Post by dan000 on 2013-02-04
> **YourSurrogateGod said:**
> I have the following documentation at my job:

How would I run that regular expression?  What command could I use?

If I'm reading this right, what this is telling you to do is to save an xls to html, then use sed to convert that html file to a tsv file with only the first two columns.

What I don't understand is why in the world you wouldn't just save it as a tsv file straight from Excel (or LibreOffice). If I remember correctly, that's supported. All you would have to do would be delete any columns beyond the second one, and then save as, and choose Tab-separated values as the file type.

But don't take my word for it. I could be reading that regex wrong (although I'm pretty sure I'm not).

---

