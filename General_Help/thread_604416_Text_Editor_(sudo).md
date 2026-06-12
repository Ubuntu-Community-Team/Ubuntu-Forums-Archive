---
title: "Text Editor (sudo)???"
date: 2007-11-06
forum: General Help
---

### Post by calvinc on 2007-11-06
Hello,

This may seem a very newbie question but I do have some limited Linux experience.  I've just installed Ubuntu on my MacBook and am going through the Ubuntu Community help page on how to complete the installation (sound, sleep, etc.) and need to edit some files in the /etc folder.  Obviously these are all root owned and when editing them with the TextEditor I cannot save them.

1) Why does it not let me attempt to save them but then ask for the root password?
2) I have changed my user to belong to the root group but still nothing.
3) Is the only way to do this through the terminal (sudo vi filename)?

Thanks,
Calvin.

---

### Post by mpierce on 2007-11-06
You edit them by using sudo and the name of the text editor, e.g., sudo vi /etc/exportfs

This would let me edit the file exportfs in /etc using vim as the editor. 

To save the file after editing, I would then :wq! which would write the file and exit me gracefully. Each editor will have its own commands. 

Nano is probably installed by default and my preferred editor vim probably is an option. 

Hope this helps...

---

### Post by brnetonboy on 2008-07-09
you have to open the text editor as sudo to begin with. the name of text editor is "gedit". 

```
sudo gedit /locationofyourfile/yourfilename
```

then you should be able to save after the edits are done.

---

