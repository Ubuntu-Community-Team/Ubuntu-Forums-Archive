---
title: "How to convert .jpg to-pdf with a desktop tool(!)"
date: 2015-03-05
forum: General Help
---

### Post by 171742 on 2015-03-05
Hi,

thats the question. A tool that can manage converting a lot of pdfs without having to open them all one by one.

(I:Please do not get into a discussion about how much better the terminal is, this is not the question.)

Thanks!

---

### Post by nerdtron on 2015-03-05
Need to convert files? I use this: [http://www.zamzar.com/](http://www.zamzar.com/)

---

### Post by HermanAB on 2015-03-05
There is a program called 'phatch' that can be used to do batch processing of pictures.

---

### Post by 171742 on 2015-03-05
I am far too rookie for getting that done in this program.

---

### Post by slickymaster on 2015-03-05
LibreOffice as the possibility to export as PDF. You can open you jpg file in LibreOffice Draw and then File -> Export as PDF

---

### Post by ajgreeny on 2015-03-05
Or you can open them in any program that will open jpegs and then print to file, choosing pdf as the output type.
I show a screenshot of the print dialogue, not of a jpeg being printed, but this forum page, just to show you how easy it is, and nothing more to install.

---

### Post by 171742 on 2015-03-05
Yes, but then I am set with one by one again.

---

### Post by dragonfly41 on 2015-03-05
For jpg2pdf batch processing see if [COLOR=#808080]**coverseen**[/COLOR] fits the bill .. from Ubuntu Software Centre.

---

### Post by howefield on 2015-03-05
Is running something like mogrify -format pdf -- *.jpg in a terminal beyond your rookie ability ? 

Install imagemagick, navigate to the jpg containing folder and run the command.

---

### Post by 171742 on 2015-03-05
see I:

---

### Post by howefield on 2015-03-05
> **171742 said:**
> see I:

You mean this "(Please do not get into a discussion about how much better the terminal is, this is not the question.)"

Do try again, I am not telling you it is better, just the possibility that it will do your job a hundred times over in the time it took to post your thread. :)

---

### Post by dragonfly41 on 2015-03-05
I read the op requirements as _batch processing_ jpg's to pdf's.

---

### Post by howefield on 2015-03-05
> **dragonfly41 said:**
> I read the op requirements as _batch processing_ jpg's to pdf's.

Nothing wrong with your powers of deduction.... :)

---

### Post by dragonfly41 on 2015-03-05
Aye, laddie ..

---

### Post by 171742 on 2015-03-06
> **dragonfly41 said:**
> For jpg2pdf batch processing see if [COLOR=#808080]**coverseen**[/COLOR] fits the bill .. from Ubuntu Software Centre.


hi,

thanks, but its not. Terminal install does not work.

Other Ideas?

---

### Post by ajgreeny on 2015-03-06
OK, so you are prepared to use terminal!  It really is the way to go, I think.
If you have imagemagick installed you can use a very simple command 
```
convert *.jpg image%d.pdf
```This will produce output files with the names image0.pdf, image1.pdf etc etc, and I am sure you could also do it in way that keeps the original filename but simply changes the filetype but my bash skills are not quite good enough yet to show you how but I will do a search for my own info and then come back again.

---

### Post by 171742 on 2015-03-06
> **ajgreeny said:**
> OK, so you are prepared to use terminal!  It really is the way to go, I think.
If you have imagemagick installed you can use a very simple command 
```
convert *.jpg image%d.pdf
```This will produce output files with the names image0.pdf, image1.pdf etc etc, and I am sure you could also do it in way that keeps the original filename but simply changes the filetype but my bash skills are not quite good enough yet to show you how but I will do a search for my own info and then come back again.

Look, its for my father, he most certainly wont do that. If you want to discuss that further do open a new thread please. Its perfectly fine if you do not know an answer to the question posted, then please do not answer.

For all others: Any ideas?

---

### Post by nerdtron on 2015-03-06
Well I haven't looked (probably) looked enough, but I think on this situation, I'll just create a script.
Something like:

1. Create a source folder and put at .jpg in there.
2. Create a destination folder that will hold the pdfs.
3. Run the script (probably a desktop link) to batch convert the files.

We can help write the script if you like this scenario.

---

### Post by sudodus on 2015-03-06
There might be no suitable tool, that will keep your hands clean. But we can help you keep your father's hands clean (from commands in terminal windows).

1. Make a script file, that does batch conversion from jpg to pdf for all files in a directory (and subdirectories if you wish)

2. Make a desktop file, that runs that script file. It appears as a clickable icon on the desktop (and in a file browser).

3. Copy it to your father's computer and teach him how to use the desktop file :-)

---

### Post by ajgreeny on 2015-03-06
Having done some searching as a result of your post #17, it does look as though phatch will do exactly what your father wants;  it's a GUI program and it's in the repos so try it, as I intend to do.

EDIT:
I just installed phatch to try it out, but I have to say, it took a lot more to figure out how to use it, and I did not find out how to change image filetypes so quickly uninstalled it.

Whilst I accept that I do not know everything about *ubuntu, I can usually manage to sort out GUI progs quickly and easily; that one beat me, though perhaps I did not try hard enough because I didn't need to..

---

