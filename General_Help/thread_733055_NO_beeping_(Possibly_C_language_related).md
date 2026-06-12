---
title: "NO beeping (Possibly C language related)"
date: 2008-03-23
forum: General Help
---

### Post by Crushyerbones on 2008-03-23
Hi, I'm a college student who's had quite a bit of problems during one my classes: Basicaly our main objective is to use the internal speakers to produce certain sounds.

After running into a bit of problems I've tried using  echo -e '\a' on the terminal but it doesn't seem to do anything. Could it be my laptop doesn't have an internal speaker?

Also, the following program gives me a segfault for some reason. Shouldn't it enable the internal speakers?
This is what I'm using right now:

```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <sys/io.h>
#include <unistd.h>



void set_freq(unsigned int desired_freq){
	iopl(2);
	outb(0x43,0xB6);
	unsigned int real_freq;
	real_freq = 1193180UL / desired_freq;
	
	outb(0x42,real_freq);
	outb(0x42,real_freq>>8);

	return;
}
    

void sound_on(){
	iopl(3);
	unsigned char anterior;
	anterior=inb(0x61);
	outb(0x61, anterior | 0x11 );

	return;
}

void sound_off(){
	iopl(0x61);
	unsigned char anterior;
	anterior=inb(0x61);
	outb(0x61, anterior & 0x00 );

	return;
}
int main(){
sound_on();
set_freq(12222);
	
	
return 1;}

```

---

### Post by Crushyerbones on 2008-03-23
Anyone? :S Guess I'll just move back to XP

---

### Post by nvteighen on 2008-03-23
> **Crushyerbones said:**
> Anyone? :S Guess I'll just move back to XP
Ehm... not quite a C programmer, but maybe this helps you.

I've compiled your code using the -g flag and gdb shows segfault on line 48

```

Program received signal SIGSEGV, Segmentation fault.
0x08048447 in inb (port=97) at /usr/include/sys/io.h:48
48        __asm__ __volatile__ ("inb %w1,%0":"=a" (_v):"Nd" (port));

```

---

### Post by Crushyerbones on 2008-03-23
I already know it crashes on that line. And it's not actually my program, it's sys/io.h's fault :P I've been thinking I could have been sending it the wrong parameters but I just can't figure out what's wrong :(

---

