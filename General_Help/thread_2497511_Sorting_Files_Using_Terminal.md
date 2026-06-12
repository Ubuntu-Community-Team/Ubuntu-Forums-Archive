---
title: "Sorting Files Using Terminal"
date: 2024-05-08
forum: General Help
---

### Post by wyattwhiteeagle on 2024-05-08
I have over 600 mp3 audio files.
In scripting, is there a way to sort these files into separate subdirectories while retaining a max size limit for the subdrectories?
Each subdirectory can hold no more than 100 megabytes.
(avoiding using "current working directory")

---

### Post by TheFu on 2024-05-08
Yes.
I'd probably just use EasyTag to tag the files with ID3 headers, then have it create and move the files based on those tags.  I've never done this myself, so be certain you make backups of anything you don't want to lose.

Or you could create a script.  Use this reference: [https://tldp.org/LDP/abs/html/](https://tldp.org/LDP/abs/html/)  Is covers everything.

For Music, I use a layout like this:
```
Music
&#9492;&#9472;&#9472; Genre
    &#9492;&#9472;&#9472; Artist
        &#9492;&#9472;&#9472; Album
            &#9492;&#9472;&#9472; 01-Track_name.ext
            &#9492;&#9472;&#9472; 02-Track_name.ext
```
I place a playlist file, .m3u, inside each album/ directory.  Playback is through **mpd** or a **jellyfin **media server or **mpv** that is fed a list of playlist files. Seldom, do I want to play just 1 file.  There are music players like clementine which can do this easier, at least on a desktop.  They have a client/server capability now so the music can be played locally or on the remote system.

Of course, if you have specialized desires for the sorting or how they are grouped, then scripting is likely the only answer.  When I needed split up some large directories with hundreds of files, but didn't have any real mandated organization, I'd typically start with looking at the filenames. If they were evenly spread across the alphabet, then I'd just create subdirs named, a, b, c, d, ..... z, then move all the files that started with 'a' in the the 'a/' subdir.  Simple.

---

### Post by dragonfly41 on 2024-05-08
Extending the EasyTag idea from TheFu  (I just installed EasyTag through Synaptic) this is another option for opening *.mp3 files indexed through Recoll. After indexing all desktop files (although you can narrow to media) search ext:mp3 and open with EasyTag (from list of media apps). The final stage in required workflow is routing *.mp3 files to prebuilt bins and Recoll can do that as well. A Helper script can be written to route selected *.mp3 to required bin (if that is needed). But truly Recoll as indexer makes it less necessary to have a hierarchy of folders (which you then have to remember). At least that is the way I now work. Recoll is my command hub to access multiple scattered file types.

---

### Post by currentshaft on 2024-05-08
a

---

### Post by wyattwhiteeagle on 2024-05-08
Can this also be done with "mkdir" and "size limit"? Something like...```
mkdir /home/wyatt/Desktop/Audio-001 size-limit=100M
```Then make the next directory after moving up to 100M to the Audio-001 directory

---

### Post by currentshaft on 2024-05-08
b

---

### Post by wyattwhiteeagle on 2024-05-08
> **currentshaft said:**
> Here you go. No warranty - use at your own risk, as I made in in 10 minutes on the morning toilet for entertainment purposes only.

```

#!/bin/bash

source_dir=mp3s
target_dir=music
size_limit=100000  # 100 Mb

n=0

while find $source_dir -mindepth 1 -maxdepth 1 | read ; do

  target="$target_dir-$n"

  if [[ ! -d $target ]] ; then mkdir $target ; fi

  while [[ $(du $target | awk '{print $1}') -lt $size_limit ]] ; do
    if find $source_dir -mindepth 1 -maxdepth 1 | \
        grep ".mp3" >/dev/null; then
      find $source_dir -type f -name "*.mp3" \
        -exec mv {} $target \; -quit
    else
      break
    fi
    sleep 1
  done

  n=$((n + 1))

done

```
I'm needing to make several subdirectories.
How should I edit the script above to accomplish this?
Or is the script repeated for each desired subdirectory?

---

### Post by currentshaft on 2024-05-08
c

---

### Post by wyattwhiteeagle on 2024-05-08
> **currentshaft said:**
> The script already makes directories, named music-N, where N starts at 0 and increments by 1 each time the previous folder reaches >10 Mb.
So the only things that need editing is the source and target?
Thanks for clearing that up for me.
Time for a bit of practice :)

---

### Post by dragonfly41 on 2024-05-09
After your experiments I suggest that you still experiment with Recoll+EasyTag to more easily index and find your collection(s).

---

