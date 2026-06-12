---
title: "How can I undo the shred command?"
date: 2014-12-03
forum: General Help
---

### Post by andrew_niklawski on 2014-12-03
So I really messed up. I wrote a three-page document for my English class (I'm in high school). I finished it yesterday. I saved it as "giuseppe.docx" in LibreOffice because the name fits if you have read the story. I always misspell "giuseppe" so today, I created a symbolic link (in the same directory) called "g.docx" via ```
ln -s
```. I decided I didn't need the symbolic link, so with my working directory in the same directory as both files ($HOME/Documents), I ran ```
shred g.docx
```. I immediately realized that you're not supposed to be able to shred symbolic links. So, just in case, I immediately attempted to open the original giuseppe.docx in LibreOffice. Just my luck, it decided to shred the original file. The file now reads (via ```
nano
```, Gedit, LibreOffice itself, and all other text editors) as it does in the following link (I tried pasting it into the post text box thing and it decided to have a metaphorical seizure): [https://docs.google.com/file/d/0ByTgD6076H73N0tJQ19Qazd3ZzA/view](https://docs.google.com/file/d/0ByTgD6076H73N0tJQ19Qazd3ZzA/view)

Any help with recovering the file would be greatly appreciated as I'm currently failing English class and turning this assignment in would bring me up to a B minus.

Thanks!

---

### Post by Bucky Ball on 2014-12-03
Welcome. Your link gives me an error and I can't see your document. Ironic.

---

### Post by Habitual on 2014-12-03
n/m. I'm punch drunk after 15 hours on the computer.
Sorry.

---

### Post by andrew_niklawski on 2014-12-03
> **Bucky Ball said:**
> Welcome. Your link gives me an error and I can't see your document. Ironic.

As I said before, I shredded the file. It's a .docx and unless I change the file extension to .txt, it'll say there's an error. You're gonna need to download it and open it in LibreOffice or nano or whatever you would like.

---

### Post by coldcritter64 on 2014-12-03
> Welcome. Your link gives me an error and I can't see your document. Ironic.                 Hi Bucky Ball, I just downloaded the file from google docs and tried opening with libreoffice. 
It asks for Character set etc.; then when actually opened with "utf-8" has scrambled looking contents. If that is the original file posted on google docs this is not looking good for the OP. See the attached screenshots.

Shred _*without*_ the "iterations" (-n) switch or the remove switch (-u), as used by the OP, will overwrite a file 3 times with data and leave the scrambled file behind as has happened here.
 
> shred g.docxSorry OP, going by what you posted on google docs, that file is gone forever. It has been overwritten 3 times at least. The file is still on the system but is corrupted by the shred command. 

When using the trash bin and even after emptying it is sometimes possible to pull back a file with tools like "testdisk". Not this time though as the shred command actually does repeated write operations on a file _*contents*_ even if accessed from a link.

Bad news for that file sorry OP, but if you take a lesson from this use only the trash can for deleting files never a terminal command, even with emptying the trash, files can sometimes be recoverable. Terminal commands particularly "shred" and "dd" can be catastrophic to your data, use them with extreme caution and only as needed.

Directly overwriting a file 3 times leaves no hope of recovery. Being a "write" operation, even on a link, it overwrites the original file that is being linked to.
**Edit:** I should add using the trash bin on a link WON'T remove the original file. Your file would have been safe if you had "trash binned" the link.

---

### Post by mc4man on 2014-12-03
If you happened to enable backups in lo writer  then you may find a copy in ~/.config/libreoffice/4/user/backup 
(-though it's not enabled by default.. so I'd think you'd remember doing so...

---

