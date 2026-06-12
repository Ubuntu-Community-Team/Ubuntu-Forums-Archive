---
title: "bash script for mencoder"
date: 2014-04-24
forum: General Help
---

### Post by davidwillis on 2014-04-24
I think this should be easy, but I don't know how to do it.  I would like to make a script that would execute these two lines:

mencoder <input.mp4> -ovc xvid -oac mp3lame -lameopts cbr:br=128 -xvidencopts pass=1 -o /dev/null
mencoder <input.mp4> -ovc xvid -oac mp3lame -lameopts cbr:br=128 -xvidencopts pass=2:bitrate=-<filesize> -o <output.avi>

I would like to be able to just run something like:

convert video.mp4 700000

And the script will run those two lines and output a video.avi 

I don't think this should be too hard, but maybe I am wrong.

Thanks

---

### Post by cbraxton on 2014-04-24
I would probably do something quick and dirty like this:

```

INFILE=$1
OUTFILE=`echo $INFILE | cut -d . -f 1`.avi
BITRATE=$2

mencoder $INFILE -ovc xvid -oac mp3lame -lameopts cbr:br=128 -xvidencopts pass=1 -o /dev/null
mencoder $INFILE -ovc xvid -oac mp3lame -lameopts cbr:br=128 -xvidencopts pass=2:bitrate=-$BITRATE -o $OUTFILE

```

It won't work for files that have more than one "." in the name, and for that matter you'd need to add quotes around the filenames if you have embedded spaces.

---

### Post by andrew.46 on 2014-04-24
Have a look at xvidenc which should do all of this and a great deal more :)

---

### Post by davidwillis on 2014-04-25
> **cbraxton said:**
> I would probably do something quick and dirty like this:

```

INFILE=$1
OUTFILE=`echo $INFILE | cut -d . -f 1`.avi
BITRATE=$2

mencoder $INFILE -ovc xvid -oac mp3lame -lameopts cbr:br=128 -xvidencopts pass=1 -o /dev/null
mencoder $INFILE -ovc xvid -oac mp3lame -lameopts cbr:br=128 -xvidencopts pass=2:bitrate=-$BITRATE -o $OUTFILE

```

It won't work for files that have more than one "." in the name, and for that matter you'd need to add quotes around the filenames if you have embedded spaces.

Thanks.... That is what I was looking for  :)

---

### Post by Vaphell on 2014-04-25
instead of that pipe
```
outfile=${infile%.*}.avi
```

---

### Post by davidwillis on 2014-04-26
> **andrew.46 said:**
> Have a look at xvidenc which should do all of this and a great deal more :)

Thanks... I am installing that now to give it a try

---

