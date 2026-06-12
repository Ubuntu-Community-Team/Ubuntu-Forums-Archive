---
title: "Mismatched Assembler and Processor Arcitecture causing problems"
date: 2006-10-15
forum: General Help
---

### Post by Belistner on 2006-10-15
Hi,

I am having some problems trying to compile a programs - getting errors like this:

relay16asm.s: Assembler messages:
relay16asm.s:36: Error: suffix or operands invalid for `mov'
relay16asm.s:124: Error: suffix or operands invalid for `mov'
relay16asm.s:213: Error: suffix or operands invalid for `mov'
relay16asm.s:355: Error: suffix or operands invalid for `mov'

After some research I've found that these kinds of errors are quite common when you have 32bit version of linux and a 64bit processor (as I do). It's producing 64bit binaries when it shouldn't be so the assembler falls down.

Is there any workaround known? Searching google and these forums hasn't turned up any solution. ](*,) 

Thanks
Lewis

---

### Post by nereid on 2006-10-15
Isn't there a switch in the assembler to compile the code to 64 bit? Which assembler do you use, nasm?

---

### Post by Belistner on 2006-10-15
> Isn't there a switch in the assembler to compile the code to 64 bit? Which assembler do you use, nasm?

Your dealing with someone barely above a beginner here sorry - so I don't know very much :-)

As far as I know I'm using the bog standard assembler (the one that comes in the binutils package) - but again I don't know and a really don't know how I'd go about passing it a switch.

I had a look in the configure script for the app thats causing the problem and it seemed to be setting "as --32" upon detecting x86_64 but I am COMPLETELY unfamiliar with the syntax iso that's only a guess.

Also shouldn't I be trying to compile the code to 32bit and NOT 64bit? Or do I have it the wrong way round?

Thanks
Lewis

---

### Post by nereid on 2006-10-16
You want to get 64 bit code, after all you've got a 64 bit processor. I don't know about the bog assembler but you can use nasm to get 64 bit code ([->](http://www.tortall.net/projects/yasm/manual/html/nasm-directives.html)).

---

### Post by Belistner on 2006-10-16
> You want to get 64 bit code, after all you've got a 64 bit processor. I don't know about the bog assembler but you can use nasm to get 64 bit code (->).

64 bit processor yes... but only 32bit version of linux. I didn't install the 64bit version of Ubuntu as I had heard bad things about it.

How would I use the nasm instead of the standard one? Do I have to edit the configure script of the thing I'm trying to use?

thanks
Lewis

---

