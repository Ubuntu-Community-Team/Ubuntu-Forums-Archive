---
title: "Check return value of find"
date: 2018-08-11
forum: General Help
---

### Post by raleigh3 on 2018-08-11
I know I will need to use an if/then to improve this.

I want to test the find statements and then exit if it finds no files older than 3 days.

```
Docs_Backups=/media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/Documents_Backups/
Scripts_Backups=/media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/Script_Backups/

echo "Files older than 3 days."
find $Docs_Backups -mindepth 1 -mtime +3 -print -exec rm {} \;
find $Scripts_Backups -mindepth 1 -mtime +3 -print -exec rm {} \;
echo "Files older than 3 days have been deleted."
```

---

### Post by TheFu on 2018-08-11
a) $? has the last return code or you can assign it to a variable and check it.

b) rather than using **-exec rm**, perhaps using **-delete** which is built-into find would be better?  It will definitely save an external process.

The ABSG has lots of examples for stuff like this.

---

### Post by raleigh3 on 2018-08-11
Thanks.

```
find $Docs_Backups -mindepth 1 -mtime +3 -print -delete {} \;
```


```
find: paths must precede expression: `{}'
```

But path does precede it ?

What is ABSG.

---

### Post by steeldriver on 2018-08-11
You don't need the `{}` (or `\;`) with -delete, that's what's being treated in this context as a "path"

---

### Post by raleigh3 on 2018-08-11
Ok, thanks.

---

### Post by steeldriver on 2018-08-11
FYI I'm not sure you can rely on the exit status (return value) to tell you whether any matching files were found. From `man find`:

```

EXIT STATUS
       find  exits  with  status  0  if  all files are processed successfully,
       greater than 0 if errors occur.   This is  deliberately  a  very  broad
       description,  but  if the return value is non-zero, you should not rely
       on the correctness of the results of find.

```

---

### Post by edadasiewicz on 2018-08-11
You could capture the result of find in an environment variable and then test the variable.  For example:

files=$(find $Scripts_Backups -mindepth 1 -mtime +3 -print -delete)
if [[ $files ]]; then
echo 'Files deleted'
fi

---

### Post by raleigh3 on 2018-08-11
Thanks.

I noticed that deleted files do not end up in trash.

I gotta be careful.

---

### Post by TheFu on 2018-08-11
trash is a GUI thing.  It has NOTHING to do with the OS or any GNU tools.

Google "ABSG bash"  Almost all the questions asked in these forums about bash scripting are covered there.

---

