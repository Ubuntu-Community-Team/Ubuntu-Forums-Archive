---
title: "Replace &quot;tab space&quot; with a paragraph?"
date: 2007-03-04
forum: General Help
---

### Post by aktiwers on 2007-03-04
I have a text document containing the list of 2500 unique names. The problem  is that they are separated by a  tab.  I need  the tab to be replaced with a paragraph, so that each name will have its own line.   

Is there a way to do this?

I was thinking maybe theres a command or something that could replace the "tab space" with a "paragraph", like replacing a character with another one. Something like the "replace character" -function in openoffice.

I have the file in an Exel document as well.

---

### Post by Ramses de Norre on 2007-03-04
What kind of text document? Just plain text? And do you mean <p> stuff for paragraphs?
If so: ```
sed -e 's/\t/<\/p><p>/g' -i file
```
I don't know how paragraphs are denoted in other formats, and binary files like .doc or open office formats will be very difficult without built-in functions.

---

### Post by lloyd_b on 2007-03-04
Assuming it's a text file, and that those "tab spaces" you refer to are actually the <TAB> character, open up a terminal window and run the following (substituting the actual filename, of course):
```
cat file.txt | tr '\t' '\n' > newfile.txt
```
will take the contents of "file.txt", translate all tab characters to "newline" characters, and save the results to "newfile.txt".  Net results: A file with a list of tab-separated entries becomes a list of one-entry-per-line.

Lloyd B.

---

### Post by aktiwers on 2007-03-04
Thanks Ramses!
I also found that the search funktion in Openoffice could do it. 
By enabling "regular expression" and then searching for \t and replacing it with \n also did the job.

Thanks again.
EDIT:
Thx for the reply Lloyd :)

---

