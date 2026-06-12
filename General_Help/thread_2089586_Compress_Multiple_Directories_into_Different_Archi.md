---
title: "Compress Multiple Directories into Different Archives"
date: 2012-11-29
forum: General Help
---

### Post by V13 Noob on 2012-11-29
Hello forums,

I have an issue with compressing multiple folders into their own respective archives. I have close to 600 folders I need to compress. I'm running on pangolin

The set up is like this:
     Parent Directory >
          > Sub Directory 1
          > Sub Directory 2
          > .......
          > Sub Directory 600

The only option I see is going one by one but that would take a long, exhausting time. I don't want to compress all the folders into one Parent Directory either though. So is their any way to this fast, like an application or command? It doesn't matter if its zip, rar, etc.

I have found command lines like these:

```
for f in *; do zip -9r "$f.zip" "$f"; done
```

```
find . -mindepth 1 -maxdepth 1 -exec tar -czf {}.tar.gz {} \;
```

```
for i in * ; do zip -r /aaron/zipdir/$i.zip $i ; done
```

But either I'm not using them correctly or there is another issue? Any help would be awesome and save me lot of clicking. Thanks.

---

### Post by btindie on 2012-11-29
Try the following:
```
mkdir /tmp/archive
cd <Parent Directory>
find . -maxdepth 1 -type d ! -name . -exec tar -zcf /tmp/archive/'{}'.tar.gz '{}'/ \;
```

It'll place all the archives in the /tmp/archive directory.

The other method being:
```
for dir in *; do [ -d $dir ] && tar -zcf /tmp/archive/$dir.tar.gz $dir/; done
```

Both methods will only archive directories and their contents, ignoring normal files in the parent directory.

---

### Post by V13 Noob on 2012-11-29
Success!! Thanks for the quick response.

---

