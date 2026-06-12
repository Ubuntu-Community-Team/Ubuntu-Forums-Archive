---
title: "Find files feature not working?"
date: 2018-09-02
forum: General Help
---

### Post by iamtheeggman2 on 2018-09-02
Hi I am trying to locate a file on the hdd however the search function in the file viewer PCManFM 1.2.5 doesn't bring up any results of known filenames, any ideas? Thanks in advance.

i have discovered it works if you put in the filename but I dont know the exact filename of the file i'm after?

Do any of you use a decent file manager in Ubuntu that is as capable as the one you get in windows including a file search facility?

---

### Post by Holger_Gehrke on 2019-01-17
Thunar - the filemanager of XFCE / XUbuntu - integrates the search tool 'catfish' quite well (there's a menu item 'Search in the current folder' in the 'File'-menu and an item 'Search in this folder' in the context-menu of any directory; both will start catfish and set the starting point for the search). catfish can be installed without thunar and if I remember PCManFM right then it should be possible to add an action to it to use catfish.

Beyond that I use 'find' on the command line; as long as you're searching for something and don't want to / need to search the contents of files, find has all the tests and actions you could possibly want.

Holger

---

### Post by dragonfly41 on 2019-01-17
And if you *do* need to search for files containing some string pattern there is [ripgrep]("https://github.com/BurntSushi/ripgrep")
or even searchmonkey (a gui).

---

### Post by HermanAB on 2019-01-18
The find command very fast and you can put multiple wild cards in the search string:
$ find ~ -name *what*ever*

---

