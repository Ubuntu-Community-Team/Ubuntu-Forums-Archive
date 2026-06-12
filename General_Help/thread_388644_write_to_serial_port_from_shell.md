---
title: "write to serial port from shell"
date: 2007-03-19
forum: General Help
---

### Post by vtec on 2007-03-19
Is it possible to write to a serial port located at /dev/ttyUSB0 (serial over usb) with the command:

'echo "Some message to send" > /dev/ttyUSB0'

I can see data by using 'cat /dev/ttyUSB0'

---

### Post by Co.Sinecure on 2007-03-19
I don't know about over the command line, but you can use C to do it:


```
/*
 *  example.c: very simple example of port I/O
 *
 *	Compile with `gcc -O2 -o example example.c',
 *	and run as root with `./example'.
 */

#include <stdio.h>
#include <unistd.h>
#include <sys/io.h>

#define BASEPORT 0x378 /* lp1 */

int main()
{
	int count;
	
        /* Get access to the ports */
        if (ioperm(BASEPORT, 3, 1)) {perror("ioperm"); return 0;}

        /* Set the data signals (D0-7) of the port to all low (0) */
        outb(0, BASEPORT);

        /* Sleep for a while (100 ms) */
        usleep(100000);

	count = 0;

        while (1)
        {
		printf("Count: %d\n", count);
                outb(count, BASEPORT);
                usleep(1000000);
		count = count + 8;
        }

        /* We don't need the ports anymore */
        if (ioperm(BASEPORT, 3, 0)) {perror("ioperm"); return 0;}

        return 0;
}

/* end of example.c */
```

I would credit the source but I don't remember where I got it :-\   (pun intended!)

---

