---
title: "how to install scribes text editor on Ubuntu 15.10"
date: 2016-03-26
forum: General Help
---

### Post by meltingpot2015 on 2016-03-26
If you've just installed Ubuntu 15.10, and would like to install your favorite text editor 'Scribes', read on.

The instructions at the [scribes website]("http://scribes.sourceforge.net/download.html") are useful, but are not specific to Ubuntu 15.10. After [downloading scribes]("http://launchpad.net/scribes/0.4/scribes-milestone1/+download/scribes-0.4-dev-build954.tar.bz2"), you will need to install several packages. 

Here are the packages that are needed:

1) bzr
2) gnome-common
3) libglib2.0-dev
4) gnome-doc-utils
5) python-gtk2-dev
6) libgtksourceview-3.0-dev
7) gtksourceview-3.0
8) scrollkeeper

You can install them using the Ubuntu Software Centre or terminal. To install using Terminal, open a Terminal window and type:

```
sudo apt-get install <package name>

```

Do this for each package 1 to 8. I don't know if the order you install them matters or not, but I installed them in the order above and installed them one at a time. How come I installed them in this order: When I ran autogen.sh the first time, it gave an error, I looked up the error online and it hinted that I need gnome-common, so installed gnome common..ran the script..script was annoyed with something..searched the causes for that error and found it's to do with libglib2.0-dev, so installed that, then ran the script...that gave another error...looked-up that error...found gnome-doc-utils was needed, installed that...ran the script again...and so on...you get the picture...

After installing 'scrollkeeper', the script completed successfully. Then ran 'make', after that ran 'sudo make install'.

---

### Post by Impavidus on 2016-03-26
The order doesn't matter. If one of those packages depends on another, it will pull it in automatically. You can even install all of them in a single command.

Note the usual caveat for manually installing something from source: you have to update manually too. It's the last resort for installing stuff on Ubuntu, but it's fine otherwise.

---

### Post by meltingpot2015 on 2016-03-27
> **Impavidus said:**
> The order doesn't matter. If one of those packages depends on another, it will pull it in automatically. You can even install all of them in a single command.

Note the usual caveat for manually installing something from source: you have to update manually too. It's the last resort for installing stuff on Ubuntu, but it's fine otherwise.

Usually go for the automatic install from repository. But with this installation it didn't pan out.

1) Using the instructions [here]("http://mystilleef.blogspot.com/2010/10/scribes-gets-ubuntu-ppa.html"), I opened a terminal and typed: 

```
sudo add-apt-repository ppa:mystilleef/scribes-daily

```

This part was okay (no warnings/errors).

2) Then I did: 

```
sudo apt-get update
```

It got to the finish and gave a warning about the repository added in step (1)

```
W: Failed to fetch ......
```

3) ran ```
sudo apt-get install scribes

```

got the error ```
E: Unable to locate package scribes

```

So, used the manual installation option instead.

Pretty sure I didn't use the manual installation from source when Scribes was installed on my Ubuntu 14.04 build.

---

