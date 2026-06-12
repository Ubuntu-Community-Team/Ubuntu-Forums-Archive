---
title: "Subversion is adding extra lines?"
date: 2007-08-15
forum: General Help
---

### Post by Naatan on 2007-08-15
Hi, I have a problem with subversion adding extra lines to a file, I am developing on Windows, then I do a commit to a Subversion repository that runs on a Ubuntu Edgy server, now on the Ubuntu server I do a checkout at the directory of the testing website, only now the files have a empty lines after each line of text.

Also it appears that the "^M" character is added, though this is hidden, it only appears when I use PHP to send an e-mail, in this case the ^M character appears after each line as well.

Anyone know what might cause this? I've tried switching from ANSII to UTF8 but this seems to make no difference.

---

### Post by tlacuache on 2007-08-15
Text files created on DOS/Windows machines have different line endings than files created on Unix/Linux. DOS uses carriage return and line feed ("\r\n") as a line ending, which Unix uses just line feed ("\n").

This is why when you view a text file created in Windows you see the ^M, it's the carriage return.

There's a package called tofrodos in the repositories which has some command line utilities for converting from one line ending to another. Alternatively, most decent editors will have a way you can set the line ending type manually, so you could do that before checking the file in.

Long story short, subversion isn't adding the characters, you're adding the characters when you create the file in Windows.

---

### Post by psusi on 2007-08-15
Most decent editors ( like emacs ) automatically detect the msdos line endings and ignore the carriage returns.  Also subversion has a property you can set on the files to specify that svn should convert the line endings for you to be the correct type for the machine you check out on.  See the subversion manual.

---

### Post by Naatan on 2007-08-15
Thanks both :) I managed to solve the problem, after I changed the setting in Subversion it was still adding the extra lines but then I used notepad++ to convert all the files to UNIX and now it works.

---

