---
title: "I2C on my motherboard?"
date: 2023-07-18
forum: General Help
---

### Post by josephchrzempiec on 2023-07-18
Hello everyone. I use microcontrollers for a lot of stuff Mostly arduino micro processors. I notice on a server motherboard I have from the manual it has i2c on it. Is it possible to connect to that and read some information from it? I normally go through usb and run a python script I found online to connect to an arduino board to be able to read the system information. Made me really curious if it is possible. A friend of mine gave me this server which I was surprised it has a very cool emdedded mothboard eypc 4 core 8 thread. He has no use for it as he has got a 32 core eypc server and ask If i want it and I can not turn down a free server. I looked up the manual to see if what memory I need and how to connect the power supply it takes a 8pin eps connection only 12v. Here is a link to the board I have.

[https://www.supermicro.com/en/products/motherboard/x11sdv-4c-tln2f](https://www.supermicro.com/en/products/motherboard/x11sdv-4c-tln2f) and this is the manual for the board [https://www.supermicro.com/manuals/motherboard/D/MNL-2019.pdf](https://www.supermicro.com/manuals/motherboard/D/MNL-2019.pdf) 

Joseph

---

### Post by Holger_Gehrke on 2023-07-18
If you read that manual carefully, you'll find that there is a System Management Bus used for communication with various temperature sensors, fans and the PSU which is an I²C bus. There is a connector for additional sensors, but I'd be very careful if I were to try to put my own stuff on that bus; an address collision would probably not be fun.

Holger

---

### Post by josephchrzempiec on 2023-07-22
> **Holger_Gehrke said:**
> If you read that manual carefully, you'll find that there is a System Management Bus used for communication with various temperature sensors, fans and the PSU which is an I²C bus. There is a connector for additional sensors, but I'd be very careful if I were to try to put my own stuff on that bus; an address collision would probably not be fun.

Holger


Thank you yes I'm worried about that part for a address collision.

---

