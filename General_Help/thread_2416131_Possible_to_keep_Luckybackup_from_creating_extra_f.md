---
title: "Possible to keep Luckybackup from creating extra folder?"
date: 2019-04-05
forum: General Help
---

### Post by 777funk on 2019-04-05
EDIT: To get to the quick version of my setup, see second post.

I am moving to a new install and have all my data in two locations (original and a daily backup copy) on the old machine. Here's what I'm wanting to use LuckyBackup and RSync to do:

Hypothetical and simplified Folder Structure:
[COLOR=#008000]/Home/A/B/C/[/COLOR]
and the "supposed to be" verbatim backup (simply in a different location which my wife mistakenly has been writing new files to)
/Media[COLOR=#008000]/Home/A/B/C/
[/COLOR]
moved to an external [COLOR=#ff0000]WD3TB HDD[/COLOR]

Now for some reason while I try to backup:
[COLOR=#008000]/Home/A/B/C/ [/COLOR]to my [COLOR=#ff0000]Western Digital 3TB[/COLOR] external backup simplified as such:
[COLOR=#008000]/Home/A/B/C/[/COLOR] >>>[COLOR=#ff0000] /external/WD3TB[/COLOR][COLOR=#008000]/Home/A/B/C/[/COLOR]
followed by:
 /Media[COLOR=#008000]/Home/A/B/C/[/COLOR]>>>[COLOR=#ff0000] /external/WD3TB[/COLOR][COLOR=#008000]/Home/A/B/C/[/COLOR]

and with the flag of only write files with newer dates, I am getting an additional layer of folders like this:
[COLOR=#ff0000] /external/WD3TB[/COLOR][SIZE=4][SIZE=5][COLOR=#0000cd]/Home[/COLOR][/SIZE][COLOR=#008000][SIZE=2]/[/SIZE][/COLOR][/SIZE][COLOR=#008000]Home/A/B/C/
[/COLOR]
Is there a way to avoid this? I don't really want an extra parent directory and most of the same data twice.[COLOR=#008000] 
[/COLOR]

---

### Post by 777funk on 2019-04-05
More specifically, here's what I mean. The LuckyBackup Task:
[ATTACH=CONFIG]282968[/ATTACH]

and the result... Yuk... a new child folder with the same name as the parent (don't want this of course) and several TBs worth of duplicated data from the parent to the child folder of the same name.

[ATTACH=CONFIG]282969[/ATTACH]

---

