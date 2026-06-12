---
title: "Compiling a .asm file"
date: 2008-02-20
forum: General Help
---

### Post by jrattner on 2008-02-20
Question,

How can I compile a .asm  file in Ubuntu to a .exe that will be suitable to use on my Windows 32 box?

---

### Post by DoctorMO on 2008-02-20
you want to compile an assembler source file into an OLE windows executable file? I assume you want to link the objects too not just compile them?

Look for cross compiling solutions, there may or may not be a way to do it, it may be very expensive.

---

### Post by jrattner on 2008-02-20
Thanks for the info, I guess I'm most likely going to have to retreat to windows for this one.  And yes I wanted to link libraries and such.

---

### Post by Yellow Pasque on 2008-02-20
Have you tried nasm? (available in the repo)

It shouldn't matter what platform you're using, assembly instructions translate directly into machine object code (no "compiling" is needed).

---

### Post by jrattner on 2008-02-20
Nope I haven't tried it...Do you know off hand what the syntax for what I'm trying to do would be by any chance?

---

### Post by jrattner on 2008-02-20
Wait...I understand what your saying, but will it render a .exe in 32bit format which I could pass on to the windows machines?

---

### Post by Yellow Pasque on 2008-02-20
Sorry, I misunderstood. Nevermind what I was saying..

---

### Post by DoctorMO on 2008-02-21
It's not the assembler that's the problem (as he says it's just creating the bytes in the right places) it the linking program which has to be able to link to is different platform and executable format.

---

