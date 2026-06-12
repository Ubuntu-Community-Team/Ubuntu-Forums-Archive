---
title: "Why can't I execute from a CD-Rom?"
date: 2006-07-10
forum: General Help
---

### Post by jupiterscv on 2006-07-10
Perhaps I'm being stupid.

I have a piece of software, Stata, which I'd like to install. I have the installation CD, and I have mounted it (either in /media/cdrom or /mnt/cdrom0). I am supposed to created a specific directory in /usr to which to install the package. This I have done.

So far, so good. The CD is mounted, I can see the files (I can even more them!). I am in my new directory. I type 

/media/cdrom0/install
 
as I've been told to do. The response I get is

bash: /media/cdrom0/install: Permission denied

Any idea why this might be? I have done all of the work after suing.

---

### Post by soze on 2006-07-10
> **jupiterscv said:**
> Perhaps I'm being stupid.

I have a piece of software, Stata, which I'd like to install. I have the installation CD, and I have mounted it (either in /media/cdrom or /mnt/cdrom0). I am supposed to created a specific directory in /usr to which to install the package. This I have done.

So far, so good. The CD is mounted, I can see the files (I can even more them!). I am in my new directory. I type 

/media/cdrom0/install
 
as I've been told to do. The response I get is

bash: /media/cdrom0/install: Permission denied

Any idea why this might be? I have done all of the work after suing.

It's probably because the install script/program is not executable.

Try copying everything from the cdrom into a temporary directory then: ```
sudo chmod a+x install
```

Then you should be able to run the installer.

---

### Post by jupiterscv on 2006-07-10
OK,

tried it.

It doesn't seem to like this either.

install: missing file operand
Try `install --help' for more information.

this is the reply.

I think what bothers me is that Stata tells me that I should just be able to code:

/mnt/cdrom/install,

and all is a go.

Thanks, for the idea, though!

---

### Post by taurus on 2006-07-10
Well, what is the output of this command from a terminal then?
```

ls -la /mnt/cdrom

```

---

