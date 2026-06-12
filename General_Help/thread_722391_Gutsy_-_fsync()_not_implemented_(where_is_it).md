---
title: "Gutsy - fsync() not implemented (where is it?)"
date: 2008-03-12
forum: General Help
---

### Post by HARTEngr on 2008-03-12
Hi,

When I use fsync(fd) on an open fd,  it returns -1, and the errno is EINVAL (function not implemented).  Is there a way to get the call included into my Gutsy implementation?
Using 32-bit Ubuntu 7.10 version.
Thanks.

---

### Post by lloyd_b on 2008-03-12
> **HARTEngr said:**
> Hi,

When I use fsync(fd) on an open fd,  it returns -1, and the errno is EINVAL (function not implemented).  Is there a way to get the call included into my Gutsy implementation?
Using 32-bit Ubuntu 7.10 version.
Thanks.

From the "fsync" man page:
```
ERRORS
       EBADF  fd is not a valid file descriptor open for writing.

       EIO    An error occurred during synchronization.

       EROFS, **EINVAL**
              fd  is  bound  to a special file which does not support synchro&#8208;
              nization.

```

Exactly what are you trying to fsync?

Lloyd B.

---

### Post by HARTEngr on 2008-03-12
> **lloyd_b said:**
> From the "fsync" man page:
```
ERRORS
       EBADF  fd is not a valid file descriptor open for writing.

       EIO    An error occurred during synchronization.

       EROFS, **EINVAL**
              fd  is  bound  to a special file which does not support synchro&#8208;
              nization.

```

Exactly what are you trying to fsync?

Lloyd B.
I am writing to a serial port and need to deassert the RTS modem line as soon as the last byte is transmitted. I am currenlty using "write(fd, buffer, buffsize)" function call to transmit and giving some delay to keep RTS asserted before looking for a response. I need to control that delay more precisely as I seem to be losing some response bytes even though my read process is pending on the carrier detect line and I believe I read as soon as CD is asserted.
Thanks.

---

### Post by lloyd_b on 2008-03-12
> **HARTEngr said:**
> I am writing to a serial port and need to deassert the RTS modem line as soon as the last byte is transmitted. I am currenlty using "write(fd, buffer, buffsize)" function call to transmit and giving some delay to keep RTS asserted before looking for a response. I need to control that delay more precisely as I seem to be losing some response bytes even though my read process is pending on the carrier detect line and I believe I read as soon as CD is asserted.
Thanks.

Question: Are you opening the serial port with the O_DIRECT flag?  This *should* make the fsync() call unnecessary (but I'm not sure of the other implications - it's been many years since I did serial port programming under *nix).

Lloyd B.

---

### Post by HARTEngr on 2008-03-12
> **lloyd_b said:**
> Question: Are you opening the serial port with the O_DIRECT flag?  This *should* make the fsync() call unnecessary (but I'm not sure of the other implications - it's been many years since I did serial port programming under *nix).

Lloyd B.
I'm opening the serial port with (O_RDWR | O_NOCTTY | O_NONBLOCK). The target device to which I'm sending data on the serial port seems to start responding as soon as it gets what it needs from me/sender . So I was trying to use fsync() to switch the modem line to receive as soon as my last transmit byte is out.
Thanks.

---

