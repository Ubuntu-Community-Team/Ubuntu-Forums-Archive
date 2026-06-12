---
title: "[XSupplicant] installation problems"
date: 2005-04-18
forum: General Help
---

### Post by Derek Djons on 2005-04-18
Hallo everybody,

Since XSupplicant isn't adapted into the package manager as it is with SuSE for example I tried to install XSupplicant manually today.

I downloaded version 1.0.1 from [www.open1x.org](www.open1x.org). Using the root terminal under Ubuntu I then ran ./configure as stated in the manual. When checking the output of ./configure I saw that I missed some stuff like openssl, gcc, gawk and more. After using the package manager to install these files i ran make. But running make does bring up some errors. 

Output configure:
> 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ranlib... ranlib
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for bison... bison -y
checking for flex... flex
checking for yywrap in -lfl... yes
checking lex output file root... lex.yy
checking whether yytext is a pointer... yes
checking whether byte ordering is bigendian... no
checking Operating System... Linux
checking for openssl (required package)... /usr/lib/
checking for native frame interface... linux
checking for wireless extensions... found for linux
checking for procfs support... okay
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/cardif/Makefile
config.status: creating tools/Makefile
config.status: creating doc/Makefile
config.status: creating etc/Makefile
config.status: creating drivers/Makefile
config.status: creating tools/config-parser/Makefile
config.status: creating gui_tools/Makefile
config.status: creating gui_tools/cli/Makefile
config.status: creating gui_tools/cli/xsup_set_pwd/Makefile
config.status: creating gui_tools/cli/xsup_monitor/Makefile
config.status: linking ./src/cardif/Makefile.am.linux to src/cardif/Makefile.am
config.status: linking ./src/cardif/linux/linux_core.c to src/core.c
config.status: executing depfiles commands


Output make:
> 
Making all in src
make[1]: Entering directory `/usr/local/src/xsupplicant-1.0.1/src'
Making all in cardif
make[2]: Entering directory `/usr/local/src/xsupplicant-1.0.1/src/cardif'
make[3]: Entering directory `/usr/local/src/xsupplicant-1.0.1'
make[3]: Leaving directory `/usr/local/src/xsupplicant-1.0.1'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/usr/local/src/xsupplicant-1.0.1/src/cardif'
make[2]: Entering directory `/usr/local/src/xsupplicant-1.0.1/src'
gcc  -g -O2 -Wall    -o xsupplicant  xsup_driver.o xsup_debug.o profile.o core.o config.o eapol.o statemachine.o eap.o snmp.o wpa.o key_statemachine.o eapol_key_type1.o interactive.o eapol_key_type254.o eapmd5.o eaptls.o tls_funcs.o eapttls.o ttlsphase2.o tls_crypt.o mschapv2.o eapmschapv2.o eappeap.o peap_phase2.o eapsim.o fips.o sha1.o simd5.o simd11.o sm_handler.o sim.o eapleap.o leapmd4.o eapotp.o eapaka.o aka.o xsup_ipc.o config_grammar.o config_lexicon.o ipc_callout.o cmd_handler.o  -lfl  -lssl -lcrypto -L./cardif -lcardif
config.o(.text+0x29): In function `config_setup':
/usr/local/src/xsupplicant-1.0.1/src/config.c:157: undefined reference to `yyin'
config.o(.text+0x567): In function `config_destroy':
/usr/local/src/xsupplicant-1.0.1/src/config.c:459: undefined reference to `yyin'
config_grammar.o(.text+0x5e1): In function `yyparse':
/usr/local/src/xsupplicant-1.0.1/src/config_grammar.c:1020: undefined reference to `yyerror'
config_grammar.o(.text+0x6b6):/usr/local/src/xsupplicant-1.0.1/src/config_grammar.c:2687: undefined reference to `yyerror'
config_grammar.o(.text+0x7a1):/usr/local/src/xsupplicant-1.0.1/src/config_grammar.c:2654: undefined reference to `yylex'
config_grammar.o(.text+0x2e60):/usr/local/src/xsupplicant-1.0.1/src/config_grammar.c:979: undefined reference to `yylex'
collect2: ld returned 1 exit status
make[2]: *** [xsupplicant] Error 1
make[2]: Leaving directory `/usr/local/src/xsupplicant-1.0.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/xsupplicant-1.0.1/src'
make: *** [all-recursive] Error 1


Output make install:
> 
Making install in src
make[1]: Entering directory `/usr/local/src/xsupplicant-1.0.1/src'
Making install in cardif
make[2]: Entering directory `/usr/local/src/xsupplicant-1.0.1/src/cardif'
make[3]: Entering directory `/usr/local/src/xsupplicant-1.0.1'
make[3]: Leaving directory `/usr/local/src/xsupplicant-1.0.1'
make[3]: Entering directory `/usr/local/src/xsupplicant-1.0.1/src/cardif'
make[4]: Entering directory `/usr/local/src/xsupplicant-1.0.1'
make[4]: Leaving directory `/usr/local/src/xsupplicant-1.0.1'
test -z "/usr/local/lib" || mkdir -p -- . "/usr/local/lib"
 /usr/bin/install -c -m 644 'libcardif.a' '/usr/local/lib/libcardif.a'
 ranlib '/usr/local/lib/libcardif.a'
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/usr/local/src/xsupplicant-1.0.1/src/cardif'
make[2]: Leaving directory `/usr/local/src/xsupplicant-1.0.1/src/cardif'
make[2]: Entering directory `/usr/local/src/xsupplicant-1.0.1/src'
gcc  -g -O2 -Wall    -o xsupplicant  xsup_driver.o xsup_debug.o profile.o core.o config.o eapol.o statemachine.o eap.o snmp.o wpa.o key_statemachine.o eapol_key_type1.o interactive.o eapol_key_type254.o eapmd5.o eaptls.o tls_funcs.o eapttls.o ttlsphase2.o tls_crypt.o mschapv2.o eapmschapv2.o eappeap.o peap_phase2.o eapsim.o fips.o sha1.o simd5.o simd11.o sm_handler.o sim.o eapleap.o leapmd4.o eapotp.o eapaka.o aka.o xsup_ipc.o config_grammar.o config_lexicon.o ipc_callout.o cmd_handler.o  -lfl  -lssl -lcrypto -L./cardif -lcardif
config.o(.text+0x29): In function `config_setup':
/usr/local/src/xsupplicant-1.0.1/src/config.c:157: undefined reference to `yyin'
config.o(.text+0x567): In function `config_destroy':
/usr/local/src/xsupplicant-1.0.1/src/config.c:459: undefined reference to `yyin'
config_grammar.o(.text+0x5e1): In function `yyparse':
/usr/local/src/xsupplicant-1.0.1/src/config_grammar.c:1020: undefined reference to `yyerror'
config_grammar.o(.text+0x6b6):/usr/local/src/xsupplicant-1.0.1/src/config_grammar.c:2687: undefined reference to `yyerror'
config_grammar.o(.text+0x7a1):/usr/local/src/xsupplicant-1.0.1/src/config_grammar.c:2654: undefined reference to `yylex'
config_grammar.o(.text+0x2e60):/usr/local/src/xsupplicant-1.0.1/src/config_grammar.c:979: undefined reference to `yylex'
collect2: ld returned 1 exit status
make[2]: *** [xsupplicant] Error 1
make[2]: Leaving directory `/usr/local/src/xsupplicant-1.0.1/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/local/src/xsupplicant-1.0.1/src'
make: *** [install-recursive] Error 1


