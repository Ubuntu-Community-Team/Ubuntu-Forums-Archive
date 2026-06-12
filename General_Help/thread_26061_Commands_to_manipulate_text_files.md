---
title: "Commands to manipulate text files"
date: 2005-04-11
forum: General Help
---

### Post by artinla on 2005-04-11
Hi,  I need help with some scripting that I am trying to do.  I would like to expand upon the newbie installation script for Ubuntu that Ryan has posted.  It is a great script but I would like to customize it for my own (and possibly others) needs.

BTW Thanks Ryan for working on that project.. It is a GREAT idea and you did a great job.

I need to be able to do the following:

1.  I want to be  able to append a couple of lines to the end of an existing config file from within the script.

2.  I would like to be able to search the contents of a config file for a known value and replace the value with a new one.  

Are there command line programs that will allow me to accomplish this?

Thanks

Art

---

### Post by nobodysbusiness on 2005-04-11
I'm not an experienced scripter, but I know of a few shell commands that might help you.

To add some lines to a config file, you can use the 'cat' command:

cat my_config_file.cfg new_lines_file.cfg > finished_file.cfg

To search a file and replace one string with another, you can use the 'sed' command:

sed s/text_to_replace/replace_it_with/g file_to_search.cfg > new_file.cfg

Hope this helps.

---

### Post by artinla on 2005-04-11
Thanks!  I will try those out tonight.

The cat command should work, but I was hoping to not have to include a seperate text file to add to the end of the config.. I wanted to be able to just include the lines in my script and have them appended. 

Art

---

### Post by sreid on 2005-04-12
You could do this:

echo Some configuration thing.>>file.txt

The >> means append.

Google for "shell script" and read a tutorial. Redirection is pretty basic stuff.

---

### Post by artinla on 2005-04-12
Thanks, that is certainly an easy way.

I have some advanced shell scripting books, but unbelievably they don't really cover the two scenarios I mentioned above in any detail.   The cat command is in there, but cat is not the best way to do it.  Your way is much better.    That is why I asked here instead of wasting a night googling for answers... Google is filled with answers but not necessarily the best ones.  I find that the most creative and knowledgeable people in the linux world seem to hang out right here.

I am still working with using sed to find and replace text.  That is the last piece of the puzzle that I need in order to put together a very nice post-install script.  I hope to make it available once I have written and tested it.

Art

---

