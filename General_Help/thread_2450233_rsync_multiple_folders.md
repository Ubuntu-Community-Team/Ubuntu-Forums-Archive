---
title: "rsync multiple folders?"
date: 2020-09-09
forum: General Help
---

### Post by Aleksandar_Djordje on 2020-09-09
Is there a possibility for rsync to sync multiple folders at the same time but also copying subfolders of them. 

As an example i have folders structure

app/clients/user1/app1/web
app/clients/user1/app2/web
app/clients/user2/app1/web
app/clients/user3/app1/web

Is there a possibility to use rsync in one line command to copy from all USER and all APP web folders. 

Example like this maybe

```

[COLOR=#474B51][FONT=Consolas]rsync -avz 'ssh -p <port-number>' --stats --delete user@remote-server:/[/FONT][/COLOR]app/clients[COLOR=#474B51][FONT=Consolas]/user*/app*/web /path/to/local/folder
[/FONT][/COLOR]
```[COLOR=#474B51][FONT=Consolas]
[/FONT][/COLOR]

---

### Post by HermanAB on 2020-09-10
Almost there!

Globbing:
? is for one character
* is for many characters

Quotes:
"  " is used to tell Bash to expand variables and globs.

So replace your asterisks with question marks and put double quotes around everything.

---

### Post by SeijiSensei on 2020-09-10
I find it much easier to use the --files-from option in rsync and put the list of files and globs into a file.
>      --files-from=FILE       read list of source-file names from FILE

[https://linux.die.net/man/1/rsync](https://linux.die.net/man/1/rsync)

---

### Post by Aleksandar_Djordje on 2020-09-10
> **HermanAB said:**
> 
Globbing:
? is for one character
* is for many characters


Would this make a difference as sometimes folders will be double digits for example it will have /user3/app12 or /user11/app2 so if ? is for one character i guess double digit numbers are counted as two characters, or is it safe to use ? after all?

> **HermanAB said:**
> 
" " is used to tell Bash to expand variables and globs.


I will execute the command from terminal from my pc so i am not sure if i understand this part with double quotes. This is used if i would make bash script?

Or i just need to use it like this ?

```
rsync -avz "ssh -p <port-number> --stats --delete user@remote-server:/app/clients/user*/app*/web /path/to/local/folder"
```

---

### Post by SeijiSensei on 2020-09-10
If you want to match both app2 and app12, use the star.

You can also include alternative characters inside square brackets.  For instance,

```
app1[12345]
```

would match app11 to app15, but not app16.

This applies to file references at the command prompt in bash as well.

```
rm -rf app1[12345]
```

would remove the directories app11 to app15 and the files they contain.

---

### Post by Aleksandar_Djordje on 2020-09-10
Thanks guys you help me out, the working command is this

```

"rsync -avz -e 'ssh -p <port-number>' --stats --delete user@remote-server:/app/clients/user*/app*/web /path/to/local/folder"

```

I got it with bash script set.

---

