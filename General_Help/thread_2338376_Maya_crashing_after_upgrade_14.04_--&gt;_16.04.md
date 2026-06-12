---
title: "Maya crashing after upgrade 14.04 --&gt; 16.04"
date: 2016-09-27
forum: General Help
---

### Post by john_patterson on 2016-09-27
I had Maya running for about a year on ubuntu 14.04, even though it is not officially supported.  I used some ideas from this thread to get it working:


[http://forums.autodesk.com/t5/installation-licensing/installing-maya-on-ubuntu/m-p/6049537#M123377](http://forums.autodesk.com/t5/installation-licensing/installing-maya-on-ubuntu/m-p/6049537#M123377)




Yesterday I upgraded from 14.04 to 16.04.  Everything went OK, (maybe there were some errors?) but now Maya crashes on startup, right after the splash screen shows up.  I reinstalled the nvidia-352 driver, but then I couldn't get X windows running, even in failsafe mode.  I upgraded to nvidia-364.19 and things are back to normal, but I still can not run Maya.  Here is the output when it crashes.  Any suggestions?:


```
john@colfax-ESC1000-G2:~$maya


terminate calledafter throwing an instance of 'std::logic_error'
  what(): basic_string::_S_construct null not valid
Stack trace:
 /lib/x86_64-linux-gnu/libc.so.6(+0x354a0) [0x7f25830de4a0]
  gsignal
  abort
 __gnu_cxx::__verbose_terminate_handler()
 /usr/lib/x86_64-linux-gnu/libstdc++.so.6(+0x8d6b6) [0x7f2583b8d6b6]
 /usr/lib/x86_64-linux-gnu/libstdc++.so.6(+0x8d701) [0x7f2583b8d701]
 /usr/lib/x86_64-linux-gnu/libstdc++.so.6(+0x8d919) [0x7f2583b8d919]
 std::__throw_logic_error(char const*)
  char*std::string::_S_construct<char const*>(char const*, charconst*, std::allocator<char> const&,std::forward_iterator_tag)
 std::basic_string<char, std::char_traits<char>,std::allocator<char> >::basic_string(char const*,std::allocator<char> const&)
 /usr/autodesk/maya2016/lib/libMC3.so.8(+0xb7330) [0x7f2581f54330]
 /usr/autodesk/maya2016/lib/libMC3.so.8(+0x139c7f) [0x7f2581fd6c7f]
 /usr/autodesk/maya2016/lib/libMC3.so.8(+0xb7f69) [0x7f2581f54f69]
 CMLFacade::Initialize(CMLWaypoint*, wchar_t const*, wchar_t const*,wchar_t const*, int, unsigned int, long long, long long, MC3_MODE,wchar_t const*)
 TCIPClient::initialize()
 TCIPClient::TCIPClient()
 TCIPClient::theOne()
 TbaseApp::cipReportStartup()
 TbaseApp::initGeneral()
 /usr/autodesk/maya2016/bin/maya.bin() [0x415a52]
 Tapplication::start()
 /usr/autodesk/maya2016/bin/maya.bin() [0x40e6ff]
  main
  __libc_start_main
 /usr/autodesk/maya2016/bin/maya.bin() [0x40debd]


Segmentation fault(core dumped)
john@colfax-ESC1000-G2:~$
```

---

