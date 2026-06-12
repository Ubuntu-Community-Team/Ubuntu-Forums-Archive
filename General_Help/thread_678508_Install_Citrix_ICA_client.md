---
title: "Install Citrix ICA client"
date: 2008-01-25
forum: General Help
---

### Post by Kbeginner on 2008-01-25
I found a helpful "how to" here:  [https://help.ubuntu.com/community/CitrixICAClientHowTo]("https://help.ubuntu.com/community/CitrixICAClientHowTo")

My question is when it says to download and then extract, Kubuntu defaults to using Ark to open, and then when I get to this command:
> 
sudo tar xvfz en.linuxx86.tar.gz 

I get this error:

> tar: en.linuxx86.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Anyone shed some light on what I am missing?  Thx.

---

### Post by gvartser on 2008-01-26
try to add the full path to the file. In other words the path to where you saved the file.

```
sudo tar xvfz <full/path/to/file>/en.linuxx86.tar.gz
```

/g

---

### Post by Kbeginner on 2008-01-27
OKay, I tried the above like this:

> sudo tar xvfz /home/myname/en.linuxx86.tar.gz

But I get the same error.  So when I click on the download link to get the .tar file from CITRIX, how should I extract/open it once downloaded?  Should I not use ARK?

Thanks

---

### Post by gvartser on 2008-01-27
I am lost,
1) I downloaded the file from citrix download page.

2) Saved it under /tmp/ICA

3) moved into /tmp/ICA

4) Extracted the gzipped tar file: (NOT using sudo)
```
tar zxvf en.linuxx86.tar.gz
```

5) No problems. Extracted without errors.

So my tip is. Move into the directory where you saved the file, make sure that its there, then extract it as yourself, no need to do that as root. (See example in step 4)

/G

---

### Post by Kbeginner on 2008-01-27
Hmm, okay.  I am so new that it's embarrassing -- hence my confusion.

Right now, in console, I am stuck in the desktop...but the file is in my /home dir.

How do I get back to the basic console prompt (i.e. out of desktop)??

THx.

---

### Post by gvartser on 2008-01-27
to get into your home dir inside a shell.
Just type 
```
cd
```

That will always take you back to /home/<user_name> or whatever path you have..

Another way of doing it is to use the tilde character: ~
```
cd ~/
```

That will also bring you to your home directory.

To see where you are in the directory structure, you can type:
```
pwd
```
Then it will display where you are at the moment:
Example: (And I guess also in your case:)
/home/<user_name>/Desktop

If that is the case you could also use:
```
cd ..
```

which means step back one directory.

Best regz,
/g

---

### Post by Kbeginner on 2008-01-27
Okay, thank you.  It still shows me as being in the desktop, but when I do "pwd" it shows me as being in "home"...not sure why, but it seems to know where I am even if I don't.  

I'm going to try again.  THx.

---

### Post by Kbeginner on 2008-01-27
Success!  Took some finagling, but I got it to work. Thanks for your help!

---

### Post by gvartser on 2008-01-28
Ahh you are welcome.

/g

---

### Post by evolving_monkey on 2008-02-04
Thank you,,,,,,a very helpful thread.

---

