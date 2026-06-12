---
title: "Upgrade breaks serial port"
date: 2012-11-08
forum: General Help
---

### Post by spikeynick on 2012-11-08
I have a rather difficult problem.  I have a device that connects to serial port.  I have an older machine running 8.04 which talks just fine to the device.  I tried using the device on 10.04 and 12.04 machines and I can no longer talk to the device.  The exact same c++ code compiled without errors on all three machines. 

Here are the g++ versions on the three machines:

8.04 : 4.2.4
10.04 : 4.4.3
12.04 : 4.6.3

I added print statements for the termios flags.  They are the same across machines:

c_cflags: 2224 
c_iflags: 0 
c_oflags: 0
c_lflags: 0
c_cc: all are 0 except VMIN is 1


dmesg gives the exact same info for ttyS0 on all machines:

$ dmesg | grep ttyS0
[    3.550511] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.978751] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A



On the 10.04 and 12.04 machines I do get some communication.  There is a "heartbeat" that does work.  The computer sends 0x04 and the device responds with 0x04.  This is just used to let the device know the computer is running and vice versa.  However, none of the actual commands from the computer to the device seem to be working.

The heartbeat command is just a single character.
The real commands are all multi character and end with a newline (\n).

Does anybody have any clue what might have changed and what I need to do to get serial communication working on 12.04?


Thanks

P.S. I wasn't sure which forum would be most appropriate for this question, so I'm putting it in General Help.  Please let me know if it should be posted somewhere else

---

### Post by dcstar on 2012-11-09
> **spikeynick said:**
> I have a rather difficult problem.  I have a device that connects to serial port.  I have an older machine running 8.04 which talks just fine to the device.  I tried using the device on 10.04 and 12.04 machines and I can no longer talk to the device.  The exact same c++ code compiled without errors on all three machines. 
.........
Does anybody have any clue what might have changed and what I need to do to get serial communication working on 12.04?


The kernels used in 8.04 are way different from what is used in 10.04 and now.

Since you do have some communication I would guess that the serial TTYs are set up with different default settings in the later systems and you need to dig around and find out what you need to set to get them to the same state as the 8.04 system.

It could be flow control, 8-bit mode or any of the other various settings that can be made on these things:

```
man stty
```

---

### Post by spikeynick on 2012-11-09
stty shows the exact same settings for 8.04 and 12.04:

12.04
```
$ stty -F /dev/ttyS0 -a
speed 9600 baud; rows 0; columns 0; line = 0;
intr = <undef>; quit = <undef>; erase = <undef>; kill = <undef>; eof = <undef>; eol = <undef>; eol2 = <undef>; swtch = <undef>; start = <undef>; stop = <undef>;
susp = <undef>; rprnt = <undef>; werase = <undef>; lnext = <undef>; flush = <undef>; min = 1; time = 0;
-parenb -parodd cs8 -hupcl -cstopb cread clocal -crtscts
-ignbrk -brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr -icrnl -ixon -ixoff -iuclc -ixany -imaxbel -iutf8
-opost -olcuc -ocrnl -onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
-isig -icanon -iexten -echo -echoe -echok -echonl -noflsh -xcase -tostop -echoprt -echoctl -echoke
```

8.04
```
$ stty -F /dev/ttyS0 -a
speed 9600 baud; rows 0; columns 0; line = 0;
intr = <undef>; quit = <undef>; erase = <undef>; kill = <undef>; eof = <undef>; eol = <undef>; eol2 = <undef>; swtch = <undef>; start = <undef>; stop = <undef>;
susp = <undef>; rprnt = <undef>; werase = <undef>; lnext = <undef>; flush = <undef>; min = 1; time = 0;
-parenb -parodd cs8 -hupcl -cstopb cread clocal -crtscts
-ignbrk -brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr -icrnl -ixon -ixoff -iuclc -ixany -imaxbel -iutf8
-opost -olcuc -ocrnl -onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
-isig -icanon -iexten -echo -echoe -echok -echonl -noflsh -xcase -tostop -echoprt -echoctl -echoke
```

All of the settings displayed by stty appear to be also handled by the termios struct.  Like I mentioned before I have verified at runtime that the termios struct is exactly the same on the different machines.  

for completeness sake here is the code that sets termios:
```

    newtio.c_iflag &= ~(IGNBRK | BRKINT | PARMRK | ISTRIP | INLCR | IGNCR | ICRNL | IXON);
    newtio.c_oflag &= ~OPOST;
    newtio.c_lflag &= ~(ECHO | ECHONL | ICANON | ISIG | IEXTEN);
    newtio.c_cflag &= ~(CSIZE);
    

    //turn off parity bit and input parity checking
    newtio.c_cflag &= ~(PARENB | INPCK);
    
    newtio.c_cflag |= CS8;
    
    newtio.c_iflag &= ~(IXOFF | IXON);
    newtio.c_cflag &= ~(HUPCL | CSTOPB);
    newtio.c_cflag |= (CLOCAL | CREAD);

    
    //disable flow control
    newtio.c_cflag &= ~CRTSCTS;

    // set input mode (non-canonical, no echo,...)
    newtio.c_lflag = 0;
    newtio.c_cc[VTIME] = 0; // min time between chars (*.1sec)
    newtio.c_cc[VMIN] = 1; // min number of chars for read
    
    int posix_baud = B9600;
    
    cfsetispeed(&newtio, posix_baud);
    cfsetospeed(&newtio, posix_baud);
    tcflush(fd, TCIFLUSH);
    tcsetattr(fd, TCSANOW, &newtio);

```

So it seems to me that there is either some setting that is not controlled by termios or stty that I need to change, or there is something in kernel that changed the details on how one of these settings is implemented.  I'm not really sure where to start looking for either of these.


One other thing.  Just for a sanity check we scrounged up an old serial modem with an auto dialer and we were able to use cu to send and receive data with the auto dialer, so the serial port does work.

---

### Post by ummelum on 2012-12-03
i'm currently facing the same problem:

[http://ubuntuforums.org/showthread.php?t=2089911](http://ubuntuforums.org/showthread.php?t=2089911)

---

### Post by ummelum on 2012-12-06
> **dcstar said:**
> The kernels used in 8.04 are way different from what is used in 10.04 and now.

Since you do have some communication I would guess that the serial TTYs are set up with different default settings in the later systems and you need to dig around and find out what you need to set to get them to the same state as the 8.04 system.

It could be flow control, 8-bit mode or any of the other various settings that can be made on these things:

```
man stty
```
i just tried with every possible combination, to rule this out. and it isn't making a difference...

***can someone clue me in why this isn't working as it should? i find it hard to believe i'm the only ubuntu-user that needs a working serial port.***

---

### Post by RogerDavis on 2012-12-07
Me too, same situation.

**_[COLOR="Red"]H E  L    P !!![/COLOR]_**

---

### Post by ummelum on 2012-12-07
silent bump, and link to the launchpad bug:
[https://bugs.launchpad.net/ubuntu/+bug/1087519](https://bugs.launchpad.net/ubuntu/+bug/1087519)

---

