---
title: "running problem of matlab 6.5"
date: 2006-09-13
forum: General Help
---

### Post by tiptop on 2006-09-13
After installation matlab 6.5 on 6.06.1, matlab could run in graphic mode but I close the program without any testing. After that when I typed "matlab" to start the program, after the splash window, a whole blank window appeared with out any response. But matlab could run in the console without any problem as far.
I've search a lot and found someone said to run matlab with "env LANG=C LC_ALL=C matlab". Then matlab started successfully. But I pressed the keyboard, the matlab window appeaed blank again without respose.

Can anyone help me? Thanks a lot.

---

### Post by Rumo on 2006-09-13
I had problems with matlab, too. Some matlab functions didn't really seem to work. The program started fine, though.

These problems were fixed by increasing the stacksize from 8192 to unlimited (try 'ulimit -s' - this will show your actual stack size). Perhaps this works for you, too. Just type 'ulimit -s unlimited' before starting matlab.

If this works you can add an 'ulimit -s unlimited' at the end of your /etc/profile file.

---

### Post by tiptop on 2006-09-13
sorry, it doesn't work either.

---

### Post by buttari on 2006-09-13
the Matlab GUI doesn't work fine on linux. I suggest you to use Matlab in command line mode. Just add the flag "-nojvm" to the matlab command:

```
$matlab -nojvm
```

Regards,
alfredo

---

### Post by tiptop on 2006-09-14
Thanks. I've tried this. And in console mode, it seems that the command "plot" works fine and draws the output in a new window. No further testing yet.

---

