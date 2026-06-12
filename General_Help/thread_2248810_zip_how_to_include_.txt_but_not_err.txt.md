---
title: "zip: how to include *.txt but not err*.txt?"
date: 2014-10-17
forum: General Help
---

### Post by bulrush2 on 2014-10-17
I 'm writing a backup program using zip. I have a directory structure like this: 

```

perl/dir1/subdira (contains .pl files)
perl/dir1/subdira/done/ (files with err*.txt and .xls files)
perl/dir2/subdira/ (some .pl files)
perl/dir2/subdira/done (files with err*.txt and .xls files)
perl/dir3/subdira/ (files with .pl)
perl/dir3/subdira/done/ (files with err*.txt and .xls files)

```

My backup script, called 'backperl' which calls the zip command is in the 'perl' directory. I want to back up all files in the perl directory and subdirectories, except those which match files in exclude.lst. 

I want to back up all files but: 
```

*.bck
*.bak
any files in done/err*.txt
any files in done/*.xls

```

My current command line is: 
```
zip -r -u -sf backup.zip backperl * -x@exclude.lst
```

My exclude.lst contains:
```

*.bck
*.bak
*.zip
*.pdf
*.xls
done/err*.txt

```


I'm having some problems. The zip command line is currently including done/err*.txt and done/*.xls but I don't want those. 
Can someone help me make this work? 

Thanks.

---

