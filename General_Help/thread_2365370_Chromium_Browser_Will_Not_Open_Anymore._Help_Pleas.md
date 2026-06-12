---
title: "Chromium Browser Will Not Open Anymore. Help Please."
date: 2017-07-06
forum: General Help
---

### Post by jooge on 2017-07-06
So I have been having problems with my Chromium browser the past few days. When I try to open it it shows up for a split second in my system tray then dissappears and never actually opens. I tried to run it with a terminal using

```
[COLOR=#111111][FONT=Consolas]chromium-browser[/FONT][/COLOR]
```

and this is the read out I get

```
jooge@xxxxxx:~$ chromium-browserReceived signal 11 SEGV_MAPERR 000000000010
#0 0x7f6b20c25d47 base::debug::StackTrace::StackTrace()
#1 0x7f6b20c26133 <unknown>
#2 0x7f6b20932330 <unknown>
#3 0x7f6b215439f8 <unknown>
#4 0x7f6b21544fb1 <unknown>
#5 0x7f6b21545633 <unknown>
#6 0x7f6b21545bc7 <unknown>
#7 0x7f6b20c9ab91 <unknown>
#8 0x7f6b20c27269 base::debug::TaskAnnotator::RunTask()
#9 0x7f6b20c4e040 base::MessageLoop::RunTask()
#10 0x7f6b20c4f97d base::MessageLoop::DeferOrRunPendingTask()
#11 0x7f6b20c5079d <unknown>
#12 0x7f6b20c51250 base::MessagePumpLibevent::Run()
#13 0x7f6b20c4d422 base::MessageLoop::RunHandler()
#14 0x7f6b20c75df8 base::RunLoop::Run()
#15 0x7f6b20c9fd56 base::Thread::ThreadMain()
#16 0x7f6b20c9aa96 <unknown>
#17 0x7f6b2092a184 start_thread
#18 0x7f6b16d7bffd clone
  r8: 0000000000000000  r9: 0000000000000003 r10: 00007f6a8d29cd18 r11: 00007f6b16e08110
 r12: 00007f6a8d29cfe0 r13: 0000000000000008 r14: 0000000000000008 r15: 00007f6a8d29cfe0
  di: 0000000000000000  si: 00007f6a8d29cfe0  bp: 0000000000000000  bx: 00007f6a8d29d0f0
  dx: 00007f6b178673d8  ax: 00007f6b178673d8  cx: 0000000000000000  sp: 00007f6a8d29cf90
  ip: 00007f6b215439f8 efl: 0000000000010206 cgf: 0000000000000033 erf: 0000000000000004
 trp: 000000000000000e msk: 0000000000000000 cr2: 0000000000000010
[end of stack trace]
Calling _exit(1). Core file will not be generated.
jooge@xxxxxx:~$ chromium-browser

```

Can some please tell me what I can do to fix this?

Thank you :)

---

### Post by jooge on 2017-07-06
[COLOR=#111111][FONT=Ubuntu][FONT=inherit]My question was answered over at askubuntu. Here is what I was told to do which worked like a charm.

```

This issue is caused by a corruption of your config files (~/.config/chromium). I don't think there is an easy way to fix the config but if you move/delete/rename the config directory chromium should restart. You will have lost your config though.
```[/FONT][/FONT][/COLOR]

---

