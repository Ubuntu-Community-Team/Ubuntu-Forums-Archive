---
title: "rsync - quoting arguments"
date: 2019-07-25
forum: General Help
---

### Post by dazzle-razzle on 2019-07-25
I am building a Python wrapper around rsync to group the variety of parameter options into categories, and to simplify building the rsync call.  The most commonly-used parameters do not take arguments, such as -a, -v, and -z.

But many of the more advanced parameters take arguments, such as:
  --logfile=FILE
  --sockopts=OPTIONS
The sockopts parameter is a good example of something that should be included in a wrapper, but is a bit beyond my OS scope.

I am trying to get a grasp on quotation marks:
1.  Can all arguments be enclosed in quotes? 
2.  Even if the argument is numeric, as in  --max-delete=NUM.
3.  Do both single and double quotes work?
4.  Can embedded quotes simply be escaped?

Thanks for any suggestions.

---

### Post by dragonfly41 on 2019-07-25
I would try the GUI grsync which is a wrapper for rsync.
You can specify different sessions.

---

### Post by SeijiSensei on 2019-07-25
Strings enclosed in double quotes are interpreted by bash with substitutions for environment variables. Bash treats strings in single-quotes literally.

```

PARAM=xyzzy
echo "$PARAM"
echo '$PARAM'

```

The first will return "xyzzy". The second will return "$PARAM". 

Enclosing a string in single quotes will enable you to embed double quotes e.g, 'this is a "monster"' without the need for escaping with back slashes. However, in the example above, if you need to substitute for $PARAM, then you'd need to use double quotes and escape any included double quotes in the string.

```
echo "hello, \"$PARAM\""
```

---

### Post by TheFu on 2019-07-25
rsync has different globbing rules than shells have. There are times when "" is preferred and there are times when '' is necessary so the rsync globbing gets used, not the shell's.

You will need to handle both situations correctly to get the rsync command desired.

---

### Post by dazzle-razzle on 2019-07-25
[SIZE=3]Thank you all for your comments!

dragonfly41: grsync is interesting but I need to be able to specify rsync arguments from Python code, and the aspiration is to organize, and simplify access to, all the parameters.  

The wrapper is actually in two parts.  The rsync-specific "Rsync" module passes option specs to a more general "CmdParams module, which can be used to create the composite parameter string for any Unix-style command line call.  Here are a few sample Rsync option specs:[FONT=arial]
[/FONT][/SIZE]
[SIZE=1][FONT=courier new]    'verbose':              Option(categ=Categ.FEEDBACK,[INDENT]descrip = 'verbose output',
                                        flag    = '-v',
                                        altflag = '--verbose'),
[/INDENT]
 'log-file':             Option(categ=Categ.FEEDBACK,[INDENT]descrip = 'log actions taken into the specified FILE',
                                        flag    = '-log-file',
                                        argtype = CmdParams.FILE_NAME,
                                        quote   = True),
[/INDENT]
 'max-size':             Option(categ=Categ.FILTER_SRC,[INDENT]descrip = 'do not transfer any file larger than SIZE',
                                        flag    = '--max-size',
                                        argtype = CmdParams.FILE_SIZE,
                                        quote   = False),
[/INDENT]
 
[/FONT][/SIZE][SIZE=3]Is there available definitive documentation on rsync's globbing rules (because of Fu's comment), and the shell's globbing rules (because of SeijiSensei's comment)?[/SIZE]

---

### Post by TheFu on 2019-07-25
Yes.  The rsync manpage.

But most people file examples to be more helpful.  Some linux backup tools also use the rsync globbing rules, so there are reasons to learn it.  OTOH, many people only need to learn a few common methods and delve deeper only when specifically needed.  --include --exclude --filter uses, for example.

Your code needs to handle both single-quote and double-quote styles.

---

### Post by HermanAB on 2019-07-25
Hmm, nice idea.  

Note that with a tool like rsync, it is usually better to think negatively and create a rule that includes everything and then make an exclude rule to remove things you don't want, such as caches, trash and ISO files.  

The reason being that the things you don't want tend to remain the same, while the things you do want are always changing and you better  fail on the side of caution and have a backup set that is too large, than missing something new and important.

---

### Post by SeijiSensei on 2019-07-25
I find it easiest to use --exclude-from which lets you put globs to ignore into a file. On my backup server I have files with exclusions like these:
```

proc/
sys/
run/
dev/
*.iso
*.avi
*.mkv
*.mp?
.VirtualBox

```

---

