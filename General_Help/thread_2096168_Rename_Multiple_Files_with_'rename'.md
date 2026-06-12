---
title: "Rename Multiple Files with 'rename'"
date: 2012-12-19
forum: General Help
---

### Post by phsleague on 2012-12-19
Hello All,

I have a bunch of files that I would like to rename and increment a number at the end of each renamed file (to keep them in order numerically).

For example:

from:

picture.jpg, picture5.jpg, picture90.jpg, picture12.jpg

to: 

picture1.jpg, picture2.jpg, picture3.jpg, picture4.jpg

Is it possible to use the 'rename' command to change all those files and putting it in order from 1 and so on.

I've been reading up on the rename command and learned some regexp on it, but I haven't figured out a way to increment it (1,2,3) at the end of each file name. So I'm curious if this is possible. 

Thank you.

---

### Post by vanadium on 2012-12-19
Some ideas here:
[http://stackoverflow.com/questions/3211595/renaming-files-in-a-folder-to-sequential-numbers](http://stackoverflow.com/questions/3211595/renaming-files-in-a-folder-to-sequential-numbers)

---

### Post by Vaphell on 2012-12-19
regexes don't do math, they are all about sequences of characters.

for-loop approach mentioned in the link is your best bet

---

### Post by wladypauly on 2012-12-19
May I suggest [gprename]("http://gprename.sourceforge.net/") - a tool I use just to do that - sequentially rename files? I think it's in the repos...

---

### Post by phsleague on 2012-12-19
Thank you everyone for the comments. I wasn't sure if regexp could do math. I'll look at the link and the tool also. Happy Holidays.

---

### Post by RedRat on 2012-12-19
If you don't mind using a GUI interface, I suggest Thunar file manager. It has an excellent renaming app built in.

---

### Post by phsleague on 2012-12-19
I checked out the link, and it is useful, but I'm not that good at bash scripts and I don't really have a clear idea on what the different scripts is doing, I partially get it. 

By luck, I was able to get it to work though by just playing around with it. But a step by step explanation of what the script is doing would help. If you have any bash tutorial sites that explains it would be great. 

I've searched for bash tutorials, but I haven't really found one that matches the examples in the link provided.

Thanks.

---

### Post by Vaphell on 2012-12-19
```
c=1 [COLOR="DimGray"]# counter set to 1[/COLOR]
for f in picture*.jpg; do [COLOR="DimGray"]#for each file matching picture<anything>.jpg, 1 at a time, do[/COLOR]
  new=$(printf "picture[COLOR="Teal"]%04d[/COLOR].jpg" ${c}) [COLOR="DimGray"]# create new name: picture[COLOR="Teal"]X[/COLOR].jpg where [COLOR="Teal"]X[/COLOR] is 0-padded value of the counter (4chars wide)[/COLOR]
  **echo** mv "${f}" "${new}" [COLOR="DimGray"]# rename current file to new name[/COLOR]
  ((c++)) [COLOR="DimGray"]# increment counter by 1[/COLOR]
done
```
*echo* before *mv* makes the command completely harmless, it merely prints the mv command that would be executed. If you are 100% sure the results are satisfactory, remove echo to actually perform *mv*. If you don't feel comfortable with bash, copy the files somewhere so you can revert if something goes wrong.
If the name formats before and after are the same, you potentially risk overwriting some file if the new number happens to land on already existing file. In such a case I'd rename to some other format like '__pictureX.jpg' to avoid collisions and then trim the __ with *rename* or with another for-loop.

---

### Post by phsleague on 2012-12-19
vaphell, thanks this was helpful. do you have a tutorial link where I can learn more about this. thanks.

---

