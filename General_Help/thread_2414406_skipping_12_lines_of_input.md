---
title: "skipping 12 lines of input"
date: 2019-03-10
forum: General Help
---

### Post by Skaperen on 2019-03-10
i am trying to skip the first 12 (it might change to a variable) lines of input and feed the rest to a program.  but it seems to usually skip a lot more and mess up some lines (cut in the middle),  the input is coming in on the terminal so i run the program like this:
```

(head -n12 >/dev/null;program)
```

in the future instead of skipping a fixed number of lines i will need to skip all the lines until one with a certain string in it.  is there a command that can do that?  i don't know, yet, if the line with the string in it needs to be skipped, or not.

---

### Post by Impavidus on 2019-03-10
```
tail -n +13 | program
```That will print all lines starting at line 13, i.e., skip 12 lines.

---

### Post by sudodus on 2019-03-10
Try the following method to [skip the first 12 lines and] start using line #13,

```

tail -n+13 

```

---

### Post by Holger_Gehrke on 2019-03-10
> **Skaperen said:**
> in the future instead of skipping a fixed number of lines i will need to skip all the lines until one with a certain string in it.  is there a command that can do that?  i don't know, yet, if the line with the string in it needs to be skipped, or not.

That sounds like a job for awk.
```

cat yourfile|awk -- 'BEGIN {showline=0}; showline==1; /a certain string/ {showline=1}' 
cat yourfile|awk -- 'BEGIN {showline=0}; /a certain string/ {showline=1}; showline==1'  

```
The first variant will skip the line with the string, the second will print it. Read the manual of awk if you'd like to understand how it works.

Holger

---

### Post by Skaperen on 2019-03-11
so why is mine not working?  i did something like it back when i worked on IBM mainframes and it worked just fine.

---

### Post by sudodus on 2019-03-11
You are 'writing 12 lines to cyberspace'; then you start your program 'program'. How can it know/care about the previous 'head' action?

---

### Post by Holger_Gehrke on 2019-03-11
I think he left something off at the beginning, like perhaps a cat piping in a (text) file. The 'head' is supposed to read the first 12 lines from standard input and send them to nowhere and then leave the rest for 'program'. The problem is that filters in Unix are meant to **filter out** everything they are not letting through. The kind of logic he's trying to use could be done in the shell with something like
```
cat file.txt|(for (( i=0 ; i<12 ; i++ )) ; do read; done ; less -)
```pipe in a file, read 12 lines than leave the rest for 'less' (representing 'program') to show. If one uses a 'while' or 'until' loop instead of 'for', reads into a variable and checks its contents as part of the condition to continue/end the loop, this could be made to read up to a specific bit of content before passing control to 'program'

Holger

---

### Post by Skaperen on 2019-03-12
> **sudodus said:**
> You are 'writing 12 lines to cyberspace'; then you start your program 'program'. How can it know/care about the previous 'head' action?

it has read 12 lines.  the next line is number 13?

---

### Post by Holger_Gehrke on 2019-03-12
'head' is a filter. It reads **all** of standard input and writes to standard output **what it's told to write**. So it first read it all, writes the first 12 lines to stdout and you discard that. No stdin for your program to work with.

Holger

---

### Post by Skaperen on 2019-03-13
with that in mind i read the man page, again.  it didn't really say how much was read, only how much was printed.  but the program really did get some input; just not the correct input.  some other reading and asking around plus this thread suggests that head reads stdin in buffer sized chunks until it has enough to have the 10 lines.  exactly what happens depends on the buffer size and the number of bytes to make the 10 lines or however many lines it is asked for.  then the next program gets the next buffer.  this is going to make it hard to have a stream of data arriving over a network in real time divided up to 2 or more programs in sequence.

---

### Post by Impavidus on 2019-03-13
That must be it. Seems that on your old IBM mainframe head actually read a single line at a time, but the implementation of head on Ubuntu uses a larger buffer for better performance.

Note that the split utility can also pipe its output to a command, but every piece of the data will be sent to a separate instance of the same command.

---

### Post by Skaperen on 2019-03-13
there was no "head" command, literally.  but there were commands to do the equivalent.  which command varied by which source it was.

the project i was prototyping needed to be able to switch which program was running to read a network stream.  i think the solution will have to be a forever-running program that reads the stream and writes to whatever program is connected to it or sleeps waiting for a connection when none is.

---

