---
title: "How to compile YPOPS 0.85"
date: 2006-07-04
forum: General Help
---

### Post by JerryE on 2006-07-04
Though freepops has POP3 support it has no SMTP feature.
YPOPS has all the nice features, but I cannot get it to compile.

Here is what I did and got:
1. download the source e.g.
wget [http://umn.dl.sourceforge.net/sourceforge/yahoopops/ypops-src-0.8.5.zip](http://umn.dl.sourceforge.net/sourceforge/yahoopops/ypops-src-0.8.5.zip)

2. unpack the archive as root and place it into 
/usr/src/ypops

5. get mimepp-1.3.3
find it on  [http://www.findmyfile.com/](http://www.findmyfile.com/)  e.g.
wget [http://gnu-darwin.org/packages/x86/All/mimepp-1.3.3.x86.tgz](http://gnu-darwin.org/packages/x86/All/mimepp-1.3.3.x86.tgz)

6. unpack the archive as root and place it into
 /usr/src/ypops/lib/mimepp-1.3.3

7.copy makefile-linux from 
/usr/src/ypops/lib/mimepp-1.3.3/share/examples/mimepp to
/usr/src/ypops/lib/mimepp-1.3.3

8. install curl and check openssl
sudo apt-get install curl
sudo apt-get install openssl

9. find their locations
find / -iname curl -xdev 2>/dev/null
find / -iname ssl -xdev 2>/dev/null

10. adjust the appropriate lines in the usr/src/ypops/src makefile
according to README.unix-linux

INSTALL_DIR 	= /usr/local/bin
RUN_DIR 	= /usr/local/ypops
MIMEPP 	= ../lib/mimepp-1.3.3

CURL_INC 	= /usr/include/curl
SSL_INC 	= /usr/include/openssl
CURL_LIB 	= /usr/lib
SSL_LIB 	= /usr/lib

mimelib:
	cd $(MIMEPP);make -f makefile-linux rel_lib;cd $(YPSRCDIR)

11. adjust the appropriate lines in the ypops/src/lib/re_lib makefile.unix 

PROF= -Dstatic='/* */' | -p

12. make
cd /usr/src/ypops/src
sudo make

This is what I get

rm -f ypops
make mimelib;make libre_lib;make ypops
make[1]: Entering directory `/usr/src/ypops/src'
cd ../lib/mimepp-1.3.3;make -f makefile-linux rel_lib;cd
make[2]: Entering directory `/usr/src/ypops/lib/mimepp-1.3.3'
make[2]: *** No rule to make target `rel_lib'.  Stop.
make[2]: Leaving directory `/usr/src/ypops/lib/mimepp-1.3.3'
make[1]: Leaving directory `/usr/src/ypops/src'
make[1]: Entering directory `/usr/src/ypops/src'
cd ../lib/re_lib;make -f makefile.unix
make[2]: Entering directory `/usr/src/ypops/lib/re_lib'
ar q libre_lib.a regexp.o regsub.o
make[2]: Leaving directory `/usr/src/ypops/lib/re_lib'
make[1]: Leaving directory `/usr/src/ypops/src'
make[1]: Entering directory `/usr/src/ypops/src'
rm -f DataHolder.o
g++ -g -fkeep-inline-functions -fno-default-inline -D_REENTRANT -I../lib/re_lib -I../lib/mimepp-1.3.3/src -I../lib/mimepp-1.3.3/examples/email -I/usr/include/curl -I/usr/include/openssl -c DataHolder.cpp
rm -f Email.o
g++ -g -fkeep-inline-functions -fno-default-inline -D_REENTRANT -I../lib/re_lib -I../lib/mimepp-1.3.3/src -I../lib/mimepp-1.3.3/examples/email -I/usr/include/curl -I/usr/include/openssl -c Email.cpp
rm -f HttpClient.o
g++ -g -fkeep-inline-functions -fno-default-inline -D_REENTRANT -I../lib/re_lib -I../lib/mimepp-1.3.3/src -I../lib/mimepp-1.3.3/examples/email -I/usr/include/curl -I/usr/include/openssl -c HttpClient.cpp
rm -f HttpClientResponse.o
g++ -g -fkeep-inline-functions -fno-default-inline -D_REENTRANT -I../lib/re_lib -I../lib/mimepp-1.3.3/src -I../lib/mimepp-1.3.3/examples/email -I/usr/include/curl -I/usr/include/openssl -c HttpClientResponse.cpp
rm -f HttpSession.o
g++ -g -fkeep-inline-functions -fno-default-inline -D_REENTRANT -I../lib/re_lib -I../lib/mimepp-1.3.3/src -I../lib/mimepp-1.3.3/examples/email -I/usr/include/curl -I/usr/include/openssl -c HttpSession.cpp
rm -f LogFile.o
g++ -g -fkeep-inline-functions -fno-default-inline -D_REENTRANT -I../lib/re_lib -I../lib/mimepp-1.3.3/src -I../lib/mimepp-1.3.3/examples/email -I/usr/include/curl -I/usr/include/openssl -c LogFile.cpp
rm -f ServiceClient.o
g++ -g -fkeep-inline-functions -fno-default-inline -D_REENTRANT -I../lib/re_lib -I../lib/mimepp-1.3.3/src -I../lib/mimepp-1.3.3/examples/email -I/usr/include/curl -I/usr/include/openssl -c ServiceClient.cpp
In file included from ServiceClient.h:69,
                 from ServiceClient.cpp:55:
WebBrowser.h:70:26: error: EmailMessage.h: No such file or directory
WebBrowser.h:114: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
WebBrowser.h:114: error: ISO C++ forbids declaration of &#8216;EmailAttachmentList&#8217; with no type
ServiceClient.cpp: In function &#8216;UINT ServiceClientThread(void*)&#8217;:
ServiceClient.cpp:383: error: expected type-specifier before &#8216;CMemoryException&#8217;
ServiceClient.cpp:383: error: expected `)' before &#8216;e2&#8217;
ServiceClient.cpp:383: error: expected `{' before &#8216;e2&#8217;
ServiceClient.cpp:383: error: &#8216;e2&#8217; was not declared in this scope
ServiceClient.cpp:383: error: expected `;' before &#8216;)&#8217; token
ServiceClient.cpp:392: error: expected primary-expression before &#8216;catch&#8217;
ServiceClient.cpp:392: error: expected `;' before &#8216;catch&#8217;
ServiceClient.cpp:401: error: expected primary-expression before &#8216;catch&#8217;
ServiceClient.cpp:401: error: expected `;' before &#8216;catch&#8217;
ServiceClient.cpp:407: error: expected primary-expression before &#8216;catch&#8217;
ServiceClient.cpp:407: error: expected `;' before &#8216;catch&#8217;
make[1]: *** [ServiceClient.o] Error 1
make[1]: Leaving directory `/usr/src/ypops/src'
make: *** [all] Error 2

I am suspicious that the problem maybe in part in the structure of the mimepp directory, but the problem is way over my head

I have no clue how to resolve to begin with
make[2]: *** No rule to make target `rel_lib'.  Stop.

It will take someone much smarter to tackle this.

Cheers,

Jerry

---

### Post by Rui Pais on 2006-07-04
Hi, just 2 suggestions. 

Have a look [here]("http://www.ypopsemail.com/index.php?name=PNphpBB2&file=viewtopic&t=2574").

Or maybe give a look at a similar application more linux oriented, like [YoSucker]("http://yosucker.sourceforge.net/") (that name sucks!) or [FetchYahoo]("http://fetchyahoo.twizzler.org/").

---

### Post by JerryE on 2006-07-04
Thank you!

However, I looked already at
[http://www.ypopsemail.com/index.php?name=PNphpBB2&file=viewtopic&t=2574](http://www.ypopsemail.com/index.php?name=PNphpBB2&file=viewtopic&t=2574)

and I had  already curl-devel installed and still got the same problem.
Moreover they do not seem to have a solution either.

I could not find if either of the programs you mentioned actually supports SENDING email through yahoo. Do they?

Thank you again,

Jerry

---

### Post by Rui Pais on 2006-07-05
hi,
yes they didn't... Porting an application over other OS is not always easy.

I don't know this apps, so couldn't give much help. 
Essencially just wanted to point that the problem was not ubuntu specific and that app have a own forum for quest directly its devs. 
Maybe there you find more advanced suggestions on this topic.

The other 2 apps/scripts are linux oriented so they may work easely.
No i don't think they send mail. Look at FetchYahoo Other Programs List.
It links to [Sendymail]("http://sendymail.sourceforge.net/") and [Mechanoid]("http://python.org/pypi/mechanoid") that do that part.
Boring to have different apps/scripts to do that, but may help if you didn't find a way to make YPops work under tux.

Sorry if i can help more, good luck!

---

### Post by AmandaKerik on 2007-02-01
This may or may not help, but...
If you're using Thunderbird, you can just grab two add-ons and you're up and rocking!
[http://webmail.mozdev.org/](http://webmail.mozdev.org/)

Hope it helps,
Amanda

---

