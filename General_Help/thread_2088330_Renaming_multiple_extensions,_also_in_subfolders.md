---
title: "Renaming multiple extensions, also in subfolders"
date: 2012-11-26
forum: General Help
---

### Post by 1204 on 2012-11-26
Well I would like to change from .JPG to .jpg because I can't upload pics from my hard drive to photo service. It seeks only .jpg and it's case sensitive, so it finds nothing. 

This changes JPG -> jpg in current folder, but there are like 100 folders.
```
rename 's/JPG$/jpg/' *
```

---

### Post by steeldriver on 2012-11-26
You could either use 'find' to search the directory tree recursively - something like

```
find . -type f -name '*.JPG' -exec rename -nv 's/[.]JPG$/.jpg/' '{}' \;
```(I added the literal '.' to your regex just to be safe)

If you've got a LOT of files, then a more robust find-based version would be something like 

```
while read -r -d $'\0' file; do echo mv "$file" "${file%.JPG}".jpg; done < <(find . -type f -name '*.JPG' -print0)
```Alternatively, if you enable the shell's 'globstar' option you could use shell globbing with your existing 'rename' command, like

```
shopt -s globstar; rename -nv 's/[.]JPG$/.jpg/' **/*.JPG
```

NOTE: none of these will actually do anything until you remove the '-n' switch from the renames or the 'echo' from the mv

---

### Post by ajgreeny on 2012-11-26
The final post in [http://ubuntuforums.org/showthread.php?t=1688586](http://ubuntuforums.org/showthread.php?t=1688586) shows you an answer.

---

### Post by 1204 on 2012-11-26
Thank you guys for help! :KS

edit. this did the job (when removed "echo" as you suggested ;) ):
> **steeldriver said:**
> ```
while read -r -d $'\0' file; do echo  mv "$file" "${file%.JPG}".jpg; done < <(find . -type f -name  '*.JPG' -print0)
```

---

