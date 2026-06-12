---
title: "how do i install .sh files"
date: 2006-12-23
forum: General Help
---

### Post by BTBadger on 2006-12-23
Hi, im new to Ubuntu, and im running the Dapper Drake version. I'm trying to setup the battlefield 2 linux server on my computer, and when i download it, it is a .sh file. I saw some commands that i can enter into the terminal, but none of them worked. So does anyone have any suggestions or links or anything? And if you need more info about my computer, just ask.

Thanks

---

### Post by Jussi Kukkonen on 2006-12-23
It is a script file -- you can't install it really, but you can run it. I hope you realize that running unknown scripts can be dangerous: You'll have to decide if you trust the place you downloaded the script from before you run it...

That said, here are the instructions: Open a terminal, go to the directory the file is in and do this:```

chmod +x <filename>
./<filename>
```

---

### Post by dbott67 on 2006-12-23
Generally speaking, you need to make sure that the file is 'executable'.

```
chmod 755 filename
```

-Dave

Oops! Beaten to the punch by Jussi!  But yes, everything Jussi said applies.

---

### Post by BTBadger on 2006-12-23
so i opened the terminal and i typed in

```
 andrew@Andrew-Server:~$ chmod +x /home/andrew/desktop/bf2-linuxded.sh

```

and it came up with
```
chmod: cannot access `/home/andrew/desktop/bf2-linuxded.sh': No such file or directory

```

its sitting on my desktop, so did i enter the wrong directory, or is it just not compatible?

---

### Post by iamhugeinjapan on 2006-12-23
Paths are often case sensitive.

A non console way is to right click the file and choose Properties. Then the Permissions tab. Check the box by 'Allow executing file as program'

Then double click the file and choose Run

---

### Post by BTBadger on 2006-12-23
thank you very much, that worked well. But now when im installing it, it is asking me where i should install it to, is there a good generic directory i can install it to?

---

### Post by iamhugeinjapan on 2006-12-23
Not knowing what you are actually installing this could be bad advice but in general  /usr/bin/ would be okay.

---

