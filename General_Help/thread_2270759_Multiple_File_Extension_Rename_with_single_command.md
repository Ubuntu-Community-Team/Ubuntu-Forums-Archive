---
title: "Multiple File Extension Rename with single command"
date: 2015-03-25
forum: General Help
---

### Post by thewhiteeye on 2015-03-25
Hello,     I have a few files that i received which look something like this:                                          abc.zip1                                        bca.zip2                                        bcd.zip3    etc           I want to rename all these file extensions to zip. The result  should look something like this:                                          abc.zip                                        bca.zip                                        bcd.zip    etc   Please help me do this as there are about 200 files like these.

---

### Post by SeijiSensei on 2015-03-25
Takes a bit more than one command.

```

cd /path/to/the/files
for f in *.zip*
do
    NAME=$(basename $f)
    mv $f $NAME.zip
done

```

---

### Post by Lars Noodén on 2015-03-25
There's **rename** which takes normal Perl Regular Expressions (you've seen them before as PCRE)

```

rename -n '**s/**[color=blue]\.zip.*$[/color]**/**[color=purple].zip[/color]**/**' *./*.zip**

```

If that does what you want, then take out the -n

---

### Post by thewhiteeye on 2015-03-30
Thank you soo much for your replies.  The rename command suggested by Mr Lars did the trick.  I am grateful to  Lars and  SeijiSensei for helping me getting around this issue.

---

