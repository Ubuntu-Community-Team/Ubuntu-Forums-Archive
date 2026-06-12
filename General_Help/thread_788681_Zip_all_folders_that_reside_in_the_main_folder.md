---
title: "Zip all folders that reside in the main folder"
date: 2008-05-10
forum: General Help
---

### Post by flashuni on 2008-05-10
Hello, I would like to zip all the folder I have in a folder (Lets call this folder zip).  If their are any folders inside of zip I want it to zip them.  I am currently trying to make this into a shell script.  If you have any advice please help :)

Thanks,
Flashuni

---

### Post by Monicker on 2008-05-10
I'm not sure about what you mean when you say folders inside of a zip file.  Why not just do a recursive zip in the first place.
```

zip -r files.zip /dir
```


That will zip everything in /dir and any of its subdirectories.

---

### Post by flashuni on 2008-05-10
```
## zip the contents of each folder in the current directory into an archive:
for d in *; do if [ -d "$d" ]; then cd "$d"; cd ..; fi; done

## zip every folder in the current directory into an archive:
for d in *; do if [ -d "$d" ]; then zip -r "$d.zip" "$d"; fi; done

## example recursively forces the deletion of the directory if zip returns true:
for d in *; do
        if [ ! -d "$d" ]; then
                continue
        fi
        if ! zip -r "$d.zip" "$d"; then
                continue
        fi
done
```
Figured it out.  Automatically finds any folder and zips it. :KS

---

