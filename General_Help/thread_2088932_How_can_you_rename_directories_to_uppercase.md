---
title: "How can you rename directories to uppercase?"
date: 2012-11-27
forum: General Help
---

### Post by alkal0id on 2012-11-27
When I try to rename a directory to uppercause (i.e. directory to Directory, or directory to DIRECTORY etc.), it won't let me do it because it says "the name is already in use. Please use another name.". Is there any way around this, besides changing the name of the file to something else, then back again after the cases are fixed?

---

### Post by leclerc65 on 2012-11-27
* deleted

---

### Post by steeldriver on 2012-11-27
Are these directories on an NTFS partition by any chance? What you are trying to do should work fine on Linux partitions - but although NTFS is case-preserving in terms of how it displays names, it's not really case sensitive under the hood - I don't know if there's a workaround for that apart from the one you've already discovered

---

### Post by StinkySQL on 2012-11-27
If you are in a windows world, rename it something else and create a new directory. Then move the files over and delete the old renamed item. Windows is definitely case-insensitive.

SS

---

### Post by rnerwein on 2012-11-28
> **alkal0id said:**
> When I try to rename a directory to uppercause (i.e. directory to Directory, or directory to DIRECTORY etc.), it won't let me do it because it says "the name is already in use. Please use another name.". Is there any way around this, besides changing the name of the file to something else, then back again after the cases are fixed?
just copy it to another name e.g. cpopy bla > blu
then copy blu to BLA
better is: mv (move) bla blu
                   mv blu BLA

---

### Post by alkal0id on 2012-11-30
Yeah its an NTFS external harddrive that has the directories on it. Due to a problem, I couldn't format it as Ext3. I shoulda went with FAT32 instead (unless the same problem exists with that).

I need to batch rename a load of directories so I can't just do this manually. I found a program GPRename which capitalises each word in the directory name (what I need to do) but the NTFS file system won't let it rename them. If GPRename let me perform two operations at the same time, for example if it let me change the case of the name, as well as adding a random character after the name, then it would work because the new file names would have an extra letter and thus, be different but it only lets you do one operation at a time. Thunar comes with a file renamer but its not that good. Anyone know of an advanced file renamer that will let me perform multiple renaming operations at the same time? 

I could write a shell script to do this form me but my knowledge of bash is very limited. I could do it with PHP but I run PHP on an apache server and it doesn't let me manipulate files outside of the /var/www (there may be a way around that, which I'm unaware of).

---

### Post by Vaphell on 2012-11-30
assuming single location, you could try something like this
```
for d in */; do mv "$d" "__$d"; mv "__$d" "${d^^}"; done
```

oldname -> __oldname; __oldname -> OLDNAME

---

### Post by alkal0id on 2012-11-30
> **Vaphell said:**
> assuming single location, you could try something like this
```
for d in */; do mv "$d" "__$d"; mv "__$d" "${d^^}"; done
```oldname -> __oldname; __oldname -> OLDNAME

I don't fully understand your code but I think I see what you're getting at. Add __ before the names of every directory, then change the case of the names and remove the __ at the same time. Is that it? The part of the code I don't understand is ${d^^}. What does the $ do, what are the curly braces for and what is d^^ for? Sorry for asking you to break down every single piece of that bit of code lol. I'm new to bash and as a PHP programmer, I find the syntax pretty mind boggling.

EDIT: Ah, I see you explain what your code does at the bottom of your reply. What I need to do though is:
**directory name -> Directory** [B]Name
[/B]In PHP the uc_words() function replacing the first letter of every word in a string with an uppercase letter.

---

### Post by alkal0id on 2012-11-30
I found out that to capitalize the first letters of each word in a string, I can do this:
```
string='mIXed uP CAse' 
string=${string,,} 
string=${string~} 
```
I don't know how that works, I still don't understand what this ${ } thing does but I know everything I need to know to rename these folders. Thanks for all the help!

---

### Post by Vaphell on 2012-11-30
it's parameter expansion (as in 'get value of that thing')
$d and ${d} are equivalent, but ${} syntax allows for on the fly operations on the value
[http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion](http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion)
,, modifier means lowercase-all
~ is upcase first chars in words

using sed
```
for d in */; do mv "$d" "__$d"; mv "__$d" "$( echo "$d" | sed -r 's/\<./\U&/g' )"; done
```

```
$ old="abc    def"
$ new=$( echo "$old" | sed -r 's/\<./\U&/g' )
$ echo "$new"
Abc    Def
```

[COLOR="Blue"]\<[/COLOR][COLOR="Red"].[/COLOR] matches [COLOR="Blue"]left-word-boundary[/COLOR][COLOR="Red"]any-char[/COLOR] and replaces it with uppercased (\U) selection (&)

EDIT: i completely forgot about ${var~} and it's not mentioned on that reference page.

```
for d in */; do new=${d,,}; new=${new~}; mv "$d" "__$d"; mv "__$d" "$new"; done
```

---

### Post by alkal0id on 2012-11-30
Ah I see. Thats pretty cool, I don't think PHP has anything like that. Thanks a lot for the explanation. I'll look into sed. I'm guessing its similar to regular expressions used in other languages.

---

