---
title: "Epson dx4400 drivers"
date: 2021-03-03
forum: General Help
---

### Post by fe-berber on 2021-03-03
Hello

I'm new to ubuntu and i'm trying to get my printer working.

I followed this method : [https://doc.ubuntu-fr.org/tutoriel/installer_imprimante_epson#installation_des_pilotes](https://doc.ubuntu-fr.org/tutoriel/installer_imprimante_epson#installation_des_pilotes)

And when i run ```
./configure
``` i get this : ```
./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for bison... no
checking for byacc... no
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /usr/bin/sed
checking how to recognise dependent libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0... yes
checking GTK_CFLAGS... -pthread -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libmount -I/usr/include/blkid -I/usr/include/pango-1.0 -I/usr/include/fribidi -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/harfbuzz -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/uuid -I/usr/include/freetype2 -I/usr/include/libpng16
checking GTK_LIBS... -lgtk-x11-2.0 -lgdk-x11-2.0 -lpangocairo-1.0 -latk-1.0 -lcairo -lgdk_pixbuf-2.0 -lgio-2.0 -lpangoft2-1.0 -lpango-1.0 -lgobject-2.0 -lglib-2.0 -lharfbuzz -lfontconfig -lfreetype
checking for xml2-config... yes
checking for cups-config... no
./configure: line 8538: test: =: unary operator expected
configure: error: *** 'cups-config' missing, please install CUPS or fix your $PATH ***
```

Can i get some help ? 
Thank you ! :cool:

---

### Post by blackbird34 on 2021-03-03
Edit: read speartip's post below. 

Hi. 

That command looks like it's for installing the driver from source code. 

I googled the printer model and found this product page: 
[https://www.epson.fr/products/printers/inkjet-printers/for-home/epson-stylus-dx4400/Support-et-telechargements](https://www.epson.fr/products/printers/inkjet-printers/for-home/epson-stylus-dx4400/Support-et-telechargements) (yes I speak french too; for any English speakers the page also offers an English language version)
[LIST]
[*]Download the file and save it somewhere e.g ~/Downloads and extract it 
[*]There's a driver available as a .zip package with an executable file and a README inside. 
[*]In the readme go to "6.1 Software Installation" 
[*]Open a terminal and go to the folder with the driver: 
[/LIST]
```
cd Downloads
```
then:   cd <folder> 
then: sudo sh <name of the driver> to run  the install script. 

It's strange that Ubuntu didn't detect the printer automatically. It's 14 years old. Are you sure the Printers preferences can't detect it?

---

### Post by speartip on 2021-03-03
Before you try anything complicated, try installing the printer-driver-escpr package from the repo. My DX7450 works off that.

---

### Post by blackbird34 on 2021-03-03
> **speartip said:**
> Before you try anything complicated, try installing the printer-driver-escpr package from the repo. My DX7450 works off that.

Yes, although how a new Ubuntu user can discover that package is anyone's guess.

---

### Post by speartip on 2021-03-04
You are right it's not easy to find. I just searched "Epson" in Synaptic. However as you imply, you need to know that in the 1st place.

---

### Post by fe-berber on 2021-03-04
Printer-driver-escpr package was installed and my printer was detected. I tried on two different documents. She printed a line of symbol and then nothing. Thats why i wanted to try another driver..

---

### Post by fe-berber on 2021-03-07
Thank you I tried the Blackbird method then ubuntu detected the printer. When I print a document, it outputs a line of letters and symbols then a blank page then letters and symbols. I have to stop it manually otherwise it continues over and over again. The printer works fine on other computers and copying scanned documents works as well.


Help ! :confused:

---

### Post by speartip on 2021-03-07
I can't understand why that model printer wasn't detected automatically. Try turning the printer off, delete the printer from the printer settings, then turn the printer back on. Are you seeing a notification that tells you the printer is being configured?

---

### Post by fe-berber on 2021-03-08
Yes i'm seeing a notification on top of my screen, and in settings i can configure the printer but i didn't touch anything. The printer just won't print what it is supposed to print. Just letters and symbols. Couldn't it be a hardware issue ?
I'm trying to print this : [https://ibb.co/L5qn34H](https://ibb.co/L5qn34H)
And i get that : [https://ibb.co/x79bkLK](https://ibb.co/x79bkLK)

---

### Post by speartip on 2021-03-08
Are you trying to print directly from the web? Or are you downloading it first & then printing?

---

### Post by fe-berber on 2021-03-08
Its downloaded.

---

### Post by speartip on 2021-03-08
OK. It prints fine here either way. when you go into Printers, click "add". Do you see your printer & model listed on the Left hand side? If so try adding it again, & see if it offers you a different driver option. also try printing other documents PDFs etc.. Do you get the same results?

---

### Post by fe-berber on 2021-03-08
Other documents, it comes out the same. I add my printer again and i get one choice : [https://ibb.co/Wt1MT7b](https://ibb.co/Wt1MT7b)

---

### Post by speartip on 2021-03-08
Interesting. I don't have anything gutenprint installed. Did you install that manually?  It may be that you need to uninstall everything that you installed manually, delete your printer & start again with just the escpr driver from the repos installed. Your printer should appear in the left hand panel as in my pic.

[ATTACH=CONFIG]288084[/ATTACH]

---

### Post by fe-berber on 2021-03-08
How do i uninstall my drivers ? :-k

---

### Post by fe-berber on 2021-03-08
Ok i managed to uninstalled gutenprint. i installed [[IMG]https://i.ibb.co/mzFtdxL/Drivers.png[/IMG]]("https://ibb.co/mzFtdxL")

But i have the same result when i'm printing .. ](*,)

---

### Post by speartip on 2021-03-09
Did you delete your printer, from the Printers module and then let it auto install after the new driver was installed?

---

### Post by speartip on 2021-03-09
Actually another way. Boot into your live usb, Install the escpr driver, then turn on your printer. Let it auto install and see if it prints properly now.

---

### Post by fe-berber on 2021-03-14
Sorry i was off for a few days. I tried with live usb and follow your instructions but it can't print another thing that a line of letters and symbols..

---

### Post by speartip on 2021-03-14
OK. This is the last suggestion I have. I don't like pointing people to internet downloads, however I have tried this before, & it works well. Try Turboprint. It is only free for 30 days, but if it works well it might be worth it:
[Epson Stylus DX4400 Linux Printer Driver | TurboPrint]("https://www.turboprint.info/printer_Epson_StylusDX4400.html")

---

