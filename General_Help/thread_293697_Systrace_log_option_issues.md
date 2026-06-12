---
title: "Systrace log option issues"
date: 2006-11-05
forum: General Help
---

### Post by pchavez on 2006-11-05
Hello!  I was wondering if anyone has had any experience with the debian/linux port of systrace.

I got the program to install and it runs just fine.  It catches system calls and pops up windows just great.  My problem is when I try to use the "log" option.

For example, if I have the following policy file for /bin/ls that was generated with the help of "systrace ls":

```
Policy: /bin/ls, Emulation: linux
	linux-read: permit
	linux-close: permit
	linux-write: permit
	linux-read: permit
	linux-exit: permit
```

I decide I want to log the write system call so I stick "log" on the linux-write: permit line:

```
Policy: /bin/ls, Emulation: linux
	linux-read: permit
	linux-close: permit
	linux-write: permit log
	linux-read: permit
	linux-exit: permit
```

After I run "systrace ls" again I get a "syntax error" message with the line number of the "log" option (line 4).  Other than that it works great!  But because I want to use systrace to record system calls for a research project not having the "log" option work is pretty frustrating.

Any ideas or experience with this?


For those who are curious, this are the steps I took to install systrace on my Kubuntu 6.10 i386 system:

[LIST=1]
[*]Download and install libevent1
[INDENT]Systrace flagged the libevent1 package as a dependency.  I found it at [http://packages.unbuntu.com/dapper/libs/libevent1](http://packages.unbuntu.com/dapper/libs/libevent1) as a .deb package.  Right-clicking package gives a Kubuntu Package Menu -> Install Package option that works great.[/INDENT]
[*]Download and install systrace
[INDENT]Get systrace from [http://www.citi.umich.edu/u/provos/systrace/systrace_1.6d_i386.deb](http://www.citi.umich.edu/u/provos/systrace/systrace_1.6d_i386.deb) and install it using the same procedure as above.[/INDENT]
[*]Download and install libgtk1.2-common.  
[INDENT]I found it at [http://packages.ubuntu.com/dapper/misc/libgtk1.2-common](http://packages.ubuntu.com/dapper/misc/libgtk1.2-common) .  Libgtk1.2 requires this.[/INDENT]
[*]Download and install libgtk1.2
[INDENT]The older GTK library is required for the xsystrace gizmo that pops up and informs the user about what system calls are being made.  I found it at [http://packages.ubuntu.com/dapper/libs/libgtk1.2](http://packages.ubuntu.com/dapper/libs/libgtk1.2) and installed it using the same method.[/INDENT]
[*]Download and install xsystrace
[INDENT]This is the GUI that displays the permit/deny buttons and I found it at [http://www.citi.umich.edu/u/provos/systrace/xsystrace_0.1_i386.deb](http://www.citi.umich.edu/u/provos/systrace/xsystrace_0.1_i386.deb) .[/INDENT]
[/LIST]

---

