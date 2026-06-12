---
title: "scp and Special Characters"
date: 2006-09-15
forum: General Help
---

### Post by hiptahop on 2006-09-15
I am trying to use scp to transfer a file, but the file and its folder have special characters and neither quotes nor \'s fix the problem.  The characters are commas and parentheses.

File:
~/Media/Title, The/File Name (Xvid).avi

Failed Syntaxes:
scp user@host:Media/Title\,\ The/File\ Name\ \(Xvid\).avi user@otherhost

scp "user@host:Media/Title, The/File Name (Xvid).avi" user@otherhost

scp user@host:"Media/Title, The/File Name (Xvid).avi"

Error for \'s:
bash: -c: line 0: syntax error near unexpected token `('
bash: -c: line 0: `scp -f File Name (XviD).avi'

Error for quotes:
scp: /home/user/Media/Title,: No such file or directory
scp: The: No such file or directory

I'm attempting to securely transfer files from my ubuntu box to my (new... woo hoo!) MacBook.  I'm working from my laptop and the results are the same whether I ssh into the box or work directly from terminal.

Can I use boolean operators?  What is the proper syntax?!

---

### Post by hiptahop on 2006-09-16
I found a solution (but unfortuneately no explanation).

Asterisks.

scp user@host:Media/Title*/*Name* user@otherhost

---

