---
title: "can't restore backed up home folder"
date: 2007-09-09
forum: General Help
---

### Post by cm666 on 2007-09-09
I used the home user backup program which seems to have worked, in that it has created two files, an archive and a catalog file, both *.dar. The problem is when I run the home user restore program it doesn't do anything. It starts to open then disappears. Is there another program or command I can use to restore my data from these two files? Or is there a fix to get the home user restore program to work? Please help.

cm

---

### Post by wirawan0 on 2007-09-10
What program do you use? If you don't mind working from command line, then you can extract the backup using "dar" command-line program. You may need to install that program if you don't have it currently.

I'm not familar with DAR ([http://dar.linux.free.fr/](http://dar.linux.free.fr/)), but did you try using "dar" command line utility to view the content of the .dar file:

dar -l /path/your_archive_file

(no .dar extension). Then try testing for its integrity:

dar -t /path/your_archive_file

(again no .dar extension).

To extract, I think the command is like this:

dar -x /path/your_archive_file -R /home/your_user_name

The man page for dar is available here:

[http://dar.linux.free.fr/doc/man/dar.html](http://dar.linux.free.fr/doc/man/dar.html)

HTH. Good luck!

---

### Post by cm666 on 2007-09-10
Thanks,

that has done the trick. I had to use su to get the extract to work, and append the .dar on the file names.

Thanks again.
cm
:)

---

