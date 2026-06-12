---
title: "xclip paste without ending return statement"
date: 2013-03-15
forum: General Help
---

### Post by heepie on 2013-03-15
I have a small script which extracts some text and pipes it to xclip ready for pasting somewhere else by using

```
$ some command | xclip -selection c
```

The problem I'm having is that the return string giving back from xclip always has a return statement added at the end of it. This is very well for pasting on a text editor but if I want to paste it on the terminal as one of the parameters everytime I paste it it ends the command not allowing me to enter the full command.

```
$ comand (xclip paste) some more command
```

So, is there a way to paste from xclip without the ending return statement?

---

### Post by sudodus on 2013-03-15
The output from the command, that you pipe into xclip contains a newline, that you need to remove. Try to remove it with tr like this

```
echo '# hello world' |tr -d '\n'| xclip -selection c
```

---

### Post by heepie on 2013-03-15
That work!!!

Thank you so much

---

