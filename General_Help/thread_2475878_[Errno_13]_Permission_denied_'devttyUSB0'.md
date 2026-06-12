---
title: "[Errno 13] Permission denied: '/dev/ttyUSB0'"
date: 2022-06-10
forum: General Help
---

### Post by Billisnice on 2022-06-10
Trying to use Chirp to program my amateur radio and I get the error msg:

[Errno 13] could not open port /dev/ttyUSB0: [Errno 13] Permission denied: '/dev/ttyUSB0'

---

### Post by Holger_Gehrke on 2022-06-10
Check that /dev/ttyUSB0 exists and what permissions are set on it with 'ls -l /dev/ttyUSB0'. If it's anything like standard serial lines (/dev/ttyS{0..31}) it belongs to the group dialout. Become a member of that group ('sudo usermod -a -G dialout your_username_here'). You might have to log out and back in for that to take effect.

Holger

---

### Post by Billisnice on 2022-06-10
After

billn@billn-N107:~$ ls -l /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 0 Jun 10 18:09 /dev/ttyUSB0
billn@billn-N107:~$ sudo usermod -a -G dialout billn
[sudo] password for billn: 
billn@billn-N107:~$ 

I get the same [Errno 13] could not open port /dev/ttyUSB0: [Errno 13] Permission denied: '/dev/ttyUSB0'

---

### Post by Billisnice on 2022-06-11
Finally found the fix after Holger's great advice. 

System Setting>Chirp>Turn ON Access USB hardware directly        It was toggled off.

---

