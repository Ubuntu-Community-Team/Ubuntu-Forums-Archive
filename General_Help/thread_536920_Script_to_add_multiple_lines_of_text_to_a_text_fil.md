---
title: "Script to add multiple lines of text to a text file"
date: 2007-08-28
forum: General Help
---

### Post by dje on 2007-08-28
Is there a command i could incorporate into a shell script that would add multiple lines of text to a text file without user interaction? Thanks in advance

---

### Post by 505 on 2007-08-28
Depends on which file (does the user have write permission) and on the place in the file. If you just want to add a line to the end of a file, use:

echo "This is a line" >> /home/user/file.txt

You can have multiple command below each other to add more lines of text.

---

### Post by dje on 2007-08-28
The user doesn't have write permission to the file can i just put sudo in front of it?

---

### Post by Wolki on 2007-08-28
No, as redirections will not work with sudo. You'll need to use the program tee.
```
echo "blabla" | tee -a file.txt
```

To append multiple lines, you can use the -e parameter and "\n" to indicate a line break like this:

```
echo "first line\nsecond line"
```

If you are more explicit on what exactly your script is supposed to do and how you want to start it, we can give you better hints how to do it.

---

### Post by dje on 2007-08-28
Thanks Wolki but i needed to do > echo "blabla" | sudo tee -a file.txt for the command to work, btw i'm creating a script to install compiz fusion and i'm trying to make it so no user interaction is needed, at the moment you need to add text to files manually but now i wont it will just run straight through and install it automatically :) However is it possible to override the command if the text is already present?

---

### Post by Wolki on 2007-08-28
> **dje said:**
> Thanks Wolki but i needed to do  for the command to work

D'oh... of course you need the sudo, that comes from answering to fast and not reading through it a second time... Glad you figured it out by yourself :)

> However is it possible to override the command if the text is already present?

You could for example grep for it and make adding conditional on the return value. Need to be careful with lines that are present but commented out though, and make sure it works with different amounts of spaces and so on (learning some regular expressions is always a good idea, it'll make a lot of things easy).

I'm not that familiar with compiz stuff, but good luck with your script.

---

### Post by dje on 2007-08-28
Thanks you can take a look at it if you want, just go to the Ubuntu Shell Scripts link below :)

---

