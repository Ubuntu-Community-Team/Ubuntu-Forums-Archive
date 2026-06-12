---
title: "Intel vs AMD Integrated Graphics for a Workstation PC"
date: 2012-11-11
forum: General Help
---

### Post by Sobari on 2012-11-11
I've been wanting to build a PC from scratch specifically for basic video capture/editing and general internet usage, and am trying to decide what CPU to purchase. As of now, I've mostly looking at the AMD A10 APUs and Intel Core i3 CPUs, since their pricing is very similar, and I'd like the keep the cost of the build down as much as possible, since this is more of a hobby build and not an actual profession.

I'm still a bit of a Linux newbie, so I'm not familiar with the state of GPGPU on Linux. I don't know if there are even applications that make use of it, or if the video drivers for either of these two solutions supports it. If not, I guess it comes down to which would offer better performance in a multithreaded environment. Does anyone have any advice as to what would be the best choice here? Thanks.

---

### Post by pqwoerituytrueiwoq on 2012-11-11
AMD's APU will obliterate any Intel GPU
benchmarks:
[http://www.hardwaresecrets.com/article/A10-5800K-vs-Core-i3-3220-CPU-Review/1646/4](http://www.hardwaresecrets.com/article/A10-5800K-vs-Core-i3-3220-CPU-Review/1646/4)

Intel will give you OpenGl 3 and AMD will give you 4.X

i know with intel there are no gpu driver headaches on linux, it will just work

---

### Post by Sobari on 2012-11-11
AMD is certainly an appealing choice since they offer their own proprietary drivers as an option, though I'd have to research the current state of the fglrx drivers to be sure. Intel's Haswell architecture is also around the corner, which might change the game up a fair bit, so it's a pretty complicated affair.

I guess my only question now is if anyone knows of any video editing apps on Linux that support OpenCL hardware acceleration. It's not a necessity, but it'd be nice to use the integrated graphics to accelerate some tasks. I tried researching this myself, but I've always come up empty handed. I'm not sure if it's because it's not widely supported on Linux yet, or if it's just not a typically listed feature.

---

### Post by gordintoronto on 2012-11-11
What kind of video capture?

I have an AMD CPU with a cheap Nvidia video card (9400 GT), and I use Cinelerra for video editing. Works great! (See [http://www.g-raffa.eu/Cinelerra/HOWTO/](http://www.g-raffa.eu/Cinelerra/HOWTO/) for lots of great information, plus there are many tutorials on Youtube.)

---

