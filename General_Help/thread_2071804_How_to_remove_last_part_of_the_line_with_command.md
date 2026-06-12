---
title: "How to remove last part of the line with command?"
date: 2012-10-16
forum: General Help
---

### Post by abcuser on 2012-10-16
I got Windows file with file paths in it. I need to retain only directory structure and remove file names.

Sample data in myfile.txt:
```

C:\aaa\bbbb\cccc\xxx.txt
C:\aaa\bbbb\abc.txt
C:\aaa\zzzz.txt
<many hundreds of lines with different path depth>

```

So in myfile.txt I need to search for the last backslash character "\" and remove everything to the end of line, to get:
```

C:\aaa\bbbb\cccc
C:\aaa\bbbb
C:\aaa

```

How to remove file names from path?
Thanks

---

### Post by Lars Noodén on 2012-10-16
I tried basename and dirname, but they did not work.  However, [sed](http://manpages.ubuntu.com/manpages/precise/man1/sed.1.html) does the job.

```

sed -e 's/\\[^\\]*$//' < myfile.txt > output.txt

```

---

### Post by evilsoup on 2012-10-16
I think you'll have to use sed for this.

```
cat filename | sed 's\(.*\\\)/\1/' > outputfile
```will give you an output file with the xxx.txt removed, but it keeps the final backslash, I don't know how to remove that.

EDIT: nevermind, ninja'd with a better solution

---

### Post by steeldriver on 2012-10-16
or you could use bash substitution

```
while read -r path; do echo "${path%\\*}"; done < myfile.txt
```

---

