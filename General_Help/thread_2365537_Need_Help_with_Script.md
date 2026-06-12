---
title: "Need Help with Script"
date: 2017-07-07
forum: General Help
---

### Post by scpatl4now on 2017-07-07
My knowledge of scripts is basic (and that's kind) so I need help.  I had to recover a 2TB disk using photorec.  I was able to recover everything but for some reason the file extension .mpg gives you a TON of garbage files mixed in with the valid ones.  What I need to do is find a script that will take all files in the directory smaller than say 20kB (that seems to be the dividing line between them...others are much larger) and move them to another folder so I can delete them.  If anyone can help me with this you are most definitely my favorite person in the world today (there are over 900 directories of mostly trash)

---

### Post by TheFu on 2017-07-07
```
$ find /tmp/path/to/the/directories/where/the/files/are -type f -size -20K -delete

```
This is a recursive delete - it will find all the files less than 20M below the specified directory and delete them.  It looks in all subdirectories too.  You probably want to be much more selective.  

Find is an impressive tool.  Be **very** careful.  Lots and lots of examples on the internet. Would be useful to review a few examples.  Also, the manpage for find is surprisingly useful.  **man find** will show it.

Update: update from -20M to -20K.

---

### Post by untrustytahr on 2017-07-07
> ** said:**
> ```
$ find /tmp/path/to/the/directories/where/the/files/are -type f -size -20M -delete

```



size -20[COLOR=#ff0000][B]K
[/B][/COLOR]
Assuming the OP actually meant kilobytes.  A copy/paste might include wrong files.

---

### Post by TheFu on 2017-07-07
Ooops.  I'll fix the other post ASAP!  But even 20M files will be pretty short.

I would probably include a *-iname \*mpg* too, BTW.

---

### Post by sisco311 on 2017-07-07
If you want to move the file before you delete them, try something like
```
mkdir ./target && find ./ -maxdepth 1 -iname \*.mpg -size -20k -type f -exec sh -c 'mv -- "$@" ./target' _ {} +
```
or
```
mkdir ./target && find ./ -maxdepth 1 -iname \*.mpg -size -20k -type f -exec mv -- -t ./target {} +
```

Note: for Kilobytes you have to use a lowercase K ;)

See also: [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

---

### Post by TheFu on 2017-07-07
Yep. I'm wrong again. Not my day. ;(

```
-size n[cwbkMG]
              File uses n units of space, rounding up.  The following suffixes
              can be used:

              `b'    for  512-byte blocks (this is the default if no suffix is
                     used)
              `c'    for bytes
              `w'    for two-byte words
              `k'    for Kilobytes (units of 1024 bytes)
              `M'    for Megabytes (units of 1048576 bytes)
              `G'    for Gigabytes (units of 1073741824 bytes)
```

---

