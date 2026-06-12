---
title: "Bash help - split/use multi-line varaible"
date: 2018-07-11
forum: General Help
---

### Post by kazakore on 2018-07-11
Pretty sure I need to use IFS in some way but not managed to find any useful guides or snippets so much not be searching for the right things.

How would I make this split the dirl variable, with is a list of every subfolder from where the command was run, into single folder path strings so that can each be used and operated on as expected?

```
#!/bin/bash
dirl="$(find  -type d)"
if [ -d "${dirl}" ] ; then
  cd "${dirl}" && for f in *.flac; do sox "$f" -b 16 -t wav - -S | lame -b 320 -m j -q 0 - "${f%.flac}.mp3"; done 
fi 
```

Unsurprisingly if this is attempted in anything but a directory with no more directories in it then it just fails as the multi-line list of directories isn't recognised as a valid path.

---

### Post by steeldriver on 2018-07-11
You could do something like

```

find . -type d -print0 |
  while read -r -d '' dir; do
    (
      shopt -s nullglob
      cd "$dir" && for f in *.flac; do sox "$f" -b 16 -t wav - -S | lame -b 320 -m j -q 0 - "${f%.flac}.mp3"
      done
    )
  done

```

although perhaps it would be a whole lot simpler to just find the `.flac` files directly e.g.

```

find . -type f -name '*.flac' -execdir sh -c 'for f; do sox "$f" -b 16 -t wav - -S | lame -b 320 -m j -q 0 - "${f%.flac}.mp3"; done' find-sh {} +

```

---

### Post by kazakore on 2018-07-11
Well the top one works so that's good, the second one throws up an error I thought may just be due to a missing done to close it but doesn't seem to be. Also didn't understand why using the version that ends with the + sign, seems that should pass all the arguments at once from the manpage no?? I definitely need to read more!!



But I totally agree that finding the files and running the command on them, rather than the directory, would be much neater. A little history as to why this came about (not that it gives a valid reason but I did raise such things at the time but as it worked settled with it since then until now.)

Mainly the scripts were for my personal use to turn audio files into a format recognised by my mp3 player. At the time I had literally just started with Ubuntu and my Bash knowledge was literally zero and I had pointers for these scripts (I think through this forum but I'm not positive) and the result I ended up with was a messy two stage process, where I would run the find command which would then execute the transcoding script for each directory. It's not used so much but after ~4 years my Bash has gone from absolutely zero to barely intermediate and I felt it was time to try anf tidy up these scripts to at least be self-contained, and hopefully learn a little something at the same time.

---

### Post by steeldriver on 2018-07-11
Ooops yes I missed a `done` in the second one - should be correct now

---

### Post by kazakore on 2018-07-11
Ah i should have spotted the done belonged in there.

What's the find-sh? Google brings no useful results. I'm guessing it tells find to stop executing the sh? Then {} is the variable carried into it and does the + form at the end means it sends each it finds in turn?

Nice one though, definitely the kind of form I was originally looking for :)

---

### Post by Holger_Gehrke on 2018-07-12
> **kazakore said:**
> 
What's the find-sh? Google brings no useful results. I'm guessing it tells find to stop executing the sh? Then {} is the variable carried into it and does the + form at the end means it sends each it finds in turn?


When calling 'sh -c 'command-string' additional arguments are assigned to the positional parameter starting with **$0**. The 'for'-loop starts at **$1**. If you didn't pass an extra-argument, the command would not be executed for the first found file. Also $0 is used in warning and error messages, so assigning something sensible is a good idea. Using a '+' instead of a ';' at the end of the command passed to the -exec option of find makes it 'stuff'  as many found items as will fit into the command line. If you used a ';' it would be rather inefficient, since it would only put a single parameter per call.
What threw me for a loop here was the use of 'for variable' without 'in list'. Had to look it up in the bash manual page to find out that that's a short form of looping over the positional parameters.

Holger

---

