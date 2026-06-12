---
title: "aMule won't crashes on start-up"
date: 2005-10-18
forum: General Help
---

### Post by jhardtone on 2005-10-18
Hi, when I try to start amule, it crashes/won't start. I get the following error message:
```
--------------------------------------------------------------------------------
A fatal error has occurred and aMule has crashed.
Please assist us in fixing this problem by posting the backtrace below in our
'aMule Crashes' forum and include as much information as possible regarding the
circumstances of this crash. The forum is located here:
    http://forum.amule.org/board.php?boardid=67
If possible, please try to generate a real backtrace of this crash:
    http://www.amule.org/wiki/index.php/Backtraces

----------------------------=| BACKTRACE FOLLOWS: |=----------------------------
Current version is: aMule 2.0.3 using wxGTK2 v2.6.1 (Unicoded)
Running on: Linux 2.6.12-9-386 i686

[2] wxFatalSignalHandler in /usr/lib/libwx_baseu-2.6.so.0[0xb7aa6cba]
[3] ?? in [0xffffe420]
[4] wxCheckBoxBase::~wxCheckBoxBase() in amule [0x81b6081]
[5] wxArchiveInputStream::Peek() in amule [0x8132c32]
[6] wxArchiveInputStream::Peek() in amule [0x8134bc0]
[7] wxArchiveInputStream::Peek() in amule [0x81382f9]
[8] wxArchiveInputStream::Peek() in amule [0x8138524]
[9] wxString::wxString(wchar_t const*) in amule [0x8077441]
[10] wxStringTokenizer::~wxStringTokenizer() in amule [0x807b199]
[11] wxAppConsole::CallOnInit() in amule[0x807a95d]
[12] wxEntry(int&, wchar_t**) in /usr/lib/libwx_baseu-2.6.so.0[0xb7a4dab2]
[13] wxEntry(int&, char**) in /usr/lib/libwx_baseu-2.6.so.0[0xb7a4db88]
[14] wxStringTokenizer::~wxStringTokenizer() in amule [0x807b0ce]
[15] __libc_start_main in /lib/tls/i686/cmov/libc.so.6[0xb779cea2]
[16] __gxx_personality_v0 in amule[0x8065d11]

--------------------------------------------------------------------------------
```

This started when I upgraded to breezy. Any ideas?

---

### Post by Moonhill on 2006-03-07
Same problem....

---

### Post by moeFinley on 2006-07-27
They say in the aMule forum that you need wxGTK2 2.6.3

It's not available in the standard Ubuntu multiverse repositories.  Does anyone know where's best to install it from?

---

### Post by easyease on 2006-07-27
its probabley available from sourceforge. ill have a look.....

---

### Post by easyease on 2006-07-27
sorry cant find that file. found this link to how to get the latest version of amule for ubuntu.
 
[http://forum.amule.org/thread.php?threadid=10281&sid=1d6b74dd3c0cf043538fbd36d0c4dd53](http://forum.amule.org/thread.php?threadid=10281&sid=1d6b74dd3c0cf043538fbd36d0c4dd53)

---

### Post by moeFinley on 2006-07-27
Cool thanks, that is exactly what I needed!

I did search the amule forum for Ubuntu posts but I didn't see that one :confused:

---

