---
title: "error in compiling problem"
date: 2007-10-17
forum: General Help
---

### Post by tomerl on 2007-10-17
hi, 

i'm trying to compile few softwares and i'm getting the same errors every time:

[I]tomer@tomer-desktop:~/Desktop/usbsink-0.3.3$ make
make  all-recursive
make[1]: Entering directory `/home/tomer/Desktop/usbsink-0.3.3'
Making all in data
make[2]: Entering directory `/home/tomer/Desktop/usbsink-0.3.3/data'
LC_ALL=C ../intltool-merge -d -u -c ../po/.intltool-merge-cache ../po usbsink.desktop.in usbsink.desktop
Generating and caching the translation database
Merging translations into usbsink.desktop.
make[2]: Leaving directory `/home/tomer/Desktop/usbsink-0.3.3/data'
Making all in help
make[2]: Entering directory `/home/tomer/Desktop/usbsink-0.3.3/help'
Making all in usbsink
make[3]: Entering directory `/home/tomer/Desktop/usbsink-0.3.3/help/usbsink'
xsltproc -o usbsink-C.omf --stringparam db2omf.basename usbsink --stringparam db2omf.format 'docbook' --stringparam db2omf.dtd "-//OASIS//DTD DocBook XML V4.1.2//EN" --stringparam db2omf.lang C --stringparam db2omf.omf_dir "/usr/local/share/omf" --stringparam db2omf.help_dir "/usr/local/share/gnome/help" --stringparam db2omf.omf_in "/home/tomer/Desktop/usbsink-0.3.3/help/usbsink/usbsink.omf.in"  --stringparam db2omf.scrollkeeper_cl "`scrollkeeper-config --pkgdatadir`/Templates/C/scrollkeeper_cl.xml" `/usr/bin/pkg-config --variable db2omf gnome-doc-utils` C/usbsink.xml || { rm -f "usbsink-C.omf"; exit 1; }
make[3]: Leaving directory `/home/tomer/Desktop/usbsink-0.3.3/help/usbsink'
make[3]: Entering directory `/home/tomer/Desktop/usbsink-0.3.3/help'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/tomer/Desktop/usbsink-0.3.3/help'
make[2]: Leaving directory `/home/tomer/Desktop/usbsink-0.3.3/help'
Making all in pixmaps
make[2]: Entering directory `/home/tomer/Desktop/usbsink-0.3.3/pixmaps'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/tomer/Desktop/usbsink-0.3.3/pixmaps'
Making all in po
make[2]: Entering directory `/home/tomer/Desktop/usbsink-0.3.3/po'
file=`echo pt_BR | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file pt_BR.po
/bin/sh: -o: not found
make[2]: *** [pt_BR.gmo] Error 127
make[2]: Leaving directory `/home/tomer/Desktop/usbsink-0.3.3/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tomer/Desktop/usbsink-0.3.3'
make: *** [all] Error 2 [/I]

i've tried to search for solution for this line **/bin/sh: -o: not found** but nothing came up.

help me please.

---

### Post by SeanTater on 2007-10-17
Just in case you are not aware, Ubuntu has a Package Management program called APT. It installs software for you without compiling. You can easily use this using a program called Synaptic. For that, Look here: [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

In your case, I don't believe it's possible to correctly compile that program without changing it. -o obviously is not a program, it's an option to be sent to a program, and you can't execute an option.

---

### Post by erginemr on 2007-10-17
Unlike some other distros, Ubuntu does not come with preinstalled compilers needed to build programs from source. You need to install the meta package "build-essential" first to be able to compile anything with "sudo aptitude install build-essential".

Besides, almost all compilation tasks in Linux starts with "./configure" command in the following order:
./configure
make
sudo make install

---

### Post by tomerl on 2007-10-17
i'm familiar with apt and aptitude, this is not the case.
not every new software can be installed with apt and synaptic, so from time to time you may need to compile things on your own, which i think it's part of the fan using linux, not using automatic installation by clicking next-next-yes like windows.

build-essentials is already installed.
./configure -> complete successfully
make -> giving the same errors
make install -> don't i need to pass the previous step before? :cool:

---

### Post by erginemr on 2007-10-17
OK then. In the line:
file=`echo pt_BR | sed 's,.*/,,'`.gmo \
&& rm -f $file && -o $file pt_BR.po
/bin/sh: -o: not found

In the Bash convention, the backslash is put there to continue a command with a new line, and && is to separate commands and execute them one after the other provided that the previous command has been executed successfully.

In this respect, in the line
 -o $file pt_BR.po
there is something missing. Normally, -o is one of the gcc (c compiler) arguments as in
gcc -o "file name". What makes me wonder is that the script already erases the $file with the command:
rm -f $file
and tries to do something with that afterwards. :confused:

Do you happen to run into this error when trying to compile other programs, too? Otherwise, I would say there is something wrong with the source of this program (usbsink-0.3.3).

---

### Post by posterboy on 2007-10-17
Hmmm, that's a mystery, isn't it? /bin/sh -o prints out the current options, which here looks like:
errexit         on
noglob          on
ignoreeof       on
interactive     on
monitor         on
noexec          on
stdin           on
xtrace          on
verbose         on
vi              on
emacs           on
noclobber       on
allexport       on
notify          on
nounset         on
nolog           on
debug           on

Let me suggest you try that in a bash shell. /bin/sh -o and let's see what you get.

---

### Post by darjeeling on 2007-10-20
Hmmmmm, this is happening to me as well.
Odd. Compiling on Feisty went fine...

Even tried unlinking /bin/sh from dash and putting it to bash. No go.
Possible bug.

---

### Post by toadmess on 2007-11-16
Hello,

Have just had a similar problem whilst trying to install a particular flavour of gnomad2 on gutsy. 

If it helps, I managed to resolve it simply by installing the gettext package (in addition to the already installed gettext-base). A quick re- ./configure && make later it compiled fine.

Hope this helps.

---

### Post by Ymer on 2008-01-17
I had the same error compiling Geany 0.12 which is not in the repository.

Thanks to toadmess, by installing the gettext it got compiled. I wonder why they don't have this to be checked in their configure system.

---

### Post by Shii on 2008-05-05
I had the same error and gettext fixed it so I filed a bug about it here.

[https://bugs.launchpad.net/ubuntu/+source/build-essential/+bug/227163](https://bugs.launchpad.net/ubuntu/+source/build-essential/+bug/227163)

---

### Post by Shii on 2008-05-06
Apparently my bug is "wishlist" quality, as if this is a feature I wish Ubuntu would have.

I wish Ubuntu wouldn't break when I installed software, is my honest desire here.

---

