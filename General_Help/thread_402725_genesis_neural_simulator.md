---
title: "genesis neural simulator"
date: 2007-04-06
forum: General Help
---

### Post by dbbolton on 2007-04-06
i installed GENESIS neural simulator (packages genesis and genesis-data), but can't get it working. here is the cl output:

```
daniel@lennox:~$ genesis
Cannot find a simrc file in the execdir/working or
home directories.  Copy one from startup/.simrc
in the GENESIS installation directory and try
again or see the README in the same location.

```

the problem is that i can't find any of these files. i don't know what "startup/.simrc" or "execdir/working" are.

according to the website, [http://www.genesis-sim.org/](http://www.genesis-sim.org/) , it appears that there should have been a folder created in /usr/local/ called "genesis", but that doesn't exist.

i installed this from synaptic, so where should the folder with the config files and so forth be ?

---

### Post by nikhilk on 2007-04-06
The output of this command
```
which genesis
```
will show you the path of the genesis executable, which will most probably be the installation path.

---

### Post by dbbolton on 2007-04-06
i already know that the executable is in /usr/bin, but there's no folder containing other files related to genesis. there's also no hidden folder in ~/ containing config files.

---

### Post by WW on 2007-04-06
I'm pretty sure that Ubuntu and Debian packages *never* put files in /usr/local.

It appears that the files that you want are in /usr/share/genesis/startup/.

FYI:
I found this by going to [http://packages.ubuntu.com](http://packages.ubuntu.com), and searching for genesis in, say, edgy. In the search results page,  I clicked on the **edgy** link in the genesis-data package.  In the package web page, I clicked on **list of files** in the "Download genesis-data" table.  In the files page, I clicked on **all** for "Result per page".  Finally, I did ctrl-F, and searched for **simrc**. (I am using Firefox, where ctrl-F allows you to search within a page.)  It took a lot longer for me to describe this process than to actually do it!

EDIT:
You can also browse the installed files in Synaptic: Use the Search button to find genesis-data.  Right-click on the package, and select Properties.  In the Properties window, click on the Installed Files tab.  (You won't be able to see the files if you don't have genesis-data installed.)

---

### Post by dbbolton on 2007-04-06
thank you very much !


i did 'cd /usr/share/genesis/' and launched 'genesis', then 'cd /usr/share/genesis/startup' and launched 'genesis', but i still get the same error.

---

### Post by WW on 2007-04-06
I *think* it wants you to put something like .simrc in either your home directory, or in the directory where you are running genesis.  Try this command, for example:
```

$ cp /usr/share/genesis/startup/simrc  ~/.simrc

```
That will copy simrc to the file .simrc in your home directory.

Then run genesis.

---

### Post by dbbolton on 2007-04-06
ok, i got it working. thanks again !

---

