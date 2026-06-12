---
title: "How would you recover a hidden file?"
date: 2012-10-17
forum: General Help
---

### Post by YourSurrogateGod on 2012-10-17
Or recover lost space for that matter!

I'm reading this article in an attempt to educate myself how Linux works with files (primarily trying to figure out the difference between hard links and soft links, which I now know full well).

[http://linuxgazette.net/105/pitcher.html](http://linuxgazette.net/105/pitcher.html)

This is the part that has me stumped:
> By the way, the count also reflects how many times the file has been opened without being closed (in other words, how many references to the file are still active). This has some ramifications which aren't obvious at first: you can delete a file so that no "filename" part points to the inode, without releasing the space for the data part of the file, because the file is still open.

Now, say I 'lose' a file this way, how could I free the space where the data resides?  Reboot the machine?

Also, they have a very pertinent code example:
```
     {
        FILE *fp;

        fp = fopen("some.hidden.file","w");
        unlink("some.hidden.file"); /* deletes the filename part */

        /* some.hidden.file no longer has a filename and is truely hidden */
        fprintf(fp,"This data won't be found\n"); /* access the data part */
        /*etc*/
        fclose(fp); /* finally release the data part */
     }
```
Say the program exits before I get a chance to fclose the file programmatically, what happens to the file?  Is the stream to it closed the instant the program exits or does it linger somewhere hidden?  And if it's 'hidden', is there any way to find that file again?

That article blew my mind, would love to have some answers.

---

