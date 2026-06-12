---
title: "Infinite X11 Loop"
date: 2015-08-16
forum: General Help
---

### Post by oldefoxx on 2015-08-16
I've got Ubuntu 14.04 Deskrop installed on my laptop.  It works fine, and I added PureBasic 5.31 to it, which loads and runs fine.  Except I tried to compile and run one of the example files provided, the one named FileSystem.pb.  Anf that gets a compiler error.Seems its Linker looked for a file and could not find it, so it quit.  I'm attaching a screenshot of the message in case you are interested.  The line reads funny, and I had to first try and check it out, then sleep on it,  before I figured it out, at least in part:

It reads "/usr/bin/ld: cannot find -lX11".  The last line reads "collect2: error: ld returned 1 exit".

What I didn't understand was "-lX11"// I read it initially as "-IX11".  I looked in /usr/bin/ and found an X11 folder, but nothing like that as a filename.  In fact. after I went into terminal mode, I quickly learned that the "dir" and "ls" commands will not accept a "-" (hypjen or minus sign" as the lead character in a folder or file name.  The bash interpreter sees this as the indicator of an option for a command no matter how you try to frame it.  So I went to sleep with some confusion in ,my head.  And woke up with an answer there instead.

If it is actually "-lX11" instead of "-IX11", then the Linker is looking at a link to library X11 as an argument.  And it wasn't finding it.  But there was a folder named /usr/bin/X11 there, I had seen it.  So I turned on the laptop and used the GUI Nautilus File Manager and looked inside /usr/bin/X11, and after a vit of a delay (unusual, as this is a fast laptop), I saw another folder named X11 and a bunch of files that looked like a repeat of what I had seen in /usr/bin/X11.  So I went into that X11 folder, and saw the same thing again.  So I went into that one, and again saw the same thing.  Is this real?  the way to find out was to get back into Terminal mode and see what happened as I repeated the process.  I began with this simple step:
```

cd /usr/bin
dir -d1 X11
X11
cd X11

```
And kept repeating the last command as I watched the path begin to grow with more X11s being tagged on over and over, rhen repeated the whole process from scratch so that I could get a screenshot of it, which is the second attachment.  Obviously I have a link somwhere that is looping back to itself over and over, but where was it, and how do I find it, and where will this end?  Let's keep going and see if we can find out.  That will be the third screenshot.  So while the loop itself is infinite, the length of a path is not.  You go beyond its limits, it begins over, as least when chasing after subfolders that are misslinked inside.

I've never created a logical or symbolic link, and can't even tell you why to use one and not the other.  I installed this OS and am the only user of this laptop.  So to find a problem in this area suggests it was done elsewhere, and is part of the install package,  Which is pretty much my  reason for opening this thread.  That, and learning how to fix it.  Now it's someone elses turn.

---

### Post by steeldriver on 2015-08-16
The convention for library linkage is that the directive

```

-lfoo

```

on the compiler/linker command line means "link the library whose name is libfoo". So you should be looking for files like libX11.so or libX11.a - both of which are provided by the libx11-dev package:

```

dpkg -S libX11.{so,a}
libx11-6:amd64: /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
libx11-6:amd64: /usr/lib/x86_64-linux-gnu/libX11.so.6
libx11-dev:amd64: /usr/lib/x86_64-linux-gnu/libX11.so
libx11-dev:amd64: /usr/lib/x86_64-linux-gnu/libX11.a

```

As to your other "issue", yes it seems that /usr/bin/X11 is indeed a symbolic link to its parent, /usr/bin:

```

$ ls -l /usr/bin/X11
lrwxrwxrwx 1 root root 1 Feb 15 09:45 /usr/bin/X11 -> .

```

I don't know why that is, however it shouldn't have any relevance to your linker errors.

---

### Post by oldefoxx on 2015-08-17
I also confirmed that the link loop is generic to at least 14.04, as I have 3 other installs on my old laptop that behave the same way.  And I appreciate the information on what the -l stands for, and what I should be looking for.

