---
title: "Problem using find and xargs"
date: 2008-04-28
forum: General Help
---

### Post by quixote on 2008-04-28
Linux question rather than ubuntu problem, but I'm hoping someone here can help!  I'm using Imagemagick to create thumbnails for a large directory tree.  The only thing I can't see is how to get it to write the thumbnails to a "thumbs" subdirectory!

Either of these two commands from the Imagemagick site  [http://www.imagemagick.org/Usage/basics/#mogrify_not](http://www.imagemagick.org/Usage/basics/#mogrify_not) does most of the job:
 ```
find -name '*.jpg' | xargs -n1 sh -c 'convert $0 -format gif -thumbnail 160x160 thumbs/$0.gif
```
which gives me this error
```
`thumbs/./Moorpark/PCR-Workshop/03intro.jpg.gif': No such file or directory.
```
or this one
```
find * -name '*.jpg' -exec convert '{}' -format gif -thumbnail 160x160 thumbs/'{}'.gif \;
```
which gives me this error:
```
`thumbs/Moorpark/PCR-Workshop/03intro.jpg.gif': No such file or directory.
```

Either way, that thumbs subdirectory is always assumed to be relative to the dir from which the command was executed rather than the subdir being processed. It'll process and rename files in the top level dir just fine.

How the hell do I tell it to look for "thumbs" under the subdir it's processing?  ??  I've studied the man pages, tried googling everything I could think of, tried variants I invented (that was the most hopeless of all!) and gotten nowhere.

I did manually make all those "thumbs" subdirectories.  Ideally, I'd also like to be able to tell it to make that directory on the fly, but that's my next problem, unless someone has the answer. :D

---

