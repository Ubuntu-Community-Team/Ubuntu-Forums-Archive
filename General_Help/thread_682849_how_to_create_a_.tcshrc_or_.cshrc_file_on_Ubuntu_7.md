---
title: "how to create a .tcshrc or .cshrc file on Ubuntu 7.10?"
date: 2008-01-30
forum: General Help
---

### Post by saitang on 2008-01-30
Hi all,

I am fairly new to Ubuntu and not very familiar with Linux systems.

I am installing an application that requires me to add a few lines into my ,cshrc (I was told later that I could use tcsh as well, so I could also change my .tcshrc).

However my Ubuntu 7.10 does not have a .cshrc or tcshrc file. I have installed tcsh as well.

I've been trying to create a .xxxrc file and include some lines like:

setenv PATH /home/sai/bin

but afterwards the shell does not understand commands like "ls" and I can't even change back to bash by typing "bash".

The lines that I need to add are as follows:

# local directory where we are installing everything

setenv HOMEDIR /space/kulka020

# library name extension used by Perl on our system

setenv LIBDIR /space/kulka020/MyPerlLib

# UMD developed code, we need to set their /bin directories in the PATH

setenv SENSECLUSTERS $HOMEDIR/SenseClusters-v0.93
setenv NSP $HOMEDIR/Text-NSP-1.01

# externally developed C code, directories contain executable code so must
# be included in PATH

setenv SVDPACK $HOMEDIR/SVDPACKC
setenv CLUTO $HOMEDIR/cluto-2.1.1

# pick the right version of Cluto (Solaris or Linux)

set OSNAME=`uname -s`

if ($OSNAME == "SunOS") then
        setenv MYCLUTO $CLUTO/Sun
else if ($OSNAME == "Linux") then
        setenv MYCLUTO $CLUTO/Linux
else echo "lost"
endif

# set the path that Perl searches for CPAN modules

setenv PERL5LIB $LIBDIR

# set the path that is searched for executables

set AKPATH = ($SVDPACK $NSP/bin $MYCLUTO $SENSECLUSTERS/bin .)

set path = ($AKPATH $path)

Anyone knows how to properly create a tcshrc or cshrc? This is really urgent because I need to get this working for my project.

Any help would be appreciated!

Sai

---

### Post by geraldm on 2008-01-30
genuine is on sourceforge.net  You may have a closer mirror than this one
[http://umn.dl.sourceforge.net/sourceforge/tcshrc/tcshrc-1.6.0.tar.gz](http://umn.dl.sourceforge.net/sourceforge/tcshrc/tcshrc-1.6.0.tar.gz)

Gerald

---