I tried this, first as user, then with sudo, then had to become superuser as I was getting Permission Denied repeatedly:
```

~# find / -name libX11.*
/usr/share/doc/libx11-dev/libX11/libX11.pdf.db.gz
/usr/share/doc/libx11-dev/libX11/libX11.html
/usr/share/doc/libx11-dev/libX11/libX11.html.db
/usr/lib/x86_64-linux-gnu/libX11.a
/usr/lib/x86_64-linux-gnu/libX11.so
/usr/lib/x86_64-linux-gnu/libX11.so.6
/usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
/usr/lib/i386-linux-gnu/libX11.so.6
/usr/lib/i386-linux-gnu/libX11.so.6.3.0

```
I see in the middle the .a and ,so files.  But they are not in /usr/bin/ where the linker is looking for them.  Can I just copy them there, or should I find out if the linker can be redirected to that path?  What's best?  If I copy them there, the chances are that future updates will miss them.  And actually the linker error message stated /usr/bin/ld.  The ld might be significant, or just a tag-on used in the error message.

I'm just getting started with programming in linux.  So there are vast gaps in my knowledge of the subject.  If you search on "basic programming linux", you will find links to languages like FreeBasic, KBasic,  BaCon,  and many more.  In fact, if you visit [http://basic.mindteq.com/index.php?i=linux]("http://basic.mindteq.com/index.php?i=linux"), you will find a list where they are each rated.  But not all are free, a fact not noted there.  Nor does it tell you where to go to get them.  That would be a separate search.

Some dispise BASIC in any form.  They go with C, C++. or C#.  To them, that is mainstream programming.  But any version of C is so dense and terse that picking up a printout and trying to understand it is super hard.  In fact, they came up with an add-on tool named Lint that was suppose to find errors in the code for you.  Of course similar tools are available for other languages, including BASIC, but these are generally known as debuggers.  And there is a distinction between languages that are just interpreted and others that are actually compiled.  Compiled code is a lot faster when executed.  And if you want a linux scripting language, you have choices like Python , Perl, Ruby, Bash, and so on.  To choose where to start, do a search that deals with best linux languages or best linux scripting languages.  Here are a couple of such links:
[http://stackoverflow.com/questions/70453/which-scripting-language-is-best](http://stackoverflow.com/questions/70453/which-scripting-language-is-best)
[http://www.freeos.com/guides/lsst/]("Linux Shell Scripting Tutorial v1.05r3  A Beginner's handbook")

Keep in mind, that a scripting language does not cover different operating systems readily, while an actual programming language may.  Some of the languages cover linux, windows, and the Mac, which is a handful.   You can't write one program that runs on all these, but you can pretty much recompile the same source code into an executable to run on each platform independently.

X11 provides a graphics engine and interface for certain applications, called clients.  It is heavily used for terminal sessions in Linux and Unix, but has been largely replaced by newer graphics solutions elsewhere.  Though still available for the MacOS, it has mostly been discontinued there.   PureBasic apparently makes use of it.  I like PureBasic as an option for shifting over to programming for linux, as the same source code can be compiled to run under Windows or the MacOS.  But for the MacOS, from what I've just read, you have to add in the X11 library.  Unless the PureBasic compiler for the MacOS uses something else in its place.  Different compilers involved, but all for just one price.

I've got to go to the PureBasic forums and find out what they recommend for resolving the X11 placement issue.  But it still leaves unanswere whether I should just remove the symbolic link that was uncovered.  It could make a mess out of a rm -r command for that structure, unless the link gets removed first.

---

### Post by steeldriver on 2015-08-17
What makes you think the linker is looking in /usr/bin? that would be a non-standard place to look for libraries. Is there a way to invoke PureBasic from the command line, so you can get a more informative error message than the one shown in the dialog box?

Alternatively, if you can share a link to where you got PureBasic from / how you installed it, I can try to install it on my machine and do some diagnostics for you

Meantime I **don't** recommend removing any system files or symbolic links

---

