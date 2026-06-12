---
title: "mv files and structure"
date: 2013-07-13
forum: General Help
---

### Post by JohnnyC35 on 2013-07-13
I'm looking to be able to find a bunch of pdfs, move those pdfs to  another directory, keep the directory structure, and remove the previous  structures.
So far I have been able to use the find command and copy the files while keeping the structure:

       find /home/john/books1/ -regex ".*\(pdf\|epub\|mobi\)$" -type f -exec cp '{}' /home/john/temp/ ';'

but if I use mv I get all the files in one directory...

     find /home/john/books1/ -regex ".*\(pdf\|epub\|mobi\)$" -type f -exec mv -b '{}' /home/john/temp/ ';'


Am I stuck using 'cp'? Which is fine, I just need to find a way to then delete them...

     find /home/john/books1/ -regex ".*\(pdf\|epub\|mobi\)$" -type f -exec rm '{}' /home/john/temp/ ';'

I plan to also have this in a cron job but that shouldn't be a problem once I have figured out the script

Thanks for any help :smile:

---

### Post by SeijiSensei on 2013-07-13
If you use rsync, it will preserve directory hierarchies.

Another option is to use tar like this:

```
tar cpf - /path/to/some/location | (cd /path/to/new/location; tar xf -)
```

That creates a "tarball" of the source location and "pipes" it to another instance of tar that unpacks the tarball in the new location.  The tarball itself is not perserved.

@RayanaSmith 
Rayana, if I had posted an "i don't know the answer to that question" response in every thread to which it applies, my post count would easily be pushing 100,000.

---

### Post by JohnnyC35 on 2013-07-18
I couldn't seem to get tar to be used with find but I was able to get rsync to work. so I'm happy

**rsync -r -R --include='*/' --include='*.pdf' --include='*.epub' --include='*.mobi' --exclude='*' --remove-source-files /storage/unsorted/ /home/john/Books/**

---

