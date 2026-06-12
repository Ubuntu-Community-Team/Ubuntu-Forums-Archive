---
title: "help me install Fontlinge, please (make, sed problems)"
date: 2006-10-14
forum: General Help
---

### Post by Makrie on 2006-10-14
Problem solved thanks to Fontlinge creator - replace original module folder with revised module folder as found on Sourceforge! Thanks!


Hi! 

I'm trying to install Fontlinge ([www.fontlinge.de](www.fontlinge.de)) on my system and having a great deal of trouble...

I am running Ubuntu 6.06 Dapper Drake and believe I have installed all the prerequisites.

When I run 'make', I encounter a problem:

mark@mango:~/Desktop/fontlinge/fontlinge-2.0.1$ make
sed "s/@VERSION@/2.0.1/g" < fontlinge.spec.in > fontlinge.spec
make -C modules
make[1]: Entering directory `/home/mark/Desktop/fontlinge/fontlinge-2.0.1/modules'
sed ' \
s&#65533;@prefix@&#65533;/usr/local&#65533; ; \
s&#65533;@bindir@&#65533;/usr/local/bin&#65533; ; \
s&#65533;@datadir@&#65533;/usr/local/share&#65533; ; \
s&#65533;@docdir@&#65533;/usr/local/share/doc/fontlinge&#65533; ; \
s&#65533;@mandir@&#65533;/usr/local/share/man&#65533; ; \
s&#65533;@man3dir@&#65533;/usr/local/share/man/man3&#65533; ; \
s&#65533;@shareddir@&#65533;/usr/local/share/fontlinge&#65533; ; \
s&#65533;@htmldir@&#65533;/usr/local/share/fontlinge/webgui&#65533; ; \
' < fontlinge/Config.pm.in > fontlinge/Config.pm || { rm -f fontlinge/Config.pm ; exit 1 ; }
sed: -e expression #1, char 355: unterminated address regex
make[1]: *** [fontlinge/Config.pm] Error 1
make[1]: Leaving directory `/home/mark/Desktop/fontlinge/fontlinge-2.0.1/modules'
make: *** [make_modules] Error 2
mark@mango:~/Desktop/fontlinge/fontlinge-2.0.1$


Googling for this problem, I came across some discussion of a problem with make and sed in 6.06 - I wondered if this might be to blame.

[http://os.inf.tu-dresden.de/pipermail/l4-hackers/2006/002972.html](http://os.inf.tu-dresden.de/pipermail/l4-hackers/2006/002972.html)

This leaves me with no idea what to do, any help would be greatly appreciated!


Cheers

Mark

---

