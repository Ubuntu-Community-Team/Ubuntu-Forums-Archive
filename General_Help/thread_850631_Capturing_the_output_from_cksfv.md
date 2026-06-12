---
title: "Capturing the output from cksfv"
date: 2008-07-05
forum: General Help
---

### Post by markeee on 2008-07-05
Hi,

I'm trying to create a script which will run throuh dirs and perform sfv checks using cksfv and then take appropriate action depending on the result from cksfv


I can't seem to figure out how to assign the output from cksfv to a variable to use to check the result

Im trying to store the whole output from the cksfv command to a variable (so i can then cut and just use the last line i.e. 'everything ok' 

cksfv -f file.sfv


I've tried var=$('cksfv -f file.sfv') - which doesn't work 

var=`cksfv -f file.sfv` also doesn;t work

i wondered if perhaps it's because it checks numerous files so it's not a continous output stream 

any help greatly appreciated

Thanks


Mark

---

### Post by markeee on 2008-07-05
Anyone? this is seriously annoying me, ahhh!

---

### Post by ghostdog74 on 2008-07-05
why not try md5sum ?

```

md5sum * > md5sumfile
md5sum -c md5sumfile | grep "FAILED"

```

---

### Post by markeee on 2008-07-05
Thanks for the reply

surely that wouldn't work right? as i would be creating a new hash to verify the files

not verifying them against the hash supplied when the files were downloaded??

---

### Post by markeee on 2008-07-05
looks like it could work,

if i was to:

. open dir check for *.sfv
.create a new hash using md5sum
. then assign result of md5sum to a var, check the result and go from there


Any ideas why i can get the output of md5sum to be assigned to a var

i.e.

var=`md5sum -c file`
echo $var


but i cannot get var=`cksfv -f file` -- to work

echo $var when using the above outputs nothing

Thanks

Mark

---

### Post by ghostdog74 on 2008-07-05
ok, since you have a predefined sfv file, 
```

cksfv -f my_predefined_sfvfile 2>&1 | grep "different CRC"

```

---

