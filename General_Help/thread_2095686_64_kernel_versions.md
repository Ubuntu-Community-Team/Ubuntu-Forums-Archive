---
title: "64 kernel versions?"
date: 2012-12-17
forum: General Help
---

### Post by Heeter on 2012-12-17
Hi all,

Was wondering: Does the linux kernel have 32 or 64 bit versions, like the OS itself?

Or does one version (Say 3.6.5) good for all OS's?

Thanks

Heeter

---

### Post by pqwoerituytrueiwoq on 2012-12-17
it will end in amd64 (64bit) or i386 (32bit)
not sure if this applies if you are compiling it yourself

if you are looking at the iso downloads
[ubuntu-12.10-desktop-i386.iso]("http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.iso")  32bit
[ubuntu-12.10-desktop-amd64.iso]("http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-amd64.iso") 64bit

---

### Post by Heeter on 2012-12-17
thanks for the response

But I am looking for the kernel itself, not the operating system. Is the kernel 64bit?


Heeter

---

### Post by Cheesemill on 2012-12-17
Yes.

The kernel comes in either a 32 or 64 bit version depending on which architecture OS you have installed.

---

### Post by Heeter on 2012-12-17
> **Cheesemill said:**
> Yes.

The kernel comes in either a 32 or 64 bit version depending on which architecture OS you have installed.


Great, Thanks Cheesemill.

Heeter

---

### Post by 1clue on 2012-12-17
The same source applies to both kernels.  If you get a 'pure' kernel from kernel.org, you can compile either 32 or 64 from that.

I haven't tried compiling from Ubuntu-modified source, so I can't say whether it's one or the other.

Usually you choose the kernel target hardware and set compiler options and based on that you get either 64 or 32 bit code.

The place to start learning about that is at [http://www.kernel.org](http://www.kernel.org)

There is probably an Ubuntu-specific place as well.

---

### Post by 1clue on 2012-12-17
Another thing evident from your original post:  You seem to be confused about what is an operating system and what is an application.

The kernel is the operating system.  Everything else you load is a service or application which facilitates running a computer.

The operating system is the interface between hardware and software.  It implements a common application programming interface between the hardware you have and the software that uses it.  This includes networking, task scheduling, memory management, and certain user-space utilities or services which facilitate kernel operations.

What most people refer to as the operating system is in fact a bunch of services which are in turn used by applications.  For example, cron and syslog and file services.

When people refer to Linux or Ubuntu, they're referring not only to those things but also to Libre Office, Firefox and any other app that came on the installation medium, which on Windows or Mac would be clearly not the operating system but pure user-space applications.

When it comes to 32 or 64 bit, the kernel must be compiled for one or the other, and then the other code (services, applications, etc) must be compiled in such a way as to be compatible with whatever mode you picked.

---

### Post by Portaro on 2012-12-17
You can search what kernels are compatible with your system with curl tool command simply 
> curl [https://www.kernel.org/kdist/finger_banner](https://www.kernel.org/kdist/finger_banner)
:popcorn:

---

