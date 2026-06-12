---
title: "How to find files from the command line?"
date: 2008-01-02
forum: General Help
---

### Post by ka1eui on 2008-01-02
Good morning.  Is there a way that I can type in the name or partial name of a file from the command line and have the computer search for it?  
Thanks
Jim

---

### Post by heimo on 2008-01-02
> **ka1eui said:**
> Good morning.  Is there a way that I can type in the name or partial name of a file from the command line and have the computer search for it?  
Thanks
Jim

Sure there is! :-) At least couple ways to do it. You could use locate command or find. Former is easier to use. Just type:
```
locate file_im_searching
```
where *file_im_searching *is what you're looking for.

Find command is more complex, but also _very_ flexible and powerful.

---

### Post by capink on 2008-01-02
If you are looking for a file created less than 24 hours ago, chances are you are not to going to find it using the locate command unless you refresh the cache first using this command:

```
sudo update-db
```

find command is more complex but also more flexible. And it searches the filesystem directly not any premade cache, so it is slower than the locate command.

to find a file that contain 'cat' in it's filename in you home directory:

```
find /path/to/your/home -name '*cat*'
```

If you want the search to be case insensitive:

```
find /path/to/your/home -[COLOR="Red"]i[/COLOR]name '*cat*'
```

one great thing about find command it that it allows you to preform actions on the files it finds based on your search criteria. For example, if you want to delete all files that contain cat on their filename on your entire filesystem (in just in your home directory) type:

```
sudo find / -name '*cat*' -exec rm {} \;
```


You can find more on the find command on the internet. Or by typing man find.

---

