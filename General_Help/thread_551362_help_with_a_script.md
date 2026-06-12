---
title: "help with a script"
date: 2007-09-15
forum: General Help
---

### Post by jmvidalvia on 2007-09-15
I knwow forums are not here for this kind of help but...:oops:
¿would anyone be so kind as to help me to prepare a script?
I set up a new server in my company, an one of the folders is a repository where people share big files, instead of sending mails.
I need to check if those files are older than lets say 30 days: if ther are, they must be deleted. I they are not, just leave them.
I am skilled enough to prepare the cron tab, but not for the script.
Thank you very much in advanced!:)

---

### Post by psusi on 2007-09-15
man find.  IIRC, it has switches to ask it to find files based on their age.  You can then pipe that output to xargs rm, and it will run rm to delete them and pass that list of files to rm.

---

### Post by TheExplorer on 2007-09-15
Read [here]("http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/")

---

### Post by jmvidalvia on 2007-09-16
Thank you very much!
That is exactly what I was trying to do.

Now , I first find "old" files, list them in a .txt file and add a header in order to send an e-mail to the owner of the files advising him about the soon deleting of his files.

But still have a silly problem: I don't want to send empty emails (for owners with no files to be deleted).

Any idea about: if file size(*) = 0, then do this, if not, do that.

Thanks a lot!


(*) this file is supposed to be the one with the list of files to be ereased.

---

### Post by Delkster on 2007-09-16
> **jmvidalvia said:**
> Any idea about: if file size(*) = 0, then do this, if not, do that.

Check out the man page for "test" (or "["). You can perform many kinds of tests regarding files with that. You could do something like:
```

if [ -s filename ]; then
    # do stuff when the file size is non-zero
fi

```

The exclamation mark (!) reverses the effect:
```

if ! [ -s filename ]; then
    # do stuff when the file size is zero
fi

```

---

### Post by jmvidalvia on 2007-09-16
Thank you very much for your help!

---

