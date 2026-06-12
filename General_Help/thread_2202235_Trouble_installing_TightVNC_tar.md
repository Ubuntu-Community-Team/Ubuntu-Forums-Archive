---
title: "Trouble installing TightVNC tar"
date: 2014-01-28
forum: General Help
---

### Post by daveabes on 2014-01-28
On the subject matter however, I am also a newish user and am having some trouble copiling software.

I have downloaded the TightVNC latesd edition from their server. I run tar -xzvf filename.tar.gz and the extraction completes OK.
Now there is a new folder with many files in. One of the is a readme with various instructions.
When trying to run sudo ./configure I receive command not found.

Within the README file is this. I'm not sure how to proceed with the README instructions.
I don't know what xmkmf or makeworld is....
Any help appreciated.

README CONTENTS:

  TightVNC version 1.3.10
  Source distribution for Unix platforms

======================================================================

First you must have a reasonably recent version of X installed (this includes
/usr/openwin on Solaris machines).  Also, TightVNC requires JPEG and zlib
libraries installed in the system (e.g. under /usr/local).  To build
everything but Xvnc, do:

    % xmkmf
    % make World

This should build first the vncauth library which is used by each of the
programs, then vncviewer, vncpasswd and vncconnect.

Xvnc differs from the other programs in that it is built inside a cut-down
version of the X build tree.  This is based around the XFree86 3.3.2 "server
only" distribution, which in turn is based on the X11R6.3 distribution from
the X consortium.  To build Xvnc, do:

    % cd Xvnc
    % ./configure
    % make

If you have trouble building Xvnc, see the Xvnc/README file for more details.

If it all builds OK you should copy the programs to some directory which
is in your PATH environment variable, such as /usr/local/bin.  Also, it's
handy to install manual pages in a directory where the man utility can find
them.  You can use the vncinstall script to do this for you (man path is
optional):

    % cd ..
    % ./vncinstall /usr/local/bin /usr/local/man

If you want to use the Java VNC viewer, you should copy the class files from
the classes directory to some suitable installation directory such as
/usr/local/vnc/classes:

    % mkdir -p /usr/local/vnc/classes
    % cp classes/* /usr/local/vnc/classes

We recommend that you use the vncserver script to run Xvnc for you.  You can
edit the script as appropriate for your site.  Things you may need to change
include:

 * The location of Perl - if Perl is not installed in /usr/bin you'll need
   to edit the "#!/usr/bin/perl" first line of vncserver.

 * $vncClasses - this specifies the location of the Java classes for
   the VNC viewer applet.  The default is /usr/local/vnc/classes.

 * Xvnc's font path and color database.  If you have an installation of
   X which is not in the standard place you may need to add arguments to the
   Xvnc command line to set these.  These should be appended to the $cmd
   variable at the comment "# Add font path and color database...".

---

### Post by monkeybrain20122 on 2014-01-28
> **daveabes said:**
> ROFL at caps rant. I agree.

On the subject matter however, I am also a newish user and am having some trouble copiling software.

I have downloaded the TightVNC latesd edition from their server. I run tar -xzvf filename.tar.gz and the extraction completes OK.
Now there is a new folder with many files in. One of the is a readme with various instructions.
When trying to run sudo ./configure I receive command not found.

.

There should be a script name configure in the extracted folder (Xvnc) 
and you need to cd (change directory) into it to run the configure script 
so 

cd Xvnc (or whatever the path is, if it is in Downloads, then cd Downloads/Xvnc)
./configure

After running this check if there is any error message. Usually it will tell you some dependencies are missing, install them from the package manager (usually the -dev files, so for example, if it complains that it cannot find foo, install libfoo-dev or something like that,--maybe it is called libfoo1234-dev. I find synaptic particularly useful for locating these packages)

There is no need for "sudo", just use it in the last step (sudo make install)

If you have checkinstall installed (from the repo) you can replace the  last step with "sudo checkinstall", it will create a .deb and install  that so you can neatly remove it from the package manager (e.g synaptic)  if need to.

---

### Post by Bucky Ball on 2014-01-28
*Post moved to own thread.*

Please do not hijack threads for a wide range of reasons. Post a new thread with a title describing your problem. This will improve your chances of getting help. Thanks.

---

