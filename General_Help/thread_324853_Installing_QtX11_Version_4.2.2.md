---
title: "Installing Qt/X11 Version 4.2.2?"
date: 2006-12-24
forum: General Help
---

### Post by BetaMaster on 2006-12-24
I recently downloaded a program that said it required Qt/Xll to be installed.

> sven@sven-desktop:~/apps/maltonmap$ ./maltonmap
./maltonmap: error while loading shared libraries: libQtGui.so.4: cannot open shared object file: No such file or directory

So I tried installing Qt/X11. The installation instructions didn't make a lot of sense to me.

>                           INSTALLING A.

1.  If you have the commercial edition of Qt, install your license
    file as $HOME/.qt-license.

    For the open source version you do not need a license file.

2.  Unpack the archive if you have not done so already:

        cd /tmp
        gunzip qt-x11-opensource-src-4.2.2.tar.gz        # uncompress the archive
        tar xvf qt-x11-opensource-src-4.2.2.tar          # unpack it

    This creates the directory /tmp/qt-x11-opensource-src-4.2.2 containing the files
    from the archive. We only support the GNU version of the tar
    archiving utility. Note that on some systems it is called gtar.

3.  Building

    To configure the Qt library for your machine type, run the
    ./configure script in the package directory.

    By default, Qt is configured for installation in the
    /usr/local/Trolltech/Qt-4.2.2 directory, but this can be
    changed by using the -prefix option. Alternatively, the
    -prefix-install option can be used to specify a "local"
    installation within the source directory.

        cd /tmp/qt-x11-opensource-src-4.2.2
        ./configure

    Type "./configure -help" to get a list of all available options.

    To create the library and compile all the demos, examples, tools,
    and tutorials, type:

        make

    If you did not configure Qt using the -prefix-install option,
    you need to install the library, demos, examples, tools, and
    tutorials in the appropriate place. To do this, type:

        su -c "make install"

    and enter the root password.

    Note that on some systems the make utility is named differently,
    e.g. gmake. The configure script tells you which make utility to
    use.

    If you need to reconfigure and rebuild Qt from the same location,
    ensure that all traces of the previous configuration are removed
    by entering the build directory and typing

        make confclean

    before running the configure script again.

4.  Environment variables

    In order to use Qt, some environment variables needs to be
    extended.

        PATH               - to locate qmake, moc and other Qt tools

    This is done like this:

    In .profile (if your shell is bash, ksh, zsh or sh), add the
    following lines:

        PATH=/usr/local/Trolltech/Qt-4.2.2/bin:$PATH
        export PATH

    In .login (in case your shell is csh or tcsh), add the following line:

        setenv PATH /usr/local/Trolltech/Qt-4.2.2/bin:$PATH

    If you use a different shell, please modify your environment
    variables accordingly.

    For compilers that do not support rpath you must also extended the
    LD_LIBRARY_PATH environment variable to include
    /usr/local/Trolltech/Qt-4.2.2/lib. On Linux with GCC this step
    is not needed.

5.  That's all. Qt is now installed.

    If you are new to Qt, we suggest that you take a look at the demos
    and examples to see Qt in action. Run the Qt Examples and Demos
    either by typing 'qtdemo' on the command line or through the
    desktop's Start menu.

    You might also want to try the following links:

        [http://doc.trolltech.com/4.2/how-to-learn-qt.html](http://doc.trolltech.com/4.2/how-to-learn-qt.html)
        [http://doc.trolltech.com/4.2/tutorial.html](http://doc.trolltech.com/4.2/tutorial.html)
        [http://www.trolltech.com/developer](http://www.trolltech.com/developer)

    We hope you will enjoy using Qt. Good luck!


Step four is where I got lost. I don't know what it means by that. Could anyone help me?

---

### Post by Unterseeboot_234 on 2007-01-04
OK, you did the same thing I did. You went to Trolltech and downloaded the source, finally got it to make and install. My problem was even with checkinstall, there were no sym links where ubuntu wants them. I have revised .bash_profile PATH and it does nothing.

If you can live with QT 4.1.1 that is in the Synaptic repositories and it comes in chunks. Locate it with the Advanced, search for Trolltech. Get at least the core-qt for 4.1.1. It is a completely different install, ie it puts executables throughout the File system. In usr/bin it adds qt3/qmake... and other symlinks. Now, I can build a silly, tiny program to calibrate my color on the monitor.

The default install put 4.2.2 in usr/local/Trolltech/Qt-4.2.2. All the libraries. All the executables. Synaptic puts 4.1.1 all over the File system.

Too bad, QT 4.2.2 source bundle comes with demo, tutorial, code samples. Took forever and a day to ./configure then make, then checkinstall. To use this version, I will have to study up on getting the symlinks in the correct location. Glad I used **checkinstall**. I can ```
dpkg -r qt-x11-opensource-src
```

and go back and gedit .bash_profile back to the way it was.

---

### Post by Luggy on 2007-01-08
I solved the issue through this thread [http://ubuntuforums.org/showthread.php?t=331676&highlight=PATH]("http://ubuntuforums.org/showthread.php?t=331676&highlight=PATH")
thanks taurus!

So the easy awnser is to edit your .bashrc instead of your .bash_profile.
Add ```
PATH=/usr/local/Trolltech/Qt-4.2.2/bin:$PATH
export PATH
```

at the end of your .bashrc

I did a restarted X just to make sure my profile loaded right and it worked!

---

