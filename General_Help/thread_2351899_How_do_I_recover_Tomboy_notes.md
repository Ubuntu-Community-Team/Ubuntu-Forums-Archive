---
title: "How do I recover Tomboy notes?"
date: 2017-02-07
forum: General Help
---

### Post by truepurple2 on 2017-02-07
For some reason a bunch of tomboy notes of mine have vanished for no apparent reason. Hopefully it is not because my system is compromised or something. I really need to recover those files. Though my Tomboy installation itself says there is no way to recover deleted notes, I found a online resource talking about it. But there are still issues.

[https://wiki.gnome.org/Apps/Tomboy/Backup](https://wiki.gnome.org/Apps/Tomboy/Backup)
[https://wiki.gnome.org/Apps/Tomboy/Directories](https://wiki.gnome.org/Apps/Tomboy/Directories)

So I found the folder it was talking about, managed to open these files with "notepad", but none of the backup files are the missing files. Only two files in backup even had much in them.  I looked through the other files in the main Tomboy directory even though I am pretty sure they all show in the program, but none of those were it either.

Maybe I should try some restore hard drive program? 

Any suggestions/concerns etc? Was I hacked? Could my HDD be failing? How might I get these files back?

---

### Post by dragonfly41 on 2017-02-07
First set aside the worry about being hacked.
Since tomboy notes end with ".note" extension, start by searching throughout your entire filesystem.
```
sudo updatedb
sudo locate .note
```

The first command line might take several minutes to complete since it indexes all your files. There is no returned output.
The second line is the one which searches.

Compare the list of located files with the ones you see through say Nautilus or Thunar.

---

### Post by ajgreeny on 2017-02-07
They should all be in **/home/*username*/.local/share/tomboy/** so enable hidden files and folders with Ctrl+H and have a look there.

---

### Post by truepurple2 on 2017-02-08
> Compare the list of located files with the ones you see through say Nautilus or Thunar.

You mean when I just search using regular search? This sudo locate .note might find more than that search, even with regular search set to find hidden files too? 


[**[COLOR=#C61919][B]@ajgreeny**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=27747")

I mentioned already having done what you advise me to do in my original post. I also looked through **/home/*username*/.local/share/tomboy/backup **and told the results.

I am using a different borrowed PC at the moment, I am concerned that if I keep using that PC, if the missing tomboy notes were somehow deleted, using the OS it is on might overwrite those and make recovery more impossible. 

I also found some other clues since having wrote the original post. It might be that all the missing notes were notes I had opened when I had closed down my PC the night before, I am not sure for all of them, but at least some of them. And I found a Tomboy log where it errors trying to access a number of notes. Presumably Tomboy trying to open all those notes again (since Tomboy reopens what was open upon closing when restarting)

---

### Post by truepurple2 on 2017-02-18
Dragonfly starts helping me but then ignores my followup questions.  Ajhgreen tells me to look somewhere I mentioned looking in the original post. It's been a week since then with nothing but silence. 

Would someone please help.

---

### Post by wildmanne39 on 2017-02-18
You can bump your thread once every twelve hours and it is up to you to do so if you go away and let the thread get stale that is on you at this point, you will not get much help by complaining about the people that have tried to help you so far, this is a community of volunteers and we all donate our time.

I do not know the answer or I would help you.

---

### Post by oldos2er on 2017-02-18
Edited a couple posts to bring them in line with the Code of Conduct.

---

### Post by dragonfly41 on 2017-02-18
I'm sorry I could not add much more than I wrote above.

Although I still use Tomboy I have read that tomboy note loss does occur.   
I tend to backup my Tomboy notes.

Here is one of many threads if you just Google search "recover Tomboy notes".

[https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/580333](https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/580333)

There is a tomboy.log in ~/.config/tomboy/tomboy.log.

Personally I have moved to cherrytree as my main note manager.
If you install cherrytree there is an option to import Tomboy notes.

Returning to your problem, the chances of recovery seem slim.

If the notes are very important you could try a data recovery tool such as testdisk or photorec to look for deleted files.

---

