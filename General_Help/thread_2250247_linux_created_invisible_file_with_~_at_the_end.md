---
title: "linux created invisible file with ~ at the end"
date: 2014-10-27
forum: General Help
---

### Post by pull0betty on 2014-10-27
today I deleted a text file on my computer. When I went into the documents folder (where the file was) there was an invisible file with no .extention but ~ at the end of the file. When trying to open the file Ubuntu was searching for an application to open backup files which it could not find. I then added a .txt extention to it and could open it with gedit and to my surprise it was the deleted text file with its complete content. This seems rather irritating. Does linux Ubuntu (Gnome) do that?

---

### Post by sgoranov on 2014-10-27
Yep. Gedit especially, vim too. 
If you are using gedit you can turn of the automatic backups, check the settings.

Regards,
S.

---

### Post by lisati on 2014-10-27
The tilde ("~") at the end of a file name is a common equivalent of the ".BAK" file extension in MS-DOS/Windows.  :D

---

### Post by pull0betty on 2014-10-27
Well the weird thing is it didn't do that with any of my other text files.. and I don't seem to be able to see where this setting is? can you tell me where this setting would be? Ah just realize when I edit one of those files it will do the backup..

---

### Post by sgoranov on 2014-10-27
> **pull0betty said:**
> Well the weird thing is it didn't do that with any of my other text files.. and I don't seem to be able to see where this setting is? can you tell me where this setting would be?

Check this one bellow:
[http://askubuntu.com/questions/83026/prevent-gedit-from-creating-files-with-the-tilde-suffix](http://askubuntu.com/questions/83026/prevent-gedit-from-creating-files-with-the-tilde-suffix)

---

### Post by pull0betty on 2014-10-27
thanks a lot! that did the trick =)

---

### Post by Dennis N on 2014-10-27
> **pull0betty said:**
> Well the weird thing is it didn't do that with any of my other text files.. and I don't seem to be able to see where this setting is? can you tell me where this setting would be? Ah just realize when I edit one of those files it will do the backup..

Whether such files are created depends on the application that made the file, not the file type. Some don't offer any option to make backups. So you need to look at the settings or preferences of each application.

---

### Post by ajgreeny on 2014-10-27
Even the cli application nano gives you the option of making backups (with the -B option) which I have set as an alias in both my home .bash_aliases file, and also in root's .bashrc file so that nano always makes a backup of a file for me without the need for me to think ahead.

It's been a great help to me a few times as well, so don't dismiss it as something that is not needed; you just might need one of its auto-backed up files one day.

---

