---
title: "Nautilus - mass assign file permissions?"
date: 2005-08-29
forum: General Help
---

### Post by 5-HT on 2005-08-29
Hi, after switching to ubuntu it seems as if all my files no longer have write permissions (maybe it has to do with copying them over from a cd?).

I was wondering if there's anyway from within nautilus to change the permissions off all files within a directory (or just the permissions of certain file extensions within the directory), as manually changing the permissions of each file seems a little tedious?

After doing a little research I believe using "chmod" with some wildcards should hopefully let me do what I'm looking for from the command line, but is there any way of doing this through nautilus?


Also, as switching from windows to ubuntu appears to have changed the file attributes to read-only (or maybe it has nothing to do with the os's but rather that I copied the files from a cd?), I'm wondering if there are any file permission compatibility issues at all in terms of being able to modify the permissions of a file generated on ubuntu from a windows pc 
(I'm guessing hopefully not, but just want to make sure that I'm not digging myself into a possible hole down the road) ?

Thanks for any help

---

### Post by heimo on 2005-08-29
Have you tried to "view as list", sort by type, select files you want to change (hold ctrl or shift), right-click -> properties -> permissions and do the change?

---

### Post by 5-HT on 2005-08-29
Thanks for the suggestion.

The only problem with that for me is that for some reason or another I tend to go directory crazy having tons of em' with smaller file content per directory. 

So if I try to change permissions of files like you said, everything works great but that trick won't work recursively throughout directories.


I was just thinking though...that if I  go with the "chmod" route, I'll then have to make everything executable (so that I can search directories) which isn't a good thing either...

Guess either way then I'll have to do it directory by directory (well I guess this gives me a chance to clean them out).
Thanks

---

### Post by heimo on 2005-08-29
[QUOTE=5-HT]
I was just thinking though...that if I go with the "chmod" route, I'll then have to make everything executable (so that I can search directories) which isn't a good thing either...
[/QUOTE]
No.

[QUOTE=5-HT]
Guess either way then I'll have to do it directory by directory (well I guess this gives me a chance to clean them out).
[/QUOTE]
No.

:) Why would you have to make anything executable with chmod? You can give exactly the permissions you want. And you  definitely don't need to do it per directory on shell. You could combine *find *and *chmod *or in some cases, just use wildcards.

---

### Post by 5-HT on 2005-08-30
[QUOTE=heimo]
And you  definitely don't need to do it per directory on shell. You could combine *find *and *chmod *or in some cases, just use wildcards.[/QUOTE]

Yeah, I was trying to be lazy and just change everything with a simple command. 

Sounds like filtering *chmod * through wildcards and* find* seems the best to get what I want with the directories executable and the files only read/write.

Thanks for the help.

---

