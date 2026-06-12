---
title: "How to use Emacs with Free Pascal?"
date: 2007-11-06
forum: General Help
---

### Post by AxAeo on 2007-11-06
I installed the Free Pascal Compiler on my computer... and I've had Emacs for quite a while, but never used it. I know how to use the compiler (fpc "filename") and I have a fair amount of knowledge as to how to write Pascal... though up to now my experience has been on Windows with Turbo Pascal.

The IDE doesn't seem to respond to clicks... (though I hear this is a known and reported bug) so using Emacs and the compiler seems to be my only route.

First of all, I don't have a clue how to use Emacs... I'm not even sure what buffers are (though I assume that's basically what it calls files?)

Secondly, I tried to save the basic HelloWorld program into an Emacs buffer...

```
program HelloWorld(output);
begin
  writeln('Hello, World!')
end.
```

I tried "fpc HelloWorld" which returned me an error...

> Error: ppc386 can't be executed, error message: Failed to execute ppc386 : 127

So I'm pretty much clueless at the moment. Can somebody help me out here?

---

