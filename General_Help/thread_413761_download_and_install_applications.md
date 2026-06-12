---
title: "download and install applications"
date: 2007-04-19
forum: General Help
---

### Post by obzone on 2007-04-19
Installing applications:

1. I'm trying to install XAMPP. I have downloaded the tar.gz file to the desktop.
I need to copy it to the /opt folder and then run tar zxvf (as per instruction in the book)
But I can't transfer the file to /opt - I type in:

sudo cp xampp-linux-1.6.1.tar.gz

it asks for my password and accepts it (no error message)
but nothing happens and no transfer.

Similarly 
2. trying to install bluefish I do as the website suggest for a ubuntu system:

sudo apt-get install bluefish

again it accepts the password and does nothing


Any suggestions what I am doing wrong?
(Using dapper)

---

### Post by zeekay on 2007-04-19
About the tar.gz, I suspect you downloaded the source code of it. Open it normally, and extract it to a folder.

After that, take a look on that folder and search for a file named "configure", if it's there, you've downloaded the source and need to compile it. Else, take a look on the README.

To compile it, go to the terminal, and access the folder you got the esctracted files.
Type in:
```
# ./configure
```
If after it stops processing there were no errors, then type:
```
# sudo make
```
Again, if no errors ocurred... type:
```
# sudo make install
```

Then the program would be installed on your system.

For the second question, sometimes the program's name differs from the package's name. What I'd recommend is that before doing the "apt-get install", you search the repositories for the real name of it, with the following command:
```
# apt-cache search [program's name]
In your case it would be
# apt-cache search bluefish
```

And then it would most likely return a list of programs with that name or that are somehow related to it. Pick the one you think it is the program you want to install, and then do the "sudo apt-get install [program's name]" the way you've been doing.

I hope I had helped. :)

---

### Post by obzone on 2007-04-19
Thanks for your comments

Downloading the XLAMPP application is a set of binary files and multiply folders. It is't source.

The instructions are very straight forward in Jono Bacon's book
Also I downloaded it to the desktop and I can't even copy it to the /opt path before trying to extract it

The apt-cache search bluefish command did the same as the others - it came back with the prompt and that's all.

I think I'm having more of a problem controlling the file access than the installation ?

---

