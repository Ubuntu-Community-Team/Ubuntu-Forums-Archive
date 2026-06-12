---
title: "find -delete -name &quot;*SOMETHING*&quot;"
date: 2014-07-23
forum: General Help
---

### Post by jrnix18 on 2014-07-23
So I wanted to find and delete files that contained a particular string.

I found and listed all those files I wanted to delete by: find -name "*SOMETHING*"

I looked through find -help and saw there was a -delete option. Unfortunately I misjudged what that -delete option meant. It didn't just delete the files it found, it all sorts of stuff. it appeared it might have planned on deleting everything. I hit ctrl-c in time to stop some of the madness.

I'm incredibly upset about what just happened. I can't find anything about -delete in the man pages.

Does anyone know what -delete is supposed to do?

Does anyone know how I might be able to bring back the files that have been removed?

---

### Post by jrnix18 on 2014-07-23
what a nightmare. is it because i put -delete infront of -name that it decided to delete everything?

---

### Post by steeldriver on 2014-07-23
Yes unfortunately the find command chains things logically from left to right - you would need to put the action (-delete) after the test(s) that you want it to apply to (-name '*SOMETHING*)

If you don't have backups, then you should stop using the system NOW and go research data recovery (testdisk, photorec etc.)

---

### Post by Dennis N on 2014-07-23
> **jrnix18 said:**
> what a nightmare. is it because i put -delete infront of -name that it decided to delete everything?

Unfortunately, yes. This is from the man page:

> Warnings:  Don't  forget that the find command line is evaluated
              as an expression, so [B]putting -delete first will make find try to
              delete everything below the starting points you specified.[/B]  When
              testing a find command line that you later intend  to  use  with
              -delete,  you should explicitly specify -depth in order to avoid
              later surprises.

---

### Post by sudodus on 2014-07-23
Yes, I'm afraid that happened. Put the action commands after the selection commands or use the action command -exec with echo to test before running the real action

```
find path -name "*.tmp" -exec echo rm {} \;
```  then if OK, remove echo and run the real action
```
find path -name "*.tmp" -exec rm {} \;
```


 ```
ACTIONS
       -delete
              Delete  files;  true  if  removal  succeeded.   If  the removal
              failed, an error message is issued.  If -delete  fails,  find's
              exit status will be nonzero (when it eventually exits).  Use of
              -delete automatically turns on the -depth option.

              Warnings: Don't forget that the find command line is  evaluated
              as  an  expression, so [COLOR=#ff0000]putting -delete first will make find try
              to delete everything below the starting points  you  specified.[/COLOR]
              When  testing  a find command line that you later intend to use
              with -delete, you should explicitly specify -depth in order  to
              avoid  later  surprises.   Because  -delete implies -depth, you
              cannot usefully use -prune and -delete together.

       -exec command ;
              Execute command; true if 0 status is returned.   All  following
              arguments  to  find  are  taken  to be arguments to the command
              until an argument consisting of `;' is encountered.  The string
              `{}'  is  replaced  by  the  current  file name being processed
              everywhere it occurs in the arguments to the command, not  just
              in  arguments  where  it is alone, as in some versions of find.
              Both of these constructions might need to be  escaped  (with  a
              `\')  or  quoted  to  protect them from expansion by the shell.
              See the EXAMPLES section for examples of the use of  the  -exec
              option.   The  specified  command  is run once for each matched
              file.  The command  is  executed  in  the  starting  directory.
              There  are unavoidable security problems surrounding use of the
              -exec action; you should use the -execdir option instead.

       -exec command {} +
             [COLOR=#006400] This variant of the -exec action runs the specified command  on
              the  selected files,[/COLOR] but the command line is built by appending
              each selected file name at the end; the total number of invoca&#8208;
              tions  of  the  command  will  be  much less than the number of
              matched files.  The command line is built in much the same  way
              that xargs builds its command lines.  Only one instance of `{}'
              is allowed within the command.  The command is executed in  the
              ...

```

---

### Post by jrnix18 on 2014-07-23
i've been trying to use testdisk. It finds the deleted folders but when I look in the folders I get the message "No file found, filesystem may be damaged"

---

### Post by sudodus on 2014-07-23
> **steeldriver said:**
> Yes unfortunately the find command chains things logically from left to right - you would need to put the action (-delete) after the test(s) that you want it to apply to (-name '*SOMETHING*)

If you don't have backups, then you should **[COLOR=#ff0000]stop using the system NOW and go research data recovery (testdisk, photorec etc[/COLOR]**.)

+1000 (my red and bold text)

---

### Post by sudodus on 2014-07-23
> **jrnix18 said:**
> i've been trying to use testdisk. It finds the deleted folders but when I look in the folders I get the message "No file found, filesystem may be damaged"
 
Keep trying with testdisk, because if it works it is more convenient than photorec. What files did you remove? From which directory? If system files, it might be easier to re-install. If personal data (documents, pictures ...) you should keep trying to get them back. PhotoRec means a lot of hard work, but can recover a lot of files even without any file system.

---

### Post by jrnix18 on 2014-07-23
photorec seems to be working. they are personal files. the recovered files have lost their names but at least they are being recovered. now comes the long task of renaming everything.

---

### Post by jrnix18 on 2014-07-23
now i'm starting to worry my destination drive for the data recovery is going to run out of space. does anyone know what will happen in that case? 

i'm reading now i could have set options to only recover certain file types. would it be possible/wise to stop the recovery and select those file types?

is it possible to have photorec recover the files in-place? just put them back on the disk where they were when they were deleted?

---

### Post by nothingspecial on 2014-07-23
> **jrnix18 said:**
> 

is it possible to have photorec recover the files in-place? just put them back on the disk where they were when they were deleted?

When you delete something from an ext4 filesystem you remove the bit of the file that knows where it is placed in the file system but you do not delete the data which is why you can recover the file but it just has a gobbldygook name. Last time I checked that is the best that can be done.

find is one of the most destructive commands there is (as I discovered myself the hard way).

---

### Post by sudodus on 2014-07-23
> **jrnix18 said:**
> now i'm starting to worry my destination drive for the data recovery is going to run out of space. does anyone know what will happen in that case? 

i'm reading now i could have set options to only recover certain file types. would it be possible/wise to stop the recovery and select those file types?

is it possible to have photorec recover the files in-place? just put them back on the disk where they were when they were deleted?

I think you can interrupt PhotoRec, change the settings to recover only the file types you are interested in, and start again. Anyway, it might be a good idea to get more external drive space, a HDD or USB 3 pendrive.

Notice that open document files are recognized as compressed files, PhotoRec allows you to select only ***zip*** format files, so along with the odt files there will be other open document files, regular zip archive files etc.

Do *not* recover the files in-place. Write only to external drives, otherwise you might overwrite the data you want to recover, and for the same reason do not boot into your internal system, only boot into a live drive (for example a USB pendrive with Ubuntu).

---

### Post by sudodus on 2014-07-23
> **nothingspecial said:**
> ...

find is one of the most destructive commands there is (as I discovered myself the hard way).


This is why I suggest to use the action  command -exec with echo to test before running the real action

```
find path -name "*.tmp" -exec echo rm {} \;
```  then if OK, remove echo and run the real action
```
find path -name "*.tmp" -exec rm {} \;
```

---

