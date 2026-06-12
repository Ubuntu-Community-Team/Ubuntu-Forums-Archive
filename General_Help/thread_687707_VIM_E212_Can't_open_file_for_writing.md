---
title: "VIM E212: Can't open file for writing"
date: 2008-02-04
forum: General Help
---

### Post by zorkerz on 2008-02-04
I have gotten into a bad habit of opening every text file I want to edit by giving vim superuser privileges (sudo vim). I do this because I often do not know the permissions of the target file and don't want have to make my edits again.

 "Without sudo many files are unwritable returning this error in VIM. "E212: Can't open file for writing" and then on the next line it saysPress ENTER or type command to continue"

This last line made me think there could be a way to give vim the necessary privileges only when im ready to write instead of when opening the program. Is this possible?

---

### Post by zarqoon on 2008-02-04
I dont think its possible for vim to gain su while its already running. My advice is use su as little as possible and check for write ability before you edit. After opening a file with vim before you enter any command the bottom line shows the name of the file you are editing and if you dont have any write privileges there it will show [Read-Only] right next to the filename. In that case you can just reopen the file with sudo or change its permissions/owner

---

### Post by zorkerz on 2008-02-04
thanks i just found it waistful to have to check the permissions of every file by opening it or otherwise. Thats is why i open using sudo vim it saves me time and also why I was hoping to be able to give vim su powers afterwords only when it really needs them.

---

### Post by zarqoon on 2008-02-04
you can always just check the file permissions before opening it. Or just go by this
Everything in your home folder -> you should not need su in most cases
Everything else -> you most likely need su

---

