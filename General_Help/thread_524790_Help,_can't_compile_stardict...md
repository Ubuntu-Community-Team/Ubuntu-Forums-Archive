---
title: "Help, can't compile stardict.."
date: 2007-08-13
forum: General Help
---

### Post by zhangsong023 on 2007-08-13
I want to compile the latest version of stardict(3.0.0), I use
sudo apt-get build-dep startdict 
to install necessary package.
But compile process still exit with this error:
.libs/advertisement.o: In function `unload_dict':
/home/zhangjinsong/Desktop/stardict/stardict-3.0.0/stardict-plugins/stardict-advertisement-plugin/advertisement.cpp:183: undefined reference to `g_free'
.libs/advertisement.o: In function `stardict_plugin_init':
/home/zhangjinsong/Desktop/stardict/stardict-3.0.0/stardict-plugins/stardict-advertisement-plugin/advertisement.cpp:224: undefined reference to `g_print'
/home/zhangjinsong/Desktop/stardict/stardict-3.0.0/stardict-plugins/stardict-advertisement-plugin/advertisement.cpp:228: undefined reference to `g_strdup_printf'
.libs/advertisement.o: In function `build_dictdata':
/home/zhangjinsong/Desktop/stardict/stardict-3.0.0/stardict-plugins/stardict-advertisement-plugin/advertisement.cpp:65: undefined reference to `g_ascii_table'
/home/zhangjinsong/Desktop/stardict/stardict-3.0.0/stardict-plugins/stardict-advertisement-plugin/advertisement.cpp:95: undefined reference to `g_malloc'
/home/zhangjinsong/Desktop/stardict/stardict-3.0.0/stardict-plugins/stardict-advertisement-plugin/advertisement.cpp:81: undefined reference to `g_malloc'
/home/zhangjinsong/Desktop/stardict/stardict-3.0.0/stardict-plugins/stardict-advertisement-plugin/advertisement.cpp:106: undefined reference to `g_malloc'
.libs/advertisement.o: In function `load_dict':
/home/zhangjinsong/Desktop/stardict/stardict-3.0.0/stardict-plugins/stardict-advertisement-plugin/advertisement.cpp:120: undefined reference to `g_file_get_contents'
/home/zhangjinsong/Desktop/stardict/stardict-3.0.0/stardict-plugins/stardict-advertisement-plugin/advertisement.cpp:164: undefined reference to `g_utf8_strdown'
/home/zhangjinsong/Desktop/stardict/stardict-3.0.0/stardict-plugins/stardict-advertisement-plugin/advertisement.cpp:166: undefined reference to `g_free'
/home/zhangjinsong/Desktop/stardict/stardict-3.0.0/stardict-plugins/stardict-advertisement-plugin/advertisement.cpp:176: undefined reference to `g_free'
/home/zhangjinsong/Desktop/stardict/stardict-3.0.0/stardict-plugins/stardict-advertisement-plugin/advertisement.cpp:122: undefined reference to `g_print'
.libs/advertisement.o: In function `stardict_virtualdict_plugin_init':
/home/zhangjinsong/Desktop/stardict/stardict-3.0.0/stardict-plugins/stardict-advertisement-plugin/advertisement.cpp:249: undefined reference to `g_print'
.libs/advertisement.o: In function `lookup':
/home/zhangjinsong/Desktop/stardict/stardict-3.0.0/stardict-plugins/stardict-advertisement-plugin/advertisement.cpp:189: undefined reference to `g_utf8_strdown'
/home/zhangjinsong/Desktop/stardict/stardict-3.0.0/stardict-plugins/stardict-advertisement-plugin/advertisement.cpp:214: undefined reference to `g_free'
/home/zhangjinsong/Desktop/stardict/stardict-3.0.0/stardict-plugins/stardict-advertisement-plugin/advertisement.cpp:199: undefined reference to `g_malloc'
/home/zhangjinsong/Desktop/stardict/stardict-3.0.0/stardict-plugins/stardict-advertisement-plugin/advertisement.cpp:200: undefined reference to `g_malloc'
/home/zhangjinsong/Desktop/stardict/stardict-3.0.0/stardict-plugins/stardict-advertisement-plugin/advertisement.cpp:202: undefined reference to `g_strdup'
/home/zhangjinsong/Desktop/stardict/stardict-3.0.0/stardict-plugins/stardict-advertisement-plugin/advertisement.cpp:204: undefined reference to `g_malloc'
/home/zhangjinsong/Desktop/stardict/stardict-3.0.0/stardict-plugins/stardict-advertisement-plugin/advertisement.cpp:207: undefined reference to `g_memdup'
collect2: ld returned 1 exit status

Someone told me use glibn and glibndev can solve this problem, but I can't find these tow package in repository. 
Any suggestions?

---

### Post by Paulmd on 2007-08-14
What that error means is that the programmer called a function that is not defined. In this case, it  PROBABLY means that he forgot to include the header file that contains the definitions in question.



All of those functions are defined in glib.h 

make sure there is 

```
#include <glib.h>
``` 

in the file gcc is complaining about.

```
 /home/zhangjinsong/Desktop/stardict/stardict-3.0.0/stardict-plugins/stardict-advertisement-plugin/advertisement.cpp) 
```


The #include statements should be right at the very top of a .c (or .cpp)  file. 

.c and .cpp files are standard text files that can be opened with gedit.

---

### Post by zhangsong023 on 2007-08-14
Thanks, I'll try it.

---

### Post by netimen on 2007-10-12
I get the following error: 
> /usr/include/festival/festival.h:44:17: error: EST.h: No such file or directory

but I have this include in /usr/include/speech_tools

---

### Post by shenhanc on 2008-07-07
> **netimen said:**
> I get the following error: 


but I have this include in /usr/include/speech_tools

By examing "/opt/stardict-3.0.1/stardict-plugins/stardict-festival-tts-plugin/Makefile", there is a line: 

   FESTIVAL_CFLAGS = -I/usr/include/speech-tools/EST -ffriend-injection -Wno-deprecated

But the real path is "/usr/include/speech_tools", so the simplest method is to make a softlink speech-tools to speech_tools and replace the above line with:

   FESTIVAL_CFLAGS = -I/usr/include/speech-tools/EST -I/usr/include/speech-tools -ffriend-injection -Wno-deprecated

That will solve the problem.

(Stardict 3.0.1 + Ubuntu 8.04)

---

