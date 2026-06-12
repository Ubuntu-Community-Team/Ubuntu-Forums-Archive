---
title: "problems compliing pftpfxp-mew"
date: 2005-08-25
forum: General Help
---

### Post by luckie on 2005-08-25
i am having some problems compiling this porgram.  here is the output from make.


```
$ make dynamic
cd src;make dynamic;cd ..
make[1]: Entering directory `/home/luckie/pftpfxp-mew/pftpfxp-mew/src'
g++-3.4 -c -Wall -D_REENTRANT -I../include -O2 -I/usr/include -DTLS main.cc
main.cc:4:20: curses.h: No such file or directory
main.cc:5:19: panel.h: No such file or directory
In file included from main.cc:13:
../include/tcp.h: In member function `void CTCP::ResetMessage()':
../include/tcp.h:83: error: `FALSE' undeclared (first use this function)
../include/tcp.h:83: error: (Each undeclared identifier is reported only once for each function it appears in.)In file included from main.cc:14:
../include/server.h: At global scope:
../include/server.h:61: error: `FALSE' was not declared in this scope
../include/server.h: In member function `void CServer::SetTransfering()':
../include/server.h:151: error: `TRUE' undeclared (first use this function)
../include/server.h: In member function `void CServer::ClearTransfering()':
../include/server.h:155: error: `FALSE' undeclared (first use this function)
../include/server.h: In member function `void CServer::SetRetrying()':
../include/server.h:156: error: `TRUE' undeclared (first use this function)
../include/server.h: In member function `void CServer::ClearRetrying()':
../include/server.h:157: error: `FALSE' undeclared (first use this function)
../include/server.h: In member function `void CServer::SetAllowChaining()':
../include/server.h:158: error: `TRUE' undeclared (first use this function)
../include/server.h: In member function `void CServer::ClearAllowChaining()':
../include/server.h:159: error: `FALSE' undeclared (first use this function)
In file included from main.cc:15:
../include/displayhandler.h: At global scope:
../include/displayhandler.h:47: error: ISO C++ forbids declaration of `WINDOW' with no type
../include/displayhandler.h:47: error: expected `;' before '*' token
../include/displayhandler.h:51: error: ISO C++ forbids declaration of `PANEL' with no type
../include/displayhandler.h:51: error: expected `;' before '*' token
../include/displayhandler.h:68: error: `WINDOW' has not been declared
../include/displayhandler.h:68: error: ISO C++ forbids declaration of `window' with no type
../include/displayhandler.h:69: error: `WINDOW' has not been declared
../include/displayhandler.h:69: error: ISO C++ forbids declaration of `window' with no type
../include/displayhandler.h:72: error: `WINDOW' has not been declared
../include/displayhandler.h:72: error: ISO C++ forbids declaration of `window' with no type
../include/displayhandler.h:76: error: `WINDOW' has not been declared
../include/displayhandler.h:76: error: ISO C++ forbids declaration of `parameter' with no type
../include/displayhandler.h:78: error: `WINDOW' has not been declared
../include/displayhandler.h:78: error: ISO C++ forbids declaration of `parameter' with no type
../include/displayhandler.h:199: error: `WINDOW' has not been declared
../include/displayhandler.h:199: error: ISO C++ forbids declaration of `parameter' with no type
../include/displayhandler.h:212: error: `WINDOW' has not been declared
../include/displayhandler.h:212: error: ISO C++ forbids declaration of `parameter' with no type
../include/displayhandler.h:213: error: `WINDOW' has not been declared
../include/displayhandler.h:213: error: ISO C++ forbids declaration of `parameter' with no type
../include/displayhandler.h:262: error: `WINDOW' has not been declared
../include/displayhandler.h:262: error: ISO C++ forbids declaration of `parameter' with no type
../include/displayhandler.h:288: error: variable or field `mywborder' declared void
../include/displayhandler.h:288: error: `WINDOW' was not declared in this scope
../include/displayhandler.h:288: error: `win' was not declared in this scope
In file included from main.cc:16:
../include/keyhandler.h: In member function `void CKeyHandler::WantQuit(bool)':
../include/keyhandler.h:20: error: `TRUE' undeclared (first use this function)
../include/keyhandler.h: In member function `void CKeyHandler::WantFireupLocal()':
../include/keyhandler.h:23: error: `TRUE' undeclared (first use this function)
main.cc: At global scope:
main.cc:32: error: `FALSE' was not declared in this scope
main.cc:32: error: `FALSE' was not declared in this scope
main.cc:32: error: `FALSE' was not declared in this scope
main.cc:53: error: variable or field `mywborder' declared void
main.cc:53: error: redefinition of `int mywborder'
../include/displayhandler.h:288: error: `int mywborder' previously defined here
main.cc:53: error: `WINDOW' was not declared in this scope
main.cc:53: error: `win' was not declared in this scope
main.cc:53: error: expected `,' or `;' before '{' token
main.cc: In function `void adjust(int)':
main.cc:117: error: `TRUE' undeclared (first use this function)
main.cc: In function `bool FilterFilename(char*, char*)':
main.cc:228: error: `FALSE' undeclared (first use this function)
main.cc:251: error: `TRUE' undeclared (first use this function)
main.cc: In function `bool FireDisplayHandler()':
main.cc:298: error: `FALSE' undeclared (first use this function)
main.cc:301: error: `TRUE' undeclared (first use this function)
main.cc: In function `void FireupLocalFilesys()':
main.cc:341: error: `FALSE' undeclared (first use this function)
main.cc: In function `bool ReadConfig(char*)':
main.cc:460: error: `FALSE' undeclared (first use this function)
main.cc:555: error: `TRUE' undeclared (first use this function)
main.cc: In function `bool ReadKeymap(char*)':
main.cc:987: error: `FALSE' undeclared (first use this function)
main.cc:1031: error: `TRUE' undeclared (first use this function)
main.cc: In function `int main(int, char**)':
main.cc:1108: error: `FALSE' undeclared (first use this function)
main.cc:1113: error: `TRUE' undeclared (first use this function)
main.cc: In function `bool FilterDirname(char*, char*)':
main.cc:1236: error: `FALSE' undeclared (first use this function)
main.cc:1258: error: `TRUE' undeclared (first use this function)
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/luckie/pftpfxp-mew/pftpfxp-mew/src
```'

thanks in advance for any help.
let me know if you need anymore information.

luckie

---

### Post by soydeedo on 2008-03-21
Yes this post is ages old, but I wanted to respond to this for anyone else who happens upon it with google. You need to install the ncurses developer library, which is currently "libncurses5".

This will solve the following two errors at the top which in turn solve the rest:

main.cc:4:20: curses.h: No such file or directory
main.cc:5:19: panel.h: No such file or directory

---

