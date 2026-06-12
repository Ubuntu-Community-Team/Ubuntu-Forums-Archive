---
title: "Complex sorting/moving operation with backed up files"
date: 2015-11-09
forum: General Help
---

### Post by lwfx on 2015-11-09
Not sure what to call this but I will do my best. Basically I have years and years of backed up pics, docs, php files, mov, etc. around 300GB Worth over the past 15 years now.

Is there a way from terminal to search out say, JPG files, read the parent folder, make a new folder of same name in another place then proceed to move any JPGs in that file to the new location. Basically want to do this so that I can further sort. If I simply transfer all JPG over, then I will have of course conflicting file names, but more importantly no reference as to where they were at one point, and would have to spend weeks guessing and cross-checking where everything belongs. Does this make sense? Thanks.

---

### Post by SeijiSensei on 2015-11-09
Are all these files in some common location like /home/username, or are they scattered all over the filesystem?  One simple method would use rsync like this
```

cd /home/username
rsync -av . /path/to/new/location --include=*.jpg --include=*.JPG

```
You could also start at the root of the filesystem ("/") to copy all JPEGs to the new location, but you'll end up with any parent directories.  So if you have some photos in /home/username and some in /data, the new location will not merge the photos into one common directory.

---

