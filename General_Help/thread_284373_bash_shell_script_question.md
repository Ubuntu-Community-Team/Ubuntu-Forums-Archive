---
title: "bash shell script question"
date: 2006-10-25
forum: General Help
---

### Post by dorhelp on 2006-10-25
I am migrating a bunch of shell script programs from RH 7.3 to Ubuntu. 
I am having problems with some of my  shell scripts. Below is the first lines of the script through the line that causes the error and the error. This has always worked even back with AT&T unix any idea what I need to
do? The /usr/tmp directory is present and rwx by the user running the
script. The script is suppose to create the file.

# Mprice_ prints missouiri price list
TEMP=/usr/tmp/price
show=MO
echo "What type of price list do you want? (Q P)"
read style
echo "How many copies do you want? "
read copies
echo "^[E
" > $TEMP

/usr/local/lbin/Tent/Mprice_: line 9: /usr/tmp/price: No such file or
direc tory


Thank you so much
        Linda

---

### Post by po0f on 2006-10-25
dorhelp,

Does the script reside in your PATH?  It must be in one of the directories listed in the output of:
```
$ echo $PATH
```

[EDIT]

Blar, I thought you meant the script was /usr/tmp/price.  Maybe put a `touch $TEMP` at the top of the script?

---

### Post by dorhelp on 2006-10-25
Sorry this was stupidity on my part. I was just working with a bunch of C++ programs that used /usr/local/lib/tmp and was in that directory not /usr/tmp when I checked permissions! Atleast the touch made me realize what I had done.
                    Thanks
                     Linda

---

### Post by bsussman on 2006-10-25
the last two lines of your script don't make sense to me - but when I created and ensured writieability to the /usr/tmp, the script as presented worked for me.

---

### Post by bettlebrox on 2006-10-25
/usr/tmp is very odd. Try changing it to /tmp .

/tmp is a directory (or partition) for temporary files that are removed upon reboot.

---

### Post by dorhelp on 2006-10-25
Thanks, that is a good point. The tmp file is acutally removed when it is printed. Originally it used /usr/tmp because /usr and /tmp were on different partitions which mattered for some programs. Since the machines were almost never rebooted it gave me just one location to watch for tmp files that were left by idiots that used ctrl c to break out of programs.
                             Linda

---

