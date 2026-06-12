---
title: "Help with compiling something."
date: 2007-03-03
forum: General Help
---

### Post by cubanresourceful on 2007-03-03
Unfortunately, this game I would like to play doesn't have a package for any type of linux. So compilation is a must. But, I cannot seem to compile it, it gives me errors. Here is the website:
[http://fftrader.sourceforge.net/index.shtml](http://fftrader.sourceforge.net/index.shtml)
I seem to have all the required libs to compile installed, but it just wont compile. Can anyone help me? :D Thanks.

---

### Post by taurus on 2007-03-03
Can you please post the exact error message when you try to compile it?  It helps to diagnose what's the problem is with the error message.

---

### Post by cubanresourceful on 2007-03-03
Okay, with FFT, there is no ./configure, so i have to type make. Here is the output:

```
cubanresourceful@cubanresourceful:~/Library/Downloads/fft$ make
make: sdl-config: Command not found
make: sdl-config: Command not found
g++ -c  -Wall -ansi -O2 -g   fftfile.cpp -o fftfile.o
In file included from fftfile.cpp:1:
fftfile.h:9:17: error: SDL.h: No such file or directory
fftfile.h:10:23: error: SDL_image.h: No such file or directory
fftfile.h:11:23: error: SDL_mixer.h: No such file or directory
fftfile.h:12:21: error: SDL_ttf.h: No such file or directory
fftfile.h:13:20: error: physfs.h: No such file or directory
In file included from fftfile.h:14,
                 from fftfile.cpp:1:
graphics.h:10:23: error: SDL_syswm.h: No such file or directory
graphics.h:11:26: error: SDL_rotozoom.h: No such file or directory
graphics.h:12:31: error: SDL_gfxPrimitives.h: No such file or directory
graphics.h:28: error: variable or field &#8216;drawString&#8217; declared void
graphics.h:28: error: &#8216;TTF_Font&#8217; was not declared in this scope
graphics.h:28: error: &#8216;font&#8217; was not declared in this scope
graphics.h:28: error: expected primary-expression before &#8216;int&#8217;
graphics.h:28: error: expected primary-expression before &#8216;int&#8217;
graphics.h:28: error: expected primary-expression before &#8216;text&#8217;
graphics.h:28: error: &#8216;SDL_Color&#8217; was not declared in this scope
graphics.h:28: error: initializer expression list treated as compound expression
graphics.h:29: error: variable or field &#8216;centerString&#8217; declared void
graphics.h:29: error: &#8216;TTF_Font&#8217; was not declared in this scope
graphics.h:29: error: &#8216;font&#8217; was not declared in this scope
graphics.h:29: error: expected primary-expression before &#8216;int&#8217;
graphics.h:29: error: expected primary-expression before &#8216;int&#8217;
graphics.h:29: error: expected primary-expression before &#8216;text&#8217;
graphics.h:29: error: &#8216;SDL_Color&#8217; was not declared in this scope
graphics.h:29: error: initializer expression list treated as compound expression
graphics.h:30: error: variable or field &#8216;DrawIMG&#8217; declared void
graphics.h:30: error: &#8216;SDL_Surface&#8217; was not declared in this scope
graphics.h:30: error: &#8216;img&#8217; was not declared in this scope
graphics.h:30: error: expected primary-expression before &#8216;int&#8217;
graphics.h:30: error: expected primary-expression before &#8216;int&#8217;
graphics.h:30: error: initializer expression list treated as compound expression
graphics.h:31: error: variable or field &#8216;DrawIMG&#8217; declared void
graphics.h:31: error: redefinition of &#8216;int DrawIMG&#8217;
graphics.h:30: error: &#8216;int DrawIMG&#8217; previously defined here
graphics.h:31: error: &#8216;SDL_Surface&#8217; was not declared in this scope
graphics.h:31: error: &#8216;img&#8217; was not declared in this scope
graphics.h:31: error: expected primary-expression before &#8216;int&#8217;
graphics.h:31: error: expected primary-expression before &#8216;int&#8217;
graphics.h:31: error: expected primary-expression before &#8216;int&#8217;
graphics.h:31: error: expected primary-expression before &#8216;int&#8217;
graphics.h:32: error: &#8216;Uint8&#8217; has not been declared
graphics.h:32: error: &#8216;Uint8&#8217; has not been declared
graphics.h:32: error: &#8216;Uint8&#8217; has not been declared
graphics.h:35: error: &#8216;Uint32&#8217; does not name a type
graphics.h:36: error: variable or field &#8216;putpixel&#8217; declared void
graphics.h:36: error: &#8216;SDL_Surface&#8217; was not declared in this scope
graphics.h:36: error: &#8216;surface&#8217; was not declared in this scope
graphics.h:36: error: expected primary-expression before &#8216;int&#8217;
graphics.h:36: error: expected primary-expression before &#8216;int&#8217;
graphics.h:36: error: &#8216;Uint32&#8217; was not declared in this scope
graphics.h:36: error: initializer expression list treated as compound expression
graphics.h:37: error: &#8216;SDL_Surface&#8217; was not declared in this scope
graphics.h:37: error: &#8216;surface&#8217; was not declared in this scope
graphics.h:38: error: &#8216;SDL_Rect&#8217; was not declared in this scope
graphics.h:38: error: &#8216;SDL_Rect&#8217; was not declared in this scope
graphics.h:38: error: initializer expression list treated as compound expression
graphics.h:39: error: variable or field &#8216;ColorizeSurface&#8217; declared void
graphics.h:39: error: &#8216;SDL_Surface&#8217; was not declared in this scope
graphics.h:39: error: &#8216;surf&#8217; was not declared in this scope
graphics.h:39: error: &#8216;Uint8&#8217; was not declared in this scope
graphics.h:39: error: &#8216;Uint8&#8217; was not declared in this scope
graphics.h:39: error: &#8216;Uint8&#8217; was not declared in this scope
graphics.h:39: error: initializer expression list treated as compound expression
graphics.h:66: error: ISO C++ forbids declaration of &#8216;SDL_Surface&#8217; with no type
graphics.h:66: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
graphics.h:78: error: ISO C++ forbids declaration of &#8216;SDL_Surface&#8217; with no type
graphics.h:78: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
fftfile.h:42: error: ISO C++ forbids declaration of &#8216;SDL_Surface&#8217; with no type
fftfile.h:42: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
fftfile.h:45: error: &#8216;PHYSFS_file&#8217; was not declared in this scope
fftfile.h:45: error: &#8216;fp&#8217; was not declared in this scope
fftfile.h:46: error: &#8216;PHYSFS_file&#8217; was not declared in this scope
fftfile.h:46: error: &#8216;fp&#8217; was not declared in this scope
fftfile.h:49: error: &#8216;PHYSFS_file&#8217; was not declared in this scope
fftfile.h:49: error: &#8216;fp&#8217; was not declared in this scope
fftfile.h:50: error: &#8216;PHYSFS_file&#8217; was not declared in this scope
fftfile.h:50: error: &#8216;fp&#8217; was not declared in this scope
fftfile.h:52: error: &#8216;SDL_RWops&#8217; was not declared in this scope
fftfile.h:52: error: &#8216;rw&#8217; was not declared in this scope
fftfile.h:52: error: expected primary-expression before &#8216;int&#8217;
fftfile.h:52: error: expected primary-expression before &#8216;int&#8217;
fftfile.h:52: error: initializer expression list treated as compound expression
fftfile.h:53: error: &#8216;SDL_RWops&#8217; was not declared in this scope
fftfile.h:53: error: &#8216;rw&#8217; was not declared in this scope
fftfile.h:53: error: expected primary-expression before &#8216;void&#8217;
fftfile.h:53: error: expected primary-expression before &#8216;int&#8217;
fftfile.h:53: error: expected primary-expression before &#8216;int&#8217;
fftfile.h:53: error: initializer expression list treated as compound expression
fftfile.h:54: error: &#8216;SDL_RWops&#8217; was not declared in this scope
fftfile.h:54: error: &#8216;rw&#8217; was not declared in this scope
fftfile.h:54: error: expected primary-expression before &#8216;const&#8217;
fftfile.h:54: error: expected primary-expression before &#8216;int&#8217;
fftfile.h:54: error: expected primary-expression before &#8216;int&#8217;
fftfile.h:54: error: initializer expression list treated as compound expression
fftfile.h:55: error: &#8216;SDL_RWops&#8217; was not declared in this scope
fftfile.h:55: error: &#8216;rw&#8217; was not declared in this scope
fftfile.h:56: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
fftfile.h:57: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
fftfile.h:58: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
fftfile.h:59: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
fftfile.h:60: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
fftfile.h:68: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
fftfile.h:101: error: ISO C++ forbids declaration of &#8216;SDL_Surface&#8217; with no type
fftfile.h:101: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
fftfile.h:103: error: ISO C++ forbids declaration of &#8216;SDL_Surface&#8217; with no type
fftfile.h:103: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
fftfile.h:104: error: &#8216;Uint8&#8217; has not been declared
fftfile.h:104: error: &#8216;Uint8&#8217; has not been declared
fftfile.h:104: error: &#8216;Uint8&#8217; has not been declared
fftfile.h:116: error: ISO C++ forbids declaration of &#8216;SDL_Surface&#8217; with no type
fftfile.h:116: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
fftfile.h:130: error: ISO C++ forbids declaration of &#8216;SDL_Surface&#8217; with no type
fftfile.h:130: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
fftfile.cpp:6: error: redefinition of &#8216;char PHYSFS_getc&#8217;
fftfile.h:45: error: &#8216;char PHYSFS_getc&#8217; previously defined here
fftfile.cpp:6: error: &#8216;PHYSFS_file&#8217; was not declared in this scope
fftfile.cpp:6: error: &#8216;fp&#8217; was not declared in this scope
fftfile.cpp:15: error: redefinition of &#8216;std::string PHYSFS_getline&#8217;
fftfile.h:46: error: &#8216;std::string PHYSFS_getline&#8217; previously declared here
fftfile.cpp:15: error: &#8216;PHYSFS_file&#8217; was not declared in this scope
fftfile.cpp:15: error: &#8216;fp&#8217; was not declared in this scope
fftfile.cpp:53: error: redefinition of &#8216;std::string getNextName&#8217;
fftfile.h:49: error: &#8216;std::string getNextName&#8217; previously declared here
fftfile.cpp:53: error: &#8216;PHYSFS_file&#8217; was not declared in this scope
fftfile.cpp:53: error: &#8216;fp&#8217; was not declared in this scope
fftfile.cpp:67: error: redefinition of &#8216;aries::DataNode* ReadDoc&#8217;
fftfile.h:50: error: &#8216;aries::DataNode* ReadDoc&#8217; previously defined here
fftfile.cpp:67: error: &#8216;PHYSFS_file&#8217; was not declared in this scope
fftfile.cpp:67: error: &#8216;fp&#8217; was not declared in this scope
fftfile.cpp:162: error: redefinition of &#8216;int physfsrwops_seek&#8217;
fftfile.h:52: error: &#8216;int physfsrwops_seek&#8217; previously defined here
fftfile.cpp:162: error: &#8216;SDL_RWops&#8217; was not declared in this scope
fftfile.cpp:162: error: &#8216;rw&#8217; was not declared in this scope
fftfile.cpp:162: error: expected primary-expression before &#8216;int&#8217;
fftfile.cpp:162: error: expected primary-expression before &#8216;int&#8217;
fftfile.cpp:234: error: redefinition of &#8216;int physfsrwops_read&#8217;
fftfile.h:53: error: &#8216;int physfsrwops_read&#8217; previously defined here
fftfile.cpp:234: error: &#8216;SDL_RWops&#8217; was not declared in this scope
fftfile.cpp:234: error: &#8216;rw&#8217; was not declared in this scope
fftfile.cpp:234: error: expected primary-expression before &#8216;void&#8217;
fftfile.cpp:234: error: expected primary-expression before &#8216;int&#8217;
fftfile.cpp:234: error: expected primary-expression before &#8216;int&#8217;
fftfile.cpp:246: error: redefinition of &#8216;int physfsrwops_write&#8217;
fftfile.h:54: error: &#8216;int physfsrwops_write&#8217; previously defined here
fftfile.cpp:246: error: &#8216;SDL_RWops&#8217; was not declared in this scope
fftfile.cpp:246: error: &#8216;rw&#8217; was not declared in this scope
fftfile.cpp:246: error: expected primary-expression before &#8216;const&#8217;
fftfile.cpp:246: error: expected primary-expression before &#8216;int&#8217;
fftfile.cpp:246: error: expected primary-expression before &#8216;int&#8217;
fftfile.cpp:255: error: redefinition of &#8216;int physfsrwops_close&#8217;
fftfile.h:55: error: &#8216;int physfsrwops_close&#8217; previously defined here
fftfile.cpp:255: error: &#8216;SDL_RWops&#8217; was not declared in this scope
fftfile.cpp:255: error: &#8216;rw&#8217; was not declared in this scope
fftfile.cpp:267: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
fftfile.cpp:288: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
fftfile.cpp:307: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
fftfile.cpp:322: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
fftfile.cpp:334: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
fftfile.cpp: In function &#8216;int FPK_count()&#8217;:
fftfile.cpp:365: error: &#8216;PHYSFS_enumerateFiles&#8217; was not declared in this scope
fftfile.cpp:373: error: &#8216;PHYSFS_freeList&#8217; was not declared in this scope
fftfile.cpp: In function &#8216;float FPK_versionByName(std::string)&#8217;:
fftfile.cpp:383: error: &#8216;PHYSFS_getSearchPath&#8217; was not declared in this scope
fftfile.cpp:391: error: &#8216;PHYSFS_file&#8217; was not declared in this scope
fftfile.cpp:391: error: &#8216;fp&#8217; was not declared in this scope
fftfile.cpp:391: error: &#8216;PHYSFS_openRead&#8217; was not declared in this scope
fftfile.cpp:397: error: &#8216;ReadDoc&#8217; cannot be used as a function
fftfile.cpp:408: error: &#8216;PHYSFS_close&#8217; was not declared in this scope
fftfile.cpp:409: error: &#8216;PHYSFS_removeFromSearchPath&#8217; was not declared in this scope
fftfile.cpp:412: error: &#8216;PHYSFS_freeList&#8217; was not declared in this scope
fftfile.cpp:417: error: &#8216;PHYSFS_getBaseDir&#8217; was not declared in this scope
fftfile.cpp:417: error: &#8216;PHYSFS_addToSearchPath&#8217; was not declared in this scope
fftfile.cpp:418: error: &#8216;PHYSFS_enumerateFiles&#8217; was not declared in this scope
fftfile.cpp: In function &#8216;std::string FPK_ByName(std::string)&#8217;:
fftfile.cpp:438: error: &#8216;PHYSFS_getSearchPath&#8217; was not declared in this scope
fftfile.cpp:445: error: &#8216;PHYSFS_file&#8217; was not declared in this scope
fftfile.cpp:445: error: &#8216;fp&#8217; was not declared in this scope
fftfile.cpp:445: error: &#8216;PHYSFS_openRead&#8217; was not declared in this scope
fftfile.cpp:451: error: &#8216;ReadDoc&#8217; cannot be used as a function
fftfile.cpp:458: error: &#8216;PHYSFS_close&#8217; was not declared in this scope
fftfile.cpp:459: error: &#8216;PHYSFS_removeFromSearchPath&#8217; was not declared in this scope
fftfile.cpp:462: error: &#8216;PHYSFS_freeList&#8217; was not declared in this scope
fftfile.cpp:465: error: &#8216;PHYSFS_getBaseDir&#8217; was not declared in this scope
fftfile.cpp:465: error: &#8216;PHYSFS_addToSearchPath&#8217; was not declared in this scope
fftfile.cpp:466: error: &#8216;PHYSFS_enumerateFiles&#8217; was not declared in this scope
fftfile.cpp: In function &#8216;void FPK_Invalid(std::string, std::string)&#8217;:
fftfile.cpp:482: error: &#8216;TTF_Font&#8217; was not declared in this scope
fftfile.cpp:482: error: &#8216;font&#8217; was not declared in this scope
fftfile.cpp:482: error: &#8216;TTF_OpenFont&#8217; was not declared in this scope
fftfile.cpp:483: error: &#8216;SDL_Color&#8217; was not declared in this scope
fftfile.cpp:483: error: expected `;' before &#8216;white&#8217;
fftfile.cpp:484: error: &#8216;SDL_Surface&#8217; was not declared in this scope
fftfile.cpp:484: error: &#8216;screen&#8217; was not declared in this scope
fftfile.cpp:484: error: &#8216;SDL_GetVideoSurface&#8217; was not declared in this scope
fftfile.cpp:487: error: &#8216;Uint16&#8217; was not declared in this scope
fftfile.cpp:487: error: expected `;' before &#8216;i&#8217;
fftfile.cpp:491: error: &#8216;i&#8217; was not declared in this scope
fftfile.cpp:503: error: &#8216;Uint32&#8217; was not declared in this scope
fftfile.cpp:503: error: expected `;' before &#8216;ticks&#8217;
fftfile.cpp:504: error: &#8216;SDL_Event&#8217; was not declared in this scope
fftfile.cpp:504: error: expected `;' before &#8216;event&#8217;
fftfile.cpp:506: error: &#8216;SDL_GetTicks&#8217; was not declared in this scope
fftfile.cpp:506: error: &#8216;ticks&#8217; was not declared in this scope
fftfile.cpp:508: error: &#8216;event&#8217; was not declared in this scope
fftfile.cpp:508: error: &#8216;SDL_PollEvent&#8217; was not declared in this scope
fftfile.cpp:513: error: &#8216;SDL_QUIT&#8217; was not declared in this scope
fftfile.cpp:518: error: &#8216;SDL_FillRect&#8217; was not declared in this scope
fftfile.cpp:519: error: &#8216;white&#8217; was not declared in this scope
fftfile.cpp:519: error: &#8216;drawString&#8217; cannot be used as a function
fftfile.cpp:523: error: &#8216;drawString&#8217; cannot be used as a function
fftfile.cpp:526: error: &#8216;drawString&#8217; cannot be used as a function
fftfile.cpp:527: error: &#8216;SDL_Flip&#8217; was not declared in this scope
fftfile.cpp: In function &#8216;int FPK_countPlayerShips(std::string)&#8217;:
fftfile.cpp:541: error: &#8216;PHYSFS_getSearchPath&#8217; was not declared in this scope
fftfile.cpp:548: error: &#8216;PHYSFS_removeFromSearchPath&#8217; was not declared in this scope
fftfile.cpp:550: error: &#8216;PHYSFS_freeList&#8217; was not declared in this scope
fftfile.cpp:552: error: &#8216;PHYSFS_addToSearchPath&#8217; was not declared in this scope
fftfile.cpp:556: error: &#8216;PHYSFS_file&#8217; was not declared in this scope
fftfile.cpp:556: error: &#8216;fp&#8217; was not declared in this scope
fftfile.cpp:556: error: &#8216;PHYSFS_openRead&#8217; was not declared in this scope
fftfile.cpp:562: error: &#8216;ReadDoc&#8217; cannot be used as a function
fftfile.cpp:572: error: &#8216;PHYSFS_close&#8217; was not declared in this scope
fftfile.cpp:573: error: &#8216;PHYSFS_removeFromSearchPath&#8217; was not declared in this scope
fftfile.cpp:576: error: &#8216;PHYSFS_getBaseDir&#8217; was not declared in this scope
fftfile.cpp:577: error: &#8216;PHYSFS_enumerateFiles&#8217; was not declared in this scope
fftfile.cpp: At global scope:
fftfile.cpp:591: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
fftfile.cpp: In constructor &#8216;FPKShip::FPKShip(int, int)&#8217;:
fftfile.cpp:662: error: &#8216;struct __ship_slot&#8217; has no member named &#8216;image&#8217;
fftfile.cpp:664: error: &#8216;shield&#8217; was not declared in this scope
fftfile.cpp:665: error: &#8216;image&#8217; was not declared in this scope
fftfile.cpp:673: error: &#8216;LoadIMG&#8217; was not declared in this scope
fftfile.cpp: In constructor &#8216;FPKShip::FPKShip(std::string, std::string)&#8217;:
fftfile.cpp:684: error: &#8216;struct __ship_slot&#8217; has no member named &#8216;image&#8217;
fftfile.cpp:686: error: &#8216;shield&#8217; was not declared in this scope
fftfile.cpp:687: error: &#8216;image&#8217; was not declared in this scope
fftfile.cpp:692: error: &#8216;LoadIMG&#8217; was not declared in this scope
fftfile.cpp: In destructor &#8216;FPKShip::~FPKShip()&#8217;:
fftfile.cpp:697: error: &#8216;image&#8217; was not declared in this scope
fftfile.cpp:697: error: &#8216;SDL_FreeSurface&#8217; was not declared in this scope
fftfile.cpp:698: error: &#8216;shield&#8217; was not declared in this scope
fftfile.cpp:698: error: &#8216;SDL_FreeSurface&#8217; was not declared in this scope
fftfile.cpp: In member function &#8216;void FPKShip::GetFileInfo(int, int)&#8217;:
fftfile.cpp:705: error: &#8216;PHYSFS_getSearchPath&#8217; was not declared in this scope
fftfile.cpp:715: error: &#8216;PHYSFS_removeFromSearchPath&#8217; was not declared in this scope
fftfile.cpp:717: error: &#8216;PHYSFS_freeList&#8217; was not declared in this scope
fftfile.cpp:718: error: &#8216;PHYSFS_getBaseDir&#8217; was not declared in this scope
fftfile.cpp:718: error: &#8216;PHYSFS_addToSearchPath&#8217; was not declared in this scope
fftfile.cpp:720: error: &#8216;PHYSFS_enumerateFiles&#8217; was not declared in this scope
fftfile.cpp:739: error: &#8216;PHYSFS_file&#8217; was not declared in this scope
fftfile.cpp:739: error: &#8216;fp&#8217; was not declared in this scope
fftfile.cpp:739: error: &#8216;PHYSFS_openRead&#8217; was not declared in this scope
fftfile.cpp:745: error: &#8216;ReadDoc&#8217; cannot be used as a function
fftfile.cpp:746: error: &#8216;PHYSFS_close&#8217; was not declared in this scope
fftfile.cpp:755: error: &#8216;PHYSFS_removeFromSearchPath&#8217; was not declared in this scope
fftfile.cpp: In member function &#8216;void FPKShip::GetFileInfo(std::string, std::string)&#8217;:
fftfile.cpp:780: error: &#8216;PHYSFS_getSearchPath&#8217; was not declared in this scope
fftfile.cpp:790: error: &#8216;PHYSFS_removeFromSearchPath&#8217; was not declared in this scope
fftfile.cpp:792: error: &#8216;PHYSFS_freeList&#8217; was not declared in this scope
fftfile.cpp:793: error: &#8216;PHYSFS_getBaseDir&#8217; was not declared in this scope
fftfile.cpp:793: error: &#8216;PHYSFS_addToSearchPath&#8217; was not declared in this scope
fftfile.cpp:800: error: &#8216;PHYSFS_file&#8217; was not declared in this scope
fftfile.cpp:800: error: &#8216;fp&#8217; was not declared in this scope
fftfile.cpp:800: error: &#8216;PHYSFS_openRead&#8217; was not declared in this scope
fftfile.cpp:807: error: &#8216;ReadDoc&#8217; cannot be used as a function
fftfile.cpp:808: error: &#8216;PHYSFS_close&#8217; was not declared in this scope
fftfile.cpp:929: error: &#8216;image&#8217; was not declared in this scope
fftfile.cpp:972: error: &#8216;PHYSFS_removeFromSearchPath&#8217; was not declared in this scope
fftfile.cpp:975: error: &#8216;PHYSFS_enumerateFiles&#8217; was not declared in this scope
fftfile.cpp: In member function &#8216;void FPKShip::Reload(int, int)&#8217;:
fftfile.cpp:990: error: &#8216;image&#8217; was not declared in this scope
fftfile.cpp:990: error: &#8216;SDL_FreeSurface&#8217; was not declared in this scope
fftfile.cpp:991: error: &#8216;shield&#8217; was not declared in this scope
fftfile.cpp:991: error: &#8216;SDL_FreeSurface&#8217; was not declared in this scope
fftfile.cpp:992: error: &#8216;shield&#8217; was not declared in this scope
fftfile.cpp:993: error: &#8216;image&#8217; was not declared in this scope
fftfile.cpp:996: error: &#8216;LoadIMG&#8217; was not declared in this scope
fftfile.cpp: At global scope:
fftfile.cpp:1076: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
fftfile.cpp:1084: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
fftfile.cpp:1088: error: variable or field &#8216;Colorize&#8217; declared void
fftfile.cpp:1088: error: &#8216;int FPKShip::Colorize&#8217; is not a static member of &#8216;class FPKShip&#8217;
fftfile.cpp:1088: error: &#8216;Uint8&#8217; was not declared in this scope
fftfile.cpp:1088: error: &#8216;Uint8&#8217; was not declared in this scope
fftfile.cpp:1088: error: &#8216;Uint8&#8217; was not declared in this scope
fftfile.cpp:1088: error: initializer expression list treated as compound expression
fftfile.cpp:1089: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;{&#8217; token
fftfile.cpp: In member function &#8216;void FPKShip::ZeroSlots()&#8217;:
fftfile.cpp:1158: error: &#8216;struct __ship_slot&#8217; has no member named &#8216;image&#8217;
fftfile.cpp:1158: error: &#8216;struct __ship_slot&#8217; has no member named &#8216;image&#8217;
fftfile.cpp:1158: error: &#8216;SDL_FreeSurface&#8217; was not declared in this scope
fftfile.cpp:1159: error: &#8216;struct __ship_slot&#8217; has no member named &#8216;image&#8217;
fftfile.cpp: In constructor &#8216;Preferences::Preferences(std::string)&#8217;:
fftfile.cpp:1170: error: &#8216;PHYSFS_exists&#8217; was not declared in this scope
fftfile.cpp:1198: error: &#8216;PHYSFS_file&#8217; was not declared in this scope
fftfile.cpp:1198: error: &#8216;fp&#8217; was not declared in this scope
fftfile.cpp:1198: error: &#8216;PHYSFS_openWrite&#8217; was not declared in this scope
fftfile.cpp:1199: error: &#8216;PHYSFS_write&#8217; was not declared in this scope
fftfile.cpp:1200: error: &#8216;PHYSFS_close&#8217; was not declared in this scope
fftfile.cpp: In member function &#8216;void Preferences::Load()&#8217;:
fftfile.cpp:1210: error: &#8216;PHYSFS_file&#8217; was not declared in this scope
fftfile.cpp:1210: error: &#8216;fp&#8217; was not declared in this scope
fftfile.cpp:1210: error: &#8216;PHYSFS_openRead&#8217; was not declared in this scope
fftfile.cpp:1211: error: &#8216;ReadDoc&#8217; cannot be used as a function
fftfile.cpp:1212: error: &#8216;PHYSFS_close&#8217; was not declared in this scope
fftfile.cpp: In member function &#8216;void Preferences::Save()&#8217;:
fftfile.cpp:1259: error: &#8216;PHYSFS_file&#8217; was not declared in this scope
fftfile.cpp:1259: error: &#8216;fp&#8217; was not declared in this scope
fftfile.cpp:1259: error: &#8216;PHYSFS_openWrite&#8217; was not declared in this scope
fftfile.cpp:1260: error: &#8216;PHYSFS_write&#8217; was not declared in this scope
fftfile.cpp:1261: error: &#8216;PHYSFS_close&#8217; was not declared in this scope
make: *** [fftfile.o] Error 1
cubanresourceful@cubanresourceful:~/Library/Downloads/fft$
```

Thanks for the quick reply and help!

---

### Post by zvacet on 2007-03-03
What **Read me** file say?

---

### Post by christhemonkey on 2007-03-03
You need the library libsdl1.2-dev installed.
```
sudo apt-get install libsdl1.2-dev 
```

---

### Post by cubanresourceful on 2007-03-04
I installed all the -dev packages I need, it greatly reduced the errors, but there still a little bit more. Here it is:

```

cubanresourceful@cubanresourceful:~/Library/Downloads/fft$ make
g++ -c -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -Wall -ansi -O2 -g   guiapply.cpp -o guiapply.o
units.h:244: error: extra qualification &#8216;MapObject::&#8217; on member &#8216;IsLoaded&#8217;
units.h:356: error: extra qualification &#8216;Map::&#8217; on member &#8216;GetAIUnitImageW&#8217;
units.h:357: error: extra qualification &#8216;Map::&#8217; on member &#8216;GetAIUnitImageH&#8217;
make: *** [guiapply.o] Error 1

```

---

### Post by christhemonkey on 2007-03-04
As the last update was in 2004, maybe the code is incorrect?

> # Final Frontier Trader 0.66 released    2004-08-31

My best guess is that you need to remove those extra qualifications in line 244 356 and 257 of units.h and then try to recompile...

---

### Post by cubanresourceful on 2007-03-04
Doing that made errors from units.cpp. I just have given up, I wanted to play the game, because I like games like that, space trading sims + combat, and you can upgrade your ships and such. Kind of like flashtrek, the flash version of star trek. Oh well, I guess I need to see what else I can find on sourceforge that is simular. :D Thanks for the help though!

---

### Post by christhemonkey on 2007-03-04
If i get time, il whip up a .deb package for you. Il let you know if i get round to it!

---

### Post by cubanresourceful on 2007-03-04
Thanks, that means alot to me! :D

---

### Post by christhemonkey on 2007-03-04
Its ok, but i am a prolific procrastinator so it might take a while!

---

