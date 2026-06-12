---
title: "xzvf command"
date: 2014-07-31
forum: General Help
---

### Post by AbhimanyuAryan on 2014-07-31
i was unzipping the tar file and i saw this xzvdf commad what is the purpose of this command. Also does -m and -u means? Thanks for the help :p:p

---

### Post by papibe on 2014-07-31
Hi AbhimanyuAryan.

xzvdf are tar options, not exactly a commands.

Some old commands like tar, used to have a relax syntax that allowed use options as they were parameters, i.e., '-x' as just 'x' (without the dash).

The version we used now, has backward compatibility, so you can use the old style or the new one: 'xzvdf',  '**[COLOR="#FF0000"]-[/COLOR]**xzvdf' or even '- x- z -v -d -f'.

You can read all about it by reading the documentation available on your own computer by running:
```
man tar
```
Or you can read the manual available here: [Ubuntu tar man page]("http://manpages.ubuntu.com/manpages/precise/en/man1/tar.1.html").

For useful examples and tutorials, take a look at this community documentation: [Introduction to tar]("https://help.ubuntu.com/community/BackupYourSystem/TAR").

Hope it helps. Let us know how it goes.
Regards.

---

