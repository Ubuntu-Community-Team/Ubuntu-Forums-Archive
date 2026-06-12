---
title: "Serial port interrupt conflict suspected"
date: 2021-05-28
forum: General Help
---

### Post by Cool_Javelin on 2021-05-28
Recently, I have been having difficulties writing to my ttyS0 port. It works, but is very slow.

Specifically, when I send data to the port, the program hangs for a long time (several seconds) then, finally, the data gets through.

I ran across a suggestion there may be more then one process looking at IRQ3.

***Is there a way I can list processes attached to a particular interrupt?***

Here is a partial listing of the /dev directory...

crw-rw----  1 root dialout   4,  64 May 28 10:10 ttyS0

BTW, this program (Heyu) has been working for years, and I have not changed anything (as far as I know.)

Thanks, Mark.

---

### Post by HermanAB on 2021-05-28
I would run 'top' and see what is going on with the processes, then loop the serial port back tx to rx and see how it goes in the simplest case.

BTW, my favourite serial port program is 'cutecom', but 'echo', 'cat', 'chat' etc, work if you need to script the communications.

---

### Post by SeijiSensei on 2021-05-29
You could start by looking at /proc/interrupts, though I don't see anything there that ties an interrupt to a running program.

If you can run the Heya program manually, running top in one console window and the program in another can sometimes give you a hint. If there were an interrupt conflict, the program creating the conflict might suddenly jump to the top of the top screen.

---

