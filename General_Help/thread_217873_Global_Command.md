---
title: "Global Command"
date: 2006-07-17
forum: General Help
---

### Post by mathon on 2006-07-17
Hello,

I want to write a global command for the vi which removes all lines of a Shell Script which represents comments, so every line which starts with a #. Has anybody some tips for me how I can realize that in an easy manner? 

Regards

---

### Post by Ramses de Norre on 2006-07-17
You can do this by using sed:
```
sed -e '/^**#**/d' **file**|tee **file**
```
You need to use sudo in front of tee if you need sudo rights to write to the file, This line deletes lines starting with **#** in file **file**.

---

### Post by pat270881 on 2006-07-20
I have also a question to that posting: 

What is a global command for the vi? I know what macros are for the vi but what is a global command? - do there exist any tutorials about what global commands are, examples and how to use them?

regards

---

### Post by Ramses de Norre on 2006-07-20
I didn't even know this was a vi thing:D
This is really nice!=) And I allready found out the alternative to my sed command from within vi: ```
global /^#/delete
```

I found the info [here]("http://www.networkcomputing.com/unixworld/tutorial/009/009.part3.html").

---

### Post by pat270881 on 2006-07-20
thank you very much for your tipp, I read the articles of your posted link. But there are two questions which occur by myself:

1)How can I use this global commands? Do I have to write it in a certain file to use it?

2)What is then the difference between macros in the vi and a global command in the vi??

Hopefully anybody has an answer for me...:( 

Regards

---

### Post by Ramses de Norre on 2006-07-20
You just type them as a command in vi, press shift+q if you're in visual mode (you'll get a ":" then, this is the vi prompt).
And I don't know anything about vi macro's, that will be the next thing for me to learn ;)

---

### Post by pat270881 on 2006-07-21
For me it works as follows:

In command mode I have to type in :global /^#/delete and then press enter. When I press Shift+q instead of Enter nothing happens...?

Is it possible to save global commands in a file so I can use it and I do not have to type the global command in the vi every time I want to use it? (because macros can be defined in .vimrc and so are available every time)

In previous posting from you you defined the following statement:
sed -e '/^#/d' file|tee file

So in this statement you look for a # at the beginning and then delete this row of the file and for what is the "tee file" after the pipe?? :-?

Regards

---

