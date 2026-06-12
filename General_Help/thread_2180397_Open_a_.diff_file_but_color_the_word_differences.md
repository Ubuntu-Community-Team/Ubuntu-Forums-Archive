---
title: "Open a .diff file but color the word differences?"
date: 2013-10-12
forum: General Help
---

### Post by rocky-oceans on 2013-10-12
I often receive patches (in .diff format) with minor grammatical changes. It takes several seconds for me to see that the only difference between two lines is "if" and "it". Is there a program that can open a .diff file and color the words that are different?

I'm looking for something like 

```
git diff --color-words
```

but that can work on a .diff file. Note that I could create a hack that applies the diff file and then runs a diff program that can display word differences, but I'm interested in a non-hackish solution.

---

### Post by Amorphous Serendipity on 2013-10-12
Hi rocky-oceans,

I believe you should be able to do this with "vimdiff".

If not already installed, run
```
sudo apt-get install vim
```
to install vim.

To compare the files, run
```
vimdiff FILE_1 FILE_2
```

Vimdiff will compare your files and highlight lines that are different,  as well as highlight characters in that line that are different (EX:  LINE1_FILE1:AbAbAb LINE1_FILE2:AbAbAc [will highlight "c" in second  file]).

For additional information on "vimdiff" please see - ([http://vimdoc.sourceforge.net/htmldoc/diff.html](http://vimdoc.sourceforge.net/htmldoc/diff.html))

---

### Post by rocky-oceans on 2013-10-13
Hi Amorphous Serendipity, thank you for your reply and your suggestion. I like vimdiff a lot, but for this job I'm looking for a program that can act on the diff without having the other files. I would like the command to take the diff file as the only argument.

---

### Post by Amorphous Serendipity on 2013-10-13
> **rocky-oceans said:**
> Hi Amorphous Serendipity, thank you for your reply and your suggestion. I like vimdiff a lot, but for this job I'm looking for a program that can act on the diff without having the other files. I would like the command to take the diff file as the only argument.

rocky-oceans,

I don't know of anything that will do that, nor do I think anything like that currently exists (I always could be wrong). Any sort of file differencing program will need two arguments/files.

You need:
[LIST=1]
[*]The new file 
[*]The old file 
[/LIST]
to actually compare the two and see the differences.

If you are trying to view what changes will be applied in the patches that you speak of, I would keep an old copy of the patch (currently applied) and compare it with the new patch (before it is applied) with vimdiff. If you have a test environment to test patches before they go into production and don't know what files will be changed/touched you may want to look into "auditd". It isn't exactly what you are asking for, but it may assist.

More information on "auditd" can be found here - ([http://linux.die.net/man/8/auditd](http://linux.die.net/man/8/auditd))

Sadly I can't think of anything else at the moment. If anyone else can think of anything, please feel free to jump in and assist!

---

### Post by rocky-oceans on 2013-10-13
> **Amorphous Serendipity said:**
> rocky-oceans,

Any sort of file differencing program will need two arguments/files.

You need:
[LIST=1]
[*]The new file
[*]The old file
[/LIST]
to actually compare the two and see the differences.



Right, but I'm not looking for a file differencing program. I'm looking for a program to view a .diff file.

Thanks for the suggestions.

---

