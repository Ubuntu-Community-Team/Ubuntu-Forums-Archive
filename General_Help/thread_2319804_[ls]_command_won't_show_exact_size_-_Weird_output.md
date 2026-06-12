---
title: "[ls] command won't show exact size - Weird output"
date: 2016-04-07
forum: General Help
---

### Post by pants2 on 2016-04-07
I am trying to find the size of the files on my hard drive in exact bytes, but whenever the size gets too big the number turns all weird (like 1.98329e+12). Can I stop it from doing this or convert this into exact bytes?


The command is:
ls -lR | grep -v '^d' | awk '{total += $5} END {print "Total:", total}'


Picture of exact bytes
[http://i.imgur.com/ltoVTKj.jpg](http://i.imgur.com/ltoVTKj.jpg)


Picture of weird number
[http://i.imgur.com/LHa23x6.jpg](http://i.imgur.com/LHa23x6.jpg)


-The cut-off point before it stops showing exact bytes seems to be around 500gb
-The command [du -sb] properly shows exact bytes no matter how big the directory is.
-I have tried Ubuntu Gnome 15.10 64bit (Japanese and English) and Linux Mint 17.3 Cinnamon 64bit (Japanese)
-My drives are ntfs so I tried formatting one as ext4 and copying my files over. The results are same as ntfs.

---

### Post by Impavidus on 2016-04-07
It seems awk decides to switch to scientific notation. I don't know much about awk, but if you search the documentation you may find an option to prevent this. It seems there is an option to use formatted output using printf instead of print. This may fix it.

As du -sb gives the desired results, why not simply use that command?

---

### Post by papibe on 2016-04-07
Hi pants2. Welcome to the forum ):P

First, you need to initialize your total variable:
```
ls -lR | grep -v '^d' | awk '**BEGIN{total = 0}** {total += $5} END {print "Total:", total}'
```
Then it should be OK, but if not, using an explicit printing format should solve that problem. For example:
```
... {printf "Total: %d\n", total}'
```
or
```
... {printf "Total: %.0f\n", total}'
```
If you don't mind commenting on the script itself, I'd recommend avoiding 'ls' as the source of your file list, and file sizes. For instance, 'find' would do better job at finding just files:
```
find -type f
```
as for getting the file size, I would use either 'du' or 'stat', e.g.:
```
$ du -b ./disk_info.txt 
3270	./disk_info.txt

$ stat -c %s ./disk_info.txt 
3270

```
Then all together:
```
find -type f -exec stat -c '%s' {} \; | awk 'BEGIN{total=0} {total+=$1} END {printf "Total: %.d\n", total}'
```
Hope it helps. Let us know how that goes.
Regards.

P.S.: you can get the same result by running:
```
$ du -bs .
```
or this for a human-readble amount:
```
$ du -bsh .
```

---

