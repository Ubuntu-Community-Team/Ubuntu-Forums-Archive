---
title: "Font files of mac on my ubuntu pc"
date: 2008-05-11
forum: General Help
---

### Post by flashuni on 2008-05-11
Hello, I am trying to preserve the resource fork when I zip mac font files on my ubuntu pc.  When trying this it doesnt work, but then I used the command "ditto -c -k -X --rsrc mac_fonts mac_fonts.zip". This worked fine, but I want to make a shell script that will go through the mac_fonts directory and zip all of the folders inside (Into separate zips, not into one giant zip).

I previously tried to use this script which worked fine, but didnt use ditto and didn't compress the font files correctly.

```
## zip the contents of each folder in the current directory into an archive:
for d in *; do if [ -d "$d" ]; then cd "$d"; cd ..; fi; done

## zip every folder in the current directory into an archive:
for d in *; do if [ -d "$d" ]; then zip -r -j "$d.zip" "$d"; fi; done

## example recursively forces the deletion of the directory if zip returns true:
for d in *; do
        if [ ! -d "$d" ]; then
                continue
        fi
        if ! zip -R -j "$d.zip" "$d"; then
                continue
        fi
## Delete Every Folder that Isn't Zip
find . -not -name '*.zip' -not -name 'Ziper.sh' | xargs rm -rf
done
```

Any help would be appreciated! :KS

Thanks,
       Flashuni

---

### Post by mano cazalet on 2008-05-11
maybe you can try this other method:

[http://www.ubuntu-unleashed.com/2008/05/howto-install-mac-fonts-on-ubuntu.html](http://www.ubuntu-unleashed.com/2008/05/howto-install-mac-fonts-on-ubuntu.html)

---

### Post by flashuni on 2008-05-11
I was trying to zip them up for my mac, which I wasn't clear on.:KS

---

