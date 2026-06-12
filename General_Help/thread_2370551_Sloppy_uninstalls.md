---
title: "Sloppy uninstalls"
date: 2017-09-04
forum: General Help
---

### Post by raleigh3 on 2017-09-04
I have noticed that most uninstalls do not delete their icon files.

I have over 186,000 png files.

If say 10% of those are used by installed programs,emblems,etc, that leaves 160,000 plus.

---

### Post by vasa1 on 2017-09-04
> **raleigh3 said:**
> I have noticed that most uninstalls do not delete their icon files.

I have over 186,000 png files.

If say 10% of those are used by installed programs,emblems,etc, that leaves 160,000 plus.
Could you please provide more details?

Give us a few examples of applications you've uninstalled.

Where are the .png files relating to uninstalled applications located on your computer?

How did you arrive at "over 186,000 png files"?

```
$ find /usr/share/icons -type f -iname "*.png" | wc -l
7950
$ 
```
or```
$ find /usr/share/ -type f -iname "*.png" | wc -l
13918
$ 
```

---

### Post by raleigh3 on 2017-09-05
find / -name *.png > png_file.txt

Came up with 61,000 this time.

Inkscape is one program I used to have.

/home/andy/.cache/inkscape/icons/ has 247 icons.

Inkscape also has icons in some directors under usr/share/icons.

---

### Post by vasa1 on 2017-09-05
You can safely delete the inkscape folder and all other folders clearly identifiable as belonging to uninstalled applications from ~/.cache.

You can also run```
rm -rf ~/.thumbnails
```once in a while.

---

### Post by raleigh3 on 2017-09-05
Thanks. That got rid of a lot.

---

### Post by oldos2er on 2017-09-05
I'm assuming you installed inkscape using the package manager. APT will never delete data from a user's home folder by design. 

You can use 'purge' to remove system configuration files, though I've never checked if that includes icons.

---

### Post by raleigh3 on 2017-09-05
I am wondering why APT does not remove unused icons?

---

### Post by deadflowr on 2017-09-05
Because the icons aren't part of the package removed.
Icons have their own packages.

---

### Post by vasa1 on 2017-09-05
> **raleigh3 said:**
> I am wondering why APT does not remove unused icons?You are not providing enough information. We don't know which icons you're talking about.

---

