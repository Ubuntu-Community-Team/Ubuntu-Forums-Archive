---
title: "Command Reqeuest"
date: 2007-12-26
forum: General Help
---

### Post by Salazar420 on 2007-12-26
So, basically I need a command, mostly for my own knowledge. Say, I'm in a directory. There are multiple multimedia files, if not hundreds. The file extensions vary: .avi ; .mp3 ; .mpg ; .mpeg ; etc. So, my desired affect is: I need all of these files to be "hidden" (in other words, I need to rename them all with no changes other to the names other than a '.' in front of them all). This potentially needs to be done without copying the files, therefore I wont have multiples of the same file; however, they can be copied, ,but I need it all to be one command, so maybe we could pipe a 'rm' command to remove all of said files that don't begin with a '.'. Also, if possible, I need to link in a command for excluding certain filetypes; say, mp3, for example. Could anyone assist me in such a command? Again, this is purely for edcational purposes, should I need such a command in the future.

P.S., I need to make my 'u' key work again, damn it! It's very inconsistent.

Footnote: note that the postscript was basically a footnote to myself, and now the footnote to myself has become the postscript to all of you.

P.P.S. I'm just messin' around.

---

### Post by HermanAB on 2007-12-26
Read the man page on 'find'.  Then Google for a few examples.

Cheers,

Herman

---

### Post by Salazar420 on 2007-12-26
Ty. Will do. Ironic, I was just reading about the find command at the eighth link here: [http://www.google.com/search?hl=en&q=filetype%3Apdf+linux.commands&btnG=Google+Search]("http://www.google.com/search?hl=en&q=filetype%3Apdf+linux.commands&btnG=Google+Search") , but didn't realize it's capabilities. I will read more on the matter.

---

### Post by dagnabit dang doohickey on 2007-12-26
This command will recursively prefix every file below the current directory with a dot, except those files with an .mp3 or .m4a extension.
```
find . -type f | grep -v "\(\.mp3$\|\.m4a$\)" | rename 's#^(.*\/)#$1\.#'
```
This command will recursively remove the leading dot from every file below the current directory, except those files with an .mp3 or .m4a extension. (This command differs from the above only where the escaped dot appears in the rename pattern.)
```
find . -type f | grep -v "\(\.mp3$\|\.m4a$\)" | rename 's#^(.*\/)\.#$1#'
```
Remember: These commands are *recursive* and they will rename *every file* except the ones omitted by the grep pattern.

---

### Post by Salazar420 on 2007-12-29
Thank you for the response. Definitely gtk.

---

