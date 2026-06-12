---
title: "filezilla won´t start"
date: 2008-01-18
forum: General Help
---

### Post by jaskah on 2008-01-18
hello
i made some system updates today and since then i can´t start filezilla.
i get the following information in the terminal

jason@jason-laptop:~$ filezilla
The program 'filezilla' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 203 error_code 11 request_code 146 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

i am on ubuntu 7.10

does anyone know what this could be?
thanks in advance for any help.

---

### Post by Kristopher on 2008-01-18
I have the same issue:(

The program 'filezilla' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 204 error_code 11 request_code 148 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


HP Pavilion dv6238ea Notebook PC | Ubuntu 7.10
2 Gb RAM | 120Gb HD | Nvidia Go 7400 256MB | Intel® Core™ Duo CPU T2250 @ 1.73GHz

---

### Post by hoa3r on 2008-01-18
The same error after this updates:

```
libxfont1 (1:1.3.0-0ubuntu1) to 1:1.3.0-0ubuntu1.1
xserver-xorg-core (2:1.3.0.0.dfsg-12ubuntu8) to 2:1.3.0.0.dfsg-12ubuntu8.1
```

There is stil no bug reporting at launchpad.

---

### Post by fyo on 2008-01-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This is the bug report:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)

The "solution" atm seems to be downgrading.

```
sudo apt-get install xserver-xorg-core=2:1.3.0.0.dfsg-12ubuntu8
```

---

### Post by jaskah on 2008-01-18
yup, this fixed it.
thanks for your help on this!

---

### Post by dethredic on 2008-01-19
I have the same problem but downgrading didn't help

---

