---
title: "Library folder location"
date: 2015-03-15
forum: General Help
---

### Post by michael-piziak on 2015-03-15
If I click through folders and hidden folders, where is the library/libraries folder at ?

---

### Post by ajgreeny on 2015-03-15
There is no simple answer to that question; they could be anywhere depending on the application and how and where it was installed.  Most, however, are in the system folders **/lib** or **/usr/lib**, there's a clue in their names.

Have a look at sites which tell you more about the linux filesystem hierarchy to understand more.
[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)
[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)

---

### Post by michael-piziak on 2015-03-16
Thanks.

I found one of the library files in /usr/lib.  I attempted to delete it but it wouldn't let me.

I was trying to delete Higan's (emulator) library file as it keeps games in it's list that I have removed or don't use.    (I've already deleted Higans preference but that didn't purge it).

---

### Post by ajgreeny on 2015-03-16
The command **sudo apt-get autoremove** might get rid of it for you if that library package was a dependency of higans (whatever that is) as it will no longer be needed, but frankly I would not bother.

You can have lots of library files and packages installed, but if they are not being used they do nothing except take up a small amount of space; it is not like Windows where masses of left-over files, libraries and dll files can mess up registry and slow the system.

---

### Post by michael-piziak on 2015-03-16
Well, my reason for trying to do so is that when Higan is run, it has a list of games that it has imported and can be used.  The list contains names of games that I no longer want or use.

Actually, Higan imports and saves another copy of the rom that suits it - it does this somewhere.  I know this because when I delete a game rom, it's still in Higans list and can still be run.

---

