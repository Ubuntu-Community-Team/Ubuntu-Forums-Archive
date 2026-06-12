---
title: "File location in Command Line?"
date: 2018-05-09
forum: General Help
---

### Post by PDA1 on 2018-05-09
I use the following a lot in Terminal

```
[LEFT]*[FONT=Ubuntu][SIZE=2]PDA1@PDA1:~/Desktop$ pdftk InputFileName.pdf cat 17-260 output OutputFIlename.pdf [/SIZE][/FONT]* 
[/LEFT]  
```

As seen above I'm in the folder "Desktop" but, for example, the input file is located in the folder "Basement"

Using the code above, exactly how do I edit the code to "point to" the input file which is located in another folder?

Thanks,

Mr. Umbday

Curly- "You mean I'm Umbday in pig language?"
Moe- "You're Umbday in any language".

---

### Post by yancek on 2018-05-09
Put the full path to wherever the Basement folder is which you did not mention.  Or you could change directories to the Basement folder and run the command.

---

### Post by Skaperen on 2018-05-10
put the absolute or relative name of the folder in front of the name of the file, separated with a "_/_" character.  an absolute name starts at the top (apex) of the inverted file tree.  the top directory is "_/_".  absolute names start with "_/_".  you can get the absolute name of your current directory with the "pwd" command.  a relative name is a short name that the name of the directory it is *in*.  you can leave a name as a relative name (simple names with no "_/_" at all are relative names).  or you can make any relative name into an absolute name by prefixing the relative name with the absolute directory name it is in.  learning all about relative and absolute names is important in bot Linux and Windows.  have fun!

---

### Post by PDA1 on 2018-05-10
> **Skaperen said:**
> put the absolute or relative name of the folder in front of the name of the file, separated with a "_/_" character.  an absolute name starts at the top (apex) of the inverted file tree.  the top directory is "_/_".  absolute names start with "_/_".  you can get the absolute name of your current directory with the "pwd" command.  a relative name is a short name that the name of the directory it is *in*.  you can leave a name as a relative name (simple names with no "_/_" at all are relative names).  or you can make any relative name into an absolute name by prefixing the relative name with the absolute directory name it is in.  learning all about relative and absolute names is important in bot Linux and Windows.  have fun!

I feared this.  Notice that the forward slash you showed has an underscore.

---

### Post by PDA1 on 2018-05-10
[FONT=Ubuntu]This is a possible solution.  I "copy" the file in nautilus and "paste" it into terminal.  Looks like for spaces terminal needs a "%20".

file:///home/snoopy/My%20Documents[/FONT]

  
So far so good

---

### Post by steeldriver on 2018-05-10
As others have pointed out, you need to prepend the name with either an absolute or relative path. If the path contains spaces, either escape them with backslashes or enclose the path in quotes

We can't give you an exact answer since we don't know where the folder is located, relative to your current location ~/Desktop but it might look something like

```

PDA1@PDA1:~/Desktop$ pdftk **../Basement/**InputFileName.pdf cat 17-260 output OutputFIlename.pdf                                        # folder Basement is on the same level as ~/Desktop i.e. up (..) and back down (relative path)

PDA1@PDA1:~/Desktop$ pdftk **"/home/user/path with spaces/Basement/InputFileName.pdf"** cat 17-260  output OutputFIlename.pdf            # folder Basement somewhere inconvenient to get to via relative path (use absolute path)

```

If you want the output file to go to the same place, then prepend that similarly - or change to the target directory first using the **cd **command

---

### Post by Impavidus on 2018-05-10
> **PDA1 said:**
> [FONT=Ubuntu]This is a possible solution.  I "copy" the file in nautilus and "paste" it into terminal.  Looks like for spaces terminal needs a "%20".

file:///home/snoopy/My%20Documents[/FONT]

  
So far so good

Looks like it gets formatted as an URI. Whatever you put on the command line is broken at whitespace into strings and then passed on to the application you start from the terminal. It's the job of this application to interpret this string as the location of a file, or whatever the application expects there. Some may be able to handle URI style paths. As the things you put on the command line are broken at spaces, any spaces where you don't want the string to be broken have to be escaped or quoted. I never drag files from the file manager into the terminal, as it's faster to type the path with a little help from tab completion. In fact, I don't even use the file manager.

Another way to start an absolute path is with **~/**, which refers to your home directory (/home/username, unless you configured otherwise). You can also use **~otherusername/** to refer to someone else's home directory.

---

