---
title: "sed display line after string match? help?"
date: 2007-02-19
forum: General Help
---

### Post by inonzi_prowler on 2007-02-19
hello all.

so i'm sending some text (xml) to sed and I have a particular string that I can match.

Thing is, I need the line *after* the string to be displayed.

text looks like this:

> 
        <versionEffectiveDate>2006-10-27</versionEffectiveDate>
        <Counterparty>
            <standardPartyId>0141747</standardPartyId>
        </Counterparty>
        <Owner>
            <standardPartyId>7066589</standardPartyId>
        </Owner>


I need the line that comes after the string <Owner> (i.e. the line with 7066589 in it).

I've tried this:

cat file.xml | sed -n -e '/<Owner>/n'

but I get nothing returned. I need to do this on a whole bunch of files.

Many thanks in advance for any replies.

---

### Post by inonzi_prowler on 2007-02-19
oh yeah the line <Owner> only appears once per file, but the pattern <standardPartyId> appears quite often (as you would have probably gathered).

---

### Post by sdide on 2007-02-19
Do 
$ cat file.xml | grep -A 1 <Owner>

---

### Post by inonzi_prowler on 2007-02-19
^ yeah, that was the 1st thing that i tried.

old version of sed. no supporty "-A"

---

### Post by sdide on 2007-02-19
I wrote grep, not sed

---

### Post by inonzi_prowler on 2007-02-19
> **sdide said:**
> I wrote grep, not sed

sorry i mean old version of grep. i tried that first with grep then moved onto sed. trying this on solaris 5.8

---

### Post by darrenm on 2007-02-19
About the nastiest, hackish way I can think of. In a rush so may be easier cleaning this up a bit

```
line_num=`cat -n tst | grep "<Owner>" | awk '{print $1}'` ; let "line_num++" ; echo $line_num ; cat -n tst | sed s/" "//g | grep ^6  | awk '{print $2}'
```

---

### Post by inonzi_prowler on 2007-02-19
> **darrenm said:**
> About the nastiest, hackish way I can think of. In a rush so may be easier cleaning this up a bit

```
line_num=`cat -n tst | grep "<Owner>" | awk '{print $1}'` ; let "line_num++" ; echo $line_num ; cat -n tst | sed s/" "//g | grep ^6  | awk '{print $2}'
```


thanks man.

as it happens i ended up chucking it into a script:

```

#!/bin/sh
cat TRADES-28.txt | db_icmisnoop uat2 ugw -p | sed -n '
/<Owner>/ {
N
/\n.*<standardPartyId>/p
}' > TRADES.day1.txt

```

and then took out the lines i didn't want using vi. dirty and hacky but i'm feeling kinda laaaaaaazy today.

---

### Post by inonzi_prowler on 2007-02-19
plus i only just moved onto unix/linux from windows so learning scripting and whatnot.

it's pretty cool.

---

### Post by stylishpants on 2007-02-19
FYI this is the answer to your original question about how to display the line after a string match:

```
 sed -n '/pattern/ {n;p}'
```

---

### Post by darrenm on 2007-02-19
Fair enough, yours is not as dirty anyway ;)

---

### Post by darrenm on 2007-02-19
> **stylishpants said:**
> FYI this is the answer to your original question about how to display the line after a string match:

```
 sed -n '/pattern/ {n;p}'
```

Wow. One to remember :D

---

### Post by inonzi_prowler on 2007-02-19
> **stylishpants said:**
> FYI this is the answer to your original question about how to display the line after a string match:

```
 sed -n '/pattern/ {n;p}'
```

on solaris 5.8 version of sed it no likey.

command garbled broken pipe error. i'll try it on kubuntu when i get home.

---

### Post by stylishpants on 2007-02-19
> **inonzi_prowler said:**
> on solaris 5.8 version of sed it no likey.

command garbled broken pipe error. i'll try it on kubuntu when i get home.

Often Solaris sysadmins will install the Gnu toolchain on their systems to avoid dealing with the hoary old solaris versions, so they can avoid problems like this.

You may have gnu sed available under another name, such as 'gsed'.  

Or possibly just 'sed', but located at a different path.

---

### Post by inonzi_prowler on 2007-02-19
> **stylishpants said:**
> Often Solaris sysadmins will install the Gnu toolchain on their systems to avoid dealing with the hoary old solaris versions, so they can avoid problems like this.

You may have gnu sed available under another name, such as 'gsed'.  

Or possibly just 'sed', but located at a different path.

yes, i think that there is some kind of arrangement like that here. i must investigate.

toolchain? that sounds pretty suggestive.

---

### Post by sdide on 2007-02-19
```
$ cat -n file.txt | grep  `cat -n file.txt | grep <Owner> | awk {'print $1+1'}` 
```

---

