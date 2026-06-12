---
title: "serial port and TCP port"
date: 2007-09-27
forum: General Help
---

### Post by aknight_sa on 2007-09-27
good day guys,

how can i clone or copy any information i get from a seiral port on the PC to make it available on a TCP port to be accessed on another PC....

is there a way to just map ports together?

thanks

---

### Post by tszanon on 2007-09-27
I don't know, but I don't think it would be that simple. I think it would be necessary to use a client-server architecture, where the server reads the serial port, stores the data, and waits for the client to connect to it and retrieve the data.

---

### Post by aknight_sa on 2007-09-27
> **tszanon said:**
> I don't know, but I don't think it would be that simple. I think it would be necessary to use a client-server architecture, where the server reads the serial port, stores the data, and waits for the client to connect to it and retrieve the data.

what about mapping a file to a serial port... so whenever i need to make a read data from serial port it just goes to a file and reads whatever is there..

---

### Post by tszanon on 2007-09-27
> **aknight_sa said:**
> what about mapping a file to a serial port... so whenever i need to make a read data from serial port it just goes to a file and reads whatever is there..
That seems to be feasible. I don't know if it would work and I can't test it now, but there is a command (tail, if I recall correctly) that keeps printing on screen every new entry to a file. If you use it to keep printing the output from the serial port and redirect it to a file, I think it would work.

What's the device for the serial port? I'm going to suppose it's /dev/serial0.
```
tail /dev/serial0 >> ~/serial.output.txt
```
If I'm correct, that would be the command line. Hope someone shows up to agree/disagree with me.

---

### Post by sonofusion82 on 2007-09-27
for windows, there are several utilities out there that can provide a remote virtual serial port driver. just google for "remote serial port". something like this  [http://www.fogsoft.com/RS232_to_TCP_Converter.html](http://www.fogsoft.com/RS232_to_TCP_Converter.html)
however, i suppose it won't be hard to write a simple proxy program server/client to do just the same in Linux with python.

---

