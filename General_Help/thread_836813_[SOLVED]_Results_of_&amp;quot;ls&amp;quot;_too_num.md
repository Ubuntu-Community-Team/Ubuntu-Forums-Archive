---
title: "[SOLVED] Results of &amp;quot;ls&amp;quot; too numerous for screen"
date: 2008-06-21
forum: General Help
---

### Post by lost09 on 2008-06-21
I'm trying to look through my usr/bin files (trying to find firefox and open office so as to learn to open things from CLI), but the number of files is so large that gnome-terminal can't display them all, so the top half of the list is unrecoverable. Is there a way to structure the output of "ls" differently, or perhaps get it to display the output in parts?

---

### Post by smo0th on 2008-06-21
use ```
ls | grep <filter>
``` to filter your query ;)

---

### Post by lisati on 2008-06-21
The "grep" option is a nice response to the OP's question. Other options include ```
ls | more
``` and ```
ls | less
```

---

### Post by lost09 on 2008-06-21
It gives ": syntax error near unexpected token `newline'".

Could you explain exactly what "|", "grep", and "<filter>" are doing in this instance (sorry, I'm still learning how to use command line... obviously I'm still rather new)?

---

### Post by lost09 on 2008-06-21
lisati, I posted that last response before I noticed yours; oops.

I tried "ls | less", and that seems to be what I'm looking for. However, say I've found what I need within the first few dozen lines. How do I break out (please tell me I don't have to scroll through the remaining hundred)?

---

### Post by p_quarles on 2008-06-21
> **lost09 said:**
> lisati, I posted that last response before I noticed yours; oops.

I tried "ls | less", and that seems to be what I'm looking for. However, say I've found what I need within the first few dozen lines. How do I break out (please tell me I don't have to scroll through the remaining hundred)?
Press 'q'. 

For the other suggestion, you were supposed to replace <filter> with a specific word relevant to what you were looking for. Like: 
```
ls | grep superman
```
would, for instance, return filenames that contained the word "superman." :)

---

### Post by CRISM on 2008-06-21
1. You can type the following:  ls | more   That will give you the output one page at a time. You can move on to the next page by hitting the space bar.

2. You can direct the output of the ls command to a text file that you can open later and read at your leisure. Use the command ls > /home/yourusername/filename to create a file in your own home directory. Example: If your username is lost09, and you want to name the file "listing.txt" you would type: ls > /home/lost09/listing.txt

---

### Post by lost09 on 2008-06-21
Oh, of course, "q" doesn't work the first time I try it, but now that someone has pointed it out, it behaves perfectly. *sigh* Thanks.

Yes, I replaced <filter> with what I was seeking. I was just curious as to the "|" syntax.

---

### Post by cariboo on 2008-06-21
If you know what you are looking for you could always do something like this:

```
ls -l fire*
```

In this case it will only list files starting with fire.

Jim

---

### Post by lost09 on 2008-06-21
Many thanks to all of you. Hooray Ubuntu spirit, and whatnot.

---

### Post by lisati on 2008-06-21
> **lost09 said:**
> It gives ": syntax error near unexpected token `newline'".

Could you explain exactly what "|", "grep", and "<filter>" are doing in this instance (sorry, I'm still learning how to use command line... obviously I'm still rather new)?

1) When you type in something like > ls | more the "|" means to take the output from one command (in this example, "ls") and use it as input for the next command (in this example the "more" command)
2)"grep" lets you filter through a pile of output and select what gets displayed

---

### Post by p_quarles on 2008-06-21
> **lost09 said:**
> Oh, of course, "q" doesn't work the first time I try it, but now that someone has pointed it out, it behaves perfectly. *sigh* Thanks.

Yes, I replaced <filter> with what I was seeking. I was just curious as to the "|" syntax.
The "|" symbol is known as a pipe. It transfers the output of one command into another. So:
```
ls | less
```
takes the output of "ls" and places it into the "less" paging application.

---

### Post by kevdog on 2008-06-21
Is less any different than more?  I've always wondered that myself!  Seems like the developers had a joke going when they developed these programs with one being called more and the other less.

---

### Post by p_quarles on 2008-06-22
> **kevdog said:**
> Is less any different than more?  I've always wondered that myself!  Seems like the developers had a joke going when they developed these programs with one being called more and the other less.
Yes. "more" was the original *nix pager, and "less" was later designed as an improvement/punchline. The less program is more flexible, basically, and allows you to scroll through a document one line at a time, and to go backwards. "more" displays one page at a time.

---

