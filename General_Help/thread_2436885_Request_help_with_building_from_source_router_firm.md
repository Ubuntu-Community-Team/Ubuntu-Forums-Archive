---
title: "Request help with building from source router firmware"
date: 2020-02-14
forum: General Help
---

### Post by trpted on 2020-02-14
If I posted this in the wrong area, please tell a mod / an admin so it can be moved to the right area. Thanks.

URL REF [https://bitbucket.org/AndreDVJ/advancedtomato-arm/src/master/](https://bitbucket.org/AndreDVJ/advancedtomato-arm/src/master/)

#1 If you read README.TXT it says
> There are multiple directories provided here. The release directory
contains the router source package. The uClibc directory contains the source
for uClibc. The binary tools required to build are provided as a
convenience.

To build the router:
 o Follow the instructions in the tools/ directory to install the toolchain
 o Ensure the tools in the release/tools directory are in your path
 o cd release/src
 o type 'make'

This will create a parallel directory to src called image that contains the
final image.

#2 If I go to the **tools** directory, there are no directions as what to do.

#3 I asked over **NNTP** at **news.grc.com**  in **grc.techtalk.linux** with ** issue with building AndreDVJ's AdvancedTomato-ARM**  and got the following info back
> 
[quote]
[quote]
[quote]
[quote]
Sounds like you are supposed to use a parallel toolchain because the router will be linked against different libraries than what is on your PC, what is otherwise called cross-compile. Projects like LFS also do this because tools and the resulting program will be built against different libraries even though it is on the same platform.

In plain straight english please tell me how to do that on an Ubuntu (or releated for example Lubuntu) computer.
> 
Check out the LFS (linux from scratch) documentation, I don't normally do that kind of development but they exercise the same compile method it sounds like your router needs.

What they say does that apply to Ubuntu (or releated for example Lubuntu) computer?
[/quote]
Sorry, as I stated I do not usually do this sort of development myself and do not have the experience.

As for plain english instructions, the Linux from Scratch (LFS) project is mostly understandable if not plain english.

In short what you have to do is build each program of the toolchain (compiler, linker, libraries, etc...) normally using the source tree the router project gave you, then rebuild the tree using the libraries you just built. This will have the isolation so that the final software build is based of the source tree only and not reliant on any shared libraries from your PC.

When the final software build is on your router it will look for the local libraries you built in isolation instead of looking for the libraries that are on your PC which will obviously not be available to the router.
[/quote]
I found some info about what you are talking about

[http://www.linuxfromscratch.org/lfs/view/stable/chapter01/how.html](http://www.linuxfromscratch.org/lfs/view/stable/chapter01/how.html)

Which chapters do I need to read? Chapter 5 for example

[/quote]
Not knowing your needs, and its been a while since I read LSB, I think the chapters are 5 or 6 that address compiling as I described it.

However do keep in mind that the instructions are written from the viewpoint of building an OS.

Since you are building the libraries and firmware for a router there may be differences from the LSB instructions.

I cannot advise on this having not built router firmware myself.
[/quote]

#4 I want/request:

a) a second two cents (not literally). An opinion on the matter.

b) As noted info on how to do that on Ubuntu (or releated for example Lubuntu) computer would be useful.

#5 While I have built from source before on Ubuntu (or releated for example Lubuntu) computer, I was doing for the computer that I am/was on. Not how that it matters - to be exact a program called BZflag.

Credit where credit is due. The other user's handle who was trying to help out = **DarkWolf**

Please and thank you

---

