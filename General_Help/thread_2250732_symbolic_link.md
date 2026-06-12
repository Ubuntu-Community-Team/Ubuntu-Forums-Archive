---
title: "symbolic link"
date: 2014-10-30
forum: General Help
---

### Post by mageta2 on 2014-10-30
Ok, so I'm working through a book and I made a directory called playground with two subdirectories in it; dir1 and dir2. I have a file called fun and the example in the book is to create several symbolic links to the file "fun"

[B]mageta@Lagoon:~/playground$ ln -s fun fun-sym
mageta@Lagoon:~/playground$ ln -s ../fun dir1/fun-sym
mageta@Lagoon:~/playground$ ln -s ../fun dir2/fun-sym[/B]

The last two commands I don't understand. the syntax is ln TARGET LINK NAME. Fun is in the directory playground, but the command says the target is in ../playground. Wouldn't that mean that it's referencing something in the directory above playground? ( Which in this case is home )

---

### Post by nerdtron on 2014-10-30
The last two commands will create a link file ~/playground/dir1/fun-sym pointing to the folder ~/fun

If the folder ~/fun exists, then there's no problem here.
What is the output of "ls -lh ~/playground/dir1/"

---

### Post by mageta2 on 2014-10-30
I forgot to mention that the file fun is a text file, apologies.

I figured it out though. I reread the passage in the book and it says that the target is relative to the link, so if the link is being created in dir1 or dir2, then the target, relative to the location of that link is indeed ../fun

The book is "The linux command line: a complete introduction"

---

### Post by CaptainMark on 2014-10-30
Well we've all learned something new then, I never knew links were created relative to the destination, I've always assumed they were created relative to the current directory as per most terminal programs but I've never come afoul of that mistake because of my habit of always using absolute paths for links, I'll alter my earlier post to remove my incorrect answer.

---

### Post by Impavidus on 2014-10-30
I never knew that either until about a year ago because I always create my links in the current directory, but it's actually quite logical. After creating the link, it has nothing to do with the current directory when it was created, only with the directory where the link is and the directory of the target. Now how should ln translate a relative path from the current directory to a relative path from the link directory? There are multiple ways to do that, especially if there are more symlinks in the path. The solution is not translating at all and assuming the user provides a relative path from the link directory.

I think I read exactly the same question about a year ago. Must have been somebody reading the same book.

---

### Post by nerdtron on 2014-10-30
I read that book and it's one of the easiest to read/follow among command line introductory books I have read. 
It's fun reading too.
Goodluck!

---

### Post by mageta2 on 2014-10-30
> **nerdtron said:**
> I read that book and it's one of the easiest to read/follow among command line introductory books I have read. 
It's fun reading too.
Goodluck!

It really is an easy read. In the intro the author says that you should think of the book like being tutored, and that's how it feels so far.

---

