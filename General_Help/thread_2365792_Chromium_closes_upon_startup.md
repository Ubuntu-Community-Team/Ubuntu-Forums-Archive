---
title: "Chromium closes upon startup"
date: 2017-07-10
forum: General Help
---

### Post by ian1971 on 2017-07-10
Hi,

I'm running the 32bit version of Ubuntu 16.04 LTS and I've recently installed Chromium via the Ubuntu Software Center.  When attempting to run Chromium, the application starts up but then closes within a few seconds.  I've run Chromium from the terminal (via the command 'chromium-browser'), with the following output:

Using PPAPI flash.
 --ppapi-flash-path=/usr/lib/adobe-flashplugin/libpepflashplayer.so --ppapi-flash-version=
[2344:2344:0710/183634.401142:ERROR:navigation_entry_screenshot_manager.cc(135)] Invalid entry with unique id: 1
[2344:2383:0710/183635.576656:ERROR:simple_index_file.cc(256)] Could not create a directory to hold the index file
Received signal 11 SEGV_MAPERR 000000000008
#0 0x0000b75b0f0a base::debug::StackTrace::StackTrace()
#1 0x0000b75b083a base::debug::StackTrace::StackTrace()
#2 0x0000b75b1388 <unknown>
#3 0x0000b773fcfc ([vdso]+0xcfb)
#4 0x0000805a848a <unknown>
#5 0x0000805ab01b <unknown>
#6 0x0000805ab7d4 <unknown>
#7 0x0000805abb1b <unknown>
#8 0x0000805a4586 <unknown>
#9 0x0000b7635e2e <unknown>
#10 0x0000b7635db3 <unknown>
#11 0x0000b75b280b base::debug::TaskAnnotator::RunTask()
#12 0x0000b75def3b base::MessageLoop::RunTask()
#13 0x0000b75e0292 base::MessageLoop::DeferOrRunPendingTask()
#14 0x0000b75e1399 base::MessageLoop::DoWork()
#15 0x0000b75e1fbd base::MessagePumpLibevent::Run()
#16 0x0000b75de304 base::MessageLoop::RunHandler()
#17 0x0000b760b5dd base::RunLoop::Run()
#18 0x0000b763bc61 base::Thread::ThreadMain()
#19 0x0000b7635cdf <unknown>
#20 0x0000b770c295 start_thread
#21 0x0000afced05e clone
  gs: 00000033  fs: 00000000  es: 0000007b  ds: 0000007b
 edi: 00000000 esi: 84ee0de8 ebp: 7f8e97f8 esp: 7f8e9780
 ebx: 8361a528 edx: 7f8e9714 ecx: 84ee0d38 eax: 00000000
 trp: 0000000e err: 00000004  ip: 805a848a  cs: 00000073
 efl: 00210202 usp: 7f8e9780  ss: 0000007b
[end of stack trace]
Calling _exit(1). Core file will not be generated.

Does anyone have any ideas on how to resolve this?

Thank you for any assistance provided.

---

### Post by ajgreeny on 2017-07-10
I have not seen this problem but there seem to have been several problems using chromium with hardware acceleration just recently so if you can get it to run long enough to turn that off in **Settings ->Advanced** from the hamburger icon top right you may find it will run properly.

Using a new profile may help as well but that will lose all the settings you've chosen.

Try starting chromium without any extensions with command ```
chromium-browser --disable-extensions
``` and then disable hardware acceleration in Settings and finally close and restart chromium normally to see if that has solved the problem.
You can also try starting chromium with command ```
chromium-browser --disable-gpu
``` which will disable hardware acceleration for that session only, and then turn it off in Settings where it will still be shown as enabled.

Also have a look at the bug at [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1702407](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1702407) posts 30 onwards where a patched version of chromium from a PPA seems to have worked for users; maybe it will help you also.

---

### Post by ian1971 on 2017-07-10
Thanks for the response, disabling hardware acceleration and then installing the patched version of Chromium has worked for me. 

Thank you.

---

### Post by mörgæs on 2017-07-10
Good, please mark the thread 'solved'.

---

