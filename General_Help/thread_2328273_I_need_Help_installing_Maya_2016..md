---
title: "I need Help installing Maya 2016."
date: 2016-06-19
forum: General Help
---

### Post by leod2 on 2016-06-19
I just installed Ubuntu 16.04 LTS and after installing my proprietary video drivers I attempted to install Maya 2016. I attempted to run this script ([https://www.snip2code.com/Snippet/843315/Installing-Maya-2016-SP4-on-Ubuntu-15-10](https://www.snip2code.com/Snippet/843315/Installing-Maya-2016-SP4-on-Ubuntu-15-10)), however it did not complete correctly and I went through and manually initiated all of the steps, finally getting to the point where Maya 2016 is "installed" and it launches, only to crash with a "Segmentation fault". Is there anyone who could help me diagnose this? What information do I need to provide? The text displayed in the terminal when Maya crashes is as follows:

```
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct null not valid
Stack trace:
  /lib/x86_64-linux-gnu/libc.so.6(+0x354a0) [0x7f5e442914a0]
  gsignal
  abort
  __gnu_cxx::__verbose_terminate_handler()
  /usr/lib/x86_64-linux-gnu/libstdc++.so.6(+0x8d6b6) [0x7f5e44d406b6]
  /usr/lib/x86_64-linux-gnu/libstdc++.so.6(+0x8d701) [0x7f5e44d40701]
  /usr/lib/x86_64-linux-gnu/libstdc++.so.6(+0x8d919) [0x7f5e44d40919]
  std::__throw_logic_error(char const*)
  char* std::string::_S_construct<char const*>(char const*, char const*, std::allocator<char> const&, std::forward_iterator_tag)
  std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string(char const*, std::allocator<char> const&)
  /usr/autodesk/maya2016/lib/libMC3.so.8(+0xb7330) [0x7f5e430f6330]
  /usr/autodesk/maya2016/lib/libMC3.so.8(+0x139c7f) [0x7f5e43178c7f]
  /usr/autodesk/maya2016/lib/libMC3.so.8(+0xb7f69) [0x7f5e430f6f69]
  CMLFacade::Initialize(CMLWaypoint*, wchar_t const*, wchar_t const*, wchar_t const*, int, unsigned int, long long, long long, MC3_MODE, wchar_t const*)
  TCIPClient::initialize()
  TCIPClient::TCIPClient()
  TCIPClient::theOne()
  TbaseApp::cipReportStartup()
  TbaseApp::initGeneral()
  /usr/autodesk/maya2016/bin/maya.bin() [0x415d82]
  Tapplication::start()
  /usr/autodesk/maya2016/bin/maya.bin() [0x40e8af]
  main
  __libc_start_main
  /usr/autodesk/maya2016/bin/maya.bin() [0x40e06d]


```

It seems like Maya is so close to running on Ubuntu, but for some reason it will not, I have gotten the rpm packages to install in CentOS flawlessly along with Fedora 22, however I am having a hard time getting it to run on Ubuntu (I'm guessing because of having to convert it to .deb packages, but I think its installed correctly).

Any help would be greatly appreciated.

Thanks.

---

### Post by john_patterson on 2016-09-27
I'm having the same exact problem.  Any solutions?

---

### Post by Bucky Ball on 2016-09-27
*Thread closed.*

Suggest you start a new thread rather than waking this old, dead one. You'll have more luck. Doubtful you have the 'exact' same problem unless you were following the instruction to install Maya 2016 on 15.10. The OP was.

---

