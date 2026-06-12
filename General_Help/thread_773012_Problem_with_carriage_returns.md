---
title: "Problem with carriage returns"
date: 2008-04-28
forum: General Help
---

### Post by kevpatts on 2008-04-28
Hey all,

I'm having a problem with two files that differ only by their carraige returns/line feeds. This doesn't seem to be the easy fix when you see when searching for a solution to this problem (the :%s/^M// fix), as these show up exactly the same in vim, even when I do ":set list" in both. I have two files that should be identical except one is 335 bytes and the other is 325 bytes. The larger file was created by piping the output of a find command IN CYGWIN, the smaller was the result of THE SAME COMMAND, but directly in Ubuntu.

I've attached the two files in a compressed file. How do I remove the extra invisible character from each line of the file called Yesterdays-Albums_head.txt? I've tried a good few things.

Kevpatts

---

### Post by kevpatts on 2008-05-06
Don't normally bump but I posted this on the day the Hardy was released so it kinda got lost in the mess of Hardy questions. Might get a better look at now.

Kev

---

### Post by danwood76 on 2008-05-06
There is a unix package for this very task.
Its called tofrodos.

The 2 executables it has are todos (Unix -> Dos) or fromdos (Dos -> Unix)
in your above example you just do:

```

fromdos -b Yesterdays-Albums_head.txt

```
The -b switch creates a backup called xxxxx.bak

---

### Post by kevpatts on 2008-05-06
Thanks a million Dan.

---

### Post by kevpatts on 2008-06-03
Dan,

That worked a treat, however, I've got one other strange problem with the same script, and it's to do with non-english characters. If, in my albums folder I run```
find . -mindepth 3 -type d
```then all looks fine, but when it runs inside my script these characters don't appear correctly. I've attached the incorrect resulting output from my script.

Thanks for your help,
Kev

---

### Post by danwood76 on 2008-06-03
can you post your script up?

-- edit --

I forgot to say the odd characters is probably to do with the character encoding, as the foreign characters are non ascii and are unicode instead.
Taking a look at your script might tell me why.

---

### Post by kevpatts on 2008-06-04
Dan,

I don't have the script to hand at the moment, but I'll post it when I get home. I have had a quick look into seeing if it could be a problem with the locales on my box but it doesn't seem to be. The file that's created by the script is a "Unicode UTF-8 English Text" file and the output of ```
locale
```is the same whether ouputted during or outside the script and is populated with all EN-IE.UTF8 (Ireland) apart from the last variable, LL_ALL which is blank in both cases.

Regards,
Kevin

---

### Post by kevpatts on 2008-06-04
Forgot to mention also that these directory structures are all on an NTFS drive. I don't think that is the source or the problem though cause, as stated before, the output is correct when the same command is run from the prompt.

---

### Post by kevpatts on 2008-06-04
The script is:```
#!/bin/bash

PREVIOUSPREFIX=Yesterdays-
DEPTHFILE=.depth.
AUDIODIR="/media/Windows/Documents and Settings/Kev/My Documents/My Music"
COMPLETEDIR="$AUDIODIR/Complete"
ORPHANDIR="$AUDIODIR/Orphan\ Songs"
LISTDIR="$AUDIODIR/Listings"
CHANGESDIR="$LISTDIR/Changes"
EXT=.txt
TEMP="$LISTDIR/temp-$$.txt"
index=1
date=`date +%Y%m%d`

cd "$LISTDIR"

for FILE in `ls -1p | fgrep -v / | fgrep .txt | fgrep -v Yesterdays- | sed "s/ /_/g"`
do
	mv -f "${FILE//_/ }" "$PREVIOUSPREFIX${FILE//_/ }"
done

cd "$COMPLETEDIR"
for DIRS in `ls -1p | fgrep / | sed "s/\///" | sed "s/ /_/g"`
do
	cd "${DIRS//_/ }"
	DEPTH=`ls -1 $DEPTHFILE* | sed "s/^$DEPTHFILE//"`
	OUTFILE="$LISTDIR/${DIRS//_/ }$EXT"
	OLDEROUTFILE="$LISTDIR/$PREVIOUSPREFIX${DIRS//_/ }$EXT"
	CHANGESFILE="$CHANGESDIR/$date-${DIRS//_/ }$EXT"
	echo "${DIRS//_/ } (Folder depth: $DEPTH)"
	find . -mindepth $DEPTH -type d | sed "s/^\.\///" | sort > "$OUTFILE"
	diff -ia "$OLDEROUTFILE" "$OUTFILE" | grep "^[<>] " | sed "s/^> /Added: /" | sed "s/^< /Lost:  /" >> "$CHANGESFILE"
	CHANGESCOUNT=`wc -l "$CHANGESFILE" | sed "s/^\([^ ]*\).*/\1/"`
	if [ "$CHANGESCOUNT" == "0" ]; then
		echo No changes.
		rm "$CHANGESFILE" > /dev/null 2> /dev/null
	else
		echo $CHANGESCOUNT changes.
	fi
	cd ..
done

cd "$LISTDIR"
rm $PREVIOUSPREFIX*$EXT

exit 0
```

---

### Post by kevpatts on 2008-06-05
No luck finding anyone with a solution to this I guess. Cheers though.

---

### Post by danwood76 on 2008-06-05
Ive had a few searches and there seems to be other people who have unicode issues within bash scripts.

My only experiance with scripting is perl, and I'm pretty sure ive parsed unicode filenames before when I built a gjukebox last year.

It might be worth looking into, although perl is different to bash and a little more CPU intensive its far more feature rich as it is a hugely expandable programming language.
Sorry I couldnt help out.

---

### Post by kevpatts on 2008-06-06
Thanks Dan. I'm going to ask a more specific question about the same problem andpossibly raise it as a bug.

Kevpatts

---

### Post by kevpatts on 2008-06-15
** BUMP **

Just in case anyone else can enlighten me on this?

Kevpatts

---

### Post by kevpatts on 2009-08-25
Bump again - a year later and still have this issue.

---

### Post by dcstar on 2009-08-26
> **kevpatts said:**
> Dan,

That worked a treat, however, I've got one other strange problem with the same script, and it's to do with non-english characters. If, in my albums folder I run```
find . -mindepth 3 -type d
```then all looks fine, but when it runs inside my script these characters don't appear correctly. I've attached the incorrect resulting output from my script.

Thanks for your help,
Kev

Your script is full of sed commands doing who-knows-what to the file name characters, not just that simple command.

Do normal debugging, comment out things and analyse the output of each step before assuming that everything works as you suppose it should.

---

### Post by kevpatts on 2009-08-26
Thanks David but I have done extensive testing and the output of that command is very different depending on whether it is running inside a bash script or not. It's nothing to do with the sed commands.

---

