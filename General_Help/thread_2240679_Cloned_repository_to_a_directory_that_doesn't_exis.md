---
title: "Cloned repository to a directory that doesn't exist"
date: 2014-08-21
forum: General Help
---

### Post by Conrad_Moore on 2014-08-21
Hi guys. I'm pretty new to Ubuntu (Linux in general, really), and this is my first post so I hope I'm doing this right...

Long story short, I left my terminal in a directory that I had just recently deleted, and then used hg clone to copy a repository to that location. There didn't seem to be any errors, so I didn't realize anything had gone wrong, but I couldn't find the file I supposedly cloned. Then I realized that I had cloned it to the directory that I had just deleted a few minutes earlier, and now I'm worried that the data I copied is just lying around in my computer somewhere. Is that true? If so, is there a way to delete that data?

Thanks

---

### Post by lukeiamyourfather on 2014-08-21
Can you post the history of commands used? If you type "history" into a terminal it'll show all the commands.

---

### Post by Conrad_Moore on 2014-08-25
Thanks for your response, and I'm really sorry for checking back so late. Here's what it looks like:

   38  cd alanmi-abc-4d547a5e065b/
   39  ls
   40  make
   41  hg
   42  hg tol
   43  tol
   44  hg
   45  sudo apt-get install mercurial
   46  hg
   47  hg clone [https://bitbucket.org/alanmi/abc](https://bitbucket.org/alanmi/abc)
   48  cd -

So in line 38, I went into the directory. Then, at some point between then and line 47, I decided that for some reason I didn't like that folder and used the GUI to remove it, along with all the files in it. Then, after copying the repository (not entirely understanding what hg clone was supposed to do), I started looking for it in places like the Downloads folder (again, using the GUI). When I couldn't find it, I realized what had happened and, using the terminal, backed out of the directory that no longer existed.

As a recent Windows convert, I'm still kind of going back and forth between GUI and terminal file navigation. Do you know what would happen to the data in this situation?

Thanks

---

### Post by steeldriver on 2014-08-25
It looks like when you do that, the terminal "follows" the deleted directory to your trash e.g.

```

:~/Documents/forums/tests$ cd ..
:~/.local/share/Trash/files$ 

```

so look in your trash

---

### Post by Conrad_Moore on 2014-08-26
Sorry, I should have clarified: I *permanently deleted* (Shift + Del) the folder and all of its contents. So if it follows the completely non-existent directory, does that mean it follows it into the void and therefore doesn't exist? I'm assuming that Trash is the equivalent of Windows' Recycle Bin, by the way. In any case, thanks for the help! It seems like the mystery is becoming clearer.

---