After hours and hours on the internet I still can't find the answer. So I guess it must be me who is being stupid since XSupplicant isn't that hard installing it manually.  ](*,)

---

### Post by tread on 2005-04-18
After you have installed the required packages, you should run ./configure again. You may have done that, but I couldn't get that from your post.

Also, when installing the packages also get the dev packages for each dependency .. so for say libpng you would get libpng and libpng-dev.

---

### Post by Derek Djons on 2005-04-19
[QUOTE=tread]After you have installed the required packages, you should run ./configure again. You may have done that, but I couldn't get that from your post.

Also, when installing the packages also get the dev packages for each dependency .. so for say libpng you would get libpng and libpng-dev.[/QUOTE]

Yes, I did run ./configure again after I installed all the necessary parts. 

Do I have to install the dev packages for all applications installed or only for those required by XSupplicant? I checked for all available dev packages with the apps needed by XSupplicant but there are hardly any available. Only the OpenSSL lib has a dev package which already was installed.

Today I gave the configure output a better look. Could it have something to do with these two lines?

> 
checking whether we are cross compiling... no


> 
checking whether byte ordering is bigendian... no


---

### Post by tread on 2005-04-19
No the last two messages are ok, and you just need dev packages for the dependencies. (all of them though)

Other than that don't have a clue..

---

### Post by tread on 2005-04-19
It looks like it cannot find the header files, maybe you could explicitly state these with a -I option to gcc, telling gcc where these headers are?

---

### Post by Derek Djons on 2005-04-19
Thank you for your time and trouble. Suddenly your post about 'installing all the dev's' reminded me what I forgot to do. Install all the dev's. :)

I was so convicenced that I either already had done that or it wasn't necessary.  :-# 

Once more... thnx. Installing XSupplicant went smooth and I also installed gDesklets to make sure it wasn't a coincidene... and it wasn't.  \\:D/

---

### Post by tread on 2005-04-19
:) Glad to be of help.

---

### Post by jean on 2005-05-09
hello,
   I was just wondering whether somebody could help me with installing programs which are located in the /usr/lib folder?...for example,if i wanna install the nautilus cd-burner...
   and how do i use the nautilus cd-burner to copy cds on my laptop,which has only one disc drive....
  Thanx !!

---

