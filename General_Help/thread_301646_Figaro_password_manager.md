---
title: "Figaro password manager"
date: 2006-11-17
forum: General Help
---

### Post by xender69 on 2006-11-17
Hi all, new member here.  testing out ubuntu.  it's different and interesting.  Before I submitted this thread, I did do a search on fpm but didn't see one.

Here is my question:  Has anyone successfully installed figaro password manager on their ubuntu ?

I'm getting close. I've run the rpm -ivh fpm-0.60-1.i386.rpm

but get the following failed dependencies error:
        gtk+ >= 1.2 is needed by fpm-0.60-1.i386
        libICE.so.6 is needed by fpm-0.60-1.i386
        libSM.so.6 is needed by fpm-0.60-1.i386
        libX11.so.6 is needed by fpm-0.60-1.i386
        libXext.so.6 is needed by fpm-0.60-1.i386
        libXi.so.6 is needed by fpm-0.60-1.i386
        libart_lgpl.so.2 is needed by fpm-0.60-1.i386
        libaudiofile.so.0 is needed by fpm-0.60-1.i386
        libc.so.6 is needed by fpm-0.60-1.i386
        libc.so.6(GLIBC_2.0) is needed by fpm-0.60-1.i386
        libc.so.6(GLIBC_2.1) is needed by fpm-0.60-1.i386
        libdl.so.2 is needed by fpm-0.60-1.i386
        libesd.so.0 is needed by fpm-0.60-1.i386
        libgdk-1.2.so.0 is needed by fpm-0.60-1.i386
        libgdk_imlib.so.1 is needed by fpm-0.60-1.i386
        libglib-1.2.so.0 is needed by fpm-0.60-1.i386
        libgmodule-1.2.so.0 is needed by fpm-0.60-1.i386
        libgnome.so.32 is needed by fpm-0.60-1.i386
        libgnomesupport.so.0 is needed by fpm-0.60-1.i386
        libgnomeui.so.32 is needed by fpm-0.60-1.i386
        libgtk-1.2.so.0 is needed by fpm-0.60-1.i386
        libm.so.6 is needed by fpm-0.60-1.i386
        libm.so.6(GLIBC_2.0) is needed by fpm-0.60-1.i386
        libxml2.so.2 is needed by fpm-0.60-1.i386
        libz.so.1 is needed by fpm-0.60-1.i386


My question.  is there a application in ubuntu that I can use to download & install all the dependencies ?  or will I need to download them from someplace like rpmfind ?

thanks in advance.

---

### Post by scrooge_74 on 2006-11-17
Good to hear you are joining the ranks.

In Ubuntu you install programs or make updates using the Synaptic package manager which takes care of all dependencies.  That program you are installing I think is an RPM package for Red Hat?  Over here packages end in .deb

Look for it in synaptic is probably there.

good luck and have fun

Edit i found I, think, what you are looking for in Synaptic: package call fpm descriptions says Secure password manager

---

### Post by prizrak on 2006-11-17
You might want to try an alternative as well, one I use is Keepass X which is also in repositories.

---

### Post by xender69 on 2006-11-17
Thanks for the quick reply guys.

Edit i found I, think, what you are looking for in Synaptic: package call fpm descriptions says Secure password manager
(ok, so I started synaptic and I don't see fpm, does this mean I need to download it from somewhere?)


You might want to try an alternative as well, one I use is Keepass X which is also in repositories.
(is keepass x able to launch terminal windows as well or just keep passwords? with fpm, you can launch ssh/telnet/rsh/web sessions as well as keep passwords, it's really a handy tool.)

once again thanks for the reply.  This is what makes linux so much fun. people helping each other out.

---

### Post by scrooge_74 on 2006-11-17
> **xender69 said:**
> Thanks for the quick reply guys.

Edit i found I, think, what you are looking for in Synaptic: package call fpm descriptions says Secure password manager
(ok, so I started synaptic and I don't see fpm, does this mean I need to download it from somewhere?)


You might want to try an alternative as well, one I use is Keepass X which is also in repositories.
(is keepass x able to launch terminal windows as well or just keep passwords? with fpm, you can launch ssh/telnet/rsh/web sessions as well as keep passwords, it's really a handy tool.)

once again thanks for the reply.  This is what makes linux so much fun. people helping each other out.


In synaptic you have to search for the packages using the search tool or look at them in the sections to your left, the right click and mark them for install, then you apply changes

---

### Post by xender69 on 2006-11-17
I did do a search and put fpm and didn't see any package.  also tried Keepass X and didn't see that one either.  Is synaptic package manager suppose to have all packages listed that's available for download or do I need to download more packages ?

thanks.

---

### Post by FryerFox on 2006-11-17
> **xender69 said:**
> I did do a search and put fpm and didn't see any package.  also tried Keepass X and didn't see that one either.  Is synaptic package manager suppose to have all packages listed that's available for download or do I need to download more packages ?

thanks.

I just searched my Synaptic, and I can find fpm too. It may be that you do not have all the repositories enabled (in Settings->Repositories). 

BTW, I'm using Ubuntu 6.10 (Edgy).

---

### Post by prizrak on 2006-11-17
Was just gonna ask about what version of Ubuntu you are using, Keepass is not in Dapper (6.06) repo's. 

P.S. This should be moved to support.

---

### Post by PriceChild on 2006-11-17
You can easily install fpm using synaptic... or even easier:

```
$ sudo aptitude install fpm
```

---

### Post by xender69 on 2006-11-17
Guys!! that was it.  I didn't know I could download more packages but sure enough.. had to go into the software sources and download all the open source softwares.

Found FPM.

thank you very much.  I'm beginning to like ubuntu very much.  really liked the fact that it also installed all the dependencies... very nice.

---

