---
title: "Bash: How to split a file into multiple files according to defined rules"
date: 2013-08-02
forum: General Help
---

### Post by abcuser on 2013-08-02
Hi,
using Ubuntu 12.04 I have the following text file that I get as my input:
```

Section1
col1	col2 (many columns)
100	500
101	500	
102	500
(many rows)

Section2
col1	col2 (many columns)
400	400
401	400	
402	400
(many rows)

Section3
col1	col2 (many columns)
700	600
801	700	
902	800
(many rows)

```

How to brake this file into 3 files according to the "Section" line?
From Section1 to Section2 should be saved in file file1.
```

Section1
col1	col2 (many columns)
100	500
101	500	
102	500
(many rows)

```

From Section2 to Section3 should be saved in file2.
```

Section2
col1	col2 (many columns)
400	400
401	400	
402	400
(many rows)

```
and from Section 3 to end of file should be saved in file3.
```

Section3
col1	col2 (many columns)
700	600
801	700	
902	800
(many rows)

```

How to split one file into multiple files according to above rules?
Thanks

---

### Post by steeldriver on 2013-08-02
Are the sections separated by empty lines, exactly as shown in your example? if so then you may be able to use awk with 'empty line' as a record separator, e.g.

```

awk 'BEGIN {RS=""}; {print > ""$1".txt"}' *yourfile*

```

will produce files Section1.txt, Section2.txt etc. (i.e. using the SectionN header as the output file name) although obviously you cold change that to any sequential naming like file1, file2 with some string processing

```

$ awk 'BEGIN {RS=""}; {print > ""$1".txt"}' sections.txt
$
$ cat Section2.txt
Section2
col1    col2 (many columns)
400     400
401     400
402     400
(many rows)

```

---

### Post by tgalati4 on 2013-08-02
*cat* will concatenate files.  *tac* will work in reverse.  Although I have not used it, it may do what you want.  It reads the file backwards, splitting out into separate files when it encounters a keyword.

```
man tac
tac --help
tac -r "section" myfilewithmanysectionsandcolumnsandrows.txt
```

As *steeldriver* suggests, *awk* should do it as well as *mawk*, *gawk*, *sed*, *perl*, *split* and perhaps a few other file manipulation tools.

A google search using "split file using bash" brings up:

[http://stackoverflow.com/questions/3644238/split-text-file-in-two-using-bash-script](http://stackoverflow.com/questions/3644238/split-text-file-in-two-using-bash-script)
[http://stackoverflow.com/questions/2016894/easy-way-to-split-a-large-text-file](http://stackoverflow.com/questions/2016894/easy-way-to-split-a-large-text-file)
[http://stackoverflow.com/questions/6946901/split-file-by-script-bash-cpp-numbers-in-columns](http://stackoverflow.com/questions/6946901/split-file-by-script-bash-cpp-numbers-in-columns)

Let us know what your final script looks like.

---

