---
title: "vbr encoding"
date: 2005-05-20
forum: General Help
---

### Post by remin on 2005-05-20
Ok, i've been trying to find out how I can encode mp3's using vbr -alt preset standard using lame.
Has anyone got any ideas how I can do this?? All I can find is apps that encode in CBR.
Damn this is annoying me now.....  ](*,)

---

### Post by remin on 2005-05-20
Ok, thanks to my fellow members at Atomic, i've been pointed to some answers for this question.

Post By **Redhatter** 
Actually... keep an eye out... some time back there were plans to port CDex to Linux. :-)

In any case... nothing beats good ol' shell scripts. :-)

```
#!/bin/sh 
 
STARTTRACK=$1 
ENDTRACK=$2 
ALBUM=$3 
ARTIST=$4 
 
TEMPDIR=/tmp/$$ 
DESTDIR=/path/to/mp3s/@ARTIST/@TITLE.mp3 
 
# Switch to temp directory 
mkdir -pv $TEMPDIR || exit 1 
cd $TEMPDIR 
 
# Rip the tracks from CD 
cdparanoia -B -- "${STARTTRACK}-${ENDTRACK}" 
 
if [ "$ARTIST" ]; then 
    artist=$ARTIST 
fi 
 
# Encode them as MP3 
for file in track*.wav; do 
    if [ -z "$ARTIST" ]; then 
        echo -n "$file Artist: " 
        read artist 
    fi 
    echo -n "$file Title: " 
    read title 
 
    # Work out output filename and path 
    outfile=${DESTDIR//@ARTIST/$artist} 
    outfile=${outfile//@ALBUM/$ALBUM} 
    outfile=${outfile//@TITLE/$title} 
    dir=$( dirname "$outfile" ) 
 
    # Make sure the directory exists :-) 
    if [ ! -d "$dir" ]; then 
        mkdir -pv "$dir" || exit 1 
    fi 
 
    # Encode the file 
    if ( lame --vbr-new --tt "$title" --ta "$artist" --tl "$ALBUM" "$file" "$outfile" ); then 
        rm -fv "$file" || exit 1 
    else 
        exit 1 
    fi 
done 
 
# Switch back to previous directory and clean up. 
cd $OLDPWD 
rm -fr $TEMPDIR 

```


Copy and paste the above into a file, say 'ripper.sh', chmod it 755, then let 'er rip. :-)

Post By **altorus**
[http://lly.org/~rcw/abcde/page/](http://lly.org/~rcw/abcde/page/)

ABCDE is your friend

There you go for anyone wanting to do this as well.

---

