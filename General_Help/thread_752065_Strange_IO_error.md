---
title: "Strange I/O error"
date: 2008-04-11
forum: General Help
---

### Post by Larry_web on 2008-04-11
I was testing the buffer size of system call, read(), and found a strange error on Ubuntu 7.10 server. The code is attached.

If the BUFFSIZE is set to  from 128 to 255, the code will produce an error as 

read error: Success

If the if statement (and the perror) is removed, the error disappears.

I have tried the same program on Sun Solaris 5.10 and got the same results.  

The program read from the standard input and write to standard output. Use any large file as the input redirected to standard input and dump the output to null.

How to test:

./a.out < AnySufficientLargeFile >/dev/null

----------------------------------------

#include <stdio.h>
#include <unistd.h>

#define BUFFSIZE        128

int main(void)
{
        char            n;
        char    buf[BUFFSIZE];

        while ((n = read(STDIN_FILENO, buf, BUFFSIZE)) > 0)
                if (write(STDOUT_FILENO, buf, n) != n)
                        perror("write error");

        if (n < 0)
                perror("read error");
        return 0;
}

---

### Post by ColinKing on 2008-04-21
Hi there,

write() is allowed to write less than the number of bytes you've requested to write, so this is not an error.  One needs to check the number of bytes written and then handle the residual bytes that have not yet been written by subsequent write() call(s).

To see if an error has occurred, check if the number of bytes written is < 0, and the error number is in errno (you need to #include <errno.h>).

Not that the write() call blocks until the write is complete, and software interrupts (signals) cause write() to exit prematurely. If so, the errno is -EINTR and one should re-do the write().

Hope this helps.

Colin King

---

