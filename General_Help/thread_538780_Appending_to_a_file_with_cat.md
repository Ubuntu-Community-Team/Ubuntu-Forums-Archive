---
title: "Appending to a file with cat?"
date: 2007-08-30
forum: General Help
---

### Post by phibit on 2007-08-30
I seem to remember seeing a way to appending a string of text to a file in one line in the console, but I can't find it anymore and after a few weeks of looking it's starting to bother me. This would be useful to me when editing my sources.list file, but for the life of me I can't figure out how to use the cat command correctly.

I know some on IRC would tell me to RTFM, but i've read it, and didn't get much out of it. Things like "redirecting standard output" I sort of understand, but I must've tried every permutation of "cat"  , "<"  ,  ">"  and  ">>" and I haven't gotten it yet :(

Append to a file in one line, using the cat command... Is there a way to do this, or was I just dreaming??

Maybe something like 

cat "deb ubuntu.blahblah.blah feisty main" >>>GO IN THE FREAKEN FILE>>> /etc/apt/sources.list

?

Thanks!

---

### Post by Matthijs on 2007-08-30
cat file1.txt >> sources.list

that sould work, or try 

man cat

the view the man page of cat

---

### Post by phibit on 2007-08-30
Thanks for the reply!

That command seems to append one text file to another text file. The command I'm looking for would append a string to a text file, so that for example I could add to my sources.list file in one line.

Maybe the command I'm looking for requires some sort of 'echo' command ?

Also, the man page doesn't seem to cover output / input redirection in detail.

---

### Post by p_quarles on 2007-08-30
Like this? 
```
echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
```[link]("http://www.medibuntu.org/repository.php")

P.S. The -a option for the tee command makes it "append." If you don't use that, it will overwrite.

---

### Post by vambo on 2007-08-30
I think what you're after is
```
 echo "deb ubuntu.blahblah.blah feisty main" >> /etc/apt/sources.list
```
This will tag the deb blabla onto the end of your sources.list

---

### Post by bmorency on 2007-08-30
you can use cat if you want too.

this will work:
```
cat >> file.txt
```

it will drop a line and then you can type all the text you want. you can even hit enter. to stop it from adding your text just hit ctrl-z to go back to the prompt.

---

### Post by phibit on 2007-08-30
Ah thanks for the responses guys, I can't wait to get home and try it (right now I'm at work on a Windows 2000 machine... bOOO)

---

### Post by Seq on 2007-08-30
> **bmorency said:**
> you can use cat if you want too.

this will work:
```
cat >> file.txt
```

it will drop a line and then you can type all the text you want. you can even hit enter. to stop it from adding your text just hit ctrl-z to go back to the prompt.

I believe you would want CTRL+D for an EOF instead of CTRL+Z for sending a process to the background, would you not?

---

### Post by bmorency on 2007-08-30
> **Seq said:**
> I believe you would want CTRL+D for an EOF instead of CTRL+Z for sending a process to the background, would you not?

yes, you are right. I forgot it should have been ctrl-d.

---

### Post by Paldrion on 2008-04-03
1) go to a command prompt
2) use this command:

type b.txt >> a.txt

3) If the file is big, go watch a movie.

:popcorn:

---

