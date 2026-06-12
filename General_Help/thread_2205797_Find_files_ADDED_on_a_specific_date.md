---
title: "Find files ADDED on a specific date?"
date: 2014-02-16
forum: General Help
---

### Post by PDA1 on 2014-02-16
As you'd expect, I've junked up my harddrive with a bunch of files today. 

I solve a lot of my computer problems by clicking until I get results. It works pretty well....sometimes. Except, the other day I wiped out the data on a 500g drive by using that "dd" command. Hey, how was I supposed to know it'd overwrite everything?!

Anyway, I'd like to find all of the files I've added to a drive (sda) today, that is- February 15, 2014. I want to see all of the files added in all directories on that date. Then, you know what I'm going to do?  I'm gonna' delete 'em all!!!!!

Can you provide a simple CLEAR way to do it?

Stop me before I wreck another drive!!!

---

### Post by epikvision on 2014-02-16
Hello, did you mean add **all** files into your HOME directory?  Then, you could run in your terminal:
```

$ find $HOME -daystart 

```
The -daystart option searches for all files since the start of today, not 24 hours before.

If you want to be more specific, by file-type, try this:
```

$ find $HOME -daystart -iname "*.doc"

```
This command will search for all "doc" files added today. Replace "doc" for another filetype of choice (e.g. txt, pdf, pl, etc.)

Hope this helps. :-)

---

### Post by dragonfly41 on 2014-02-16
if you prefer to use a GUI instead of command terminal try installing SearchMonkey from Ubuntu Software Centre.

You can set the date window for each search.

---

### Post by PDA1 on 2014-02-17
> **epikvision said:**
> Hello, did you mean add **all** files into your HOME directory?  Then, you could run in your terminal:
```

$ find $HOME -daystart 

```



No. I don't want to ADD files. 

I want to FIND all of the files that were added to my harddrive on February 15, 2014 with no regard to the files location (not just Home....but everywhere on the drive).

Once found I want to selectively delete them.

---

### Post by PDA1 on 2014-02-17
> **dragonfly41 said:**
> if you prefer to use a GUI instead of command terminal try installing SearchMonkey from Ubuntu Software Centre.

You can set the date window for each search.



Perfect!

Thanks.

---

