---
title: "reconfigured kernel, but where is it?"
date: 2007-06-03
forum: General Help
---

### Post by t2000kw on 2007-06-03
I followed the directions on reconfiguring a kernel here:

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
[http://www.howtoforge.com/kernel_compilation_ubuntu_p2](http://www.howtoforge.com/kernel_compilation_ubuntu_p2)

but when I get to step 7 I don't see the new kernel. 

Here's my terminal output that lists the directory contents:

donald@donald:~$ cd /usr/src
donald@donald:/usr/src$ ls
linux                    linux-headers-2.6.20-15-generic
linux-2.6.20             linux-headers-2.6.20-16
linux-2.6.20.tar.bz2     linux-headers-2.6.20-16-generic
linux-headers-2.6.20-15  rpm

I believe that I should see something with the word custom in it since I followed the directions carefully except for the kernel number, which was 2.6.20 instead of the number used in the example. 

My intent was to disable USB_SUSPEND, and that is the only thing I did. 

I also don't see a kernel with "custom" in the title in GRUB, only the original Feisty kernel and the one with the recent update. 

Is there something missing in the directions on those web pages, like a directory change or something?

I did save the changes in the menuconfig window. 

Thanks!!!

Donald

---

### Post by t2000kw on 2007-06-03
Here is more terminal output that might help in figuring out what went wrong:

root@donald:/usr/src/linux# ls
arch       Documentation  kernel                net              stamp-configure
block      drivers        lib                   README           stamp-configure-arch
conf.vars  fs             linux-2.6.21          REPORTING-BUGS   stamp-configure-indep
COPYING    include        linux-2.6.21.tar.bz2  scripts          stamp-debian
CREDITS    init           MAINTAINERS           security         stamp-indep-conf
crypto     ipc            Makefile              sound            usr
debian     Kbuild         mm                    stamp-arch-conf

---

### Post by 5-HT on 2007-06-04
Was the compilation successful? The debs should show up in /usr/src  using that method if there were no errors.

Unrelated: using /usr/src/linux may not be such a good idea  [http://linuxgazette.net/issue62/tag/4.html](http://linuxgazette.net/issue62/tag/4.html)

---

### Post by t2000kw on 2007-06-04
I'll check the link later when I get home from work, but this might help put you on to what happened. I did have errors, and I don't understand why. I follwed those directions on the links I posted verbatim. PLease see my terminal output below.

In step # 5 on those links, does the word "uname" stay the same or am I supposed to replace it with my username? I think I tried it both ways. 

cp /boot/config-`uname -r` ./.config 

---------------------------------------------------------------------------------

I was OK right to the end when trying to compile the new kernel and
got this message:

root@donald:/usr/src/linux# cd .. && dpkg -i linux*.deb
dpkg: error processing linux*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux*.deb
root@donald:/usr/src# 

When I followed the instructions exactly, using all of the terminal
text as shown on the web page, not substituting anything, I get this
at the end of the compile and after. I don't know what's wrong.

starting at the end of the compiling, the terminal output shows this:
---snip---
  CC      kernel/fork.o
  CC      kernel/exec_domain.o
  CC      kernel/panic.o
kernel/panic.c: In function \u2018panic\u2019:
kernel/panic.c:61: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.
The bug is not reproducible, so it is likely a hardware or OS problem.
make[2]: *** [kernel/panic.o] Error 1
make[1]: *** [kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.20'
make: *** [debian/stamp-build-kernel] Error 2
root@donald:/usr/src/linux# 

There was probably no reason to go any further with these errors, but
I tried the next step anyway:

root@donald:/usr/src/linux# cd .. && dpkg -i linux*.deb
dpkg: error processing linux*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux*.deb
root@donald:/usr/src#

---

### Post by t2000kw on 2007-06-04
I checked this very quickly before leaving for work in a few minutes, and this part seems to be over my head. Right now I'm a step-by-step follower of directions and don't understand every step yet. I hope to sometime soon, of course, but have to go by "good" directions.

This is the part that is over my head:

--------------------------------------------------------------------------
"At the very least, folks, while you're building new kernels out there, here's a few safety tips:

    * when you put your kernel in place don't forget to put the matching System.map in with it. Don't toast it when you toss the source tree out for some space. That's your real symbol table, /proc/ksyms probably is a poor substitute.
    * keep constantly up to date on modutils, it tries to be good across the 2.x.x range of kernels
    * when you tweak /etc/lilo.conf don't forget to actually run /sbin/lilo... before you reboot!
    * after you boot on the new kernel, run
      depmod -a -F /path/to/correct/System.map
      so you really know that your modules aren't missing any symbols.
    * backups are good things. Always keep your old kernel binary and its modules around for a little while. 

If anyone has some good checklist points to look out for when compiling userland apps, or a clearer description of what's going on in glibc's tiny brain when it reaches for "headers", let us know!"

---------------------------
So, if someone knows of a more proper set of instructions that work, please post them here and I'll bookmark them. 

Or, if you can see by my terminal output that I misunderstood the directions and did something that I shouldn't have, let me know and I'll try again. For now, I'll continue to put up with having to use a work-around for USB scanner support.

Donald

Thanks!!!

---

