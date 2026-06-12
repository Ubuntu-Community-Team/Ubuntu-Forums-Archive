---
title: "pdftk and unlocking mutipule pdfs"
date: 2008-07-05
forum: General Help
---

### Post by Mikecore on 2008-07-05
I have been trying to write a command that will unlock several pdf files in a directory. I tried the find command and piped it to pdftk but it keeps reporting back that it could not open the file. But if I actually type in the file name instead of using wildcards its works just fine.

```

find . -name '*.pdf' | pdftk *.pdf input_pw ******* output open_*.pdf 

```

any help would be great I have been tryng to figure this out all day reading the man and other examples. found where it will merge several files at once but nothing on unlocking then all at once

---

### Post by dcstar on 2008-07-05
> **Mikecore said:**
> I have been trying to write a command that will unlock several pdf files in a directory. I tried the find command and piped it to pdftk but it keeps reporting back that it could not open the file. But if I actually type in the file name instead of using wildcards its works just fine.

```

find . -name '*.pdf' | pdftk *.pdf input_pw ******* output open_*.pdf 

```

any help would be great I have been tryng to figure this out all day reading the man and other examples. found where it will merge several files at once but nothing on unlocking then all at once

Do a search for the "exec" command.

---

### Post by Mikecore on 2008-07-05
> **dcstar said:**
> Do a search for the "exec" command.

I tried the -exec argument for find and for some reason it didn't work either

```


find . -name '*.pdf' -exec  pdftk *.pdf input_pw ******* output open_*.pdf


```

I get the same errors

---

### Post by kaibob on 2008-07-06
> **Mikecore said:**
> I tried the -exec argument for find and for some reason it didn't work either

```
find . -name '*.pdf' -exec  pdftk *.pdf input_pw ******* output open_*.pdf
```

I get the same errors

With the -exec option, I don't believe you can use '*.pdf' to represent the input PDF files. You should instead try '{}'. I'm not sure how to handle the output file names. You could try using just a target directory as shown below. You could also try 'new_{}' although I don't believe that will work because '{}' includes the path. Perhaps someone else has a suggestion on this. Be sure to put \; at the end of the command.

> find /source/directory -iname '*.pdf' -exec pdftk '{}' input_pw **** output /output/directory \;

BTW, it might be easier to do this with a for loop. Perhaps you have already considered this and discarded it for other reasons. 

> for file in * ; do pdftk "$file" input_pw ***** output "new_$file" ; done

---

### Post by Mikecore on 2008-07-06
> **kaibob said:**
> With the -exec option, I don't believe you can use '*.pdf' to represent the input PDF files. You should instead try '{}'. I'm not sure how to handle the output file names. You could try using just a target directory as shown below. You could also try 'new_{}' although I don't believe that will work because '{}' includes the path. Perhaps someone else has a suggestion on this. Be sure to put \; at the end of the command.



BTW, it might be easier to do this with a for loop. Perhaps you have already considered this and discarded it for other reasons.

your correct about the -exec option I been reading the man for the find command.

I came up with this 

```

find . -name '*.pdf' -exec pdftk {} input_pw ****** output new_{} \;

```

only problem is that adds the path info or "./" <-- before the file name So pdftk gets confused. there must be a way to remove the ./ from the output of find so that just the file name gets passed. I tried passing the output to sed but some of the file names have . in them and it removes them as well which causes even more problems.

---

### Post by kaibob on 2008-07-06
This might work:

> find . -name '*.pdf' -exec sh -c 'pdftk {} input_pw ****** output new_`basename {}`' \;

---

### Post by Mikecore on 2008-07-07
no joy

---

### Post by kaibob on 2008-07-07
Well, I don't know then. The following is the same as the above except protected against whitespace:

> find . -name '*.pdf' -exec sh -c 'pdftk "{}" input_pw ****** output new_"`basename "{}"`"' \;

I suspect there is some other issue--perhaps with the way PDFtk works or something I don't understand.

---

