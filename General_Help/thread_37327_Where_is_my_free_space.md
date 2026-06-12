---
title: "Where is my free space?"
date: 2005-05-26
forum: General Help
---

### Post by userbr on 2005-05-26
I have a strange problens in my Ubuntu 5.04:

 After I delet a file the Nautilus don't recognise new free sapce.
 At terminal "df -h" show:

Syst. file                Size    Used  Free Use%  Mount at
...
/dev/hda10            9,2G   8,7G     0  100%   /home
...

9.2 - 8.7 = 500 MB

Where is the free space in my hard disk?  :? 

I need some Heeeeeelp! Thanks

---

### Post by apollyonis on 2005-05-26
This may sound silly, but have you tried looking at your Trash folder to see if its full? If you can't access Trash for some odd reason or there are files there that are not deletable, do this in terminal : 
 
```

cd ~/.Trash
sudo su
rm *.*
cd /home/.Trash-root
rm *.*
exit
```

NOTE : It is VERY important that you exit out of admin mode after you're done. You wouldn't need to delete any important files.

---

### Post by DutchLau on 2005-05-26
Why are we being so difficult apollyonis?

What you can do is just click on the " trash " icon in the bottom right corner of your screen and then once you're in you press " empty trash "

If that doesn't work do the following:

```
sudo rm -fr $HOME/.Trash/
``` 

That should do the trick!

Let us know if this fixed your problem,

Cheers, DutchLau

---

### Post by chrisubuntu on 2005-05-26
[QUOTE=userbr]I have a strange problens in my Ubuntu 5.04:

 After I delet a file the Nautilus don't recognise new free sapce.
 At terminal "df -h" show:

Syst. file                Size    Used  Free Use%  Mount at
...
/dev/hda10            9,2G   8,7G     0  100%   /home
...

9.2 - 8.7 = 500 MB

Where is the free space in my hard disk?  :? 

I need some Heeeeeelp! Thanks[/QUOTE]

I know for some Unix's (solaris springs to mind) 100% disk usage isn't really 100% disk usage... The filesystem reserves some space (something like 3-10%) to allow it to reorganise the file system (like a defrag). 

Might be an idea to check the docs on your filesystem type (ext2, ext3, reiser etc) to see if this is accurate under linux.

Chris.

---

### Post by userbr on 2005-05-28
I use ext3  and my trash is empty

---

