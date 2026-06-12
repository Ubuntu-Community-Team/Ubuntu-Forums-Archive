---
title: "Profile-Guided Optimization (PGO) and LLVM BOLT usage expansion in Ubuntu packages"
date: 2023-11-12
forum: General Help
---

### Post by zamazan4ik on 2023-11-12
Hi!

With this topic I want to start a discussion about using two optimization techniques for Ubuntu packages: Profile-Guided Optimization (PGO) and Post Link Optimization (PLO).

**Profile-Guided Optimization (PGO)**

Profile-Guided Optimization is a compiler optimization technique where runtime execution profile of your program is used on the compilation phase to improve inline decisions, hot/cold code split, and other compiler optimizations. Starting with PGO you can start even with Wiki: [https://en.wikipedia.org/wiki/Profile-guided_optimization](https://en.wikipedia.org/wiki/Profile-guided_optimization) .

I believe PGO is already enabled for some Ubuntu. Can anyone point me out - in which Ubuntu packages PGO is already enabled?

According to my tests at [https://github.com/zamazan4ik/awesome-pgo#pgo-showcases](https://github.com/zamazan4ik/awesome-pgo#pgo-showcases) I think we can try to enable PGO for a much bigger amout of Ubuntu software. What do you think about it? How can we do it?

**Post-Link Optimization (PLO)**

Post-Link Optimization is an optimization technique that tries to reduce I-cache misses in programs via binary code reordering for better CPU cache utilization. Right now there are two main tools in this area: LLVM BOLT and Google Propeller.

According to the Facebook Research Paper ([https://research.facebook.com/publications/bolt-a-practical-binary-optimizer-for-data-centers-and-beyond/](https://research.facebook.com/publications/bolt-a-practical-binary-optimizer-for-data-centers-and-beyond/)), LLVM BOLT ([https://github.com/llvm/llvm-project/blob/main/bolt/README.md](https://github.com/llvm/llvm-project/blob/main/bolt/README.md)) helps with achieving better performance for various packages like compilers and interpreters. I think it would be a good idea to enable LLVM BOLT for some packages to deliver faster binaries for users (since Propeller is a less stable solution IMO).


Here I got some examples of how LLVM BOLT is already integrated into other projects:
* Rustc: [https://github.com/rust-lang/rust/pull/116352](https://github.com/rust-lang/rust/pull/116352)
* CPython: [https://github.com/python/cpython/pull/95908](https://github.com/python/cpython/pull/95908)
* Pyston:
  - [https://github.com/pyston/pyston#building](https://github.com/pyston/pyston#building)
  - [https://github.com/pyston/pyston/blob/pyston_main/Makefile#L200](https://github.com/pyston/pyston/blob/pyston_main/Makefile#L200)
* Clang: [https://github.com/llvm/llvm-project/blob/main/clang/cmake/caches/BOLT.cmake](https://github.com/llvm/llvm-project/blob/main/clang/cmake/caches/BOLT.cmake)

So at least for the projects above LLVM BOLT effects are tested and some preparations are already done in the upstream projects. In this case, it should be easier to enable BOLT for these packages.

For some projects right now there is ongoing work on integrating LLVM BOLT into the build scripts:
* Chromium: [https://bugs.chromium.org/p/chromium/issues/detail?id=1163978](https://bugs.chromium.org/p/chromium/issues/detail?id=1163978)
* Firefox: [https://bugzilla.mozilla.org/show_bug.cgi?id=1789087](https://bugzilla.mozilla.org/show_bug.cgi?id=1789087)
  - The same for Propeller (a LLVM BOLT alternative): [https://bugzilla.mozilla.org/show_bug.cgi?id=1509314](https://bugzilla.mozilla.org/show_bug.cgi?id=1509314)
* NodeJS: [https://github.com/nodejs/node/issues/50379](https://github.com/nodejs/node/issues/50379)
* LDC: [https://github.com/ldc-developers/ldc/issues/4228](https://github.com/ldc-developers/ldc/issues/4228)
* GCC: [https://gcc.gnu.org/bugzilla/show_bug.cgi?id=112492](https://gcc.gnu.org/bugzilla/show_bug.cgi?id=112492)


More about LLVM BOLT performance results for other projects can be found in:
* Rustc:
  - [https://github.com/rust-lang/rust/pull/116352](https://github.com/rust-lang/rust/pull/116352)
  - [https://www.reddit.com/r/rust/comments/y4w2kr/llvm_used_by_rustc_is_now_optimized_with_bolt_on/](https://www.reddit.com/r/rust/comments/y4w2kr/llvm_used_by_rustc_is_now_optimized_with_bolt_on/)
* CPython: [https://github.com/python/cpython/pull/95908](https://github.com/python/cpython/pull/95908)
* YDB: [https://github.com/ydb-platform/ydb/issues/140](https://github.com/ydb-platform/ydb/issues/140)
* Clang:
  - [Slides]([https://llvm.org/devmtg/2022-11/slides/Lightning15-OptimizingClangWithBOLTUsingCMake.pdf](https://llvm.org/devmtg/2022-11/slides/Lightning15-OptimizingClangWithBOLTUsingCMake.pdf))
  - [Results on building Clang]([https://github.com/ptr1337/llvm-bolt-scripts/blob/master/results.md](https://github.com/ptr1337/llvm-bolt-scripts/blob/master/results.md))
  - [Linaro results]([https://android-review.linaro.org/plugins/gitiles/toolchain/llvm_android/+/f36c64eeddf531b7b1a144c40f61d6c9a78eee7a](https://android-review.linaro.org/plugins/gitiles/toolchain/llvm_android/+/f36c64eeddf531b7b1a144c40f61d6c9a78eee7a))
  - [on AMD 7950X3D]([https://github.com/llvm/llvm-project/issues/65010#issuecomment-1701255347](https://github.com/llvm/llvm-project/issues/65010#issuecomment-1701255347))
* LDC: [https://github.com/ldc-developers/ldc/issues/4228#issuecomment-1334499428](https://github.com/ldc-developers/ldc/issues/4228#issuecomment-1334499428)
* NodeJS: [https://aaupov.github.io/blog/2020/10/08/bolt-nodejs](https://aaupov.github.io/blog/2020/10/08/bolt-nodejs)
* Chromium: [https://aaupov.github.io/blog/2022/11/12/bolt-chromium](https://aaupov.github.io/blog/2022/11/12/bolt-chromium)
* MySQL, MongoDB, memcached, Verilator: [https://people.ucsc.edu/~hlitz/papers/ocolos.pdf](https://people.ucsc.edu/~hlitz/papers/ocolos.pdf)

Some distros like ClearLinux are already experimenting with enabling LLVM BOLT for the whole distro: [https://github.com/clearlinux/distribution/issues/2996#issuecomment-1807150916](https://github.com/clearlinux/distribution/issues/2996#issuecomment-1807150916)

If you are interested in it more, you can check many other materials (like many benchmarks, some in-depth analysis, etc.) about PGO here: [https://github.com/zamazan4ik/awesome-pgo](https://github.com/zamazan4ik/awesome-pgo)


I am creating this topic since I want to expand PGO and PLO usage across Ubuntu packages, so the end-users (including me) will get more faster packages by default. If anyone have some thoughts on how can try to expand PGO and PLO usage in Ubuntu build infrastructure - you are welcome to share your thoughts!

---

### Post by MAFoElffen on 2023-11-14
<<This is a discussion, not support. And should probably be better addressed if moved to [Programming Talk]("https://ubuntuforums.org/forumdisplay.php?f=39").>> 

No ill intent or saying anything is wrong with this discussion, but...

An example: You were trying to sell that idea to Alpine Linux: [https://gitlab.alpinelinux.org/alpine/aports/-/issues/15465](https://gitlab.alpinelinux.org/alpine/aports/-/issues/15465)

Then a whole myriad of other forums and groups, each to promote this, and saying that 'they' should all follow this path. I sounds good, but... The fervor of activity implies questions on your own intent on why? What is in it for you? 

I mean it is almost as if you are spamming messages to promote this... But then again, this may just be your passion in something you believe.

No one here is connected with Canonical. We do not have a say in how they optimize their code in package builds. Even my own. I submit it, and they build it. (I am a rare exception here.) We are just volunteer Users "here", who try to support other users who need help.

---

