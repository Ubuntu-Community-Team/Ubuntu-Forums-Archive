---
title: "Mapivi compiling error"
date: 2005-10-02
forum: General Help
---

### Post by casfindad on 2005-10-02
I'm brand new to Ubuntu, so my apologies if this question should have been posted in the newbie forum.
I'm trying to install the digital photo manager Mapivi ([http://mapivi.sourceforge.net/mapivi.shtml]("http://mapivi.sourceforge.net/mapivi.shtml")) on my Ubuntu system (PII, 400 MHz, running Hoary) without success. I installed the required Perl/Tk using Synaptic. The package also requires several perl modules be installed, which I have attempted to do using the CPAN installer (I couldn't find some of the dependencies in the repository.) Some of the modules install fine, but when I try to install Tk::JPEG, I get the following error message:
[INDENT]  CPAN.pm: Going to build N/NI/NI-S/Tk-804.027.tar.gz
/usr/bin/perl is installed in /usr/lib/perl/5.8 okay
PPM for perl5.008004
Test Compiling config/signedchar.c
Test Compile/Run config/unsigned.c
Test Compiling config/Ksprintf.c
Test Compiling -DSPRINTF_RETURN_CHAR config/Ksprintf.c
Test Compiling config/tod.c
Test Compiling -DTIMEOFDAY_TZ config/tod.c
Test Compiling -DTIMEOFDAY_NO_TZ config/tod.c
Test Compiling -DTIMEOFDAY_DOTS config/tod.c
Problem gettimeofday()
Using -L/usr/X11R6/lib to find /usr/X11R6/lib/libX11.so.6.2
Cannot find X include files via /usr/X11R6/include
Cannot find X include files anywhere at ./myConfig line 332.
Compilation failed in require at Makefile.PL line 36.
BEGIN failed--compilation aborted at Makefile.PL line 38.
Running make test
Make had some problems, maybe interrupted? Won't test
Running make install
Make had some problems, maybe interrupted? Won't install
[/INDENT]
I found that the required module (Tk::JPEG) is in the latest version of Perl/Tk (804.027), so I tried installing that with CPAN. I received a very similar error message:
[INDENT]Test Compiling -DTIMEOFDAY_TZ config/tod.c
Test Compiling -DTIMEOFDAY_NO_TZ config/tod.c
Test Compiling -DTIMEOFDAY_DOTS config/tod.c
Problem gettimeofday()
Using -L/usr/X11R6/lib to find /usr/X11R6/lib/libX11.so.6.2
Cannot find X include files via /usr/X11R6/include
Cannot find X include files anywhere at ./myConfig line 332.
Compilation failed in require at Makefile.PL line 36.
BEGIN failed--compilation aborted at Makefile.PL line 38.
[/INDENT]
Not surprisingly, if I go ahead and try to run mapivi, I get the following error message:
[INDENT]casey@Theodore:~/MapiviStuff/mapivi072$ perl mapivi
Can't locate Tk/JPEG.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at mapivi line 174.
BEGIN failed--compilation aborted at mapivi line 174.
[/INDENT]
Obviously, Tk::JPEG is not installing because of some problem accessing include files. I'm guessing I might need to change a path in the makefile, or at least link something in my directory tree.
I very much appreciate receiving any detailed instructions you can give me.
P.S. Before you suggest I use gthumb or f-spot, the reason I'm interested in mapivi is because it can edit IPTC metadata, a la GraphicConverter for the Mac. As far as I know, all the other photo managers available for linux save metadata separate from the image file.

---

### Post by Martin-Herrmann on 2006-05-03
Hi,

you will find a description how to install Mapivi on Ubuntu 5.10 in my other post here:
[http://ubuntuforums.org/showpost.php?p=978524&postcount=3]("http://ubuntuforums.org/showpost.php?p=978524&postcount=3")

Regards,  Martin

---

### Post by salguod on 2006-09-18
hi,
I believe I followed all of the Mapivi install instructions, but get stuck when I try to run mapivi.

I get the following error message. Can anyone tell me where I went wrong? Thanks.

powermac@powermac:~/downloads/mapivi081$ perl mapivi
Can't locate Tk.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at mapivi line 177.
BEGIN failed--compilation aborted at mapivi line 177.
powermac@powermac:~/downloads/mapivi081$ sudo perl mapivi
Can't locate Tk.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at mapivi line 177.

---

### Post by Martin-Herrmann on 2006-09-24
Hi,

following the error message you receive "Can't locate Tk.pm", it seems like the installation of PerlTk failed.

What was the output of "make test", while doing the steps noted below?

[INDENT]download Perl/Tk ([http://search.cpan.org/~ni-s/Tk-804.027/)](http://search.cpan.org/~ni-s/Tk-804.027/)), unzip and unpack it and change to the unpacked directory Tk-804-027.
Then:
> perl Makefile.PL
> make
> make test (some tests may fail, that's no problem)
> sudo make install[/INDENT]

Martin

---

