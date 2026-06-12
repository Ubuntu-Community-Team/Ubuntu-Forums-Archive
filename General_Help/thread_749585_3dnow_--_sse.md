---
title: "3dnow -- sse"
date: 2008-04-08
forum: General Help
---

### Post by Ampi on 2008-04-08
I am trying to install MATLAB, but when running *./install* i get the following message

[I]Error: Your computer processor is missing the SSE2 instructions that
       are required for MATLAB to run correctly.
       For system requirements consult [http://www.mathworks.com](http://www.mathworks.com) ...[/I]

The system requierements are okay, I have a 2.6.x kernel.

But the SSE2 is a big problem because I have an AMD. Any idea how I can solve this?

I do have SSE and I have the AMD equivalent 3DNOW and 3DNOWEXT, isn't there anyway to tell the program to use 3DNOW instead or to upgrade mine to a SSE2...?

---

### Post by dcstar on 2008-04-09
> **Ampi said:**
> I am trying to install MATLAB, but when running *./install* i get the following message

[I]Error: Your computer processor is missing the SSE2 instructions that
       are required for MATLAB to run correctly.
       For system requirements consult [http://www.mathworks.com](http://www.mathworks.com) ...[/I]

The system requierements are okay, I have a 2.6.x kernel.

But the SSE2 is a big problem because I have an AMD. Any idea how I can solve this?

I do have SSE and I have the AMD equivalent 3DNOW and 3DNOWEXT, isn't there anyway to tell the program to use 3DNOW instead or to upgrade mine to a SSE2...?

As the website says, your CPU **must** support SSE2, so you need one that does.

---

### Post by jespdj on 2008-04-09
AMD [3DNow!](http://en.wikipedia.org/wiki/3DNow%21) is a different set of instructions than Intel [SSE2]("http://en.wikipedia.org/wiki/SSE2").

If the program really needs the SSE2 instruction set, then it won't work if you have a processor with 3DNow! instructions.

---

