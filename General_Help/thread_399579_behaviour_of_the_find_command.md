---
title: "behaviour of the find command"
date: 2007-04-02
forum: General Help
---

### Post by lordmule on 2007-04-02
I would like some clarification on how the 'find' command works. 

I have a bunch of folders on my ~/Desktop and each of them has some number or pdf documents in them as follows

$ ls -l docs*
docs1:
total 0
-rw-r--r-- 1 john john 0 2007-04-03 03:22 a.pdf
-rw-r--r-- 1 john john 0 2007-04-03 03:22 b.pdf
-rw-r--r-- 1 john john 0 2007-04-03 03:22 c.pdf

docs2:
total 0
-rw-r--r-- 1 john john 0 2007-04-03 03:23 a.pdf
-rw-r--r-- 1 john john 0 2007-04-03 03:23 b.pdf
-rw-r--r-- 1 john john 0 2007-04-03 03:23 c.pdf

docs3:
total 0
-rw-r--r-- 1 john john 0 2007-04-03 03:23 a.pdf
-rw-r--r-- 1 john john 0 2007-04-03 03:23 b.pdf
-rw-r--r-- 1 john john 0 2007-04-03 03:23 c.pdf

I expect the commands:

~/Desktop$ find -name *.pdf 
~/Desktop$ find *.pdf 

to return for me all the .pdf files under the current directory. Not true

$ find -name *.pdf
./docs1/a.pdf
./docs1/b.pdf
./docs1/c.pdf
./docs2/a.pdf
./docs2/b.pdf
./docs2/c.pdf
./docs3/a.pdf
./docs3/b.pdf
./docs3/c.pdf


$ find *.pdf
find: *.pdf: No such file or directory

for the latter I expected that the man page looked for a path first, imo this shouldn't be the case, but I can live with it.

Ok now there is a file in ~/Desktop called sample.pdf

~/Desktop$ touch sample.pdf
~/Desktop$ find -name *.pdf
./sample.pdf

Not what I want. Fair enough ill try use the full find command

~/Desktop$ find /home/john/Desktop *.pdf
gives me all files from Desktop directory and
sample.pdf

ok now the -name version

$ find /home/john/Desktop -name *.pdf
/home/john/Desktop/sample.pdf


what happened to all the other pdfs?!

~/Desktop$ cd ~/
$ find /home/john/Desktop/ -name *.pdf

nothing!!

I have been using Linux for a while but never came across this before. I have read the man page but found no misunderstanding with my logic of how the application should work. Help appreciated thanks

PS: does this explain why the nautilus find does not find all *.pdf files from a given dir?

---

### Post by tbroderick on 2007-04-02
Try;
find ~/Desktop -name '*.pdf'

---

### Post by bapoumba on 2007-04-02
or give **locate** a try ;)

---

### Post by dcstar on 2007-04-03
> **lordmule said:**
> I would like some clarification on how the 'find' command works. 
.........?

IIRC "find" locates strings of data **inside** files.

If you use a command similar to the ones you have listed, then you seem to be asking find to search your directory (which is basically a file) for things containing the ".pdf" string, and that may explain the results you are getting.

---

### Post by lordmule on 2007-04-03
> **tbroderick said:**
> Try;
find ~/Desktop -name '*.pdf'

Yes thank you all for your response. I sometimes forget that arguments should always be enclosed in quotes.
Thanks

---

### Post by streeto on 2007-04-03
> **lordmule said:**
> Yes thank you all for your response. I sometimes forget that arguments should always be enclosed in quotes.
Thanks

Just to complement your comment. The difference between '*.pdf' and *.pdf is that the latter is parsed by the shell, the former is not. I. e., suppose there are two files in some dir., a.pdf and b.pdf. Then

$ command *.pdf

will pass a.pdf and b.pdf as arguments to command. Putting quotes around *.pdf,

$ command '*.pdf'

will pass literally *.pdf to command. It is to note that the command 'find' expects the latter kind of argument, hence the confusion.

-st.

---

