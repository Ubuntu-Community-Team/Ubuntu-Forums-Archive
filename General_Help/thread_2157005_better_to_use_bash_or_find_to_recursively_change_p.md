---
title: "better to use bash or find to recursively change permissions?"
date: 2013-06-23
forum: General Help
---

### Post by HiImTye on 2013-06-23
I just want to know if it would be better to use find or bash to recursively check and adjust ownership/permissions as necessary. currently, I have a cronjob that runs this every 5 minutes on my shared folder that is writable for other users on the network, to allow them to have write permissions on new files
```

#!/bin/bash

in='/storage/Home Folder/Files/Downloads/Torrent/Complete/'

checkperm() {
 for f in *; do
  info=$(ls -l "$f")
  if [ -d "$f" ]; then
   perm=$(echo "$info" | grep -o 'rwxrwxr') 
   if [ -z "$perm" ]; then
    chmod 0775 "$f"
   fi
   (cd "$f"; checkperm)
  else
   perm=$(echo "$info" | grep -o 'rw-rw-r')
   if [ -z "$perm" ]; then
    chmod 0664 "$f"
   fi
  fi
  bobbisGroup=$(echo "$info" | grep -o 'tye bobbi')
  if [ -z "$bobbisGroup" ]; then
   chown tye:bobbi "$f"
  fi
 done
}
cd "$in"
checkperm

```
and then I run a similar one every 2 hours to set permissions on the (larger) folders that get files from there that are not writable by those users.

thoughts/opinions?

---

### Post by Vaphell on 2013-06-23
is there a reason why you bother to check the permissions and groups at all? It's not like dirs can end up with anything other than 755 and files with 644 so blanket finds and recursive chown will get the same end result

```
find "$in" -type d -exec chmod 755 {} \;
find "$in" -type f -exec chmod 644 {} \;
chown -R tye:bobbi "$in"
```

if you need file/dir properties better look into *stat *command instead of hacking them out from the *ls *output (*ls* probably gets them from *stat* anyway), eg
```
$ stat -c %a $HOME
755
$ stat -c %A $HOME
drwxr-xr-x

[ -d "$f" ] && [ $( stat -c %a "$f" ) != 755 ] && chmod 755 "$f"
[ -f "$f" ] && [ $( stat -c %a "$f" ) != 644 ] && chmod 644 "$f"

```

---

### Post by HiImTye on 2013-06-24
haha I thought it would be faster, but after recursively setting permissions back and forth, I see that's not the case.
classic case of over thinking

re: stat, I use that in one of my scripts to compare file sizes, but I use it so infrequently, that it never even came to mind lol, I just went with what I could remember off the top of my head ;)

thanks for the input, as always :D

---

### Post by CaptainMark on 2013-06-24
Is it not better to use bindfs to get a per folder umask effect, otherwise new files may not be accesible to other users until your cron job runs

See:
[http://www.linuxquestions.org/questions/blog/kribor-618996/howto-change-umask-permissions-ownership-etc-of-a-folder-using-bindfs-23934/](http://www.linuxquestions.org/questions/blog/kribor-618996/howto-change-umask-permissions-ownership-etc-of-a-folder-using-bindfs-23934/)

---

### Post by HiImTye on 2013-06-24
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
it's not an issue, it's for newly downloaded files, and the default permissions are 0644. they just may need to wait up to 5 minutes (after download completes) to move/delete

---

### Post by Vaphell on 2013-06-24
yes, it occured to me a bit later that depending on the number of objects there might be a non-negligible performance hit with blanket finds when compared to selective approach, after all they are going recursive on everything 3 times. Didn't bother to test the extent though.

btw, i forgot completely about the** find -perm** and **find -user**/**find -group**
eg to find non-755 dirs
```
find ! -perm 755 -type d
```
Maybe it still wouldn't eliminate the performance hit in this case, but it may prove useful in other situations.

---

### Post by HiImTye on 2013-06-24
I used```
time
```to test two versions, and while find was consistently more demanding, it finished consistently faster. here's the versions I tested:
version 1
```
#!/bin/bash

in1='/storage/Videos/'
in2='/storage/Music/'

checkPerms() {
 for f in *; do
  if [ -d "$f" ]; then
   chmod 0755 "$f"
   (cd "$f"; checkPerms)
  else
   chmod 0644 "$f"
  fi
 done


cd "$in1"
checkPerms
cd "$in2"
checkPerms
chown -R tye:tye {"$in1","$in2"}
```
version2```
#!/bin/bash
in1='/storage/Videos/'
in2='/storage/Music/'

find {"$in1","$in2"} -type d -exec chmod 0755 {} \;
find {"$in1","$in2"} -type f -exec chmod 0644 {} \;

chown -R tye:tye {"$in1","$in2"}
```
and the script I used to test (repeatedly, to filter out any system performance issues)```
#!/bin/bash
in1='/storage/Launchers/delugeNotOwn'
in2='/storage/Launchers/delugeNotOwn2'
echo "$in1
$in1
$in1
$in1
$in2
$in2
$in2
$in2" | while read -r in; do
 time "$in" 2> /dev/null
done
```

[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by steeldriver on 2013-06-24
Another possibility that might work for you is

```
chmod -R ug=rwX,o=rX
```

Note that any files that are already executable would remain executable - so not quite the same as 664 for **all** regular files

---

### Post by Vaphell on 2013-06-24
> and while find was consistently more demanding, it finished consistently faster

what would that mean? demand measured in what? disk thrashing, cpu load?

is there an improvement in find based way if you filter out stuff with * find ! -perm 755 -type d -exec ... \;* ? it should significantly cut down the number of executed *-exec* parts. I guess spawning suprocess is the main part of the overhead.

btw, interesting construction with that multiline echo
you could just use for-loop for that
```
for in in "$in1" "$in1" "$in1" "$in1" "$in2" "$in2" "$in2" "$in2"
```
or double for
```
for in in "$in1" "$in2"; do
  for i in {1..4}; do
    time ...
  done
done
```

in general for loops are for data sets you know and can enumerate in advance, while read is more suited for the stuff coming from the outside
Also when you pipe data to while read, you can't return any value back to the main script. redirection with < <( cmd ) or with <<< "string" is much better.

```
$ **v=test**
$ echo $'a\nb\nc\nd' | while read x; do **v=$x**; done
$ echo $v
**test**
$ while read x; do **v=$x**; done <<< $'a\nb\nc\nd'
$ echo $v
**d**
```

---

### Post by HiImTye on 2013-06-24
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
time lists an output such as```
real    0m20.297s
user    0m0.508s
sys     0m1.244s
```and while find consistently had lower 'real' time, both 'user' (user mode CPU seconds) and 'sys' (kernel mode CPU seconds) were higher

but it could be that time wasn't able to track the cpu seconds of the first script once it forked

---

