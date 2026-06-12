---
title: "which directory to put LaTeX .sty files into?"
date: 2016-10-27
forum: General Help
---

### Post by rybnik on 2016-10-27
I want to manually install a LaTeX library.  Where do I put the .sty file?

I've already seen [this post]("https://ubuntuforums.org/showthread.php?t=1330890&p=8345011#post8345011"), but it didn't work for me.

Thanks!

---

### Post by Portaro on 2016-10-27
Please take a look here &#8594;

[https://help.ubuntu.com/community/LaTeX](https://help.ubuntu.com/community/LaTeX)

This is the steps that you need to take attention &#8594;
> [h=3]User install[/h][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]We will copy this into our personal texmf tree. The advantages of this solution are that if we migrate our files to a new computer, we will remember to take our texmf tree with us, resulting in keeping the same packages we had. The disadvantages are that if multiple users want to use the same packages, the tree will have to be copied to each user's home folder.[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]We'll first create the necessary directory structure:[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[FONT=inherit][/FONT]cd ~
[FONT=inherit][/FONT]mkdir -p texmf/tex/latex/foo[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Notice that the final directory created is labeled foo. It is a good idea to name directories after the packages they contain. The -p attribute tomkdir tells it to create all the necessary directories, since they don't exist. Now, using either the terminal, or the file manager, copy foo.styinto the directory labeled foo.[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Now, we must make LaTeX recognize the new package:[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[FONT=inherit][/FONT]texhash ~/texmf[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][h=3]System install[/h][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]We will copy the foo to the LaTeX system tree. The advantages are that every user on the computer can access these files. The disadvantages are, that the method uses superuser privileges, and in a possible reformat/reinstall you have to repeat the procedure.[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]First, go to the folder your foo is located. The following commands will create a new directory for your files and copy it to the new folder:[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[FONT=inherit][/FONT]sudo mkdir /usr/share/texmf/tex/latex/foo
[FONT=inherit][/FONT]sudo cp foo.sty /usr/share/texmf/tex/latex/foo[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Then update the LaTeX package cache:[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[FONT=inherit][/FONT]sudo texhash

[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR]

---

### Post by Impavidus on 2016-10-29
When I manually install some LaTeX packages, I put them in (subdirectories of) **/usr/local/texmf/**. The .sty files usually go in **/usr/local/texmf/tex/latex/packagename/**. This way they don't interfere with the packages supplied from the Ubuntu repositories (in **/usr/share/tex***). **/usr/local/** is the appropriate directory for system-wide manual installation.

After installation, run **sudo texhash** to update TeXs database of available packages. For most packages (with the notable exceptions of fonts and hyphenation patterns) that should work.

Note that after a release upgrade, you may have to fix your manually installed packages, whether they are in /usr/local or in your home directory. You get a new version of TexLive, which results in new versions of many packages and different packages too. Your manually installed package may now be available from the Ubuntu repositories, or one of its dependencies may no longer be available from there, or there may be version conflicts.

---

### Post by rybnik on 2016-11-10
Yay, it worked!  Thank you both for helping.

For those who might stumble across this thread, here's the quick-and-dirty of how to manually install a package:

```

cd ~

mkdir -p texmf/tex/latex/USER_DEFINED_NAME_GOES_HERE

copy the .sty file into the newly-created directory

texhash ~/texmf

```

---

