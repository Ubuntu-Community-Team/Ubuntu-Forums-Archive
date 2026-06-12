---
title: "vi doesn't work"
date: 2006-10-30
forum: General Help
---

### Post by showe1966 on 2006-10-30
Hello,

I installed version 6.06 LTS by upgrading from 5.10 using apt.
I also installed kubuntu, but never got round to using the kde yet.

I am alarmed to discover that if I type vi <filemane> from the command line, I get a "command not found" error.

If I do an apt-get install vim
It tells me vim is installed, already the latest version.

Soooo.... why is vi not working from the command line ??
Can anyone tell me what settings to check and where the noraml files to run vim are found ???

Thanxxxx a lot in advance
steve

---

### Post by skymt on 2006-10-30
If you really want to run vim as "vi", just do a "sudo ln -s /usr/bin/vim /usr/bin/vi". But why not just run it as "vim"?

---

### Post by tzulberti on 2006-10-30
vi and vim are differnt editors... You should run it as vim

---

### Post by showe1966 on 2006-10-31
Okay, point taken about using VIM as opposed to VI.
I have just always used VI, so I never even knew VIM existed until now.

But, to get back to the point if I do:-

vim foo.txt
bash: vim: command not found

So, if I step back from this whole situation and work out a methodical way to solve the problem what I need to do is the following:-

1.Find out if vim is installed or not
I guess I need to do "apt-cache search vim".
Well anyway in my case vim is installed so onto the next step unless anyone can think of a better way to do this than the above..

2.Find out exactly what files were installed when vim was installed using apt-get.
I don't know how to do this. Can anyone tell me how to do this ?

3.Find out which file is the binary in the list of files installed.
Probably quite obvious from the file name and position in the directory tree, but it would be interesting to know how to identify the binary in a better way if anyone knows how to.

4.Make the binary file work when I type in "vim" at the command prompt.
Is this called "adding it to my path" or something ??
How do I do this ??

BTW I often run into these problems when dealing with a variety of installed components in linux, so the above points would be very useful to me (and others) on a more wider scale as it is difficult to find a simple explaination of how to go about identifying component files of a package and making them useable IMHO.

Well, thanks for your time, you guys (and gals to be politically correct).

---

### Post by skymt on 2006-10-31
Sounds to me like you need to do a:```
sudo aptitude reinstall vim
```If you have the vim package installed properly, the vim command should work.

By the way, vim is VI iMproved. If you want plain vi (probably not a good idea), install the nvi package.

EDIT: vim installs into /usr/bin, and almost nothing would work if you didn't have that in your path. So don't worry about your path.

---

### Post by showe1966 on 2006-10-31
yes that worked alright.

but how about the answer to the other more general points ?
i.e. 
1.how do I find out what files are installed when you install any given package using apt?
2.How do I check if a binary file is in my current path and add it to the current path if it isn't ?

thanks for your help.

---

### Post by skymt on 2006-10-31
> **showe1966 said:**
> 1.how do I find out what files are installed when you install any given package using apt?
2.How do I check if a binary file is in my current path and add it to the current path if it isn't ?

1. Just run "dpkg -L *packagename*" in a terminal. L stands for list, as in "list files in this package". You can also see the list in Synaptic, in the package properties dialog.

2. "echo $PATH" will print your path, colon-separated. To see whether a particular executable is in one of these directories, use "which *execname*".

---

