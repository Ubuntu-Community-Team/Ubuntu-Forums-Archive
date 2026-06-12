---
title: "Chromium crashes"
date: 2016-10-31
forum: General Help
---

### Post by Axxon95 on 2016-10-31
Chromium from the Ubuntu repos works just fine, but I'm trying to get hardware accelerated video decode on my laptop.
I tested [COLOR=#333333]ppa:saiarcot895/chromium-beta and [/COLOR][COLOR=#333333]ppa:saiarcot895/chromium-dev and everything just crashes. Any and all pages I attempt to load it just goes to the "Aw, Snap!" page. Including chrome://* pages.

Anyone else have this problem or know how to fix it?

[/COLOR]A8-7410 2.2 Quad
4GB DDR3 1600MHz
Radeon R5(512MB, AMD Mullins)
240GB SSD 6Gbps Ubuntu 16.10 x64 UEFI
[COLOR=#333333]VDPAU and VAAPI drivers are installed and working properly.

Please let me know what more I can do to troubleshoot.

In the terminal I get [/COLOR]```
Received signal 4 ILL_ILLOPN 7f92c904ac70#0 0x7f92d5de3b6e base::debug::StackTrace::StackTrace()
#1 0x7f92d5de3f5b <unknown>
#2 0x7f92d5b01670 <unknown>
#3 0x7f92c904ac70 WTF::decommitSystemPages()
#4 0x7f92d04ab510 <unknown>
#5 0x7f92d04abd13 <unknown>
#6 0x7f92d04a96f6 blink::NormalPageArena::allocatePage()
#7 0x7f92d04aa148 blink::NormalPageArena::outOfLineAllocate()
#8 0x7f92d005d8bd blink::ChromeClientImpl::create()
#9 0x7f92d011b60e blink::WebViewImpl::WebViewImpl()
#10 0x7f92d011c4d3 blink::WebViewImpl::create()
#11 0x7f92d3b2c4c5 content::RenderViewImpl::Initialize()
#12 0x7f92d3b2d321 content::RenderViewImpl::Create()
#13 0x7f92d346ce82 content::mojom::RendererStub::Accept()
#14 0x7f92d55b3699 mojo::InterfaceEndpointClient::HandleValidatedMessage()
#15 0x7f92d29ba659 <unknown>
#16 0x7f92d29bbd52 <unknown>
#17 0x7f92d5de55ae base::debug::TaskAnnotator::RunTask()
#18 0x7f92d043d12a blink::scheduler::TaskQueueManager::ProcessTaskFromWorkQueue()
#19 0x7f92d043da3d blink::scheduler::TaskQueueManager::DoWork()
#20 0x7f92d5de55ae base::debug::TaskAnnotator::RunTask()
#21 0x7f92d5e0b4b9 base::MessageLoop::RunTask()
#22 0x7f92d5e0c75d base::MessageLoop::DeferOrRunPendingTask()
#23 0x7f92d5e0d4fd base::MessageLoop::DoWork()
#24 0x7f92d5e0d879 base::MessagePumpDefault::Run()
#25 0x7f92d5e2ef58 base::RunLoop::Run()
#26 0x7f92d3b47fd2 <unknown>
#27 0x7f92d3c38f84 <unknown>
#28 0x7f92d3c394ff <unknown>
#29 0x7f92d3c37751 content::ContentMain()
#30 0x5634dbdcb8cc ChromeMain
#31 0x7f92cc78d3f1 __libc_start_main
#32 0x5634dbdcb77a _start
  r8: 0000000000000000  r9: 0000000000000000 r10: 0000000000000022 r11: 0000000000000206
 r12: 000031e86961c1f8 r13: 0000000000000004 r14: 000031e86961c210 r15: 0000000000000001
  di: 00001436d3141000  si: 000000000001e000  bp: 000031e869670000  bx: 000031e86961c218
  dx: 0000000000000008  ax: ffffffffffffffff  cx: ffffffffffffff60  sp: 00007ffe0b648560
  ip: 00007f92c904ac70 efl: 0000000000010286 cgf: 002b000000000033 erf: 0000000000000000
 trp: 0000000000000006 msk: 0000000000000000 cr2: 0000000000000000

[end of stack trace]
```

---

### Post by bugless2 on 2016-11-01
Same here, but on completely different hardware (old Eee PC netbook). I ended up downgrading to Chromium 53.

---

